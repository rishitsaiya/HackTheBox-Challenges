### Impossible Password

The main idea finding the flag is that decrypt the functions called after disassembling the binary file.  

#### Step-1:

Unzip the zip with the given password as `hackthebox`

You get this binary file in the zip - `impossible_password.bin`

#### Step-2:
When you change permissions by `chmod +x baby` & run by `./baby`, we observe that binary execution is asking for a string and that can be known by diassembling the code.

#### Step-3:

Open Radar2 by just typing `r2 -A impossible_password.bin` in terminal. 

The following should appear:
```bash
[x] Analyze all flags starting with sym. and entry0 (aa)
[x] Analyze function calls (aac)
[x] Analyze len bytes of instructions for references (aar)
[x] Constructing a function name for fcn.* and sym.func.* functions (aan)
[x] Type matching analysis for all functions (aaft)
[x] Use -AA or aaaa to perform additional experimental analysis.
[0x004006a0]>
```
#### Step-4:

We check the main function by typing the following for any key to bypass for the flag.

`[0x004006a0]> pdf@main`

The following should appear on terminal:
```bash
/ (fcn) main 283
|   main (int argc, char **argv, char **envp);
|           ; var char **local_50h @ rbp-0x50
|           ; var int local_44h @ rbp-0x44
|           ; var int local_40h @ rbp-0x40
|           ; var int local_3fh @ rbp-0x3f
|           ; var int local_3eh @ rbp-0x3e
|           ; var int local_3dh @ rbp-0x3d
|           ; var int local_3ch @ rbp-0x3c
|           ; var int local_3bh @ rbp-0x3b
|           ; var int local_3ah @ rbp-0x3a
|           ; var int local_39h @ rbp-0x39
|           ; var int local_38h @ rbp-0x38
|           ; var int local_37h @ rbp-0x37
|           ; var int local_36h @ rbp-0x36
|           ; var int local_35h @ rbp-0x35
|           ; var int local_34h @ rbp-0x34
|           ; var int local_33h @ rbp-0x33
|           ; var int local_32h @ rbp-0x32
|           ; var int local_31h @ rbp-0x31
|           ; var int local_30h @ rbp-0x30
|           ; var int local_2fh @ rbp-0x2f
|           ; var int local_2eh @ rbp-0x2e
|           ; var int local_2dh @ rbp-0x2d
|           ; var char *s1 @ rbp-0x20
|           ; var unsigned int local_ch @ rbp-0xc
|           ; var char *s2 @ rbp-0x8
|           ; arg int argc @ rdi
|           ; arg char **argv @ rsi
|           ; DATA XREF from entry0 (0x4006bd)
|           0x0040085d      55             push rbp
|           0x0040085e      4889e5         mov rbp, rsp
|           0x00400861      4883ec50       sub rsp, 0x50               ; 'P'
|           0x00400865      897dbc         mov dword [local_44h], edi  ; argc
|           0x00400868      488975b0       mov qword [local_50h], rsi  ; argv
|           0x0040086c      48c745f8700a.  mov qword [s2], str.SuperSeKretKey ; 0x400a70 ; "SuperSeKretKey"
|           0x00400874      c645c041       mov byte [local_40h], 0x41  ; 'A' ; 65
|           0x00400878      c645c15d       mov byte [local_3fh], 0x5d  ; ']' ; 93
|           0x0040087c      c645c24b       mov byte [local_3eh], 0x4b  ; 'K' ; 75
|           0x00400880      c645c372       mov byte [local_3dh], 0x72  ; 'r' ; 114
|           0x00400884      c645c43d       mov byte [local_3ch], 0x3d  ; '=' ; 61
|           0x00400888      c645c539       mov byte [local_3bh], 0x39  ; '9' ; 57
|           0x0040088c      c645c66b       mov byte [local_3ah], 0x6b  ; 'k' ; 107
|           0x00400890      c645c730       mov byte [local_39h], 0x30  ; '0' ; 48
|           0x00400894      c645c83d       mov byte [local_38h], 0x3d  ; '=' ; 61
|           0x00400898      c645c930       mov byte [local_37h], 0x30  ; '0' ; 48
|           0x0040089c      c645ca6f       mov byte [local_36h], 0x6f  ; 'o' ; 111
|           0x004008a0      c645cb30       mov byte [local_35h], 0x30  ; '0' ; 48
|           0x004008a4      c645cc3b       mov byte [local_34h], 0x3b  ; ';' ; 59
|           0x004008a8      c645cd6b       mov byte [local_33h], 0x6b  ; 'k' ; 107
|           0x004008ac      c645ce31       mov byte [local_32h], 0x31  ; '1' ; 49
|           0x004008b0      c645cf3f       mov byte [local_31h], 0x3f  ; '?' ; 63
|           0x004008b4      c645d06b       mov byte [local_30h], 0x6b  ; 'k' ; 107
|           0x004008b8      c645d138       mov byte [local_2fh], 0x38  ; '8' ; 56
|           0x004008bc      c645d231       mov byte [local_2eh], 0x31  ; '1' ; 49
|           0x004008c0      c645d374       mov byte [local_2dh], 0x74  ; 't' ; 116
|           0x004008c4      bf7f0a4000     mov edi, 0x400a7f           ; const char *format
|           0x004008c9      b800000000     mov eax, 0
|           0x004008ce      e82dfdffff     call sym.imp.printf         ; int printf(const char *format)
|           0x004008d3      488d45e0       lea rax, qword [s1]
|           0x004008d7      4889c6         mov rsi, rax
|           0x004008da      bf820a4000     mov edi, str.20s            ; 0x400a82 ; "%20s" ; const char *format
|           0x004008df      b800000000     mov eax, 0
|           0x004008e4      e887fdffff     call sym.imp.__isoc99_scanf ; int scanf(const char *format)
|           0x004008e9      488d45e0       lea rax, qword [s1]
|           0x004008ed      4889c6         mov rsi, rax
|           0x004008f0      bf870a4000     mov edi, str.s              ; 0x400a87 ; "[%s]\n" ; const char *format
|           0x004008f5      b800000000     mov eax, 0
|           0x004008fa      e801fdffff     call sym.imp.printf         ; int printf(const char *format)
|           0x004008ff      488b55f8       mov rdx, qword [s2]
|           0x00400903      488d45e0       lea rax, qword [s1]
|           0x00400907      4889d6         mov rsi, rdx                ; const char *s2
|           0x0040090a      4889c7         mov rdi, rax                ; const char *s1
|           0x0040090d      e81efdffff     call sym.imp.strcmp         ; int strcmp(const char *s1, const char *s2)
|           0x00400912      8945f4         mov dword [local_ch], eax
|           0x00400915      837df400       cmp dword [local_ch], 0
|       ,=< 0x00400919      740a           je 0x400925
|       |   0x0040091b      bf01000000     mov edi, 1                  ; int status
|       |   0x00400920      e85bfdffff     call sym.imp.exit           ; void exit(int status)
|       |   ; CODE XREF from main (0x400919)
|       `-> 0x00400925      bf8d0a4000     mov edi, 0x400a8d           ; const char *format
|           0x0040092a      b800000000     mov eax, 0
|           0x0040092f      e8ccfcffff     call sym.imp.printf         ; int printf(const char *format)
|           0x00400934      488d45e0       lea rax, qword [s1]
|           0x00400938      4889c6         mov rsi, rax
|           0x0040093b      bf820a4000     mov edi, str.20s            ; 0x400a82 ; "%20s" ; const char *format
|           0x00400940      b800000000     mov eax, 0
|           0x00400945      e826fdffff     call sym.imp.__isoc99_scanf ; int scanf(const char *format)
|           0x0040094a      bf14000000     mov edi, 0x14               ; 20
|           0x0040094f      e839feffff     call sub.time_40078d
|           0x00400954      4889c2         mov rdx, rax
|           0x00400957      488d45e0       lea rax, qword [s1]
|           0x0040095b      4889d6         mov rsi, rdx                ; const char *s2
|           0x0040095e      4889c7         mov rdi, rax                ; const char *s1
|           0x00400961      e8cafcffff     call sym.imp.strcmp         ; int strcmp(const char *s1, const char *s2)
|           0x00400966      85c0           test eax, eax
|       ,=< 0x00400968      750c           jne 0x400976
|       |   0x0040096a      488d45c0       lea rax, qword [local_40h]
|       |   0x0040096e      4889c7         mov rdi, rax
|       |   0x00400971      e802000000     call sub.putchar_400978
|       |   ; CODE XREF from main (0x400968)
|       `-> 0x00400976      c9             leave
\           0x00400977      c3             ret
[0x004006a0]> 
```
We observe that after the print instruction of * and scanning the string from the user, it will print ** only if the input string was `SuperSeKretKey`.

#### Step-5:
We get an input of ** where our instruction condition is not true. To make it true and irrespective of any input file, we need to bypass this loop in order to execute the middle 3 instructions/

```bash
|       ,=< 0x00400968      750c           jne 0x400976
|       |   0x0040096a      488d45c0       lea rax, qword [local_40h]
|       |   0x0040096e      4889c7         mov rdi, rax
|       |   0x00400971      e802000000     call sub.putchar_400978
|       |   ; CODE XREF from main (0x400968)
|       `-> 0x00400976      c9             leave
```
For this we just need to send a command of: `[0x004006a0]> oo+` to be able to execute it in write mode.

Press `[0x004006a0]> v` to change the visual mode and then scroll to the required instruction. Then press `i` to insert hex at above instruction and then put 2 knobs by putting `[insert hex]> 9090` and then save and quit by putting `q`.

The instruction should like the following:

```bash
|       ,=< 0x00400968      750c           jne 0x400976
|       |   0x0040096a      90             nop                                 
|       |   0x0040096b      90             nop   
|       |   0x0040096a      488d45c0       lea rax, qword [local_40h]
|       |   0x0040096e      4889c7         mov rdi, rax
|       |   0x00400971      e802000000     call sub.putchar_400978
|       |   ; CODE XREF from main (0x400968)
|       `-> 0x00400976      c9             leave
```

#### Step-6:
Execute the`impossible_password.bin` again and in the 2nd input, you can give anything you wish.

#### Step-7:
The final flag is `HTB{40b949f92b86b18}`


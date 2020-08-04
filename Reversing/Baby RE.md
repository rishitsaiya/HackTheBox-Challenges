### Baby RE

The main idea finding the flag is that analyzing the assembly code.  

#### Step-1:

Unzip the zip with the given password as `hackthebox`

You get this binary file in the zip - `baby`

#### Step-2:
When you change permissions by `chmod +x baby` & run by `./baby`, we observe that binary execution is asking for a key and that can be known by diassembling the code.

#### Step-3:

Open ida64 by just typing `ida64` in terminal. After that open `baby` file in IDA.

We see that key had to be `abcde122313`

#### Step-4:

In Terminal, when we put that key, we directly obtain the flag.

#### Step-5:

The final flag is `HTB{B4BY_R3V_TH4TS_EZ}`
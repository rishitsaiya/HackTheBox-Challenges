### Pusheen Loves Graphs

The main idea finding the flag using ida64 decompiler and using basic techniques of stego.

#### Step-1:

Unzip the zip with the given password as `hackthebox`


You get this image in the zip - `Pusheen`


#### Step-2:

After that we just have to open the binary file in ida64.

#### Step-3:

In IDA, we need to increase the number of nodes that can be done by doing following:

`Options -> General -> Graph -> Maximum no.of nodes`

Increase it by 10 folds.

#### Step-4:

Now, just click on the main function and a graph will appear in left bottom corner which consists of flag.

#### Step-5:

The final flag is `HTB{fUn_w17h_CFGz}`

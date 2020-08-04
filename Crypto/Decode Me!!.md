### Decode Me!!

The main idea finding the flag is multiple encryption used.

#### Step-1:

Unzip the zip with the given password as `hackthebox`

You get this image in the zip - `Decode.txt`

#### Step-2:

The content of the `Decode.txt` is as follows:

```
993gmULBNujjrZCDev3W8kAVaLkXiyHhCL3500188bA=

gAAAAABboRUb0FsuiYBk1tsXRDr6KAzU1xrNSUv7grB-G-dAEeyqj99kUebz466I2VcH5xDa5HEc5KkbgTklQ7tm9JCRPlJtRng1Ns3VEvbrk7B835OINfPnRbc-UIOnnCmW3CgMdMtf5wGLN299AZEzxIvuy71WC5d9xJDchyiORycuzCth95-4nTKphlNQQ2ko3DX72RxWeEjwt3mavnFXqcOCkGxUhJYmFltz_6ND56VGTrXZi_CK5xLODOX4sj1GNwN_CrU3sJ0obTdA2wF5OaDZLbA1GBPfK0PDlC9WxoUf85K0tFXKfqbt3c5YqtqfytNG5gTkbDFM2NjE7BveBf1DP9ca8g==

```
This is clearly Fernet Encryption which is same as the Symmetric Encryption & Decryption.

#### Step-3:

By using the following python script, we decrypt the flag:

```
from cryptography.fernet import Fernet
key = '993gmULBNujjrZCDev3W8kAVaLkXiyHhCL3500188bA='
f = Fernet(key)
token = 'gAAAAABboRUb0FsuiYBk1tsXRDr6KAzU1xrNSUv7grB-G-dAEeyqj99kUebz466I2VcH5xDa5HEc5KkbgTklQ7tm9JCRPlJtRng1Ns3VEvbrk7B835OINfPnRbc-UIOnnCmW3CgMdMtf5wGLN299AZEzxIvuy71WC5d9xJDchyiORycuzCth95-4nTKphlNQQ2ko3DX72RxWeEjwt3mavnFXqcOCkGxUhJYmFltz_6ND56VGTrXZi_CK5xLODOX4sj1GNwN_CrU3sJ0obTdA2wF5OaDZLbA1GBPfK0PDlC9WxoUf85K0tFXKfqbt3c5YqtqfytNG5gTkbDFM2NjE7BveBf1DP9ca8g=='
print{f.decrypt(token)}

```

#### Step-4:

The script will be run simply as `python Symmetric_Decyption.py`

We get this as the output: 

```
set(['RCdgTl45OFs8O3tGMlZVNTRRPythcUw6bVxJNmlYJmYkMEBSeFBfdSldeHFwdW5tM3Fwb2htZmUrTGJnZl9eXSNhYFleV1Z6VFNYUVZVTnJMUVBPTkdrS0QsSEFlKERDPDtfPz5+fTVZOTg3dzUuUjJyMC8oJyZKKikoJyYlfHtBeX53djx6eXhxWTZ0c1VUcG9oLnk='])

```

#### Step-5:

This is clearly a Base64 encryption, so we decode it and we get:

```
D'`N^98[<;{F2VU54Q?+aqL:m\I6iX&f$0@RxP_u)]xqpunm3qpohmfe+Lbgf_^]#a`Y^WVzTSXQVUNrLQPONGkKD,HAe(DC<;_?>~}5Y987w5.R2r0/('&J*)('&%|{Ay~wv<zyxqY6tsUTpoh.y

```

#### Step-6:

This turned out to be a Malbolge Encryption for this we used a tool online as :

<a href="https://zb3.me/malbolge-tools/" target="_blank">Malbolge Tool</a>

Here we paste the above Base64 decrypt code.

#### Step-7:

The final flag is `HTB{U_g0t_th1$}`

### Bank Heist

The main idea finding the flag using simple crypto techniques.

#### Step-1:

Unzip the zip with the given password as `hackthebox`

You get this image in the zip - `bank_heist_message.txt`

#### Step-2:

The content of the `bank_heist_message.txt` is as follows:

```
444333 99966688 277733 7773323444664 84433 22244474433777, 99966688 277733 666552999. 99966688777 777744277733 666333 84433 443344477778 4447777 44466 99966688777 4466688777733. 84433 5533999 8666 84433 55566622255 4447777 22335556669. 4666 8666 727774447777.

47777888 995559888 4555 47777888 44999988 666555997 : 8555444888477744488866888648833369!!

```
This is clearly Multi-Tap encoding.

#### Step-3:

By online decoding the message, we get the following:

```
IIGF YOU ARE READING THE CIPHER YOU ARE OKAY YOUR SHARE OF/ODE/OED THE HEIST GHS/HGS/IRP/IS IN/IMM YOUR HOUSE THE KEY TO THE LOCK GHS/HGS/IRP/IS BELOW GO TO PARIS 

GSV XLWV GL GSV HZU OLXP TLIVGRIVNVMGUFMW 

```

#### Step-4:

The last sentence is the key: `GSV XLWV GL GSV HZU OLXP TLIVGRIVNVMGUFMW !!`

We decrypt it using a atbash cipher. 

We get the following flag:

#### Step-5:

The final flag is `HTB{GORETIREMENTFUND!!}`
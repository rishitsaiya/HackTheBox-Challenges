### Forest

The main idea exploring the image using steghide tool.

#### Step-1:

Unzip the zip with the given password as `hackthebox`


You get this image in the zip - `forest.jpg`


#### Step-2:

After we increase the brightness of the screen, we observe the following text: 

`IsJuS1Af0r3sTbR0`

#### Step-3:

We get the above code which will be used for passphrase when we will use steghide as the tool.


#### Step-4:

When we use the `binwalk forest.jpg`, we observe that there is some other file also. Hence, we use the steghide tool for flag.

#### Step-5:

When we start exploiting the image using steghide, with the command: `steghide extract -sf forest.jpg`

When the passphrase is asked, put this `IsJuS1Af0r3sTbR0`.

An output file is created as `nothinghere.txt`

#### Step-6:

The content of `nothinghere.txt` can be found using `cat nothinghere.txt`

```
Gur sberfg vf n pbzcyrk rpbflfgrz pbafvfgvat znvayl bs gerrf gung ohssre gur rnegu naq fhccbeg n zlevnq bs yvsr sbezf. Gur gerrf uryc perngr n fcrpvny raivebazrag juvpu, va ghea, nssrpgf gur xvaqf bs navznyf naq cynagf gung pna rkvfg va gur sberfg. Gerrf ner na vzcbegnag pbzcbarag bs gur raivebazrag. Gurl pyrna gur nve, pbby vg ba ubg qnlf, pbafreir urng ng avtug, naq npg nf rkpryyrag fbhaq nofbeoref. UGO{NzNm1aTfXvyYmMOe0}

```

#### Step-7:

We observe this is a Ceaser Cipher. And keep increasing the shift by 1.

So we decrpyt the text using shift=13. We observe the decryption as follows:

```
The forest is a complex ecosystem consisting mainly of trees that buffer the earth and support a myriad of life forms. The trees help create a special environment which, in turn, affects the kinds of animals and plants that can exist in the forest. Trees are an important component of the environment. They clean the air, cool it on hot days, conserve heat at night, and act as excellent sound absorbers. HTB{AmAz1nGsKilLzZBr0}

```

#### Step-8:

Finally the flag is :

`HTB{AmAz1nGsKilLzZBr0}`
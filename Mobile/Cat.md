### Cat

  

The main idea finding the flag is that it uses <strong> Mobile Registries</strong>.

  

#### Step-1:

  

Unzip the zip with the given password as `hackthebox`

  

You get this image in the zip - `cat.ab`

  

#### Step-2:

The content of the `cat.ab` is as follows:

<a  href="https://www.youtube.com/watch?v=WXFjJb2Zq7g" target="_blank">Process for extracting out content of cat.ab</a>

#### Step-3:

Go to the path where the `cat.ab` is located and put the following command:

`( printf "\x1f\x8b\x08\x00\x00\x00\x00\x00" ; tail -c +25 cat.ab ) | tar xvz`

#### Step-4:

We get 2 directories extracted named `apps` & `shared`.
  
If we explore shared directory, we get to know, we have images of cat in `shared/0/Pictures/`

#### Step-5:

Explore all images. In `IMAG0004.jpg` you find the flag if you zoom into the writing pad in bottom.

#### Step-6:

The final flag is `HTB{ThisBackupIsUnprotected}`


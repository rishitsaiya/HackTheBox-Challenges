### Keys

The main idea finding the flag using simple crypto techniques.

#### Step-1:

Unzip the zip with the given password as `hackthebox`

You get this image in the zip - `keys.txt`

#### Step-2:

The content of the `keys.txt` is as follows:

```
hBU9lesroX_veFoHz-xUcaz4_ymH-D8p28IP_4rtjq0=
gAAAAABaDDCRPXCPdGDcBKFqEFz9zvnaiLUbWHqxXqScTTYWfZJcz-WhH7rf_fYHo67zGzJAdkrwATuMptY-nJmU-eYG3HKLO9WDLmO27sex1-R85CZEFCU=
```
This is clearly Symmetric Encryption & Decryption encoding.

#### Step-3:

By using the following python script, we decrypt the flag:

```py
from cryptography.fernet import Fernet
key = 'hBU9lesroX_veFoHz-xUcaz4_ymH-D8p28IP_4rtjq0='
f = Fernet(key)
token = 'gAAAAABaDDCRPXCPdGDcBKFqEFz9zvnaiLUbWHqxXqScTTYWfZJcz-WhH7rf_fYHo67zGzJAdkrwATuMptY-nJmU-eYG3HKLO9WDLmO27sex1-R85CZEFCU='
print{f.decrypt(token)}
```

#### Step-4:

The script will be run simply as `python Symmetric_Decyption.py`

We get this as the output: `set(['Flag : HTB{N0t_A_Fl1g!}'])
`
#### Step-5:

The final flag is `HTB{N0t_A_Fl1g!}`

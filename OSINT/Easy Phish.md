### Easy Phish

The main idea is that we must have some idea of the OSINT relating to E-Mails:

Preventing Email Address Spoofing with a 10-Minute Effort. The OSINT are <strong>SPF</strong> & <strong>DMARC</strong>

#### Step-1:
For the SPF domain of a record:

```bash
nslookup -type=txt secure-startup.com
```

We get the following result:

```bash
Server:  dns.google
Address:  8.8.8.8

Non-authoritative answer:
secure-startup.com      text =

        "v=spf1 a mx ?all - HTB{RIP_SPF_Always_2nd"
```

#### Step-2:
For the DMARC domain of a record:
```bash
nslookup -type=txt secure-startup.com
```

We get the following result:

```bash
Server:  dns.google
Address:  8.8.8.8

Non-authoritative answer:
_dmarc.secure-startup.com       text =

        "v=DMARC1;p=none;_F1ddl3_2_DMARC}"
```
#### Step-3:
So finally the flag becomes:

`HTB{RIP_SPF_Always_2nd_F1ddl3_2_DMARC}`

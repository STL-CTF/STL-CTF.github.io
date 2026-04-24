---
title: Printer Shares
date: 2023-03-09 10:00:00 -0400
categories: [Write Ups, MasterCard CTF 2026, General Skills]
tags: [MasterCard CTF, General, SMB]     # TAG names should always be lowercase
---

# Printer Shares

## Hints and Challenge's information: 

1. knowing how SMB protocol works would be helpful!
2. smbclient and smbutil are good tools

## Approach 1

The service on port 53585 runs SMB protocol. 

Use `smbutil view -G //mysterious-sea.picoctf.net:53585` to show the volumes.

Mount the `shares` volume using command `mount_smbfs -N //guest@mysterious-sea.picoctf.net:53585/shares ~/shares`

This shows the flag.txt, read using `cat ~/shares/flag.txt`


## Approach 2

List shares from the server 

`smbclient -L mysterious-sea.picoctf.net -p 53261 `

Connect to the share

`smbclient //mysterious-sea.picoctf.net/shares -p 53261 `

See the files

`ls`

Download share's flag.txt to your machine as flag.txt

`get flag.txt flag.txt`


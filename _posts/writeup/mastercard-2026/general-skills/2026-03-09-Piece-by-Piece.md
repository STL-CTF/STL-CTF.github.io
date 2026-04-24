---
title: Piece by Piece
date: 2023-03-09 10:00:00 -0400
categories: [Write Ups, MasterCard CTF 2026, General Skills]
tags: [MasterCard CTF, General, ssh, bash]     # TAG names should always be lowercase
---

1. Log into the SSH server

`ssh -p port username@server`

2. Read the instructions.txt file. It says:

Hint:

- The flag is split into multiple parts as a zipped file.
- Use Linux commands to combine the parts into one file.
- The zip file is password protected. Use this "supersecret" password to extract the zip file.
- After unzipping, check the extracted text file for the flag.


3. Merge all parts together

`cat part_aa part_ab part_ac part_ad part_ae > full_file.zip`

4. Unzip the file with "supersecret" as password

`unzip full_file.zip `

5. Read the extract flag.txt file

`cat flag.txt`

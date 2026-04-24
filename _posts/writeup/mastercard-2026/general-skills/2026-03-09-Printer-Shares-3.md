---
title: Printer Shares 3
date: 2023-03-09 10:00:00 -0400
categories: [Write Ups, MasterCard CTF 2026, General Skills]
tags: [MasterCard CTF, General, SMB]     # TAG names should always be lowercase
---

Similar with Printer Shares 2

Connect to the server

The script.sh is running and the output is in cron.log

I created a local file `script.sh` and used put to replace the file in the smb server.

First, I run a ls to see the files and directories.

```sh
#!/bin/bash
# this script runs every minutes
ls -lhas /
```

Find a folder /challenge/

```sh
#!/bin/bash
# this script runs every minutes
ls /challenge
```

Found a file "metadata.json", and output it

```sh
#!/bin/bash
# this script runs every minutes
cat /challenge/metadata.json
```

Then, after it ran, I get the cron.log file and read it.

The flag is there:

```json
{"flag":"picoCTF{5mb_pr1nter_5h4re5_r3v3r53_f17d0589}"}
```

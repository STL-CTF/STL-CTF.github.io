---
title: Password-Profiler
date: 2023-03-09 10:00:00 -0400
categories: [Write Ups, MasterCard CTF 2026, General Skills]
tags: [MasterCard CTF, General, cupp]     # TAG names should always be lowercase
---

1. Clone [cupp](https://github.com/Mebus/cupp) as suggested by the comment on `check_password.py`

2. Run it interactively 

`python3 cupp.py -i`

When it asks, add the information from `userinfo.txt`. Skip what is not available and allow special characters, numbers and l33t.

3. Change the output file name to `passwords.txt` as imported by check_password.py

4. Run the check_password.py script

`python3 check_password.py`
---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "4. Ubuntu Server Command"
linktitle: "4. Ubuntu Server Command"
summary:
date: 2021-06-17T10:17:35+07:00
lastmod: 2021-06-17T10:17:35+07:00
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: book  # Do not modify.


weight: 4
---

##**Show ip wan**

> curl https://ipinfo.io/ip ;echo

##**Show Storage**

    df -h
##**Edit SSH**

> **vi /etc/ssh/sshd_config** passwordAuthen -> yes
>
> **services sshd restart**

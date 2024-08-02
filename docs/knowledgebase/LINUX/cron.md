---
title: add cron jobs
date: 2024-08-02
authors: [dbalucas]
description: >
  How do I add cron job under Linux systems
categories:
  - Linux
  - kb-base
tags:
  - cron
  - linux
  - debian
---

# basics prerequisites
Validate existance of cron binary on your system. For debian use:

```bash
#!/bin/bash
if [ ! -f /usr/sbin/cron ]; then
  echo "[INFO]: crond not installed"
  apt-get update
  apt-get install -y --no-install-recommends cron
else
  echo "[INFO]: crond is installed"
fi
```

## How to use crontab command for cron jobs
![unix-logo](../resources/unix-logo.png){aling=left} See all UNIX related articles/faqYou need to use the crontab command to edit/create, install, deinstall or list the cron jobs in Vixie Cron. Each user can have their own crontab file, and though these are files in /var/spool/cron/crontabs, they are not intended to be edited directly. You need to use crontab command for editing or setting up your own cron jobs.

## Show all active cron jobs

In `/etc/crontab` and the files in `/etc/cron.d/` have a username field.

In that file you can do this:

    * * * * * username /path/to/your/script.sh

From root's crontab sudo crontab -e you can use:

    * * * * * su username -c "/path/to/your/script.sh"

Or you can use the user's actual crontab like this:

    sudo crontab -u username -e

# credits
- [cyberciti.biz](https://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/) *2024-08-02 11:11 CEST*
- [stetic.com](https://www.stetic.com/developer/cronjob-linux-tutorial-und-crontab-syntax/) *2024-08-02 11:36 CEST*
- [stackoverflow](https://serverfault.com/a/352837/964817) *2024-08-02 11:36 CEST*

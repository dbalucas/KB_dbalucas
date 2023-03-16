---
title: wal dir full 
description: how to handle backup issue with "canceling statement due to statement timeout"
author: [dbalucas]
date: 2023-03-06
tag: 
    - canceling statement
    - statement timeout
---

## reproduce the issue

Try executing the backup again and check if the issue still persists...

```shell
hostname:~ # /usr/NBPostgreSQLAgent/nbpgsql -o backup
Assuming PostgreSQL installation mode
Failed to execute PostgreSQL query: SELECT pg_stop_backup()
ERROR:  canceling statement due to statement timeout

Failed to execute PostgreSQL query: SELECT pg_stop_backup()
ERROR:  exclusive backup not in progress
```

## understand the issue

Check the file system is fine?

```shell
hostname:~ # df -Ph
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/vgroot            25G   12G    5G  48% /
/dev/mapper/vgdata-lvpghome  5.0G    1G  4.0G  20% /home/postgres
/dev/mapper/vgdata-lvpgwal    20G   20G   84K 100% /srv/postgres/wal
/dev/mapper/vgdata-lvpgdata   45G   29G   17G  64% /srv/postgres/data
hostname:~ #
```
Congrants! You found the nasty guy.
WAL dir full is bad. If you urgently want to fix something:

* Goto the WAL directory
* Check with backup team which WALs are already backed up
* cleanup old WALs with: `pg_archivecleanup /srv/postgres/wal/ xxxxx.xxxxx.backup` (includes the latest backup)

!!!IF YOU'RE NOT 100% SURE WHAT WILL HAPPEN: DRY-RUN this command with `-n` option!!!!

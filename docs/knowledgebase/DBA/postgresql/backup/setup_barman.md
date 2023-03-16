---
title: PG Barman Setup 
date: 2023-02-10
authors: [dbalucas]
description: > 
    Setting up Barman
categories:
  - backup
  - training
tags:
  - barman
---

## Requirements

!!! warning " IMPORTANT "

    As DBAs we're not planning for backups! We're ensuring the recoverability of a system! - *PostgreSQL14 Cookbook

- python3.6 or greater
- postgres11 or greater

## Different implementations to choose

You can chosse to go with different types of backup. Every backup implementation has advantages and disadvanteges. A reliable and proper manner of backing up single node systems is using the **standalone hot physical backup** via `pg_basebackup` and xfs files systems snapshots. 
The second option was requested after implementing PostgreSQL HA and therefore the backup agent was lacking funktionalities regarding handling backups on the second or backup node.

We came up to the idea that we give pgBarman a chance and try the **approach of replicating the WAL files to the backup node**. (It somehow behaves as a standby node.)

The configuration can be found in the public dokumentation of course, due this tool is open source.

## just how I did it

- create a virtual env for barman && install barman and all dependencies (like psycopg2) ***this is only required when you can't install it via yum, apt, zypper, a.s.o.***
- create directory and config files
  - `/etc/barman.d/`
  - `/etc/barman.conf`
  - `/home/barman/barman/barman.conf`

## Backup tools

- [pgBarman](https://pgbarman.org/)
- pgBackRest
- pgboard
- wal-e
- wal-g

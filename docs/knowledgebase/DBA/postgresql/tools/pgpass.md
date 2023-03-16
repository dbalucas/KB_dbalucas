---
title: how .pgpass works
description: 
author: [dbalucas]
categories:
  - postgres
  - config
date: 2023-03-14
tags:
    - pg
---

## Introduction

the .pgpass file is required for authentication with scram-sha-256 for automation purposes.
Here you can store passwords for special use cases (like backup and vacuumdb tools).

## Template

## postgres .pgpass file

``` shell
    #hostname:port:database:username:password
    localhost:5432:*:backupuser:supersecret
    127.0.0.1:5432:*:backupuser:supersecret
    localhost:5432:*:maintenanceuser:supersecret
    127.0.0.1:5432:*:maintenanceuser:supersecret
```

Of course it's not perfect to have this available. From our point of view it's important for usability and administrativ purposes. When the server itself is secured in a well network segment and has limited access to the operating system. File permission must be set with `0600`.

Please bear in mind to maintaine the [pg_hba.conf](./pg_hba_conf.md) accordingly.
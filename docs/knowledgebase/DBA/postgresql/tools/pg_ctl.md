---
title: pg_ctl
description: How to stop a database cluster in different ways
author: [dbalucas]
categories:
  - postgres
  - config
tags:
    - pg
---

`pg_ctl` can be used to stop a database cluster:

| shortcut  | long          | Description                                                                                     |
| --------- | ------------- | ----------------------------------------------------------------------------------------------- |
| -mf       | -m fast       | Fast Mode, proper shutdown (default)                                                            |
| -mi       | -m immediate  | Immediate Mode, without complete shutdown, leads to recovery                                    |
| -ms       | -m smart      | Smart Mode, after all clients have disconnectedn (you can force close the connections manually) |
| -t [secs] | -             | seconds                                                                                         |

Always use the `-D /path/to/datadir/` to specify the cluster's datadir.

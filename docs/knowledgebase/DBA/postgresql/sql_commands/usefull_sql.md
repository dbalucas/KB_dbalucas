---
title: usefull sql commands 
description: 
author: [dbalucas]
---
## Show Configuration

- `sql> show data_directory;`
- [`sql> show [db-parameter];`](../config/postgresql_conf.md)
- `sql> \conninfo;`

## show configuration from directory

- `sql> \d pg_file_settings`
- `sql> \d pg_settings`
It describes the settings which are configured and from which layer of configuration it's comming from. Example: `sql> SELECT * FROM pg_catalog.pg_settings;`

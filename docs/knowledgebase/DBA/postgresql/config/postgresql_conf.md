---
title: postgresql.conf stuff
description: importent pg parameters and how to figure out more about postgres configuration
author: [dbalucas]
date: 2023-02-21
---

## Usefull server configurations in general

Location of the File is $PGDATA/postgresql.conf and postgresql.auto.conf
or use sql command: `show [db-parameter];`

This file contains cluster/instance wide configurations.

### Behavior of postghost:~ # usermod -a -G wheel postgresresql.auto.conf

- this configuration file must not be edited manually!!
- every `alter system set {configuration_parameter}` will be stored there
- as well as `alter database set {configuration_parameter}` (depends on your db connection)
- and of course we can do the same on user or session level: `alter user set {configuration_parameter}` or `alter session set {configuration_parameter}`.
- hierachie of applying the parameters: postgresql.conf (last line counts) > postgresql.auto.conf (last line counts, as well)
- parameters can be removed by `alter system reset {configuration_parameter}` or to remove all: `alter system reset all`

### Promote your configuration to the database cluster

To reload the new configuration please reload via: `systemctl reload postgresql.service` or via sql: `select pg_reload_conf();`.

## Let's get started with the parameters recommendations

| connection parameter           | recommendations                      |
| ------------------------------ | ------------------------------------ |
| listen_address                 | localhost,{appserver}                |
| port                           | 5432 (default)                       |
| max_connections                | 100  (default)                       |
| superuser_reserved_connections | 3 !! important !!                    |
| security + authentication      | recommendations                      |
| password_encryption            | scram-sha-256                        |
| enable_ssl                     | on                                   |
| ssl settings                   | recommendations                      |
| ssl_ca_file                    | specify CA or bundle chain           |
| ssl_cert_file                  | specify location of host certificate |
| ssl_crl_file                   |                                      |
| ssl_key_file                   | location of cert key-file on host    |
| ssl_cipher                     | configure allowed cipher             |
| ssl_dh_params_file             |                                      |

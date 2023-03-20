---
title: vacuum timeout
description: How to vacuum a database and collect statistics
author: [dbalucas]
categories:
  - postgres
  - maintenance
tags:
    - pg
---

We can try to use pg_stat_user_tables to verify the latest time of autovacuum.

``` psql
    SELECT
      schemaname, relname,
      last_autovacuum,
      last_autoanalyze
    FROM pg_stat_user_tables;
```

Establish a connection through psql or pgadmin and execute `SET statement_timeout = 0`; before issuing a VACUUM statement on that connection. A timeout of 0 disables this setting. You can also set a statement timeout value. This configured statement timeout value is in milliseconds. To check the value set for this parameter, use the command: `postgres=# show statement_timeout;`


## credits

https://stackoverflow.com/questions/72555152/postgres-pg-statistic-vacuum-timeout
https://knowledge.broadcom.com/external/article/17969/postgres-vacuum-command-fails-and-gives.html

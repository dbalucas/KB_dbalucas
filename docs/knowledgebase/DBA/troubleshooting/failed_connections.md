---
title: Troubleshooting failed database connections
summary: Troubleshooting failed database connections.
authors: [dbalucas]
date: 2023-02-08
some_url: https://github.com/dbalucas
---

# Troubleshooting failed database connections:

* at first please check that you used the correct parameters!
* check for explicit rejections. `rejects connection for...` You're violating the administrators security policies!
* check of implicit  rejections. `no pg_hba.conf entry for ...` Contact the administrator to explicitly reject or allow this connection.
* next try using `psql` (maybe you're client is badly configured)
* next use `pg_isready`-tool. It creates a minimal connection and has different returncodes:
  * server is ready and accepting connection.
  * not accepting connections due to system procedures (start, stop, recover)
  * connection attempt, but failed
  * no connection attempt was made (client problem or out of memory)
  -> here the database administrator has to step in:
  * check if server is down
  * check if the server is listening for remote / local connections
  * check if db or user exists
  * check the system log
  * check if you have connected to the `MASTER` or `HOT_STANDBY=ON`


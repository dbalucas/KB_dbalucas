---
title: Disaster Recovery issues
summary: Troubleshooting failed database connections.
authors: [dbalucas]
date: 2023-02-08
some_url: https://github.com/dbalucas
tag: 
 - backup
 - recovery
---
## pg_resetwal is a bad choice

Before executing it,take care you have a backup avialable!
This tool will cause data lost, due to it's functionality of cleaning up old WAL's in pg_wal. 
To quote Simon Riggs from his Cookbook: "You don't know for certain that doing this will fix a problem, but once you've done it, going back will be hard."

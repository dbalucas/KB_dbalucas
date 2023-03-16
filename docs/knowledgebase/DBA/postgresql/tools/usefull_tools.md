---
title: dba tools
description: This document list all known tools for administration of postgresql
author: [dbalucas]
categories:
  - postgres
  - config
date: 2023-03-14
tags:
    - pg
---

## Documentation

1. [mkdocs](https://squidfunk.github.io/mkdocs-material/) hosts our general documentation written in markdown
2. [pandoc](https://pandoc.org/installing.html) helps you converting word and other formats to markdown

## Administration

1. [pgAdmin4](https://pgadmin.org) is the database developer and admin interface.
2. pgTune help setting the correct database parameters for system tuning
3. pg_basebackup is a good backup solutions or go with [pgBarman](../backup/setup_barman.md)

## Automation

1. [Ansible](https://github.com/ansible) is a free and open source configuration tool. It's developed by Red Hat and has a proprietary branch as well. 
2. [AWX](https://github.com/ansible/awx) is a free and open source alternative to the Red Hat Ansible tower. 
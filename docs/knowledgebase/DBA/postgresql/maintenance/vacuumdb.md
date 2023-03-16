---
title: db maintenance
description: How to vacuum a database and collect statistics
author: [dbalucas]
categories:
  - postgres
  - maintenance
tags:
    - pg
---

## running vacuum on all databases of a specified group including analyze via ansible1

### pre requisites

is to have an inventory file configured. In this example I created a sub group called **dev**.

### command:

`ansible **dev** -m ansible.builtin.shell -a 'su - postgres -c "vacuumdb --jobs=2 --parallel=2 --all --analyze"' -i ansible/ansible_vault_inventory/hosts.yaml -k -K -b`

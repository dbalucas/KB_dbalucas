---
title: mock env variables pytest
date: 2023-03-20
authors: [dbalucas]
description: >
  discribe mocking environments in pytest
categories:
  - python
  - pytest
---

## how it works

at first you have to 

## sources

https://stackoverflow.com/questions/31582750/python-mock-patch-os-environ-and-return-value

## the code

``` python
    import os
    import sys
    import pytest
    from unittest import mock
    from click.testing import CliRunner

    def mockenv(**envvars):
        return mock.patch.dict(os.environ, envvars)
    
    def check_sap_env():
        click.echo("Checking the Linux environment ...")
        if os.environ.get("SPECIAL_ENVVAR") is None:
            click.echo("Linux environment must be set before running this script.")
            sys.exit(1)
    
    @mockenv(SPECIAL_ENVVAR="/path/to/env")
    def test_get_os_env():
      assert os.getenv("SPECIAL_ENVVAR") is not None
```

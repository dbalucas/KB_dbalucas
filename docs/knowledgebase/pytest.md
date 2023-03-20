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

``` python
    import os
    import sys
    import pytest
    from unittest import mock
    from click.testing import CliRunner

    def mockenv(**envvars):
        return mock.patch.dict(os.environ, envvars)
    
    def check_sap_env():
    click.echo("Checking the SAP IQ 16 environment ...")
    if os.environ.get("IQDIR16") is None:
        click.echo("SAP IQ 16 environment must be set before running this script.")
        sys.exit(1)
    
    @mockenv(IQDIR16="/path/to/env")
    def test_get_os_env():
      assert os.getenv("IQDIR16") is not None
```

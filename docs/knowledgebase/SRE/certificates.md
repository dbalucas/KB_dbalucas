---
title: certificates
date: None likes them until you understand them....
authors: [dbalucas]
description: >
  {{ description }}
categories:
  - knowledge base
  - training
tags:
  - certificates
  - privatkey
  - tls
  - ssl
  - SAN
  - key
  - csr
  - signing request
---

## How to verify if a Private Key Matches a Certificate?

```
  openssl x509 -noout -modulus -in cert.crt | openssl md5
  openssl rsa -noout -modulus -in privkey.txt | openssl md5
```

## How tos....

---
title: kubernetes k8s
date: 2023-02-10
authors: [dbalucas]
description: >
  {{ description }}
categories:
  - {{ category }}
tags:
  - {{ tags }}
---

config.yml:

``` yaml
apiVersion: postgresql.cnpg.io/v1
kind: Cluster
metadata:
name: cluster-example
spec:
instances: 3
storage:
size: 1Gi
```

`kubectl apply -f config.yml`

`kubectl get cluster`

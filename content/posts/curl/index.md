---
title: "Usando Curl como alternativa ao SCP"
date: 2021-07-15T21:50:00+01:00
draft: false
hideLastModified: false
summaryImage: "images/curl-picture.png"
keepImageRatio: true
summary: "Usando Curl como \
Alternativa ao SCP"
tags: ["curl", "linux"]
---

Upload de arquivos

```
$ curl --user username:password -T /path/to/sourcefile sftp://desthost/path/
```

Download de arquivos

```
$ curl --user username:password sftp://desthost/path/filename.txt -o filename.txt
```

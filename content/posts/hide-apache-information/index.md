---
title: "Ocultando versão do Apache"
date: 2021-04-11T14:58:00+01:00
draft: false
hideLastModified: true
summaryImage: "images/apache-version-disclosed.png"
keepImageRatio: true
summary: "Ocultando versão do Apache"
tags: ["centos","apache", "debian"]
---

Edit file /etc/httpd/conf/httpd.conf (CentOS):
{{< newLine >}}
Edit file /etc/apache2/conf-enabled/security.conf (Debian):

```
ServerTokens Prod
ServerSignature Off
```

Restart Apache

(CentOS)
```
#systemctl restart httpd
```
(Debian)
```
#systemctl restart apache2
```

Done.

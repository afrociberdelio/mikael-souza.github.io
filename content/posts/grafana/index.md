---
title: "Grafana com proxy revervo no Apache"
date: 2019-06-17T23:53:00+01:00
draft: false
hideLastModified: true
summaryImage: "images/grafana_apache.jpg"
keepImageRatio: true
summary: "Configurando Grafana \
com proxy revervo no Apache"
tags: ["grafana", "apache"]
---

Create file /etc/apache2/sites-available/grafana.local.conf:

```
<VirtualHost *:80>
        ServerName grafana.local
        ServerAlias www.grafana.local

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        ProxyPreserveHost On
        ProxyRequests Off
        ProxyPass /  http://localhost:3000/  retry=1 acquire=3000 timeout=1800 Keepalive=On
        ProxyPassReverse /  http://localhost:3000/

</VirtualHost>
```



Add in file /etc/grafana/grafana.ini:

```
http_addr = 127.0.0.1
http_port = 3000
root_url = http://grafana.local
```

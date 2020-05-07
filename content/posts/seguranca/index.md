---
title: "Configurando Certificado SSL (HTTPS) em VirtualHost no Apache (Debian)"
date: 2019-06-17T23:53:00+01:00
draft: false
hideLastModified: true
summaryImage: "images/ssl.png"
keepImageRatio: true
summary: "Configurando Certificado SSL (HTTPS) em VirtualHost \
no Debian (Apache)"
tags: ["seguranca", "apache", "debian"]
---

Activate module

```
#a2enmod ssl
```

Restart Apache

```
#systemctl restart apache2
```

Create file /etc/apache2/sites-available/example.com.br.conf:

```
<VirtualHost *:80>
    ServerName example.com.br
    ServerAlias www.example.com.br
	
	ServerAdmin admin@example.com.br
	Redirect permanent / https://example.com.br
</VirtualHost>

<VirtualHost *:443>
    ServerName example.com.br
    ServerAlias www.example.com.br

	SSLEngine on
	SSLCertificateFile <Caminho do arquivo ex: /home/user/certificate.crt>
	SSLCertificateKeyFile <Caminho do arquivo ex: /home/user/private.key>
	SSLCertificateChainFile <Caminho do arquivo ex: /home/user/ca_bundle.crt>
	
	ServerAdmin admin@example.com.br
    DocumentRoot /var/www/html/example.com.br/public_html

	ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Activate Virtualhost

```
#a2dissite example.com.br
```

Restart Apache

```
#systemctl restart apache2
```

Done.

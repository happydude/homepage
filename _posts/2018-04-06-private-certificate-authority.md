---
author: Jason Davis
layout: post
title: Private Certificate Authority openssl cheat sheet
---

Generate a private key for the Certificate Authority
```bash
openssl genrsa -des3 -out myCA.key 2048
```

Generate the root certificate, myCA.crt will be the Trusted Root Certification Authority that you will need to import on client computers.
```bash
openssl req -x509 -new -nodes -key myCA.key -sha256 -days 1825 -out myCA.crt
```

Generate a private key for your site
```bash
openssl genrsa -out www.example.com.key 2048
```

Generate a Certificate Signing Request
```bash
openssl req -new -key www.example.com.key -out www.example.com.csr
```

Create a config file for Subject Alternative Name (SAN) (`www.example.com.ext`)
```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[alt_names]
DNS.1 = www.example.com
```

Sign the certificate request with the CA we created
```bash
openssl x509 -req -in www.example.com.csr -CA myCA.crt -CAkey myCA.key -CAcreateserial -out www.example.com.crt -days 1825 -sha256 -extfile www.example.com.ext
```

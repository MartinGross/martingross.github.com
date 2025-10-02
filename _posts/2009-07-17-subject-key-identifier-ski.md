---

layout: post
title: Subject Key Identifier (SKI)
date: 2009-07-17 15:50:00 +02:00
permalink: /articles/136/
comments: true
categories: 
- Web-Services
---

The [X.509 standard](/article/137/x509-certificate) defines extensions
for Version 3. One of them is the SKI extension.

From the spec:

> "The subject key identifier extension provides a means of identifying
> certificates that contain a particular public key. To facilitate
> certification path construction, this extension MUST\
> appear in all conforming CA certificates."

The authority key identifier of a certificate contains the value of the
subject key identifier of the CA (certificate authority) as a reference
to that CA.

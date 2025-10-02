---

layout: post
title: JRuby und Firewall mit Proxy
date: 2009-02-27 14:19:13 +01:00
permalink: /articles/127/
comments: true
categories: 
- JRuby
- Java
---

Wenn man mit JRuby durch einen authentifizierenden Proxy will, z.B. weil
man ein Gem installieren will, muss man vorher eine Umgebungsvariable
setzen.

Dazu braucht man die URL des Proxies, den Port und den User mit
Passwort. Auf der Kommandozeile macht man das folgendermassen:

set HTTP_PROXY=http://username:proxypassword@proxyname:port

Die Platzhalter sind dazu mit den konkreten Werten zu erstzen.\
Also beispielsweise so:

set HTTP_PROXY=http://fredfeuerstein:wilma@proxy.firma.com:8080

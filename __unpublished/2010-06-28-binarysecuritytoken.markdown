---
layout: post
date: 2010-06-28
permalink: /post/745967446/binarysecuritytoken
published: true
categories:
- ws-security
---
# BinarySecurityToken

![Keys](http://farm1.static.flickr.com/16/23390123_b6caaefc16.jpg)

The WS-Security standard defines the BinarySecurityToken xml element.

To understand what a BinarySecurityToken is we need to understand first what a Security Token is:

A Security Token represents a collection of claims that might include a name, password, identity, key, certificate, group, privilege, and so on.

The BinarySecurityToken element is just a security token that is binary encoded.The xml attribute ValueType defines the type of the token. It can contain for example a X.503 certificate.  

The encoding is described in the xml attribute EncodingType and describes the encoding format of the binary data. E.g. base64

An example:

	<wsse:BinarySecurityToken
	xmlns:wsu=”http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd” 
	EncodingType=”http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary” 
	ValueType=”http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3” 
	wsu:Id=”CertId-10011912”>MIIAv….ctM</wsse:BinarySecurityToken>

Image made by <http://www.flickr.com/people/kk/>
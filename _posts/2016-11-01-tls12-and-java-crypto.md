---
layout: post
title: "TLS 1.2 and Java Cryptography Extension (JCE)"
modified:
categories: 
tags: [TLS 1.2, Java, JCE, cryptography]
image:
  feature:
---

# TLS 1.2 and Java Cryptography Extension (JCE) 

[TLS 1.2](https://en.wikipedia.org/wiki/Transport_Layer_Security#TLS_1.2) needs strong encryption capabilities. TLS 1.2 defines certain cipher suites to be used to enforce strong encryption. A list of the TLS 1.2 cipher suites can be found [at the OpenSSL site](https://www.openssl.org/docs/manmaster/apps/ciphers.html) or [in the RFC 5246 document](https://tools.ietf.org/html/rfc5246#appendix-A.5).

## What is a cipher suite?

A cipher suite is a named combination of cryptographic algorithms. 
The TLS protocols use algorithms from a cipher suite to create keys and encrypt information. A cipher suite specifies one algorithm for each of the following tasks:

- Key exchange
- Bulk encryption
- Message authentication
https://d2mxuefqeaa7sj.cloudfront.net/s_17E99CBD6419C17583FBFDAD1533494D44CAF5895C766F44150583FE8A302E83_1473802480146_Cipher+Suite+Naming.png


Key exchange algorithms protect information required to create shared keys. These algorithms are asymmetric (public key algorithms) and perform well for relatively small amounts of data.

Bulk encryption algorithms encrypt messages exchanged between clients and servers. These algorithms are symmetric and perform well for large amounts of data.

Message authentication algorithms generate message hashes and signatures that ensure the integrity of a message.

## Limitations of standard installation of Java

Due to import regulations in some countries, the standard Oracle JRE provides a default cryptographic jurisdiction policy file that limits the strength of cryptographic algorithms. The Java website lists the [maximum key sizes allowed by this version of the jurisdiction policy](http://docs.oracle.com/javase/7/docs/technotes/guides/security/SunProviders.html#importlimits).

This means, Java’s default cryptographic functionalities have limitations related to the size of keys, e.g. Java by default supports only AES with a 128 Bit key. The restrictions are related to the US law and are supposed to prevent the application from using stronger ciphers.

[OpenJDK seems to have no limitations](http://openjdk.java.net/groups/security/) of the key sizes.

## Stronger encryption 

If stronger algorithms are needed (for example for TLS1.2 using AES with 256-bit keys), the [JCE Unlimited Strength Jurisdiction Policy Files](http://www.oracle.com/technetwork/java/javase/downloads/index.html) must be [downloaded](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) and installed in the JDK/JRE.

The Java Cryptography Extension (JCE) is an officially released extension to the Java Platform and part of [Java Cryptography Architecture](https://en.wikipedia.org/wiki/Java_Cryptography_Architecture).

JCA delivers the most basic cryptographic features. JCE provides various advanced cryptographic operation with longer keys resulting in stronger encryption.

## Installing JCE

You can install the Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files. Download the files and instructions for [Java 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html) or [Java 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html).

1. Locate the `jre\lib\security` directory for the Java instance.
2. For example, this location might be: `C:\Program Files\Java\jre8\lib\security`.
3. Remove the following `.jar` files from this directory: `local_policy.jar` and`US_export_policy.jar`.
4. Replace these two files with the `.jar` files included in the JCE Unlimited Strength Jurisdiction Policy Files download.

There is no way to distribute the files with your program; they must be installed in the JRE directory.

## How to avoid installing “Unlimited Strength” JCE policy files?

To the best of my knowledge, there is **no reliable**** **workaround to install the JCE policy files if you are using an Oracle JDK or JRE. 


1. Some websites mention a [reflection based workaround](http://stackoverflow.com/questions/1179672/how-to-avoid-installing-unlimited-strength-jce-policy-files-when-deploying-an) to enable stronger encryption but this is reported to not work with TLS1.2 ciphers.
2. Using another cryptography library such as [Bouncy Castle](http://www.bouncycastle.org/) won't let you use 256-bit TLS cipher suites, because the [standard TLS libraries call the JCE internally to determine any restrictions.](https://stackoverflow.com/a/22492582)

It might be possible to use [OpenJDK ](http://openjdk.java.net/groups/security/)without installing JCE [if that’s an option for your application](http://stackoverflow.com/a/25848375).



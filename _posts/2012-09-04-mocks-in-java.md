---

layout: post
title: Mocks in Java
date: 2012-09-04 12:26:17 +02:00
permalink: /articles/183/mocks-in-java/
comments: true
categories: 
- software-testing
- Java
---

[Mock objects](http://en.wikipedia.org/wiki/Mock_object) are simulated
objects that mimic the behavior of real objects in controlled ways.

[Mockito](http://code.google.com/p/mockito/) is my favourite mocking
framework for Java for writing mock objects usable by unit tests.

Here is an example:

<script src="https://gist.github.com/3619937.js?file=gistfile1.java">
</script>

But sometimes you need to mock something which Mockito can't handle.

[PowerMock](http://code.google.com/p/powermock/) is an extension to
Mocking frameworks like Mockito. It extends these frameworks to mock
things like static methods or constructors.

The PowerMock website has a good page explaining [how to use PowerMock
with Mockito](http://code.google.com/p/powermock/wiki/MockitoUsage13) .

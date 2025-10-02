---

layout: post
title: Testing web apps with Selenium Page Objects
date: 2012-09-04 17:59:56 +02:00
permalink: /articles/184/testing-web-apps-with-selenium-page-objects/
comments: true
categories: 
- software-testing
- Web
---

During the process of developing a web application, the structure of web
pages is often changed. If you have several
[Selenium](http://code.google.com/p/selenium/) tests that test different
functionalities of one page, you don't want to change all your tests if
the page changes only its layout.

Let's say you have twelve tests which access the page. Now you need to
change the page to display an additional table row. Your selenium test
would probably fail, because the expected data is now at a different
place on the page.

The solution: Use abstractions!

Your tests should not access the page structure itself but use
abstractions of the page. This means you would only need to adapt the
abstraction of the page and the twelve tests wouldn't need any
modification.

[Page objects](http://code.google.com/p/selenium/wiki/PageObjects)
should be the only thing that have a deep knowledge of the structure of
the HTML of a page. Think of the methods on a Page Object as offering
the "services" that a page offers rather than exposing the HTML strucure
of the web page.

From the [Page
objects](http://code.google.com/p/selenium/wiki/PageObjects) page:\
As an example, think of the inbox of any web-based email system. Amongst
the services that it offers are typically the ability to compose a new
email, to choose to read a single email, and to list the subject lines
of the emails in the inbox. How these are implemented shouldn't matter
to the test.

If you are programming in Ruby you might want to use
[page-object](https://github.com/cheezy/page-object) . page-object is a
[simple ruby gem that assists in creating flexible page
objects](http://www.cheezyworld.com/2011/07/29/introducing-page-object-gem/)
for testing browser based applications.

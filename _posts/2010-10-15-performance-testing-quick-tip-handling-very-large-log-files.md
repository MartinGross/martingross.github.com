---

layout: post
title: "Performance Testing: Quick Tip: Handling very large log files"
date: 2010-10-15 15:40:20 +02:00
permalink: /articles/172/performance-testing-quick-tip-handling-very-large-log-files/
comments: true
categories: 
- performance-testing
- Utilities
---

`<a href="http://www.flickr.com/photos/tonyapoole/2952757091/" title="Flex by adventurejournalist, on Flickr">`{=html}`<img src="http://farm4.static.flickr.com/3140/2952757091_b8d500a7a0_m.jpg" width="240" height="160" alt="Flex" />`{=html}`</a>`{=html}

Logfiles tend to grow and grow and grow. The other day I had a log file
about 1.3 GB large.

The relevant logging was only in one part of the file. Handling such a
big file is a nightmare using most editors. I could open it but the
editor would crash as soon as I tried to delete some parts of the file.

What I needed was the part of the file which contains the log entries
for the load test, i.e. split the file into smaller parts - or - even
better, cut the parts off that I would not need for my analysis.

As expected Unix-based operating systems have some built-in tools for
this task:

[split](http://www.oreillynet.com/linux/cmd/cmd.csp?path=s/split) :
Splits a file into equal-sized parts.

or

[csplit](http://www.oreillynet.com/linux/cmd/cmd.csp?path=c/csplit) :
Splits a file into context-based parts.

Examples:

Create a new file named 'output.log.00' . It should contain only the
part of the file input.log beginning with the line that matches the
regular expression '\^17:15:' . I.e. give me everything from 17:15 until
the end of the file:

    csplit -f output.log. input.log '%^17:15:%'

Now create two files out of 'output.log.00': One containing everything
before 18:00 (6pm) and one for the remaining part. I.e. I want a file
named 'log.17.00' which contains all log entries from 17:15 until 18:00
.

    csplit -f log.17. output.log.00 '/^18:/'

Using Windows? I'd recommend to install [cygwin](http://www.cygwin.com/)
which provides split/csplit and many other useful Unix tools. In my
opinion a must-have for every serious software developer working on this
platform.

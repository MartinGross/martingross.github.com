---
layout: post
title: "Run a simple webserver in one line of Ruby"
modified:
categories: 
tags: [ruby, command line]
image:
  feature:
---

Sometimes you just need a very basic ad hoc http static server in your current directory. If Ruby is already installed you just need to run the following on the commandline:

```
ruby -rwebrick -e'WEBrick::HTTPServer.new(Port: 8000, DocumentRoot: Dir.pwd).start'
```
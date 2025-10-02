---

layout: post
title: git with github through a firewall
date: 2010-07-21 13:15:58 +02:00
permalink: /articles/168/accessing-github-through-a-firewall/
comments: true
categories: 
- git
- Software-Entwicklung
---

Git supports a new, much more efficient HTTP based transport as of
version 1.6.6.

With the git's new [Smart HTTP
support](http://progit.org/2010/03/04/smart-http.html) it is possible to
access [github](http://github.com) even without ssh access. SSH access
is typically not possible from behind a corporate firewall. Though, most
environments allow http through a (authenticating) proxy. With http
support it is possible under these circumstances to access github, you
can now push over that protocol and clone private repositories as well.

To clone one of your repositories having push access as well, you can
clone this way:

    git clone https://username@github.com/username/project.git

Be sure to use SSL (https) as git asks for your github password and
sends your password unencrypted over the wire.

For a public repository you can use:\
`git clone http://github.com/username/project.git`

You need Git client version 1.6.6 or greater. For windows you can
download it here:\
<http://code.google.com/p/msysgit/downloads/list>

After the install be sure to set the path environment variable to the
directory C:\\Program Files\\Git\\cmd\\ or whereever git is installed on
your computer.

Set both (https and http) proxy environment variables:

    HTTPS_PROXY=http://user:password@proxy.firma.de:port
    HTTP_PROXY=http://user:password@proxy.firma.de:port

I got the following error message:

    error: error setting certificate verify locations:
      CAfile: /bin/curl-ca-bundle.crt
      CApath: none
     while accessing https://mgross@github.com/mgross/gmailr.git/info/refs

Which was solved by setting git config:

`git config --global http.sslverify false`

To push your changes to github use the following command:\
`git push origin master`

More about 'Working with Remotes' can be found at [Pro
Git](http://progit.org/book/ch2-5.html)

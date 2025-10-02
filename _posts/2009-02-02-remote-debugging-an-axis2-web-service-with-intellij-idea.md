---

layout: post
title: Remote Debugging an Axis2 Web service with Intellij IDEA
date: 2009-02-02 16:50:00 +01:00
permalink: /articles/125/
comments: true
categories: 
- Web-Services
- Java
---

At [wso2.org](https://wso2.org/library/3851) Eran Chinthaka described
how to debug a web service remotely.

I am summarizing the most important things assuming that you have
already Axis and your web service deployed to Apache Tomcat. The web
service needs to be also available in IDEA as Java source ( of course).

The next steps are:

1.  Start Tomcat with debugging options
2.  Add a new Run/Debug Configuration in Intellij IDEA
3.  Choose the configuration and start debug

**Start Tomcat with debugging options**

Add the following JVM parameters to your tomcat start script:

``` {.js:nocontrols name="code"}
-Xdebug
-Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=5005
```

Now you are ready to start. Start tomcat and it will listen on port 5005
for your debugger.

**Add a new Run/Debug Configuration in Intellij IDEA**

1.  Goto "Run" menu and select "Edit Configurations".
2.  Click on "+" and select "Remote" from the menu. Just keep the
    default configuration there with Port 5005 and localhost, if Tomcat
    is running on the same machine as IDEA. Otherwise enter another
    host.
3.  Give a meaningful name in the 'name' text box like 'Local Tomcat
    Debug' and press "OK". You should now be able to see your new
    configuration, under the runnable items menu.

As Eran Chinthaka describes:

> "You are now all set to receive debug messages from Tomcat. Mark
> debugging points at proper locations you want to debug and send a SOAP
> message to your Web service. You should now be able to see your debug
> points highlighted when the execution hit those marked locations."

**Choose the configuration and start debug**

Choose your configuration from the drop down menu in IDEA button bar.
Click on the debug button, to start connecting to Tomcat. Now you are
attached to Tomcat and can send requests to your web service.

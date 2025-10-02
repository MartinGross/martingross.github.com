---

layout: post
title: Using Maven to build Axis 2 projects
date: 2008-02-11 14:40:00 +01:00
permalink: /articles/114/
comments: true
categories: 
- Java
- Software-Entwicklung
---

Axis 2 provides three Maven plug-ins to build projects. These plug-ins
are used to replace the commandline tools or Ant scripts usually used.

The plug-ins must be declared inside the pom.xml file of your project.
For the following two plug-ins I want to document my experiences as it
was somehow tricky to get them working.

[AAR
Plug-in](http://ws.apache.org/axis2/tools/1_3/maven-plugins/maven-aar-plugin.html)
: Generates an Axis 2 service file (AAR file). This one was quite easy.
Just setting the filesets was needed. As I had one WSDL and 2 related
XSD files I had to set them to explicitly copy them to META-INF:

{% highlight xml %}\
...\
`<plugin>\
`<groupId>org.apache.axis2`</groupId>\
`<artifactId>axis2-aar-maven-plugin`</artifactId>\
`<version>1.3`</version>\
`<configuration>

`<fileSets>\
`<fileSet>\
`<directory>\${basedir}/src/main/axis2`</directory>\
`<outputDirectory>META-INF`</outputDirectory>\
`<includes>\
`<include>/\*.xml`</include>\
`<include>/\*.xsd`</include>\
`<include>/\*.wsdl`</include>\
`</includes>\
`</fileSet>

`</fileSets>

`<servicesXmlFile>\${basedir}/src/main/axis2/services.xml`</servicesXmlFile>\
`<wsdlFile>\${basedir}/src/main/axis2/loginservice.wsdl`</wsdlFile>\
`<wsdlFileName>loginservice.wsdl`</wsdlFileName>\
`</configuration>\
`<executions>\
`<execution>\
`<goals>\
`<goal>aar`</goal>\
`</goals>\
`</execution>\
`</executions>\
`</plugin>\
...\
{% endhighlight %}

The [WSDL2Code
Plug-in](http://ws.apache.org/axis2/tools/1_3/maven-plugins/maven-wsdl2code-plugin.html)
takes as input a WSDL and generates client and server stubs for calling
or implementing a Web service matching the WSDL.

This plug-in caused some problems when used as described on the
[official plug-in guide
page](http://ws.apache.org/axis2/tools/1_3/maven-plugins/maven-wsdl2code-plugin.html)
. The guide provides the following snippet:

{% highlight xml %}\
`<build>\
`<plugins>\
`<plugin>\
`<groupId>org.apache.axis2.maven2`</groupId>\
`<artifactId>axis2-wsdl2code-maven-plugin`</artifactId>\
`<executions>\
`<execution>\
`<goals>\
`<goal>wsdl2code`</goal>\
`</goals>\
`</execution>\
`</executions>\
`<configuration>\
`<packageName>com.foo.myservice`</packageName>\
`</configuration>\
`</plugin>\
`</plugins>\
`</build>\
{% endhighlight %}

When invoking directly as recommended with
<br/><code>mvn wsdl2code:wsdl2code`</code>
`<br/>I got an build error:

    <code>
    [INFO] Scanning for projects...
    [INFO] Searching repository for plugin with prefix: 'wsdl2code'.
    [INFO] ------------------------------------------------------------------------
    [ERROR] BUILD ERROR
    [INFO] ------------------------------------------------------------------------
    [INFO] The plugin 'org.apache.maven.plugins:maven-wsdl2code-plugin' does not exist or no valid version could be found
    [INFO] ------------------------------------------------------------------------
    </code>

Using `<code>axis2-wsdl2code:wsdl2code`</code> instead
solves this problem.

But then the next problem is:

    <code>
    [INFO] [axis2-wsdl2code:wsdl2code]
    [INFO] ------------------------------------------------------------------------
    [ERROR] FATAL ERROR
    [INFO] ------------------------------------------------------------------------
    [INFO] javax/wsdl/WSDLException
    [INFO] ------------------------------------------------------------------------
    [INFO] Trace
    java.lang.NoClassDefFoundError: javax/wsdl/WSDLException
            at org.apache.axis2.maven2.wsdl2code.WSDL2CodeMojo.execute(WSDL2CodeMojo.java:396)
            at org.apache.maven.plugin.DefaultPluginManager.executeMojo(DefaultPluginManager.java:447)
            at org.apache.maven.lifecycle.DefaultLifecycleExecutor.executeGoals(DefaultLifecycleExecutor.java:539)
            at org.apache.maven.lifecycle.DefaultLifecycleExecutor.executeStandaloneGoal(DefaultLifecycleExecutor.java:493)
            at org.apache.maven.lifecycle.DefaultLifecycleExecutor.executeGoal(DefaultLifecycleExecutor.java:463)
            at org.apache.maven.lifecycle.DefaultLifecycleExecutor.executeGoalAndHandleFailures(DefaultLifecycleExecutor.java:311)
            at org.apache.maven.lifecycle.DefaultLifecycleExecutor.executeTaskSegments(DefaultLifecycleExecutor.java:278)
            at org.apache.maven.lifecycle.DefaultLifecycleExecutor.execute(DefaultLifecycleExecutor.java:143)
            at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:333)
            at org.apache.maven.DefaultMaven.execute(DefaultMaven.java:126)
            at org.apache.maven.cli.MavenCli.main(MavenCli.java:282)
            at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
            at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
            at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
            at java.lang.reflect.Method.invoke(Method.java:585)
            at org.codehaus.classworlds.Launcher.launchEnhanced(Launcher.java:315)
            at org.codehaus.classworlds.Launcher.launch(Launcher.java:255)
            at org.codehaus.classworlds.Launcher.mainWithExitCode(Launcher.java:430)
            at org.codehaus.classworlds.Launcher.main(Launcher.java:375)
    [INFO] ------------------------------------------------------------------------
    </code>

Changing the group id from 'org.apache.axis2.maven2' to
'org.apache.axis2' and setting the version number explicitely to 1.3
like the following solves this problem, too:

{% highlight xml %}\
...\
`<groupId>org.apache.axis2`</groupId>\
`<artifactId>axis2-wsdl2code-maven-plugin`</artifactId>\
`<version>1.3`</version>\
...\
{% endhighlight %}

The description how to configure the plug-in is a bit unclear as it says
you should set the paramters from the command line. But with Maven the
configuration is done inside the enclosing configuration tags. I.e. for
each configuration parameter you create an own XML tag. For example for
databinding and packagename params you would add the following tags:

{% highlight xml %}\
...\
`<configuration>\
`<databindingName>xmlbeans`</databindingName>\
`<packageName>your.pkg.name.here`</packageName>\
`</configuration>\
...\
{% endhighlight %}

With this in mind "WSDL to Code" and AAR packaging for Axis 2 can be
integrated smoothly into Maven.

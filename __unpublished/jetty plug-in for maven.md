It is very common to use Maven in the Java world. 

For web applications you usually need to build the web app, stop the web app server (e.g. Tomcat), deploy the web app and start again.

Advantage of using jetty plugin:

- You don't need to install a locally running web app server.
- No need to deploy each time
- jetty scans for file changes
- really fast start up time compared to Tomcat
- jetty understands your project structure reading it from pom.xml


Add to your Maven pom.xml file:

            <!-- Start local Jetty with "mvn jetty:run" -->
            <plugin>
                <groupId>org.mortbay.jetty</groupId>
                <artifactId>maven-jetty-plugin</artifactId>
                <version>6.1.2</version>
                <configuration>
                    <webAppSourceDirectory>${basedir}/development/application</webAppSourceDirectory>
                    <connectors>
                        <connector implementation="org.mortbay.jetty.nio.SelectChannelConnector">
                            <port>8080</port>
                        </connector>
                    </connectors>
                    <scanIntervalSeconds>10</scanIntervalSeconds>
                </configuration>
                <dependencies>
                    <dependency>
                        <groupId>mysql</groupId>
                        <artifactId>mysql-connector-java</artifactId>
                        <version>5.1.18</version>
                    </dependency>
                </dependencies>
            </plugin>



Add new file jetty-env.xml to WEB-INF:

<?xml version="1.0"?>
<!DOCTYPE Configure PUBLIC "-//Mort Bay Consulting//DTD Configure//EN" "http://jetty.mortbay.org/configure.dtd">
<Configure class="org.mortbay.jetty.webapp.WebAppContext">


    <New id="myIDTravel" class="org.mortbay.jetty.plus.naming.Resource">
        <Arg>jdbc/myIDTravelDS</Arg>
        <Arg>
            <New class="com.mysql.jdbc.jdbc2.optional.MysqlConnectionPoolDataSource">
                <Set name="Url">jdbc:mysql://80.77.223.75/t10myidtravel?autoReconnect=true&amp;zeroDateTimeBehavior=convertToNull</Set>
                <Set name="User">t10myidtravel</Set>
                <Set name="Password">sZZXvd8KRGdR6c5Q</Set>
            </New>
        </Arg>
    </New>

</Configure>

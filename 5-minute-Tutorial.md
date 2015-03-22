You'll need Linux or Mac OS, [Git](http://git-scm.com/), [Maven](http://maven.apache.org/) and a [JDK](http://openjdk.java.net/) installed in order to be able to continue.

1. Grab the latest nanohttpd

`git clone https://github.com/NanoHttpd/nanohttpd.git`

2. This will create a directory 'nanohttpd' in your current directory. Switch to it

`cd nanohttpd`

3. Build the source.

`mvn package`

4. Run the nanohttpd SimpleWebServer

`java -cp webserver/target/nanohttpd-webserver-2.1.0-jar-with-dependencies.jar fi.iki.elonen.SimpleWebServer`

5. Browse it

[http://localhost:8080](http://localhost:8080)


You can skip 1 to 3 if you download the jar from central:
[nanohttpd-webserver-2.1.1.jar](http://central.maven.org/maven2/com/nanohttpd/nanohttpd-webserver/2.1.1/nanohttpd-webserver-2.1.1.jar)
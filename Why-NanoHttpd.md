## Why fork the original repo?

The Java 6 version of *nanohttpd* was born when we realized that embedding Jetty inside our
Android application was going to inflate the size without bringing along features that we
were going to need.  The search for a smaller more streamlined HTTP server lead us
to *nanohttpd* as the project had started with exactly the same goals, but we wanted to
clear up the old code - move from Java 1.1, run _static code analysis_ tools and cleanup
the findings and pull out sample/test code from the source.

In the words of the original founder of the project
> I couldn't find a small enough, embeddable and easily modifiable HTTP server
> that I could just copy and paste into my other Java projects. Every one of them
> consisted of dozens of .java files and/or jars, usually with - from my point
> of view - "overkill features" like servlet support, web administration,
> configuration files, logging etc.

Since that time we fixed a number of bugs, moved the build to _maven_ and pulled out
the samples from the runtime JAR to further slim it down.

The two projects pooled resources in early 2013, merging code-bases, to better support the
user base and reduce confusion over why _two_ NanoHttpd projects existed.

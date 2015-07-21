# Jython 2.7 Vert.x API Implementation Module

This project builds a Vert.x module which implements Python Vert.x API support using Jython.

_This version is based on *2.0.0-final* as used by *Vert.x 2.1M5* and has been patched to run with the recently released *Jython 2.7 runtime*_

To build/install run ```./gradlew install``` this builds and installs the module to your local maven repository.

Your application ```mod.json``` should include: ```com.livefyre~lang-jython~2.0.0-jython27```
and also add a ```langs.properties``` file under ```src/main/resources/platform_lib``` with (or adjusted for your languages) 
``` 
rhino=io.vertx~lang-rhino~2.0.0-final:org.vertx.java.platform.impl.RhinoVerticleFactory
jruby=io.vertx~lang-jruby~2.0.0-final:org.vertx.java.platform.impl.JRubyVerticleFactory
groovy=io.vertx~lang-groovy~2.0.0-final:org.vertx.groovy.platform.impl.GroovyVerticleFactory
jython=com.livefyre~lang-jython~2.0.0-jython27:org.vertx.java.platform.impl.JythonVerticleFactory

.js=rhino
.coffee=rhino
.rb=jruby
.py=jython
.groovy=groovy
.class=java
.java=java
```
If your vertx platform doesn't include modules from the local maven repo, add a ```repos.txt``` file under platform_lib with (or adjusted to your paths):
```
# Maven local for dev
mavenLocal:~/.m2/repository

# Maven central
maven:http://repo2.maven.org/maven2

# Sonatype snapshots
maven:http://oss.sonatype.org/content/repositories/snapshots

# Bintray
bintray:http://dl.bintray.com

```

All Vert.x language support is implemented in the form of modules which are (potentially) loaded on demand by Vert.x when needed.


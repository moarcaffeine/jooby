[![Build Status](https://travis-ci.org/jooby-project/jooby.svg?branch=master)](https://travis-ci.org/jooby-project/jooby)
[![Coverage Status](https://img.shields.io/coveralls/jooby-project/jooby.svg)](https://coveralls.io/r/jooby-project/jooby?branch=master)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.jooby/jooby/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.jooby/jooby)
[![ASF2](http://img.shields.io/badge/license-ASF2-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0.txt)
[![Twitter](https://img.shields.io/badge/twitter--blue.svg)](https://twitter.com/j0oby)
[![Google Group](https://img.shields.io/badge/google-group-orange.svg)](https://groups.google.com/forum/#!forum/jooby-project)
[![Slack Channel](https://img.shields.io/badge/slack-join chat-orange.svg)](https://jooby.slack.com)

# &infin; do more, more easily

[Jooby](http://jooby.org) a micro web framework for Java 8 or higher.

* **Solid**. Build on top of mature technologies.

* **Scalable**. Stateless application development.

* **Fast, modular and extensible**. So extensible that even the web server is plugable.

* **Simple, effective and easy to learn**. Ideal for small but also large scale applications.

* **Ready for modern web**, with the awesome and powerful [asset module](/doc/assets)


## hello world!

Java:

```java
import org.jooby.Jooby;

public class App extends Jooby {

  {
    get("/", () -> "Hey Jooby!");
  }

  public static void main(final String[] args) throws Exception {
    new App().start(args);
  }
}

```

[JavaScript](/jooby-js):

```js

var app = jooby();

app.get('/', function () 'Hey Jooby!');

```


## killer features

* **Multi-language**. Write your application in Java or [JavaScript](/doc/js)
* **Scripting programming model**. Like [express.js](http://expressjs.com), [Sinatra](http://www.sinatrarb.com), etc.. but also
* **MVC programming model**. Like [Spring](http://spring.io) controllers or [Jersey](https://jersey.java.net) resources
* **Multi-server**. Including [Netty](http://netty.io), [Jetty](http://www.eclipse.org/jetty/) and [Undertow](http://undertow.io)
* **Web-Socket**
* **Dependency Injection**
* **Hot reload** for development


quickstart
=====

* fork one of our [templates](https://github.com/jooby-starters)

* or via [Maven Archetype](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html):

Just paste this into a terminal (make sure [Java 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) and [Maven 3.x](http://maven.apache.org/download.cgi) are installed):

```bash
mvn archetype:generate -B -DgroupId=com.mycompany -DartifactId=my-app -Dversion=1.0-SNAPSHOT -DarchetypeArtifactId=jooby-archetype -DarchetypeGroupId=org.jooby -DarchetypeVersion=0.11.2
```

You might want to edit/change:

* -DgroupId: A Java package's name

* -DartifactId: A project's name in lower case and without spaces

* -Dversion: A project's version, like ```1.0-SNAPSHOT``` or ```1.0.0-SNAPSHOT```


Let's try it!:

```bash
mvn archetype:generate -B -DgroupId=com.mycompany -DartifactId=my-app -Dversion=1.0-SNAPSHOT -DarchetypeArtifactId=jooby-archetype -DarchetypeGroupId=org.jooby -DarchetypeVersion=0.11.2
cd my-app
mvn jooby:run
```

You should see something similar to this at the end of the output:

```bash
INFO  [2015-03-19 21:34:00,365] Hotswap available on: [my-app/public, my-app/conf, my-app/target/classes]
INFO  [2015-03-19 21:34:00,368]   includes: [**/*.class,**/*.conf,**/*.properties]
INFO  [2015-03-19 21:34:00,369]   excludes: []
INFO  [2015-03-19 21:34:00,937] [dev@netty]: App server started in 502ms

GET /assets/**    [*/*]     [*/*]    (anonymous)
GET /             [*/*]     [*/*]    (anonymous)

listening on:
  http://0.0.0.0:8080/
```

Jooby! is up and running!!!

getting started
=====

exploring the newly created project
-----

A new directory was created: ```my-app```. Now, let's see how it looks like:

```bash
.
├── public
|   ├── assets
|   |   ├── js
|   |   |   └── index.js
|   |   ├── css
|   |   |   └── style.css
|   |   └── images
|   └── welcome.html
├── conf
|   ├── application.conf
|   └── logback.xml
└── src
    ├── main
    |   └── java
    |       └── com
    |           └── mycompany
    |               └── App.java
    └── test
        └── java
            └── com
                └── mycompany
                    └── AppTest.java
                    
```

The **public** directory contains ```*.html```, ```*.js```, ```*.css```, ..., ```*.png``` files.

The **conf** directory contains ```*.conf```, ```*.properties```, ..., ```*.json``` files.

The **src/main/java** contains ```*.java``` (of course) files.

The **src/test/java** contains integration or unit test files.

**NOTE**: Directories: ```public``` and ```conf``` are part of the classpath.

### App.java


```java

import org.jooby.Jooby;

public class App extends Jooby { // 1

  {
    // 2
    assets("/assets/**");

    assets("/", "/welcome.html");
  }

  public static void main(final String[] args) throws Exception {
    new App().start(args); // 3. start the application.
  }

}

```

Steps involved are:

1) extends Jooby

2) define some routes

3) call the ```start``` method

running
-----

Just open a console and type:

    mvn jooby:run

The maven plugin will compile the code (if necessary) and startup the application.

Of course, you can generate the IDE metadata from Maven and/or import as a Maven project in your favorite IDE.
Then all you have to do is run the: ```App.java``` class. After all, this is plain Java application with a ```main``` method.


versioning
=====

Jooby uses [semantic versioning](http://semver.org/) for releases.

API is considered unstable while release version is: ```0.x.x``` and it might changes and/or broke without previous notification.

This might sounds terrible but isn't. Any change on the API will be reported by the Java Compiler and it wont take you a long time to fix it. Finally, API changes can be filtered and displayed it [at any time](https://github.com/jooby-project/jooby/labels/api-change)

want to contribute?
=====

* Fork the project on Github.
* Wondering what to work on? See task/bug list and pick up something you would like to work on.
* Write unit tests.
* Create an issue or fix one from [issues](https://github.com/jooby-project/jooby/issues).
* If you know the answer to a question posted to our [group](https://groups.google.com/forum/#!forum/jooby-project) - don't hesitate to write a reply.
* Share your ideas or ask questions on the [jooby group](https://github.com/jooby-project/jooby/issues) - don't hesitate to write a reply - that helps us improve javadocs/FAQ.
* If you miss a particular feature - browse or ask on the [group](https://groups.google.com/forum/#!forum/jooby-project) - don't hesitate to write a reply, show us some sample code and describe the problem.
* Write a blog post about how you use or extend [jooby](http://jooby.org).
* Please suggest changes to javadoc/exception messages when you find something unclear.
* If you have problems with documentation, find it non intuitive or hard to follow - let us know about it, we'll try to make it better according to your suggestions. Any constructive critique is greatly appreciated. Don't forget that this is an open source project developed and documented in spare time.

help and support
=====

* [jooby.org](http://jooby.org)
* [google group](https://groups.google.com/forum/#!forum/jooby-project)
* [issues](https://github.com/jooby-project/jooby/issues)

related projects
=====

 * [Netty](http://netty.io/)
 * [Jetty](http://eclipse.org/jetty)
 * [Undertow](http://undertow.io/)
 * [Guice](https://github.com/google/guice)
 * [Type Safe](https://github.com/typesafehub/config)
 * [Logback](http://logback.qos.ch)

author
=====

 [Edgar Espina] (https://twitter.com/edgarespina)

license
=====

[Apache License 2](http://www.apache.org/licenses/LICENSE-2.0.html)

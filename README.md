# Custom Attach #

Gluon [Attach](http://gluonhq.com/products/mobile/attach/) is the component that addresses the integration with low-level platform APIs in an end-to-end Java Mobile solution.

Attach provides an uniform, platform-independent API to access device and hardware features. 
At runtime, the appropriate implementation (attach:desktop, attach:android, attach:ios) makes sure the platform specific code is 
used to deliver the functionality.

Attach is open source, and it is freely licensed under the GPL license.
[Gluon](http://gluonhq.com) can provide [custom consultancy](http://gluonhq.com/services/consulting/) and [training](http://gluonhq.com/services/training/), commercial licenses, and open source [commercial support](http://gluonhq.com/services/commercial-support/), including daily and monthly releases.

### Important Note
This is an experimental repository intended to test custom Attach services that can be created and used outside Attach itself.

As a custom service, it can't use the official `com.gluonhq.attach` package name.

## Building Custom Attach ##

### Requisites ###

These are the requisites:

* A recent version of [JDK 11](http://jdk.java.net/11/)
* Gradle 6.0 or superior. 

To build the iOS services:
 
* A Mac with with MacOS X 10.14.4 or superior
* Xcode 11.x or superior

To build the Android services:

* Android SDK and Android NDK
(The GluonFX plugin installs both when building for Android)

### How to build and install Attach ###

To build the Custom Attach services on the project's root, run:

`./gradlew clean build`

If you want to install them, run:

`./gradlew clean publishToMavenLocal`

When the process finishes successfully, the different services can be added to a Gluon Mobile project.

For instance, the Log service for desktop can be added to the project like:

```
<!-- dependencies -->
<dependency>
    <groupId>my.company.attach</groupId>
    <artifactId>log</artifactId>
    <version>4.0.12-SNAPSHOT</version>
</dependency>
<dependency>
    <groupId>my.company.attach</groupId>
    <artifactId>log</artifactId>
    <version>4.0.12-SNAPSHOT</version>
    <classifier>desktop</classifier>
    <scope>runtime</scope>
</dependency>
```

and used from the project like:

```
LogService.create().ifPresent(service -> service.log("This is a message"));
```

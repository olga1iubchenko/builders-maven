# Build the project with Maven

Installation
Maven is a Java tool, so you must have [Java](https://www.oracle.com/technetwork/java/javase/downloads/index.html) installed in order to proceed.
First, [download Maven](https://maven.apache.org/download.html) and follow the [installation instructions](https://maven.apache.org/install.html). 
After that, type the following in a terminal or in a command prompt:
```sh
mvn --version
 ```
It should print out your installed version of Maven, for example:

```sh
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
Maven home: D:\apache-maven-3.6.3\apache-maven\bin\..
Java version: 1.8.0_232, vendor: AdoptOpenJDK, runtime: C:\Program Files\AdoptOpenJDK\jdk-8.0.232.09-hotspot\jre
Default locale: en_US, platform encoding: Cp1250
OS name: "windows 10", version: "10.0", arch: "amd64", family: "windows"
```
Depending upon your network setup, you may require extra configuration. Check out the [Guide to Configuring Maven](https://maven.apache.org/guides/mini/guide-configuring-maven.html) if necessary.

**Creating a Project**
You will need somewhere for your project to reside, create a directory somewhere and start a shell in that directory. On your command line, execute the following Maven goal:
```sh
mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
```
If you have just installed Maven, it may take a while on the first run. This is because Maven is downloading the most recent artifacts (plugin jars and other files) into your local repository. You may also need to execute the command a couple of times before it succeeds. This is because the remote server may time out before your downloads are complete. Don't worry, there are ways to fix that.

You will notice that the generate goal created a directory with the same name given as the artifactId. Change into that directory.
```sh
cd my-app
```
Under this directory you will notice the following standard project structure.
    
 ```sh

├── pom.xml
└── admin
    ├──  pom.xml
    └── src
        ├── main
        │   └── java 
        │       └── ...
        │           
        └── test
            └── java 
                └── ..
 └── services
    ├──  pom.xml
    └── src
        ├── main
        │   └── java 
        │       └── ...
        │           
        └── test
            └── java 
                └── .. 
 └── utils
    ├──  pom.xml
    └── src
        ├── main
        │   └── java 
        │       └── ...
        │           
        └── test
            └── java 
                └── ..   
                
  └── web
    ├──  pom.xml 
    └── src
        ├── main
        │   └── java 
        │       └── ...
        │           
        └── test
            └── java 
                └── ..     
 ```             
The src/main/java directory contains the project source code, the src/test/java directory contains the test source, and the pom.xml file is the project's Project Object Model, or POM.

**The POM**
The pom.xml file is the core of a project's configuration in Maven. It is a single configuration file that contains the majority of information required to build a project in just the way you want. The POM is huge and can be daunting in its complexity, but it is not necessary to understand all of the intricacies just yet to use it effectively. This project's POM is:

 ```sh
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>builders</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <dependency>
            <artifactId>junit</artifactId>
            <groupId>junit</groupId>
            <scope>test</scope>
            <version>4.12</version>
        </dependency>
    </dependencies>

    <properties>
        <java.version>1.11</java.version>
        <maven.compiler.version>3.8.1</maven.compiler.version>
    </properties>

    <modules>
    <module>admin</module>
    <module>services</module>
    <module>utils</module>
    <module>web</module>
    </modules>

    <packaging>pom</packaging>

    <build>
        <pluginManagement>
            <plugins>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-compiler-plugin</artifactId>
                    <version>3.5.1</version>
                    <configuration>
                        <source>1.7</source>
                        <target>1.7</target>
                    </configuration>
                </plugin>
            </plugins>
        </pluginManagement>
    </build>
</project>
 ```  
 
**What did I just do?**
You executed the Maven goal archetype:generate, and passed in various parameters to that goal. The prefix archetype is the plugin that provides the goal. If you are familiar with Ant, you may conceive of this as similar to a task. This archetype:generate goal created a simple project based upon a maven-archetype-quickstart archetype. Suffice it to say for now that a plugin is a collection of goals with a general common purpose. For example the jboss-maven-plugin, whose purpose is "deal with various jboss items".

**Build the Project**
 ```sh
mvn package
 ```
 The command line will print out various actions, and end with the following:
 ```sh
 ...
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.953 s
[INFO] Finished at: 2019-11-24T13:05:10+01:00
[INFO] -------------------------------------------------------------------

 ```

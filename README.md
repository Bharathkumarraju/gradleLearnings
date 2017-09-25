# gradleLearnings
Leran gradle from build.gradle java project
```
gradle tasks --all
gradle task hello
gradle task wrapper // wrapper task defined first time as below :) 

[root@bharath javaproject]# cat build.gradle
task wrapper(type: Wrapper) {
gradleVersion = "4.1"
}

```

##### once we run wrapper task we can get .gradle downloaded into the users home directory with all the gradle binaries.and also graldew,gradlew.bat files and gradle folder with gradlewrapper.properties and gradlewrapper jar
##### so from next on wards we use gradlew to build our project.
##### This is best practice to maintain single version of gradle across all the projects.

### ./gradlew clean build
### ./gradlew tasks --all
### ./gradlew hello

#### https://docs.gradle.org/current/dsl/ 

```

When you run javaproject the directory structure will create like below..

[root@bharath javaproject]# vim src/main/java/com/bharathwebapp/repository/HelloWorld.java
[root@bharath javaproject]# ./gradlew build

BUILD SUCCESSFUL in 1s
2 actionable tasks: 2 executed
[root@bharath javaproject]#


[root@bharath javaproject]# tree -A build
build
├── classes
│   └── java
│       └── main
│           └── com
│               └── bharathwebapp
│                   └── repository
│                       ├── Greeter.class
│                       └── HelloWorld.class
├── libs
│   └── javaproject.jar
└── tmp
    ├── compileJava
    └── jar
        └── MANIFEST.MF

10 directories, 4 files
[root@bharath javaproject]# java -cp build/classes/java/main com.bharathwebapp.repository.HelloWorld
Hello world!
[root@bharath javaproject]#

```

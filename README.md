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

you can also do above steps with below simple command to generate wrapper  :) 

gradle wrapper --gradle-version 4.1 // no need to write inside build.gradle file also :)

```

##### once we run wrapper task we can get .gradle downloaded into the users home directory with all the gradle binaries.and also in the current directory(From where you run the gradle) has graldew,gradlew.bat files and gradle folder with gradlewrapper.properties and gradlewrapper jar
##### so from next on wards we use gradlew to build our project.
##### This is best practice to maintain single version of gradle across all the projects.
##### the best thing is copy all gradlew,gradlew.bat and gradlew to all your GIT repos, So that whomever build your java repos will use gradlew to build the project that means same version of gradle everywere :) As simple as that
##### when you run first time gradlew it downloads gradle after that :) we are good to go

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



```
Project_Name: javaproject_Dependencies

this is very very simple build.gradle with 3rd party mavenCentral repo and it's dependencies

[root@bharath javaproject_Dependencies]# cat build.gradle

apply plugin: 'java'

repositories {
mavenCentral()  // indicates that build should resolve it's dependencies from this repo
}

sourceCompatibility = 1.8
targetCompatibility = 1.8

dependencies {
    compile "joda-time:joda-time:2.2"//depndency 4 Joda Time2.2 of joda-time library in joda-time group(Read frm right 2 left)
    testCompile "junit:junit:4.12"
}

jar {
    baseName = 'bharath-webapp' // we can name and version the jar name and output as below :)
    version =  '1.0.0'
}
[root@bharath javaproject_Dependencies]#


[root@bharath javaproject_Dependencies]# ./gradlew build
Download https://repo1.maven.org/maven2/joda-time/joda-time/2.2/joda-time-2.2.pom
Download https://repo1.maven.org/maven2/joda-time/joda-time/2.2/joda-time-2.2.jar

BUILD SUCCESSFUL in 3s
2 actionable tasks: 2 executed
[root@bharath javaproject_Dependencies]# tree -A build
build/        build.gradle
[root@bharath javaproject_Dependencies]# tree -A build
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
│   └── bharath-webapp-1.0.0.jar
└── tmp
    ├── compileJava
    └── jar
        └── MANIFEST.MF

10 directories, 4 files
[root@bharath javaproject_Dependencies]#

```

# gradleLearnings
Leran gradle from build.gradle java project
```
gradle tasks --all
gradle task hello
'gradle task wrapper'

once we run wrapper task we can get .gradle downloaded into the users home directory with all the gradle binaries.
and also graldew,gradlew.bat files and gradle folder with gradlewrapper.propertied and gradlewrapper jar
so from next on wards we use gradlew to build our project.
This is best practice to maintain single version of gradle across all the projects.
```
# ./gradlew clean build
# ./gradlew tasks --all
# ./gradlew hello

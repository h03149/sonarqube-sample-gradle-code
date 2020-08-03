# sonarqube-sample-gradle-code
Following is for code coverage plugin Jacoco integration with sonarqube
Code coverage in SonarQube using Jacoco plugin- code coverage represents the how much of ur code has covered under unit/intergartion test cases. Bydefault sonarqube does not provide code coverage report in built,so u need to provide some plugins.
Add following entry in build.gradle file-



plugins {
  id "org.sonarqube" version "2.7"
  id "jacoco"
  id "java"
  
  
}


Note- id "java" , java agent will go through all ur classes and it identifies whatever test cases u have written, will executes against source code/test cases.
sonarqube {

properties {

    property "sonar.projectName" , "java :: Code coverage demo"
	property "sonar.projectKey" , "org.sonarqube:JacocoCodeCoverage"
	property "sonar.jacoco.reportPath" , "${project.buildDir}/jacoco/test.exec"



}
}


test {

ignoreFailures = true

}

Note- Whenever I am executing the test cases,if anything failes,I want the build status as success hence ignoreFailures = true

This test.exec is a file where it is going to generate that report.

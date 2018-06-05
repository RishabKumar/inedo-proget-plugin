[![Build Status](https://jenkins.ci.cloudbees.com/job/plugins/job/inedo-proget-plugin/badge/icon)](https://jenkins.ci.cloudbees.com/job/plugins/job/inedo-proget-plugin/)

This plugin integrates [Inedo ProGet](http://inedo.com/proget) with Jenkins allowing Jenkins jobs to create and upload, or download and extract, universal packages.

It requires ProGet version 4.0.12 or higher to work correctly.

See the [Wiki page](http://wiki.jenkins-ci.org/display/JENKINS/Inedo+ProGet+Plugin) for more details.

# Building The Plugin

The plugin is built using <a href="http://www.gradle.org/">Gradle</a> and the <a href="https://wiki.jenkins-ci.org/display/JENKINS/Gradle+JPI+Plugin">Gradle Jenkins JPI Plugin</a>.  The code base includes the Gradle Wrapper, which will automatically download the correct version of Gradle. 

Gradle can be run from the command line or from your IDE:

## Command line

From the command line, `cd` to the folder containing a copy of this project, and run 

  `./gradlew clean jpi` on Unix-based systems, or 
  
  `gradlew clean jpi` on Windows.
  
This will download the required dependencies, clean the existing project, recompile all source code and build the jpi file required by jenkins. 

## IDE

For Eclipse and NetBeans, you will need to install a Gradle plugin to your IDE before importing the project. See [Gradle tooling](https://www.gradle.org/tooling) for details.

On importing the project to your IDE, the required dependencies will be downloaded.

# Testing The Plugin

## Manual
To spin up a Jenkins instance with this plugin installed for manual testing, run `gradlew clean server` (see "building the plugin" above). The Jenkins instance will be available on port 8080 on your localhost. You may need to specify a path to your JDK, if so use `gradlew clean server -Dorg.gradle.java.home=/JDK_PATH`

To login the username will be admin and the password can be found in <project root>/work/secrets/initialAdminPassword

### Prerequisites
* ProGet:
    * Installed and configured with an API key
    * Add a Feed called Example using the universal package format
    * Add a package to the feed - use the ProGetApiTests.uploadPackage() method as this will put an appropriate sized file there that will allow the tests to pass
* Jenkins System Configuration page updated with BuildMaster server details and the Test Connection button returning success

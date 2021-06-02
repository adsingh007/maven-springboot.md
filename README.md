# Objective
The main objective of this document is to understand the working and use of Apache Maven and Spring-Boot. 

# Apache Maven  <img src="https://github.com/adsingh007/maven-springboot.md/blob/main/maven-logo-black-on-white.png" align="right" width="20%">

Apache Maven is a software project management and comprehension tool. Based on the concept of a project object model (POM), Maven can manage a project's build, reporting and documentation from a central piece of information.<br/>
To know installation process please click [here](https://github.com/adsingh007/maven-springboot.md/blob/main/Installation-process.md)

# Maven Overview
Maven is centered around the concept of POM files (Project Object Model). A POM file is an XML representation of project resources like source code, test code, dependencies (external JARs used) etc. The POM contains references to all of these resources. The POM file should be located in the root directory of the project it belongs to.
<img src="https://github.com/adsingh007/maven-springboot.md/blob/main/pom%201.png" align="center"> <br/>
### Maven POM Files
When you execute a Maven command you give Maven a POM file to execute the commands on. Maven will then execute the command on the resources described in the POM.A Maven POM file (Project Object Model) is an XML file that describes the resources of the project. This includes the directories where the source code, test source etc. is located in, what external dependencies (JAR files) your projects has etc. <br/><img src="https://github.com/adsingh007/maven-springboot.md/blob/main/pom%202.png" width="80%"> <br/>
Click below on details for more details.
<details> 
 
 >The POM file describes what to build, but most often not how to build it. How to build it is up to the Maven build phases and goals. <br/>
Each project has a POM file. The POM file is named pom.xml and should be located in the root directory of your project. <br/> A project divided into subprojects will typically have one POM file for the parent project, and one POM file for each subproject.  <br/> This structure allows both the total project to be built in one step, or any of the subprojects to be built separately.  <br/>
  <img src="https://github.com/adsingh007/maven-springboot.md/blob/main/pom3.png" align="center"> <br/>
  
- The **ModelVersion** element sets what version of the POM model you are using
- The **groupId element** is a unique ID for an organization, or a project. Most often you will use a group ID which is similar to the root Java package name of the project.for eg ``` com.jenkov```.
- The **artifactId** element contains the name of the project you are building. In the case of my ``` com.jenkov```project, the artifact ID would be ```java-web-crawler``` . The artifact ID is used as name for a subdirectory under the group ID directory in the Maven repository. The artifact ID is also used as part of the name of the JAR file produced when building the project. The output of the build process, the build result that is, is called an artifact in Maven.
- The **versionId** element contains the version number of the project. If your project has been released in different versions, for instance an open source API, then it is useful to version the builds. That way users of your project can refer to a specific version of your project.
- The above groupId, artifactId and version elements would result in a JAR file being built and put into the local Maven repository at the following path
  ```MAVEN_REPO/com/jenkov/java-web-crawler/1.0.0/java-web-crawler-1.0.0.jar```
  

 ### Super POM
 
 All Maven POM files inherit from a super POM or Parent POM . If no super POM is specified, the POM file inherits from the base POM.<br/>
 <img align="mid" src="https://github.com/adsingh007/maven-springboot.md/blob/main/maven-super-pom.png"> <br/>
 
 You can make a POM file explicitly inherit from another POM file. That way you can change the settings across all inheriting POM's via their common super POM. You specify the super POM at the top of a POM file like this:-
 <img src="https://github.com/adsingh007/maven-springboot.md/blob/main/ppom.png" align="center"> <br/>
 An inheriting POM file may override settings from a super POM. Just specify new settings in the inheriting POM file.
 
  </details> 
 
 
 ## Maven Build Life Cycles, Phases and Goals

When Maven builds a software project it follows a build life cycle. The build life cycle is divided into build phases, and the build phases are divided into build goals. Maven build life cycles, build phases and goals.<br/>

#### Build Life Cycles:

- default
- clean
- site

>The **default** lifecycle handles your project deployment, the **clean** lifecycle handles project cleaning, while the **site** lifecycle handles the creation of your project's site documentation.

### A Build Lifecycle is Made Up of Phases
Each of these build lifecycles is defined by a different list of build phases, wherein a build phase represents a stage in the lifecycle.

For example, the default lifecycle comprises of the following phases.
- **Validate** - validate the project is correct and all necessary information is available
- **Compile** - compile the source code of the project
- **Test** - test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed
- **Package** - take the compiled code and package it in its distributable format, such as a JAR.
- **Verify** - run any checks on results of integration tests to ensure quality criteria are met
- **Install** - install the package into the local repository, for use as a dependency in other projects locally
- **Deploy** - done in the build environment, copies the final package to the remote repository for sharing with other developers and projects.<br/>
<br/>
These lifecycle phases are executed sequentially to complete the default lifecycle. Given the lifecycle phases above, this means that when the default lifecycle is used, Maven will first validate the project, then will try to compile the sources, run those against the tests, package the binaries (e.g. jar), run integration tests against that package, verify the integration tests, install the verified package to the local repository, then deploy the installed package to a remote repository.


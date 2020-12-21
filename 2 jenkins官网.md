# [Guided Tour](https://www.jenkins.io/doc/pipeline/tour/getting-started/)

This guided tour introduces you to the basics of using Jenkins and its main feature, Jenkins Pipeline. This tour uses the “standalone” Jenkins distribution, which runs locally on your own machine.

### Prerequisites

For this tour, you will require:

* A machine with:
  * 256 MB of RAM, although more than 512MB is recommended
  * 10GB of drive space (for Jenkins and your Docker image)
* The following software installed:
  * Java 8 or 11 (either a JRE or Java Development Kit(JDK) is fine)
  * Docker (navigate to Get Docker site to access the Docker download that’s suiteable for your platform)

### Download and run Jenkins

1. Download Jenkins
2. Open up a terminal in the download directory.
3. Run `java -jar jenkins.war —httpPort=8080`
4. Browse to http://localhost:8080
5. Follow the instructions to complete the installation.

Greating your first Pipeline

What is a Jenkins Pipeline?

### Running multiple steps

Piplines are made of multiple steps that allow you to build, test and deploy applications. Jenkins Pipeline allows you to compose multiple steps in an easy way that can help you model any sort of automation process.

Think of a “step” like a single command which performs a single action. When a step succeeds it moves onto the next step. When a step fails to execute correctly the Pipeline will fail.

When all the steps in the Pipeline have successfully completed, the Pipeline is considered to have successfully executed.

#### Linux, BSD, and Mac OS

On Linux, BSD, and Mac OS (Unix-like) systems, the sh step is used to execute a shell command in a Pipeline.

# User Handbook

## User Handbook overview

This page provides an overview of the documentation in the Jenkins User Handbook.

If you want to get up and running with Jenkins, see Installing Jenkins for procedures on how to install Jenkins on your supported platform of choice.

If you are a typical Jenkins user (of any skill level) who wants to know more about Jenkins usage, see Using Jenkins. Also refer to the separate Pipeline and Blue Ocean chapters for more information about these core Jenkins features.

If you are a Jenkins administrator and want to know more about managing Jenkins nodes and instances, see Managing Jenkins.

If you are a system administrator and want to learn how to back-up, restore, maintain as Jenkins servers and nodes, see Jenkins System Administration.

## Installing Jenkins

The procedures in this chapter are for new installations of Jenkins.

Jenkins is typically run as a standalone application in its own process with the built-in Java servlet container/application server(Jetty).

Jenkins can also be run as a servlet in different Java servlet containers such as Apache Tomcat or GlassFish. However, instructions for setting up these types of installations are beyond the scope of this chapter.



## Using Jenkins

### Using credentials

### Search Box

### Referencing another project by name

### Aborting a build

### Fingerprints

### Using local language

### Change time zone

### Remote Access API

### Executor Starvation

### Using Jenkins agents


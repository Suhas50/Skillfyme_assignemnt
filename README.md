
# Project 1.1 – Implementing Jenkins Pipeline as Code Using Jenkinsfile

**GitHub Repository:** [jenkins-1.1](https://github.com/Suhas50/jenkins-1.1.git)


## Problem Statement

Traditional software build and testing processes involve manually executing commands to compile source code, run tests, and package applications. This approach is time-consuming, repetitive, and prone to human errors.

The objective of this project is to automate the Continuous Integration (CI) process using Jenkins Pipeline as Code, ensuring consistent and reliable application builds, testing, and packaging.

## Solution Approach

To overcome these challenges, a Jenkins Declarative Pipeline is implemented using a Jenkinsfile stored in a GitHub repository.

The solution involves:

1. Creating a Java Maven application with source code, unit tests, and a `pom.xml` file.
2. Hosting the project repository on GitHub for version control.
3. Configuring Jenkins on a GCP Compute Engine VM.
4. Integrating Jenkins with GitHub using Pipeline Script from SCM.
5. Creating four automated pipeline stages:
   - **Checkout:** Retrieve source code from GitHub.
   - **Build:** Compile the Java application using Maven.
   - **Test:** Execute unit tests using JUnit.
   - **Package:** Generate the application JAR file.
6. Archiving the generated JAR artifact in Jenkins.

This approach automates the complete CI workflow, reduces manual effort, and makes the build and testing process repeatable and reliable.

# Project 1.2 – Implementing Parallel CI Pipeline in Jenkins

**GitHub Repository:** [jenkins-1.2](https://github.com/Suhas50/jenkins-1.2.git)

## Problem Statement
In traditional CI pipelines, tasks such as unit testing, integration testing, and code analysis execute sequentially. This increases build execution time and delays feedback to developers.

## Solution Approach
Implemented a parallel CI pipeline using Jenkins Declarative Pipeline. The pipeline fetches Java Maven source code from GitHub, compiles the application, and executes Unit Tests, Integration Tests, and Code Analysis simultaneously using the `parallel` directive.

## Tools & Technologies
- Jenkins
- Git & GitHub
- Java
- Maven
- GCP VM


# Project 1.3 - Jenkins Master-Agent Distributed Build Architecture

## Problem Statement
Configure a Jenkins Master-Agent architecture using two separate GCP virtual machines to distribute build workloads. The Jenkins master should manage and schedule jobs, while the agent executes build tasks remotely using SSH.

## Solution Approach
- Created two GCP virtual machines: Jenkins Master and Agent.
- Installed Jenkins, Java, Git, and Maven on the Master VM.
- Installed Java, Git, and Maven on the Agent VM.
- Configured SSH key-based authentication between the Master and Agent.
- Added the Agent as a permanent node in Jenkins using SSH.
- Configured the agent with the label `java-agent` and remote root directory `/home/jenkins/agent`.
- Created a Freestyle Jenkins job and restricted execution to the `java-agent` label.
- Verified distributed execution through Jenkins Console Output.

# **DOCKER**

# Project 2.1 – Optimizing Container Images Using Multi-Stage Docker Builds

**GitHub Repository:** [Docker2.1 – Multi-Stage Docker Builds](https://github.com/Suhas50/Docker2.1-optimizing-container-image-using-multi-stage-docker-builds.git)

## Problem Statement

Traditional Docker builds for Golang applications include unnecessary build dependencies, compilers, development tools, and source code in the final image. This increases image size, storage usage, and deployment time. The objective is to optimize the Docker image by separating the build environment from the runtime environment.

## **Docker**

## Solution Approach

1. Developed a simple Golang backend application that can be compiled into an executable binary.
2. Created a traditional Dockerfile to understand how build dependencies increase the final image size.
3. Implemented a multi-stage Dockerfile with a Golang builder stage and a lightweight runtime stage.
4. Compiled the application in the builder stage and copied only the executable binary into the final runtime image.
5. Built and ran the optimized Docker image, verifying application functionality using container and HTTP health checks.
6. Compared traditional and multi-stage Docker image sizes to analyze the optimization and efficiency improvements.



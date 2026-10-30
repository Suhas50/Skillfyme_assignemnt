
# Project 1.1 – Implementing Jenkins Pipeline as Code Using Jenkinsfile

## 1. Project Overview

This project demonstrates the implementation of **Jenkins Pipeline as Code** using a Jenkinsfile to automate the Continuous Integration (CI) process for a Java Maven application.

The pipeline automates source code checkout, application compilation, unit testing, and packaging through Jenkins.

The project is implemented using **Google Cloud Platform (GCP) Compute Engine**, hosting a Jenkins server.

## 2. Problem Statement

Traditionally, software build and testing processes are performed manually, requiring developers to execute multiple commands for compiling source code, running tests, and generating application packages.

This manual approach introduces several challenges:

- Repetitive manual build and testing tasks.
- Increased chances of human error.
- Inconsistent build environments.
- Time-consuming testing and packaging processes.
- Lack of centralized pipeline visibility.

**Objective:** Automate the entire Continuous Integration workflow using Jenkins Pipeline as Code to make the build, testing, and packaging processes consistent, repeatable, and maintainable.

## 3. Solution Approach

To address these challenges, a Jenkins Declarative Pipeline is implemented using a Jenkinsfile stored in a GitHub repository.

The solution follows these steps:

1. **Application Development:** Create a Java application with Maven project configuration (`pom.xml`).
2. **Version Control:** Store application source code, test cases, and Jenkinsfile in GitHub.
3. **Jenkins Integration:** Configure Jenkins to retrieve the repository using Pipeline Script from SCM.
4. **Pipeline Automation:** Define four sequential stages in the Jenkinsfile.
5. **Build Validation:** Compile the Java application and execute unit tests using Maven.
6. **Artifact Generation:** Package the application into a JAR file.
7. **Verification:** Validate pipeline execution through Jenkins Stage View, Console Output, and archived build artifacts.

This approach eliminates the need to execute build and testing commands manually for every pipeline run.

## 4. Architecture

```text
Developer
    |
    v
GitHub Repository
    |
    | Source Code + Jenkinsfile
    v
Jenkins Server (GCP Compute Engine)
    |
    v
Checkout Stage
    |
    v
Build Stage
    |
    v
Test Stage
    |
    v
Package Stage
    |
    v
Generated JAR Artifact
    |
    v
Jenkins Artifact Archive
```

## 5. Technologies Used

| Technology | Purpose |
|---|---|
| Google Cloud Platform | Cloud infrastructure |
| Compute Engine | Hosts Jenkins server |
| Jenkins | CI pipeline automation |
| Git | Version control |
| GitHub | Source code repository |
| Java 17 | Application development |
| Apache Maven | Build and dependency management |
| JUnit 5 | Unit testing |
| Ubuntu Linux | Operating system |

## 6. Project Structure

```text
pipeline-ci-demo/
│
├── src/
│   ├── main/
│   │   └── java/
│   │       └── App.java
│   │
│   └── test/
│       └── java/
│           └── AppTest.java
│
├── pom.xml
├── Jenkinsfile
└── README.md
```

## 7. Jenkins Pipeline Stages

The Jenkinsfile defines four sequential stages:

### Stage 1 – Checkout

Retrieves the application source code and Jenkinsfile from the GitHub repository.

### Stage 2 – Build

Uses Maven to clean previous build files and compile the Java application.

```bash
mvn clean compile
```

### Stage 3 – Test

Executes unit tests using JUnit through Maven.

```bash
mvn test
```

### Stage 4 – Package

Packages the compiled application and generates a JAR artifact.

```bash
mvn package
```

The generated artifact is archived in Jenkins using the `archiveArtifacts` pipeline step.

## 8. Implementation Steps

1. Created a GCP Compute Engine VM and installed Java, Maven, Git, and Jenkins.
2. Created a Java Maven application with source code and unit tests.
3. Configured `pom.xml` with Maven dependencies and build plugins.
4. Created a declarative Jenkinsfile containing four pipeline stages.
5. Pushed the project files to the GitHub repository.
6. Created a Pipeline job in Jenkins.
7. Configured Pipeline Script from SCM with the GitHub repository URL.
8. Triggered the pipeline manually using Build Now.
9. Verified the execution stages and archived JAR artifact.

## 9. Expected Output

A successful pipeline execution should produce:

- Successful source code checkout.
- Successful Maven compilation.
- Passing JUnit unit tests.
- Successful Maven packaging.
- Generated JAR artifact.
- Successful Jenkins build status.

**Generated Artifact:**

```text
target/pipeline-ci-demo-1.0-SNAPSHOT.jar
```

## 10. Verification

The implementation is verified through the following:

- **Jenkins Stage View:** Confirms execution of all four pipeline stages.
- **Console Output:** Displays Maven build and testing logs.
- **Build Status:** Confirms successful pipeline execution.
- **Build Artifacts:** Confirms that the generated JAR file is archived and available for download.

## 11. Outcome and Learning

Successfully implemented a Jenkins Declarative Pipeline using Jenkinsfile to automate the Continuous Integration workflow for a Java Maven application.

The project demonstrates practical experience in:

- Jenkins Pipeline as Code.
- GitHub and Jenkins integration.
- Automated Java application builds.
- Maven-based unit testing.
- Application packaging and artifact archiving.
- Running CI workloads on GCP infrastructure.

## 12. Conclusion

This project demonstrates how Jenkins Pipeline as Code simplifies and standardizes the software integration process.

By defining pipeline stages in a version-controlled Jenkinsfile, the entire build, test, and packaging workflow becomes repeatable, maintainable, and easier to manage.

The implementation provides a foundation for extending the CI pipeline with additional stages such as code quality analysis, Docker image creation, and automated deployment.

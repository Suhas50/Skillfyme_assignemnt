
# Project 1.1 – Implementing Jenkins Pipeline as Code Using Jenkinsfile

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

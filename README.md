
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

# Project Docker-2.2-containerizing-microservice-and-publishing-image-to-registry

**GitHub Repository:** [ Docker-2.2-containerizing-microservice-and-publishing-image-to-registry
](https://github.com/Suhas50/Docker-2.2-containerizing-microservice-and-publishing-image-to-registry-.git)



## Problem Statement
Modern application architectures rely heavily on decoupled microservices to improve scalability and maintainability. However, packaging, managing, and distributing a multi-tier application—consisting of a frontend service, a backend API service, and a database service—across different environments introduces operational friction. 

The challenges include:
* **Environment Consistency:** Ensuring each microservice runs reliably across local development, staging, and cloud environments without missing dependencies.
* **Image Management:** Building separate, optimized container images for each distinct service layer with proper versioning.
* **Registry Distribution:** Publishing container artifacts securely to public registries (Docker Hub) for collaboration and enterprise cloud registries (AWS ECR) for production cloud deployments.
* **Verification:** Confirming that container images can be successfully pulled, instantiated, and run independently from remote registries.

---

## Solution Approach

To address these challenges, we implement a standardized containerization and deployment pipeline using Docker and cloud container registries:

### 1. Isolated Project Architecture
Organize the application into distinct project directories for each service (`frontend/`, `backend/`, and `database/`), ensuring clear separation of concerns, dependencies, and source code.

### 2. Tailored Containerization (Dockerfiles)
Write custom `Dockerfile` scripts optimized for each service stack:
* **Frontend:** Uses a lightweight Nginx web server (`nginx:alpine`) to serve static HTML assets.
* **Backend:** Uses a Node.js runtime (`node:18-alpine`) configured with Express to handle application business logic and API requests.
* **Database:** Uses an official relational database image (`postgres:15-alpine`) with automated environment setup and optional SQL initialization scripts.

### 3. Local Build & Tagging Strategy
* Build isolated container images using versioned tags (e.g., `v1.0`) to ensure traceability.
* Tag local images with standard registry naming conventions incorporating your Docker Hub username and AWS Account ID/Region.

### 4. Registry Publishing (Docker Hub & AWS ECR)
* **Docker Hub:** Authenticate via CLI and push public images for open accessibility and reuse.
* **AWS ECR:** Authenticate via AWS CLI (`aws ecr get-login-password`), dynamically create private repositories, and push enterprise-grade images for cloud deployments.

### 5. Deployment Verification
Clean up local images to test end-to-end registry functionality by pulling, running, and validating all microservices via `docker run` and `docker ps`.


# Microservices Containerization and Registry Deployment

## Problem Statement
Modern application architectures rely heavily on decoupled microservices to improve scalability and maintainability. However, packaging, managing, and distributing a multi-tier application—consisting of a frontend service, a backend API service, and a database service—across different environments introduces operational friction. 

The challenges include:
* **Environment Consistency:** Ensuring each microservice runs reliably across local development, staging, and cloud environments without missing dependencies.
* **Image Management:** Building separate, optimized container images for each distinct service layer with proper versioning.
* **Registry Distribution:** Publishing container artifacts securely to public registries (Docker Hub) for collaboration and enterprise cloud registries (AWS ECR) for production cloud deployments.
* **Verification:** Confirming that container images can be successfully pulled, instantiated, and run independently from remote registries.

---
# Project Docker-2.3-Docker-image-build-using-pipeline

**GitHub Repository:** [ Docker-2.3-Docker-image-build-using-pipeline](https://github.com/Suhas50/2.3-Docker-image-build-using-pipeline.git)

## Problem Statement
Automate Docker image creation and publication using a Jenkins CI/CD pipeline triggered by GitHub updates. The goal is to establish reliable build, tag, and push automation to Docker Hub for continuous integration.

## Solution Approach
1. **Repository Setup:** Develop the application source code, create a `Dockerfile`, and push the project files to a GitHub repository.
2. **Environment Configuration:** Install Docker and Jenkins on the server, grant Jenkins Docker group permissions, and securely store Docker Hub credentials.
3. **Pipeline Scripting:** Write a declarative `Jenkinsfile` defining stages for source code checkout, application testing, Docker image building, and version tagging.
4. **Publishing & Verification:** Configure the Jenkins pipeline job to authenticate with Docker Hub, push the container images, and verify successful execution.


# Project 2.4 - Deploying Multi-Container Applications using Docker Compose
**GitHub Repository:** [Docker-2.4-multi-container-application-using-docker-compose](https://github.com/Suhas50/Docker-2.4-multi-container-application-using-docker-compose-.git)

 
## Problem Statement

Deploying and managing multiple application services such as frontend, backend, and database separately requires multiple Docker commands and manual configuration. This makes container management and service communication difficult.

The objective is to deploy a multi-container application using Docker Compose, where all services can be configured, connected, and managed through a single YAML file.

## Solution Approach

1. Created separate directories for frontend and backend applications.
2. Created Dockerfiles for frontend (Nginx) and backend (Node.js) to build their respective images.
3. Used the official MySQL 8.0 image for the database service.
4. Created a `docker-compose.yml` file defining frontend, backend, and database services.
5. Configured port mappings, container names, and service dependencies.
6. Implemented a healthcheck to ensure MySQL is ready before starting the backend.
7. Configured Docker networking for communication between containers using service names.
8. Created a named volume (`mysql_data`) to persist MySQL database data.
9. Deployed the complete application using `docker compose up -d --build`.
10. Verified container status, service communication, and frontend functionality through a web browser.


# Project 3.1 - Deploying Scalable Applications using ReplicaSets and Deployments
**GitHub Repository:** [kubernetes-3.1-](https://github.com/Suhas50/kubernetes-3.1-.git)

## Problem Statement
Deploy and manage scalable applications in a Kubernetes cluster using ReplicaSets and Deployments. Ensure application availability, automatic Pod recovery, horizontal scaling, rolling updates, and rollback to a previous stable version.

## Solution Approach
1. Created a ReplicaSet YAML to maintain the desired number of Nginx Pods.
2. Verified automatic Pod recreation by deleting a running Pod.
3. Created a Deployment YAML to manage application Pods through ReplicaSets.
4. Scaled the application from 3 to 5 replicas.
5. Performed a rolling update by upgrading the Nginx image version.
6. Simulated a failed deployment using an invalid image.
7. Performed a rollback to restore the previous stable application version.

# Project 3.2 – Kubernetes Resource Management and Horizontal Pod Autoscaling (HPA)
**GitHub Repository:** [kubernetes-3.2-](https://github.com/Suhas50/kubernetes-3.2.git)

## Problem Statement

Deploy a containerized application on a Kubernetes cluster and configure CPU and memory resource requests and limits. Implement Horizontal Pod Autoscaling (HPA) to automatically increase or decrease the number of application Pods based on CPU utilization.

The objective is to ensure efficient resource utilization, application scalability, and availability under varying workloads.

## Solution Approach

1. Created a Kubernetes Deployment to deploy the Nginx application with two initial replicas.
2. Configured CPU and memory requests and limits for the application containers.
3. Created a Kubernetes Service to expose the application internally within the cluster.
4. Verified Pod resource allocation and monitored CPU and memory usage using Metrics Server.
5. Configured Horizontal Pod Autoscaler (HPA) with a minimum of 2 replicas, maximum of 10 replicas, and a target CPU utilization of 50%.
6. Generated application traffic using BusyBox load-generator Pods to simulate workload.
7. Monitored CPU utilization and observed HPA automatically scaling the number of Pods based on demand.
8. Stopped the load generators and verified that HPA scaled the application back toward the minimum replica count.

## Technologies Used

- Google Kubernetes Engine (GKE)
- Kubernetes
- Nginx
- YAML
- kubectl
- Metrics Server
- Horizontal Pod Autoscaler (HPA)
- BusyBox


# Kubernetes Project 3.3

**GitHub Repository:** [kubernetes-3.3-](https://github.com/Suhas50/kubernetes-3.3.git)

## Problem Statement
Deploy a containerized application on Kubernetes with persistent storage, centralized configuration management, and secure secret management. The application should be accessible externally and maintain data even when Pods restart.

## Solution Approach
1. Created Persistent Volume (PV) and Persistent Volume Claim (PVC) to provide persistent storage using GKE Persistent Disk.
2. Created a ConfigMap to manage application configuration.
3. Created a Secret to store sensitive information such as database credentials and API keys.
4. Deployed the NGINX application using a Kubernetes Deployment with multiple replicas.
5. Mounted persistent storage and injected ConfigMap and Secret values into the Pods.
6. Exposed the application externally using a LoadBalancer Service.
7. Verified Pod status, storage, configuration, secrets, and application access through the external IP.


# Project 3.4 - GitOps Application Deployment using ArgoCD on Kubernetes

## Problem Statement

**GitHub Repository:** [kubernetes-3.4-](https://github.com/Suhas50/kubernetes-project-3.4.git)


Manually deploying and updating applications in Kubernetes using kubectl can be time-consuming and difficult to maintain. It also becomes challenging to keep the Kubernetes cluster synchronized with the latest application configurations.

The objective of this project is to implement GitOps using ArgoCD, where Kubernetes deployment configurations are maintained in a GitHub repository. ArgoCD continuously monitors the repository and automatically synchronizes changes with the Kubernetes cluster.

## Solution Approach

1. **Create Kubernetes Cluster:** Created a Kubernetes cluster using Google Kubernetes Engine (GKE) to host the application.

2. **Install ArgoCD:** Installed ArgoCD in the Kubernetes cluster using Kubernetes manifests to manage application deployments through GitOps.

3. **Prepare GitHub Repository:** Created a GitHub repository containing Kubernetes deployment and service YAML files.

4. **Configure ArgoCD Application:** Created an ArgoCD Application resource and connected it to the GitHub repository by specifying the repository URL, branch, and manifest path.

5. **Deploy Application using GitOps:** Configured automated synchronization so that ArgoCD detects changes in the GitHub repository and deploys the application to the Kubernetes cluster.

6. **Verify Deployment:** Verified application deployment through the ArgoCD dashboard and Kubernetes resources using kubectl commands.

7. **Test GitOps Synchronization:** Modified the replica count in deployment.yaml from 2 to 4 and pushed the changes to GitHub. ArgoCD automatically detected the changes and updated the Kubernetes deployment.

## Technologies Used

- Google Kubernetes Engine (GKE)
- Kubernetes
- ArgoCD
- Git
- GitHub
- YAML
- Nginx


# Project 4.1 – Managing Terraform Modules, Outputs and State File

**GitHub Repository:** [Terraform-4.1](https://github.com/Suhas50/Terraform-4.1.git)


## Problem Statement

Managing infrastructure using a single Terraform configuration can become difficult as projects grow. Reusing configurations, accessing resource information, and tracking infrastructure changes are important for effective infrastructure management.

The objective of this project is to understand Terraform Modules, Outputs, and State Files by creating and managing AWS EC2 instances using reusable Terraform configurations.

## Solution Approach

1. **Project Structure:** Created a structured Terraform project with root configuration files and a separate `modules` directory.

2. **Terraform Module:** Created a reusable EC2 module containing `main.tf`, `variables.tf`, and `outputs.tf` to define and manage EC2 instances.

3. **Module Integration:** Used the EC2 module in the root `main.tf` file to provision AWS infrastructure.

4. **Variable Management:** Defined input variables in `variables.tf` and provided their values through `terraform.tfvars`.

5. **Output Configuration:** Configured Terraform outputs to display EC2 instance IDs and public IP addresses after deployment.

6. **Infrastructure Initialization:** Executed `terraform init` to initialize the working directory and download the required AWS provider.

7. **Infrastructure Deployment:** Used `terraform plan` to review infrastructure changes and `terraform apply` to create the EC2 instances.

8. **State File Analysis:** Examined the `terraform.tfstate` file to understand how Terraform tracks created resources and their attributes.

9. **Infrastructure Modification:** Modified the Terraform configuration and applied the changes to observe how Terraform updates the state file.

# Project 4.2 – Managing Multiple Environments Using Terraform Workspaces
**GitHub Repository:** [Terraform-4.2](https://github.com/Suhas50/Terraform-4.2.git)


## Problem Statement

Managing multiple environments such as Development, Staging, and Production requires separate infrastructure configurations and state management. Manually maintaining these environments can lead to configuration errors and infrastructure inconsistencies.

The objective of this project is to use Terraform Workspaces to manage multiple AWS environments independently using a single Terraform configuration.

## Solution Approach

1. **Terraform Configuration:** Created Terraform configuration files (`main.tf`, `variables.tf`, and `terraform.tfvars`) to define AWS EC2 infrastructure.

2. **AWS Provider Setup:** Configured the AWS provider with the required region (`ap-south-1`).

3. **Terraform Initialization:** Executed `terraform init` to initialize the working directory and download the AWS provider.

4. **Workspace Creation:** Created separate Terraform workspaces for different environments:
   - Development
   - Staging
   - Production

5. **Workspace Selection:** Used `terraform workspace select` to switch between different environments.

6. **Environment Configuration:** Used `terraform.workspace` and conditional configuration to assign different EC2 instance types:
   - Development – `t2.micro`
   - Staging – `t2.small`
   - Production – `t2.medium`

7. **Infrastructure Deployment:** Executed `terraform plan` and `terraform apply` separately in each workspace to provision EC2 instances.

8. **Workspace Verification:** Used `terraform workspace list` and `terraform workspace show` to verify the available and active workspaces.

9. **State Isolation:** Verified that each workspace maintains its own Terraform state, allowing independent infrastructure management.

# Project 4.3 – Infrastructure Automation Using Terraform and Jenkins
**GitHub Repository:** [Terraform-4.3](https://github.com/Suhas50/terraform-project-4.3.git)


## Problem Statement

Manually provisioning and managing AWS infrastructure can be time-consuming and error-prone. It also requires repeated execution of Terraform commands whenever infrastructure configurations are updated.

The objective of this project is to automate AWS infrastructure provisioning using Terraform and Jenkins CI/CD pipelines. The pipeline should automatically execute Terraform commands whenever changes are pushed to the GitHub repository.

## Solution Approach

1. **Terraform Configuration:** Created Terraform configuration files (`main.tf`, `variables.tf`, and `terraform.tfvars`) to define AWS infrastructure and EC2 instance configuration.

2. **GitHub Repository:** Uploaded Terraform configuration files and the Jenkinsfile to a GitHub repository for version control.

3. **Jenkins Setup:** Configured Jenkins with the required Terraform CLI and Git tools to execute infrastructure automation pipelines.

4. **AWS Credentials:** Created an AWS IAM user and configured its Access Key ID and Secret Access Key securely in Jenkins Global Credentials.

5. **Jenkins Pipeline:** Created a Jenkins Pipeline job connected to the GitHub repository.

6. **Pipeline Stages:** Implemented the following stages in the Jenkinsfile:
   - **Checkout:** Retrieves Terraform configuration files from GitHub.
   - **Terraform Init:** Initializes the Terraform working directory and downloads the required provider.
   - **Terraform Plan:** Reviews the infrastructure changes before deployment.
   - **Terraform Apply:** Automatically provisions the required AWS infrastructure.

7. **Webhook Integration:** Configured a GitHub webhook to trigger the Jenkins pipeline automatically whenever code changes are pushed.

8. **Pipeline Execution:** Executed the Jenkins pipeline and monitored the build progress through Jenkins Console Output.

9. **Infrastructure Verification:** Verified successful Terraform execution and confirmed that the EC2 instance was provisioned in AWS.


# Project 4.4 - Monitoring Kubernetes Cluster Using Prometheus and Grafana



## Problem Statement

Monitoring Kubernetes cluster performance is essential for maintaining application availability, reliability, and resource utilization. Without proper monitoring tools, it becomes difficult to track CPU usage, memory consumption, pod status, and node health.

The objective of this project is to implement a Kubernetes monitoring solution using Prometheus and Grafana on Google Kubernetes Engine (GKE). Prometheus collects cluster metrics, while Grafana visualizes the collected data through monitoring dashboards.

## Solution Approach

1. **Kubernetes Cluster Setup:** Used an existing Google Kubernetes Engine (GKE) cluster and verified that all nodes and pods were running successfully.

2. **Prometheus Deployment:** Deployed Prometheus using the Prometheus Community Helm chart (`kube-prometheus-stack`) to collect Kubernetes cluster metrics.

3. **Metric Collection:** Configured Prometheus to scrape metrics from Kubernetes nodes, pods, and services using ServiceMonitors, kube-state-metrics, and Node Exporter.

4. **Grafana Deployment:** Deployed Grafana along with the monitoring stack to visualize the metrics collected by Prometheus.

5. **Prometheus and Grafana Integration:** Configured Prometheus as a Grafana data source using the Kubernetes internal DNS name:
   `http://monitoring-kube-prometheus-prometheus:9090`

6. **External Access:** Exposed Prometheus and Grafana using Kubernetes LoadBalancer Services to access their web interfaces through external IP addresses.

7. **Dashboard Configuration:** Imported a Kubernetes monitoring dashboard into Grafana to visualize CPU usage, memory consumption, pod status, and node resource utilization.

8. **Monitoring and Validation:** Verified metric collection and monitored Kubernetes cluster health and performance through Grafana dashboards.

## Tools and Technologies

- Google Cloud Platform (GCP)
- Google Kubernetes Engine (GKE)
- Kubernetes
- Helm
- Prometheus
- Grafana
- Node Exporter
- kube-state-metrics
- PromQL



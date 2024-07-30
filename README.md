# Netflix-project


![devsecops](https://imgur.com/vORuBnK.png)


# Project Overview 

- I will be deploying a Netflix clone. I will be using Jenkins as a CICD tool and deploying my application on a Docker container and Kubernetes Cluster and i will monitor the Jenkins and Kubernetes metrics using Grafana, Prometheus and Node exporter.***


## Step 1: Launch an Ubuntu(22.04) 

## Step 2 : Install Jenkins, Docker and Trivy. Create a Sonarqube Container using Docker

- Install Jenkins, Docker and Trivy
- 2.1 — To Install Jenkins
- 2.2 — Install Docker
- 2.3 — Install Trivy

## Step 3: Create a TMDB API Key


## Step 4 : Install Prometheus and Grafana On the new Server

- Install Prometheus and Grafana On the new Server
- First of all, let's create a dedicated Linux user sometimes called a system account for Prometheus. Having individual users for each service serves two main purposes:
- It is a security measure to reduce the impact in case of an incident with the service.
- It simplifies administration as it becomes easier to track down what resources belong to which service.
- To create a system user or system account, run the following command:

```bash
sudo useradd \
    --system \
    --no-create-home \
    --shell /bin/false prometheus
```

- --system - Will create a system account.
- --no-create-home - I don't need a home directory for Prometheus or any other system accounts in our case.
- --shell /bin/false - It prevents logging in as a Prometheus user.
- Prometheus - Will create a Prometheus user and a group with the same name.
- Use the curl or wget command to download Prometheus.


## Step 5 : Install the Prometheus Plugin and Integrate it with the Prometheus server


## Step 6 : Email Integration With Jenkins and Plugin setup


## Step 7 : Install Plugins like JDK, Sonarqube Scanner, Nodejs, and OWASP Dependency Check

- Install Plugins like JDK, Sonarqube Scanner, NodeJs, OWASP Dependency Check
- 7.1 — Install Plugin
- Goto Manage Jenkins →Plugins → Available Plugins →

- Install below plugins
- 1 → Eclipse Temurin Installer (Install without restart)
- 2 → SonarQube Scanner (Install without restart)
- 3 → NodeJs Plugin (Install Without restart)

- 7.2 — Configure Java and Nodejs in Global Tool Configuration
- Goto Manage Jenkins → Tools → Install JDK(17) and NodeJs(16)→ Click on Apply and Save

- 7.3 — Create a Job
- create a job as Netflix Name, select pipeline and click on ok.

## Step 8 : Create a Pipeline Project in Jenkins using a Declarative Pipeline


## Step 9 : Install OWASP Dependency Check Plugins


## Step 10 : Docker Image Build and Push


## Step 11 : Deploy the image using Docker

- Kuberenetes Setup
- Connect your machines to Putty or Mobaxtreme
- Take-Two Ubuntu 20.04 instances one for k8s master and the other one for worker.
- Install Kubectl on Jenkins machine also.
- Kubectl is to be installed on Jenkins also


## Step 12: Kubernetes master and slave setup on Ubuntu (20.04)

- Access from a Web browser with
- <public-ip-of-slave:service port>

## Step 13: Access the Netflix app on the Browser

- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/c9fd56c4-8e24-40bd-b67a-c7cce5edc16a)
- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/0662da82-ad5c-45c1-a81b-10152b33cb44)
- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/64d0e773-4ce6-453f-9e77-368547582dd6)
- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/3662c450-6ef7-4727-ac3c-c222332ca205)
- ![image](https://github.com/user-attachments/assets/6639b3b8-9161-444c-99d2-ac0afed68fdf)
- ![image](https://github.com/user-attachments/assets/244d31a3-79aa-4e2b-aaa7-6b60949227c4)




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

- Next, I will create a TMDB API key
- Open a new tab in the Browser and search for TMDB
- Click on the first result, I will see this page
- Click on the Login on the top right. I will get this page.
- I need to create an account here. click on click here. I have account that's why i added my details there.
- once I create an account I will see this page.
- Let's create an API key, By clicking on my profile and clicking settings.
- Now click on API from the left side panel.
- Now click on create
- Click on Developer
- Now I have to accept the terms and conditions.
- Provide basic details
- Click on submit and I will get my API key.

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

- Install the Prometheus Plugin and Integrate it with the Prometheus server
- Let's Monitor JENKINS SYSTEM
- Need Jenkins up and running machine
- Goto Manage Jenkins --> Plugins --> Available Plugins
- Search for Prometheus and install it
- Once that is done I will Prometheus is set to /Prometheus path in system configurations
- Nothing to change click on apply and save
- To create a static target, I need to add job_name with static_configs. go to Prometheus server

```bash
sudo vim /etc/prometheus/prometheus.yml
```

- I will see Jenkins is added to it

- Let's add Dashboard for a better view in Grafana
- Click On Dashboard --> + symbol --> Import Dashboard
- Use Id 9964 and click on load
- Select the data source and click on Import
- Now I will see the Detailed overview of Jenkins

## Step 6 : Email Integration With Jenkins and Plugin setup

- Email Integration With Jenkins and Plugin Setup
- Install Email Extension Plugin in Jenkins
- Go to my Gmail and click on my profile
- Then click on Manage My Google Account --> click on the security tab on the left side panel I will get this page(provide mail password).
- 2-step verification should be enabled.
- Search for the app in the search bar I will get app passwords like the below image
- Click on other and provide my name and click on Generate and copy the password
- In the new update, I will get a password like this
- Once the plugin is installed in Jenkins, click on manage Jenkins --> configure system there under the E-mail Notification section configure the details as shown in the below image
- Click on Apply and save.
- Click on Manage Jenkins--> credentials and add my mail username and generated password
- This is to just verify the mail configuration
- Now under the Extended E-mail Notification section configure the details as shown in the below images
- Click on Apply and save.

```bash
post {
     always {
        emailext attachLog: true,
            subject: "'${currentBuild.result}'",
            body: "Project: ${env.JOB_NAME}<br/>" +
                "Build Number: ${env.BUILD_NUMBER}<br/>" +
                "URL: ${env.BUILD_URL}<br/>",
            to: 'tuanvu1332001@gmail.com',  
            attachmentsPattern: 'trivyfs.txt,trivyimage.txt'
        }
    }
```

- Next, I will log in to Jenkins and start to configure our Pipeline in Jenkins

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

- Install OWASP Dependency Check Plugins
- GotoDashboard → Manage Jenkins → Plugins → OWASP Dependency-Check. Click on it and install it without restart.
- First, we configured the Plugin and next, we had to configure the Tool
- Goto Dashboard → Manage Jenkins → Tools →
- Click on Apply and Save here.
- Now go configure → Pipeline and add this stage to my pipeline and build.

```bash
stage('OWASP FS SCAN') {
            steps {
                dependencyCheck additionalArguments: '--scan ./ --disableYarnAudit --disableNodeAudit', odcInstallation: 'DP-Check'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        stage('TRIVY FS SCAN') {
            steps {
                sh "trivy fs . > trivyfs.txt"
            }
        }
```

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
- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/3d6ace51-0218-475a-8b3d-0a3813c5413f)
- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/6db0292e-be3e-40d7-85ef-2541bfc0f79f)
- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/008c5e21-4ae8-4c87-a58d-80b43036b217)
- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/64d0e773-4ce6-453f-9e77-368547582dd6)
- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/3662c450-6ef7-4727-ac3c-c222332ca205)
- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/ee08dcf0-de79-4a76-a4ec-fea7aa644e02)
- ![image](https://github.com/rutikdevops/DevOps-Project-11/assets/109506158/0bfdfbd0-927e-4513-96bd-5029571fc8e3)



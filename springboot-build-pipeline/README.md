PRODUCTION GRADE DEVSECOPS CICD Pipeline

# Prereq: Create 2 EC2 servers

* Jenkinsmaster with 10GB storage - t2.micro
* Build server with 15GB storage - t2.medium
* Sonarqube server with 4 GB memory - t2.medium

![image](https://github.com/user-attachments/assets/e3ff8c48-c14d-4c1e-852b-7bd7f4999518)

## jenkins installation
https://github.com/DarrylNnon/Jenkins-Zero-To-Hero

![image](https://github.com/user-attachments/assets/2a964951-c934-42f8-b9e2-5ac9143d7672)

## Step 1: Ensure all the necessary plugins are installed in Jenkins Master

* Parameterized trigger plugin (This plugin lets you trigger new builds when your build has completed, with various ways of specifying parameters for the new build)
* Gitlab plugin (This plugin allows GitLab to trigger Jenkins builds and display their results in the GitLab UI.)
* Docker Pipeline (Build and use Docker containers from pipelines.)
* Pipeline: AWS steps (This plugins adds Jenkins pipeline steps to interact with the AWS API.)
* SonarQube Scanner (This plugin allows an easy integration of SonarQube, the open source platform for Continuous Inspection of code quality.)
* Quality Gates (Fails the build whenever the Quality Gates criteria in the Sonar analysis aren't met (the project Quality Gates status is different than "Passed"))

### Step 2: Install Docker, Java8, Java11 & Trivy on Build Server

$ sudo ./setup.sh

#### Step 3: Install Sonrqube on the t2.medium server

$ sudo apt update
$ sudo apt install -y docker.io
$ sudo usermod -a -G docker ubuntu
$ sudo docker run -d --name sonar -p 9000:9000 sonarqube:lts-community

#### Step 4: Add necessary credentials

Generate Sonarqube token of type "global analysis token" and add it as Jenkins credential of type "secret text"

Add dockerhub credentials as username/password type
Add Gitlab credentials
Add Build server credentials for Jenkins master to connect


#### Step 5: Enable Sonarqube webhook for Quality Gates & Install dependency-check plugin

# Generate webhook & add the Jenkins URL as follows - http://URL:8080/sonarqube-webhook/

# Docker-image-build-and-deploy-using-jenkins-pipeline

In this article we are building a Docker image and deploying it into Docker hub using Jenkins. We use multi agent setup for setting up our project.Here we use Jenkins pipeline to automate docker build and push to docker hub:

## Overall steps:

* Jenkins pipeline to build and push docker image:

  1. Clone flaskApp Project from Github. You can get my [FlaskApp Git](https://github.com/devasivaram/devops-flask-dev)
  2. Build docker image using docker build
  3. Login to docker hub
  4. Push image to docker hub
  5. create a conatiner from build image
  6. Log out from docker hub

## Pre-requisites:

  1. Jenkins master server with Git
  2. Build server (Docker installed)
  3. Test server
  4. Docker hub account

## Procedure:

### Step 1: Install Jenkins

We need to install jenkins for our master jenkins server, for installing jenkins:

~~~sh
amazon-linux-extras install epel -y
yum install java-1.8.0-openjdk-devel -y
wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
yum install jenkins -y
systemctl start jenkins.service
systemctl enable jenkins.service
~~~

Once Jenkins is installed, we can use this link for accesing jenkins: http://publicIPofserver:8080.

It will prompt for password token which can be fetched from: 
~~~sh
cat /var/lib/jenkins/secrets/initialAdminPassword
~~~

> We need to also install git to master server:

~~~sh
yum install git -y
~~~

### Step 2: Adding Docker hub to jenkins

Here, we add Docker Hub credentials into jenkins to get login access without passing credentials in script. 
For adding Docker hub credential in Jenkins:













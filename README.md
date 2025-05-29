# CI/CD Deployment with Jenkins, Ansible, and Tomcat

## Overview

This project creates a simple CI/CD pipeline using Jenkins, Ansible, and Apache Tomcat and three AWS EC2 instances.


<img width="468" alt="image" src="https://github.com/user-attachments/assets/52e052f7-0b06-4e93-aac4-b2112f2b7e31" />


## Architecture

- **EC2 Instance 1 (Master Node)**:  
  - Configured with Ansible  
  - User: `ansiblecontrol`  
  - Contains playbook `copywarfile.yml` to deploy WAR files to the Tomcat server

- **EC2 Instance 2 (Slave Node)**:  
  - Runs Apache Tomcat  
  - User: `managedhost`  
  - Receives WAR file deployments from Ansible

- **EC2 Instance 3 (Jenkins Server)**:  
  - Jenkins installed  
  - SSH plugins configured  
  - Triggers Ansible playbook after successful build from Git

## Workflow

1. Jenkins pulls code from GitHub.
2. Jenkins triggers the Ansible playbook on the master node.
3. Ansible copies the WAR file to Tomcat's webapps directory on the slave node.
4. Tomcat auto-deploys the application.

## Verify Deployment

http://<Tomcat_IP>:8080/manager/html



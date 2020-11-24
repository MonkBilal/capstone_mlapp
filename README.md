
[![CircleCI](https://circleci.com/gh/MonkBilal/mlapp.svg?style=svg)](https://circleci.com/gh/MonkBilal/mlapp)

## Project Summary

In this project, I have deployed a Flask app on an AWS EKS platform. This application is a pre-trained, sklearn model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on the data source site. This project is using a flask app 'app.py'-that serves out predictions (inference) about housing prices through API calls.


## Requirements

* An AWS account
* A Linux machine with Ansible installed.
* Git repository
* Dockerhub repository


## Setup the Environment

* Create IAM role with Admin access.
* Create an AWS EC2 instance for your Jenkins Machine with public ip enabled. (select t2.medium/t3.medium with ubuntu 18.04)
* Attach the previously created IAM role to your Jenkins machine.
* Add the public IP of your Jenkins Machine to your /etc/hosts file with name JenkinsMaster
  13.24.53.242  JenkinsMaster
* Login to your Jenkins machine and create default ssh keys for connecting to our Kubernetes cluster nodes.
* Go to your EC2 instance settings and enable port 8080 in your attached security group.
* Install Ansible on your machine and run the below command.
  $ ansible-playbook AnsibleJenkins2.yml -i inventory
  NOTE: Add your ec2 instance's private key path in the inventory file before running Ansible playbook.


## Setting up Jenkins

* Once your Ansible playbook finishes, go to your Jenkins machine's http://jenkinsmachinepublicip:8080 for accessing Jenkins Dashboard.
* Setup Jenkins with recommended setting and install Blue Ocean plugin.
* Add your docker hub credentials in Jenkins.
* Connect your jenkins to githubrepo.
* Run below command from your Jenkins Machine to check your LoadBalancer service and get the external IP for your app.
  kubectl get svc
  | NAME                   |  TYPE         | CLUSTER-IP       |    EXTERNAL-IP                                                              |     PORT(S)   | AGE  |
  | :----------------------: | :------------: | :----------------: | :--------------------------------------------------------------------------: | :-------------: | :---: |
  | capstone-mlapp-service | LoadBalancer |   10.100.xx.xx   | a08de26ad6c2xxxxxxxssxsssss249b800c9adq13130-XXXXXX.XXXXX.elb.amazonaws.com |  80:31591/TCP |  73m|

### Testing your app

* run below command
  $ ./make_prediction.sh <yourapphostaddress> <portnumber>

## Important Link

* Ansible Installation Guide: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
* Creating AWS account: https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/  
* Creating an IAM Role: https://www.eksworkshop.com/020_prerequisites/iamrole/
* Connect jenkins to github : https://sciencetechvideos.wordpress.com/2018/12/10/getting-started-with-blue-ocean-using-jenkins/

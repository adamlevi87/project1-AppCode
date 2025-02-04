# Deploying Dockerized App on AWS EKS Cluster using ArgoCD and GitOps methodology with CircleCI

This repository contains the code of the React application called ToDo-App. I've created this to Deploy it on the Kubernetes cluster by GitOps workflow.
As instroctued by this youtube guide (with some tweaks):
https://www.youtube.com/watch?v=LgBnbmfsIdA

## Architecture
![Architecture Diagram](https://cdn-images-1.medium.com/max/800/1*T5IRoSoiqT8qnYLUprsRUQ.png)

## List of AWS services
- Amazon EKS 
- Amazon VPC
- Amazon  IAM
- Amazon EC2
- Amazon Autoscaling 
- Amazon S3
- DynamoDB 

## Tech stack

- React Js

**This project contains Three GitHub repositories**

1. https://github.com/adamlevi87/project1-AppCode
2. https://github.com/adamlevi87/project1-kube_manifest
3. another repo (currently set to private).

the repo #3 holds: a bash script to set up a working enviorment for the creation, using Terraform (among others), for: AWS EKS, install a LB controller, ArgoCD and add the application to argoCD.
this repo is currently configrured in a way to allow this infrastructure to be created in an Amazon AWS sub-account (limited permissions) - where i am taking online course (Kodekloud- AWS playground).
Its a normal AWS account with some limitations, I have created the bash script / needed TF changes to compliy with the limitations set by them.

On this project we will be using a CI service called CircleCI. On any change on the repo #1 mentioned above it will:
a. build our dockerized application
b. push it to the selected docker service (docker hub)
c. Update the repo mentioned in #2 with the manifest (deployment & service yamls)



Variables that must be set on CircleCI's project (as mentioned in the config file project1-AppCode/.circleci/config.yml):
1. $DOCKER_USERNAME
2. $DOCKER_PASSWORD
3. $GITHUB_PERSONAL_TOKEN (created from your github account - developer settings. You must add permissions to this token too)



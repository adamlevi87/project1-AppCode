# Deploying Dockerized App on AWS EKS Cluster using ArgoCD and GitOps methodology with CircleCI

This repository contains the code of the React application called ToDo-App. I've created this to Deploy it on the Kubernetes cluster by GitOps workflow.

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


This repository will be used in the CI process where we will be using CircleCI, on any change on this repo, to:
build our dockerized application
push it to the selected docker service (docker hub)
update another github repository with the manifests (deployment & service yamls) to be used by ArgoCD to deploy/update the application on a kubernetes service (EKS) running on AWS.

Variables that must be set on CircleCI's project (as mentioned in the config file project1-AppCode/.circleci/config.yml):
1. $DOCKER_USERNAME
2. $DOCKER_PASSWORD
3. $GITHUB_PERSONAL_TOKEN (created from your github account - developer settings. You must add permissions to this token too)



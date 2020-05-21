# EKS CI/CD Pipeline with Jenkins

The Dockerfile is a build that compiles a simple nginx with default page replaced with the index.html file.

The Jenkinsfile outlines the stages from the linting of the html page, docker image build, docker image push
to DockerHUb and the deployment to kubernetes cluster on AWS EKS created with eksctl create command.

The deployment manifest files deploy the manifest and also a service that is configured wth the a LoadBalancer.
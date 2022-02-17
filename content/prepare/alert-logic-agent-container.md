# Install the Alert Logic Agent Container

You can deploy the Alert Logic Agent Container on the following container platforms:

Amazon Web Services (AWS)

* Amazon Elastic Container Service for Kubernetes (Amazon EKS)
* Amazon Elastic Container Service (Amazon ECS)
* Amazon ECS  running AWS Fargate
* AWS Elastic Beanstalk for Multicontainer Docker Environments
* CoreOS deployed on AWS EC2 instances
* Docker
* Kubernetes deployed on AWS EC2 instances

Microsoft Azure

* Azure Kubernetes Service (AKS)
* CoreOS on Azure
* Docker
* Kubernetes ACS-Engine

Google Cloud Platform

* Google Kubernetes Engine (GKE)

Data Center

* CoreOS
* Docker
* Kubernetes

Runtime Engines

* Docker
* Containerd

## Prerequisites

Before you can deploy the Alert Logic Agent Container, you must deploy and configure your [Network IDS appliance.](virtual-appliance.md)

## Deploy the Alert Logic Agent Container

Alert Logic hosts the readme files and the agent for each supported container platform on the public Alert Logic [GitHub page](https://github.com/alertlogic/al-agent-container).

## Alert Logic support for AWS Fargate

Security support for the AWS Fargate environment differs because  Fargate is a shared environment that hosts multiple customers. To learn more about AWS Fargate support, see [Deploy the Alert Logic Agent Container for AWS Fargate](agent-container-fargate.md).

## Alert Logic support for Istio

The Alert Logic Agent Container includes an Istio detector to inspect the traffic between your containers.  To learn more about Istio support, see [Istio Support for Containers](../configure/collectors/istio.md).

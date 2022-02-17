# Deploy the Alert Logic Agent Container for AWS Fargate

You can deploy the Alert Logic Agent Container in Amazon Elastic Container Service (ECS) environments that run Amazon Web Services (AWS) Fargate.

## AWS Fargate support

To  protect  environments that use  Fargate  with Amazon ECS,  the required method is to deploy the Alert Logic Agent Container as a sidecar in each Fargate ECS task. With this method, the Alert Logic agent can still access the network interfaces of that task. Alert Logic collects network traffic and syslog messages   from a specific task without violating the integrity of other customer environments in the AWS Fargate cluster.

For  Alert Logic to fully integrate with a container environment, the Docker socket must be mounted through the volume mounting capability in Docker, which the Fargate environment does not allow. For this reason, Alert Logic can protect containers on Fargate workloads but  does not discover other containers running on the host, capture traffic from their virtual network interfaces, or collect the native container logs stdout and stderr.

## Deployment instructions

Alert Logic hosts the readme file and the agent for each supported container platform on the public Alert Logic [GitHub page](https://github.com/alertlogic/al-agent-container).

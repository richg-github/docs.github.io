# Deploy the Alert Logic Agent Container for AWS Fargate (Beta)

    This document is intended for early-access customers.     
You can deploy the Alert Logic Agent Container in Amazon Elastic Container Service (ECS) environments that run Amazon Web Services (AWS) Fargate.

Use these instructions for environments running Amazon ECS tasks with the Fargate launch type. To deploy the Alert Logic Agent Container for Amazon ECS tasks with the EC2 launch type, see the [ECS README](https://algithub.pd.alertlogic.net/alertlogic/al-agent-container/blob/a8a620cc2df45dd329025064648988cd11095713/ecs/README.md) instead.

## AWS Fargate support

To  protect  environments that use  Fargate  with Amazon ECS,  the required method is to deploy the Alert Logic Agent Container as a sidecar in each Fargate ECS task. With this method, the Alert Logic agent can still access the network interfaces of that task. Alert Logic collects network traffic and syslog messages   from a specific task without violating the integrity of other customer environments in the AWS Fargate cluster.

For  Alert Logic to fully integrate with a container environment, the Docker socket must be mounted through the volume mounting capability in Docker, which the Fargate environment does not allow. For this reason, Alert Logic can protect containers on Fargate workloads but  does not discover other containers running on the host, capture traffic from their virtual network interfaces, or collect the native container logs stdout and stderr.

## Before you begin

Complete the following tasks before you deploy the Alert Logic Agent Container for Fargate.

Most customers should just need to update their IAM policy, and then auto-claim will work for Fargate. For Defender customers who do not allow us to discover their deployments, the fallback is the unique registration key. Set up your deployment and let us discover it using the latest policy. We should encourage them to set up their deployment so we can discover it using the latest policy. Still mention the fallback. URK was before we had cloud deployments and customers had to enter something that proved that it was our agent. With Fargate, we know that it is AWS, we discover it, so if an agent comes in, we have all the metadata that we need. We just need to tie that to an asset, the asset model, and we don't have that asset if fg discovery doesn't work. So that's why we need the IAM policy change. Two ways to do things. The URK is the old one. We suggest that we create the policies so that auto claim works. Let us discover your hosts so you don't have to worry about agent claim.

### Update your AWS IAM policies

To deploy and claim your containers for collection, you must update the appropriate AWS IAM policies with the following permissions:

```
`"ecs:Describe*",`
`"ecs:List*"`
`"workspaces:Describe*",`
`"workspaces:List*"`
```

The "ecs" updates enable the Alert Logic Cloud Explorer service to properly identify your ECS tasks, which later include the Fargate tasks that Alert Logic protects after you finish the Fargate deployment process. The "workspaces" updates prepare for upcoming AWS Workspaces support.

Alert Logic updated each policy with these permissions in the following files to make it easier to update the policy. Copy the appropriate policy and paste it into the AWS console.

* [Cloud Defender Minimal Policy](../pdf-files/defender-min.json)
* [Cloud Defender Full Policy](../pdf-files/defender.json)
* [MDR Minimal Policy: Automatic Mode](../pdf-files/insight-min.json)
* [MDR Full Policy: Automatic Mode](../pdf-files/insight.json)
* [MDR Minimal Policy: Manual Mode](../pdf-files/manual-min.json)
* [MDR Full Policy: Manual Mode](../pdf-files/manual.json)

If you do not add the permissions  to the appropriate policies, automatic claiming of agents fails when you deploy the Agent Container for Fargate. Cloud Defender customers who  use the minimal permission policy for deployment must also provide their unique registration key to claim their agents. Alert Logic strongly recommends deploying with full permissions to facilitate the discovery of your AWS environment and allow Alert Logic to automate the agent claim process.

### Find your unique registration key (Cloud Defender minimal permission deployments only)

Cloud Defender customers who deploy with the minimal permission policy must find their unique registration key to prepare for deploying  the  Agent Container for AWS Fargate. For all Managed Detection and Response (MDR) deployments and the Cloud Defender platform deployed with the full permission policy,  the unique registration key is not required. Alert Logic automates your AWS deployment in those environments and claims your agent automatically.

**To find your unique registration key (**Cloud Defender** platform minimal permission deployments only):**

1. In the Alert Logic console, click the Support Information icon.
2. Click "Details."
3. Copy your unique registration key.

### Install the AWS CLI

In  addition, be sure you install the AWS command line interface (CLI), and ensure you point it to, and configure it for, the appropriate AWS account. For more information about the AWS CLI, see [https://aws.amazon.com/cli/](https://aws.amazon.com/cli/).

## Deploy the Agent Container for Fargate

Complete the following tasks to protect your AWS Fargate deployments:

1. Modify your AWS Fargate task definition.
2. Update the task definition.
3. Deploy the updated task definition.

### Modify your AWS Fargate task definition

You must run the Alert Logic Agent Container  as a sidecar to each Fargate ECS task. Append the following entry to the `containerDefinitions` section of your Fargate ECS task:

```
`{`
`  "name": "al-agent",`
`  "image": "alertlogic/al-agent-container:latest",`
`  "environment": [`
`    {`
`      "name": "KEY",`
`      "value": "your_registration_key_here"`
`    }`
`  ]`
`}`
```

For the Cloud Defender platform minimal permission deployments only, in the task definition, update the `value` variable with your unique registration key.

For all MDR deployments and the Cloud Defender platform deployed with the full permission policy, leave the `KEY` environment variable undefined. AWS deployments with valid credentials do not require registration keys. The Alert Logic agent and back end gather cloud metadata to provision the deployment.

### Update the task definition

To register your task definition, enter the following command in the AWS CLI:

`aws ecs register-task-definition --cli-input-json file://path//to/task-definition.json`

### Deploy the updated task definition

Use your preferred method to deploy the updated task definition. For example, you can enter the following command in the AWS CLI and replace the `{service_using_task_definition}` and `{task_definition_name}` variables with valid values:

`aws ecs update-service --service {service_using_task_definition} --task-definition {task_definition_name}`

For reference, see the [AWS update-service documentation](https://docs.aws.amazon.com/cli/latest/reference/ecs/update-service.html).

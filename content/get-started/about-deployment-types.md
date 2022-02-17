# About  Deployment Types

A deployment allows you to monitor and protect a defined set of assets from your appliances, agents, hosts, and collectors from your environments. You can create deployments for assets found in your Amazon Web Services (AWS), Microsoft Azure, and other cloud-based or physical data centers.

Alert Logic discovers and organizes deployments into a visual topology where you can select the desired levels of protection for your assets. You must choose one of the following levels of coverage for each asset:

* Unprotected
* Alert Logic Essentials coverage
* Alert Logic Professional coverage

## Coverage protection levels

For more detailed information about protection levels, see [Get Started with Alert Logic   Subscriptions and Add-ons](subscriptions-addons.md).

### Alert Logic Essentials

Alert Logic MDR Essentials coverage provides deployment automation for assets in your AWS or Azure environments, access to continuous asset discovery, and asset visibility for your deployments. Alert Logic continuously tests your environments with vulnerability scanning and cloud configuration scanning to help you detect and remediate exposures.

### Alert Logic Professional

Alert Logic MDR Professional coverage provides the capabilities from Essentials, plus access to network intrusion detection, and log and security analytics.

## Deployment types

### AWS Deployments

Alert Logic supports integrations with several AWS security services. To protect your AWS deployment, you must set up an AWS cross-account role to allow Alert Logic access to your AWS account. The Alert Logic console steps you through IAM role creation.

Alert Logic supports integration with [AWS Outposts](https://aws.amazon.com/outposts/). AWS Outposts is a fully managed service that offers AWS infrastructure, services, APIs, and tools to any datacenter, co-location space, or on-premises facility for a consistent hybrid experience. AWS compute, storage, database, and other services run locally on Outposts, and you can access the full range of AWS services to build, manage, and scale your on-premises applications using AWS services and tools. If you have AWS Outposts configured, you can deploy Alert Logic Managed Detection and Response using whichever deployment mode you prefer.

Alert Logic provides AWS CloudFormation templates to automate creation of the correct policy and role for the deployment mode you choose. The deployment mode you choose determines how Alert Logic deploys your scanning instances. You can also choose to employ manual setup in which you log into the AWS console and create your IAM policy and role.

Each AWS deployment mode allows a different level of control over the creation of scanning instances and subnets.

#### Automatic Mode

Automatic Mode is available only for AWS deployments. Alert Logic recommends  Automatic Mode  if you want Alert Logic to deploy and maintain new VPC subnets used for scanning instances. If you choose Automatic Mode, you can create the IAM policy and role by using either an AWS CloudFormation template or your own policy document.

If you create a deployment with Automatic Mode, Alert Logic creates the following AWS resources:

* A CloudTrail log source if one is not present
* A new Outcomes SQS Queue
* An SNS Topic if one is not available and linked to the CloudTrail log source

For an Essentials subscription, Alert Logic automatically deploys the following AWS resources:

* A single /28 subnet per scoped VPC with required routing to the Internet (Internet gateway and routing table setup)
* A single scanning EC2 instance (c5.large by default)

For a Professional subscription or the Enterprise add-on, Alert Logic automatically deploys the following AWS resources:

* One /28 subnet per VPC for the scanning appliance
* A single scanning EC2 instance (c5.large by default)—outbound Internet connectivity required
* A /28 subnet for each IDS appliance deployed in each Availability Zone
* One IDS instance per Availability Zone (c5.xlarge by default)—outbound Internet connectivity required

For information about creating an AWS deployment for each subscription level by using Automatic Mode, see:

* [Amazon Web Services (AWS) Deployment Configuration—Automatic Mode (Essentials Subscription)](../deploy/aws-auto-essentials.md)
* [Amazon Web Services (AWS) Deployment Configuration—Automatic Mode (Professional Subscription)](../deploy/aws-auto-pro-ent.md)

#### Manual Mode

Select Manual Mode if you want to manage subnets for scanning instances when you create an AWS deployment. If you choose Manual Mode, you can create the IAM policy and role by using either an AWS CloudFormation template or your own policy document.

An Essentials subscription requires that you log into AWS and set up a  single scanning EC2 instance (c5.large by default)—outbound Internet connectivity required—deployed into the subnet of your choice.

Professional and Enterprise subscriptions require you to log into AWS and set up the following resources:

* A single scanning EC2 instance (c5.large by default)—outbound Internet connectivity required—deployed into the subnet of your choice
* Minimum of one IDS per VPC (c5.large by default)

    If you feel that you need to scale your appliance to a size larger than c5.2xlarge, you can mitigate costs by using multiple smaller appliances.  Alert Logic supports the use of multiple appliances with Availability Zone awareness.     
In addition, Manual Mode deployments require you to log into the AWS console and configure the following AWS services:

* Set up a CloudTrail log source:
   * Create a CloudTrail and SNS topic, or
   * Use an existing CloudTrail and SNS topic.
* Configure an Amazon S3 bucket policy.
* Deploy a network IDS appliance (Professional and Enterprise subscriptions only).
* Deploy a scanning appliance.

For information about creating an AWS deployment for each subscription level using Manual Mode, see:

* [Amazon Web Services (AWS) Deployment Configuration—Manual Mode (Essentials Subscription)](../deploy/aws-manual-essentials.md)
* [Amazon Web Services (AWS) Deployment Configuration—Manual Mode  (Professional Subscription)](../deploy/aws-manual-pro-ent.md).

### Azure Deployments

Alert Logic supports integration with several Azure services. To protect your Azure deployment, you must create a Role-Based Access Control (RBAC) role in Azure to allow Alert Logic to access your account.

As part of deployment creation, you must log into Azure and deploy appliances. An Essentials subscription requires that you set up a single IDS appliance which, for an  Essentials subscription, goes into scan-only mode.

For Professional and Enterprise subscriptions, set up:

* Install appliance
* Install agent

For information about creating an Azure deployment for each subscription level, see:

* [Microsoft Azure Deployment Configuration (Essentials Subscription)](../deploy/azure-essentials.md)
* [Microsoft Azure Deployment Configuration (Professional Subscription)](../deploy/azure-pro-ent.md)

### Data Center deployments

The Data Center deployments allow you to monitor and protect your cloud-based or on-premisis data centers. The Data Center page in the Alert Logic console displays the list of appliances, agents, hosts, and log collectors if subscribed to the Professional  coverage.

For an Essentials subscription, you must:

* Go through the Managed Detection and Response setup in the Alert Logic console.
* Deploy the Alert Logic appliance.
* Implement necessary Alert Logic firewall rules for the [US](../requirements/us-firewall-rules.md) or [UK/EU](../requirements/uk-eu-firewall-rules.md).

For Professional and Enterprise subscriptions, set up:

* Go through the Managed Detection and Response setup in the Alert Logic console.
* Deploy the Alert Logic appliance.
* Install agents or, if you do not set up agents, set up network SPAN.
* Implement necessary Alert Logic firewall rules for the [US](../requirements/us-firewall-rules.md) or [UK/EU](../requirements/uk-eu-firewall-rules.md).

For more information about creating a Data Center deployment for each subscription level, see:

* [Data Center Deployment Configuration (Essentials Subscription)](../deploy/data-center-essentials.md)
* [Data Center Deployment Configuration (Professional Subscription)](../deploy/data-center-pro-ent.md)

For information about using the Data Center deployment method for a Google Cloud Platform environment, see:

* [Data Center Deployment Configuration for Google Cloud Platform (Essentials Subscription) ](../deploy/google-cloud-essentials.md)
* [Data Center Deployment for Google Cloud Platform (Professional Subscription)](../deploy/google-cloud-pro-ent.md)

---
title: "Introduction to Deployments"
date: 2018-12-29T11:02:05+06:00
weight: 4
draft: false
---

A deployment allows you to monitor and protect a defined set of assets from your appliances, agents, hosts, and collectors from your environments. You can create deployments for assets found in your AWS, Azure, and other cloud-based or physical data centers.

Alert Logic allows you to select the desired levels of protection for your assets. You must choose one of the following levels of coverage for each asset:

* Unprotected
* Alert Logic Essentials coverage
* Alert Logic Professional coverage

### Coverage protection levels

For more detailed information about protection levels, see Get Started with Alert Logic Subscriptions and Add-ons.

### Alert Logic Essentials

Alert Logic Essentials coverage provides deployment automation for assets in your AWS or Azure environments, access to continuous asset discovery, and asset visibility for your deployments. Alert Logic continuously tests your environments with vulnerability scanning and cloud configuration scanning to help you detect and remediate exposures.

### Alert Logic Professional

Alert Logic Professional coverage provides the capabilities from Essentials, plus access to network intrusion detection, and log and security analytics.

### Deployment types

### AWS Deployments

Alert Logic supports integrations with several AWS security services. To protect your AWS deployment, you must set up an AWS cross-account role to allow Alert Logic access to your AWS account. The Alert Logic console steps you through IAM role creation.

Alert Logic provides AWS CloudFormation templates to automate creation of the correct policy and role for the deployment mode you choose. The deployment mode you choose determines how Alert Logic deploys your scanning instances. You can also choose to employ manual setup in which you log into the AWS console and create your IAM policy and role.

Each AWS deployment mode allows a different level of control over the creation of scanning instances and subnets.

### Automatic Mode

Automatic Mode is available only for AWS deployments. Alert Logic recommends Automatic Mode if you want Alert Logic to deploy and maintain new VPC subnets used for scanning instances. If you choose Automatic Mode, you can create the IAM policy and role by using either an AWS CloudFormation template or your own policy document.

If you create a deployment with Automatic Mode, Alert Logic creates the following AWS resources:

* A CloudTrail log source if one is not present
* A new Outcomes SQS Queue
* An SNS Topic if one is not available and linked to the CloudTrail log source
* For an Essentials subscription, Alert Logic automatically deploys the following AWS resources:
* A single /28 subnet per scoped VPC with required routing to the Internet (Internet gateway and routing table setup)
* A single scanning EC2 instance (c5.large by default)

For a Professional subscription or the Enterprise add-on, Alert Logic automatically deploys the following AWS resources:

* One /28 subnet per VPC for the scanning appliance
* A single scanning EC2 instance (c5.large by default)—outbound Internet connectivity required
* A /28 subnet for each IDS appliance deployed in each Availability Zone
* One IDS instance per Availability Zone (c5.xlarge by default)—outbound Internet connectivity required

### Manual Mode

Select Manual Mode if you want to manage subnets for scanning instances when you create an AWS deployment. If you choose Manual Mode, you can create the IAM policy and role by using either an AWS CloudFormation template or your own policy document.

An Essentials subscription requires that you log into AWS and set up a single scanning EC2 instance (c5.large by default)—outbound Internet connectivity required—deployed into the subnet of your choice.

Professional subscriptions require you to log into AWS and set up the following resources:

* A single scanning EC2 instance (c5.large by default)—outbound Internet connectivity required—deployed into the subnet of your choice
* Minimum of one IDS per VPC (c5.large by default)

If you feel that you need to scale your appliance to a size larger than c5.2xlarge, you can mitigate costs by using multiple smaller appliances. Alert Logic supports the use of multiple appliances with Availability Zone awareness.

In addition, Manual Mode deployments require you to log into the AWS console and configure the following AWS services:

* Set up a CloudTrail log source:
    * Create a CloudTrail and SNS topic, or
    * Use an existing CloudTrail and SNS topic.
* Configure an Amazon S3 bucket policy.
* Deploy a network IDS appliance (Professional subscription only).
* Deploy a scanning appliance.

### Azure Deployments

Alert Logic supports integration with several Azure services. To protect your Azure deployment, you must create a Role-Based Access Control (RBAC) role in Azure to allow Alert Logic to access your account.

As part of deployment creation, you must log into Azure and deploy appliances. An Essentials subscription requires that you set up a single IDS appliance which, for an Essentials subscription, goes into scan-only mode.

For Professional subscriptions, set up:

* Install appliance
* Install agent

### Data Center deployments

The Data Center deployments allow you to monitor and protect your cloud-based or on-premisis data centers. The Data Center page in the Alert Logic console displays the list of appliances, agents, hosts, and log collectors if subscribed to the Professional coverage.

For an Essentials subscription, you must:

* Deploy the Alert Logic appliance.
* Implement necessary Alert Logic firewall rules for the US or UK/EU.

For Professional and Enterprise subscriptions, set up:

* Deploy the Alert Logic appliance.
* Install agents or, if you do not set up agents, set up network SPAN.
* Implement necessary Alert Logic firewall rules for the US or UK/EU.
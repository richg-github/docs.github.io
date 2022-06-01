# Introduction to Deployments

<p>A deployment allows you to monitor and protect a defined set of assets from your appliances, agents, hosts, and collectors from your environments. You can create deployments for assets found in your <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />, <MadCap:variable name="SDKVariables.Azure" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />, and other cloud-based or physical data centers.</p>

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> allows you to select the desired levels of protection for your assets. You must choose one of the following levels of coverage for each asset:</p>

<ul>
  <li>Unprotected</li>
  <li>
    <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
    <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> coverage</li>
  <li>
    <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
    <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> coverage</li>
</ul>## Coverage protection levels

<p>For more detailed information about protection levels, see <a href="https://docs.alertlogic.com/get-started/deployments.htm" title="Get Started with Alert Logic Subscriptions and Add-ons" alt="Get Started with Alert Logic Subscriptions and Add-ons">Get Started with <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Subscriptions and Add-ons</a>.</p>

<h3>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
</h3><p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> coverage provides deployment automation for assets in your AWS or Azure environments, access to continuous asset discovery, and asset visibility for your deployments. <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> continuously tests your environments with vulnerability scanning and cloud configuration scanning to help you detect and remediate exposures.</p>

<h3>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
</h3><p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> coverage provides the capabilities from <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />, plus access to network intrusion detection, and log and security analytics.</p>

## Deployment types

### AWS Deployments

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> supports integrations with several AWS security services. To protect your AWS deployment, you must set up an AWS cross-account role to allow <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> access to your AWS account. The <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> console steps you through IAM role creation.</p>

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> provides AWS CloudFormation templates to automate creation of the correct policy and role for the deployment mode you choose. The deployment mode you choose determines how <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> deploys your scanning instances. You can also choose to employ manual setup in which you log into the AWS console and create your IAM policy and role.</p>

Each AWS deployment mode allows a different level of control over the creation of scanning instances and subnets.

#### Automatic Mode

<p>Automatic Mode is available only for AWS deployments. <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> recommends Automatic Mode if you want <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> to deploy and maintain new VPC subnets used for scanning instances. If you choose Automatic Mode, you can create the IAM policy and role by using either an AWS CloudFormation template or your own policy document.</p>

<p>If you create a deployment with Automatic Mode, <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> creates the following AWS resources:</p>

<ul>
  <li>A CloudTrail log source if one is not present</li>
  <li>A new Outcomes SQS Queue</li>
  <li>An SNS Topic if one is not available and linked to the CloudTrail log source</li>
  <li>For an <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> subscription, <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> automatically deploys the following AWS resources:</li>
  <li>A single /28 subnet per scoped VPC with required routing to the Internet (Internet gateway and routing table setup)</li>
  <li>A single scanning EC2 instance (c5.large by default)</li>
</ul><p>For a Professional subscription or the Enterprise add-on, <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> automatically deploys the following AWS resources:</p>

* One /28 subnet per VPC for the scanning appliance
* A single scanning EC2 instance (c5.large by default)—outbound Internet connectivity required
* A /28 subnet for each IDS appliance deployed in each Availability Zone
* One IDS instance per Availability Zone (c5.xlarge by default)—outbound Internet connectivity required

#### Manual Mode

Select Manual Mode if you want to manage subnets for scanning instances when you create an AWS deployment. If you choose Manual Mode, you can create the IAM policy and role by using either an AWS CloudFormation template or your own policy document.

<p>An <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> subscription requires that you log into AWS and set up a single scanning EC2 instance (c5.large by default)—outbound Internet connectivity required—deployed into the subnet of your choice.</p>

Professional subscriptions require you to log into AWS and set up the following resources:

* A single scanning EC2 instance (c5.large by default)—outbound Internet connectivity required—deployed into the subnet of your choice
* Minimum of one IDS per VPC (c5.large by default)

<p>If you feel that you need to scale your appliance to a size larger than c5.2xlarge, you can mitigate costs by using multiple smaller appliances. <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> supports the use of multiple appliances with Availability Zone awareness.</p>

In addition, Manual Mode deployments require you to log into the AWS console and configure the following AWS services:

<ul>
  <li>Set up a CloudTrail log source:</li>
  <ul>
    <li>Create a CloudTrail and SNS topic, or</li>
    <li>Use an existing CloudTrail and SNS topic.</li>
  </ul>
  <li>Configure an Amazon S3 bucket policy.</li>
  <li>Deploy a network IDS appliance (<MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> subscription only).</li>
  <li>Deploy a scanning appliance.</li>
</ul>### Azure Deployments

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> supports integration with several Azure services. To protect your Azure deployment, you must create a Role-Based Access Control (RBAC) role in Azure to allow <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> to access your account.</p>

<p>As part of deployment creation, you must log into Azure and deploy appliances. An <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> subscription requires that you set up a single IDS appliance which, for an <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> subscription, goes into scan-only mode.</p>

<p>For <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> subscriptions, set up:</p>

* Install appliance
* Install agent

### Data Center deployments

<p>The Data Center deployments allow you to monitor and protect your cloud-based or on-premisis data centers. The Data Center page in the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> console displays the list of appliances, agents, hosts, and log collectors if subscribed to the <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> coverage.</p>

<p>For an <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> subscription, you must:</p>

<ul>
  <li>Deploy the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> appliance.</li>
  <li>Implement necessary <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> firewall rules for the US or UK/EU.</li>
</ul><p>For <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> and Enterprise subscriptions, set up:</p>

<ul>
  <li>Deploy the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> appliance.</li>
  <li>Install agents or, if you do not set up agents, set up network SPAN.</li>
  <li>Implement necessary <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> firewall rules for the US or UK/EU.</li>
</ul>

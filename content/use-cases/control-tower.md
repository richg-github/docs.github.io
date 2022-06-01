# AWS Control Tower

<p>The following capabilities are included with <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />:</p>

* Threat detection that spans the entire attack surface and operates at scale
* Protection for your business, including your containers and applications, with the proven combination of a network [intrusion detection system](https://www.alertlogic.com/solutions/network-intrusion-detection-system-ids/) (IDS), [vulnerability management](https://www.alertlogic.com/solutions/network-vulnerability-management/), [log management](https://www.alertlogic.com/solutions/log-management-solution/), [extended endpoint protection](https://www.alertlogic.com/solutions/extended-endpoint-protection/) and [web application firewall](https://www.alertlogic.com/solutions/web-application-firewall/) protection for hybrid, cloud, and on-premises environments
* Threat intelligence based on industry data and expert security analyst research, with machine-learning based on data analysis across thousands of customers’ attack surface
* Real-time alerting, incident verification, and remediation guidance from experts available 24/7 with a 15-minute service-level agreement for verified incidents

## Supported subscription types

<ul>
  <li>
    <MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
    <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>
    <MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
    <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
</ul>## Architecture diagram

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Control Tower Automation uses the following AWS Services to enable automatic protection of newly added AWS Accounts:</p>

<ul>
  <li>Amazon EventBridge</li>
  <li>
    <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> CloudFormation Stack and StackSets</li>
  <li>
    <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Lambda</li>
  <li>Cross-account IAM Roles</li>
</ul>
The automation CloudFormation Stack is deployed in a Control Tower master account which creates two Lambda FunctionsCloudFormation StackSet that deploy to protected linked accounts.

<p>
  <MadCap:annotation MadCap:createDate="2020-06-15T12:08:46.9407956-05:00" MadCap:creator="jacqueline.reyes" MadCap:initials="JA" MadCap:comment="This sentence is in passive voice, but I don't have more information on it to help you rewrite it" MadCap:editor="jacqueline.reyes" MadCap:editDate="2020-06-15T12:09:10.2302412-05:00" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">In</MadCap:annotation> the Security Account, an SNS Topic is created, two Lambda functions are deployed, and an Amazon EventBridge is created to subscribe for tag updates from linked accounts.</p>

![](../Resources/Images/Alert-Logic-AWS-ControlTower-Implementation Guide/Architecture diagram.png)<MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
Accounts Presented in the Architecture Diagram

<ol>
  <li>Control Tower Account—Master account on which <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Control Tower was enabled</li>
  <li>Log Archive Account—A centralized CloudTrail log account</li>
  <li>Audit Account—A centralized CloudTrail SNS Topic account </li>
  <li>Security Account—An account where <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Control Tower automation orchestration is deployed</li>
  <li>Linked Account—One or more <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> accounts protected by <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />. <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> deploys appliances and agents are deployed into this account.</li>
</ol>## Overview

<ol>
  <li>During the CloudFormation Stack deployment, the following changes are made to the Control Tower master account of the customer:</li>
  <ol style="list-style-type: lower-alpha;">
    <li>AlertLogic-CT StackSet is created. This StackSet is deployed to linked accounts to correctly set them up to be protected by <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />.</li>
    <li>Onboarding Lambda is created and called to setup CloudTrail SQS to enable <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> subscription to <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> CloudTrail.</li>
    <li>Lifecycle Lambda is created which subscribes to CreateManagedAccount Control Tower events.</li>
  </ol>
  <li>When new linked account is added to Control Tower, Lifecycle Lambda function creates and launches AlertLogic-CT StackSet in a linked account. The following changes are made: </li>
  <ol style="list-style-type: lower-alpha;">
    <li>AlertLogic-CT StackSet creates a third-party role to enable monitoring and automatic deployment of <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> infrastructure to linked Account.</li>
    <li>Sends SNS Notification to Security Account SNS Topic to indicate new account provisioning.</li>
  </ol>
  <li>
    <MadCap:annotation MadCap:createDate="2020-06-15T16:51:16.8911612-05:00" MadCap:creator="jacqueline.reyes" MadCap:initials="JA" MadCap:comment="This sentence doesn't make any sense, " MadCap:editor="jacqueline.reyes" MadCap:editDate="2020-06-15T16:51:58.4688500-05:00" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">Security</MadCap:annotation> Account Lambdas  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Deployments in the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> and scope of protection. The later is done when a VPC is tagged with AlertLogic tag.</li>
</ol>## Prerequisites

The solution does not require any additional resources to be enabled outside the ones already enabled by AWS Control Tower.

In addition, it is unlikely that a customer will need to increase any limits, but it is important to note that the automation solution creates an EventBridge in a security account to capture tag updates in linked accounts.

<p>Before you implement this solution, <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> recommends that you become familiar with <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> CloudFormation, <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Lambda, <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> CloudTrail and Amazon EventBridge services.</p>

<p>If you are new to <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />, see <a href="https://aws.amazon.com/getting-started/">Getting Started with AWS</a>.</p>

<p>For additional information on <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />Marketplace, see <a href="https://aws.amazon.com/marketplace/help/about-us?ref_=footer_nav_about_aws_marketplace">this documentation on AWS Marketplace</a>.</p>

To get started with awsControl Tower, see the [AWS documentation on Control Tower](https://docs.aws.amazon.com/controltower/latest/userguide/getting-started-with-control-tower.html).

## Deployment and Configuration

<h3>Subscribe to <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> on the AWS Marketplace</h3><ol>
  <li>
    <p>Locate <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> in the AWS Marketplace (<a href="https://aws.amazon.com/marketplace/pp/B07K2J16QH?ref_=beagle"><MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> (US)</a>, <a href="https://aws.amazon.com/marketplace/pp/B07KJMQN6X?ref_=beagle"><MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> (UK)</a><a href="https://aws.amazon.com/marketplace/pp/B07S64BX2Q?ref_=beagle"><MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Professional - SaaS Contract (US)</a> or <a href="https://aws.amazon.com/marketplace/pp/B07SB6P6N7?ref_=beagle"><MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Professional - SaaS Contract (UK)</a>).</p>
    <img src="../Resources/Images/Alert-Logic-AWS-ControlTower-Implementation Guide/Deployment and.png" class="body" />
    <MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>Click <b>Continue to Subscribe</b>.</li>
  <p>
    <img src="../Resources/Images/Alert-Logic-AWS-ControlTower-Implementation Guide/Deployment and_1.png" />
  </p>
  <li>
    <p>Next, configure your contract. You can select the <b>Contract Duration</b> and set the <b>Renewal Settings</b>.</p>
    <img src="../Resources/Images/Alert-Logic-AWS-ControlTower-Implementation Guide/Deployment and_2.png" class="body" />
    <MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>
    <p>Select the Contract Options to be activated with your contract.</p>
    <img src="../Resources/Images/Alert-Logic-AWS-ControlTower-Implementation Guide/Deployment and_3.png" class="body" />
    <MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>When you configure your contract, click <b>Create contract</b>.</li>
  <li>You will be prompted to confirm the contract. If you agree to the pricing, click <b>Pay Now</b>.</li>
  <li>Check your email for the validation email from <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />. After you confirm receipt, <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> sends another email to enable password reset and the access to the <MadCap:variable name="SDKVariables.ALUI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> is granted.</li>
</ol>### Log into the Partner UI        

<ol>
  <li>Create  an access key and a secret key in the <MadCap:variable name="SDKVariables.ALUI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />. For more information about how to create an access key and secret key, see <a href="https://docs.alertlogic.com/prepare/access-key-management.htm" title="Create and Manage Alert Logic Access Keys" alt="Create and Manage Alert Logic Access Keys">Create and Manage <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Access Keys</a>.</li>
  <li>Download the code from <kbd>&amp;lt;partner-github-repository&amp;gt;</kbd></li>
  <li>Log into<kbd> &amp;lt;MASTER|LOG|XXX&amp;gt; </kbd>account in AWS Control Tower as <kbd>&amp;lt;Permissions&amp;gt;</kbd>.</li>
  <li>To deploy the solution, create a new CloudFormation Stack using <a href="https://s3.amazonaws.com/alertlogic-public-repo.us-east-1/templates/ct-al-master-onboarding.yaml">this template</a>.</li>
  <li>
    <p>Provide the following information to deploy the CloudFormation Stack:</p>
  </li>
  <ul>
    <li>
      <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> API Access Key and <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> API Secret Key</li>
    <li>
      <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> CustomerID –  on the Support page in the <MadCap:variable name="SDKVariables.ALUI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /></li>
    <li>Control Tower Audit Account ID – Control Tower AWS audit account</li>
    <li>LogArchiveAccount  Control Tower  account</li>
    <li>SecurityAccount – Designated <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> security account</li>
    <li>TargetRegion – List of regions to enable <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> deployment into</li>
  </ul>
</ol>### Verify linked accounts

<p>After CloudFormation deployment completion, you will see linked accounts listed as deployments in the <MadCap:variable name="SDKVariables.ALUI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />.</p>

### Validate that the solution is properly deployed

<p>The <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> appliance will automatically deployed within 15 minutes to the linked accounts.</p>

<p>In addition, you are responsible for installing  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Agents to protected hosts. </p>

<p>Follow these instructions to deploy <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Agents for <a href="https://docs.alertlogic.com/prepare/alert-logic-agent-linux.htm">Linux</a> or <a href="https://docs.alertlogic.com/prepare/alert-logic-agent-windows.htm">Windows.</a></p>

The agents are automatically claimed and assigned to the appliances.

### After installation        

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  <MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> solution automatically analyzes network traffic, logs (CloudTrail and host logs) and scan hosts for vulnerabilities. This information can be accessed through the <MadCap:variable name="SDKVariables.ALUI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />.</p>

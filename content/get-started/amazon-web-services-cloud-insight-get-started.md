# Get Started with Alert Logic Cloud Insight and Cloud Insight Essentials

Cloud Insight Essentials requires you perform some actions within Amazon Web Services (AWS) before  Cloud Insight Essentials can start protecting your deployments. These actions and other configurations, both in AWS and in Cloud Insight Essentials, allow Alert Logic to provide you with the most relevant data you want to monitor.

## About Cloud Insight Essentials deployments

When you set up Cloud Insight Essentials, you create a [deployment](#ci-deployments), which allows Alert Logic access to your AWS account and the services you want to monitor and protect. Deployments typically consist of one AWS account and all the associated AWS services for that account, but Cloud Insight Essentials allows you to define exactly what to monitor. When you create a deployment, you must choose a level of assessment to monitor and protect your assets. Alert Logic offers the following assessment levels:

* Cloud Insight Essentials2. Cloud Insight
   * Includes all the capabilities of Cloud Insight Essentials, plus vulnerability assessments in your deployment, which adds visibility to vulnerabilities on your EC2 instance workloads.
   * Allows Alert Logic to spin up AWS subnets and instances in your AWS infrastructure, which incurs additional costs from Alert Logic for scanning per host, and additional costs from AWS for the instances Alert Logic creates.
   * Configuration checks based on a library of AWS and Alert Logic configuration best practices checks that are continuously tested in your AWS accounts to help detect and remediate exposures.
   * Integration with AWS services, like Amazon GuardDuty, Inspector, and Config Rules.

    To help manage costs associated with scanning, Alert Logic shuts down  scanning instances after completion of each scanning cycle. If you want to disable this feature and keep scanning instances running in your subnets, see this [Alert Logic Knowledge Base article](https://support.alertlogic.com/hc/en-us/articles/360001452271).     ## About Amazon GuardDuty

Amazon GuardDuty is a continuous security monitoring service that requires no customer-managed hardware or software. GuardDuty analyzes and processes VPC Flow Logs and AWS CloudTrail event logs. GuardDuty uses security logic and AWS usage statistics techniques to identify unexpected and potentially unauthorized and malicious activity, like escalations of privileges, uses of exposed credentials, or communication with malicious IPs, URLs, or domains.

If you enable GuardDuty in AWS, your Cloud Insight and Cloud Insight Essentials deployments can integrate GuardDuty security findings for display on the Incidents page, which allows  you to analyze the findings, and get recommendations on how to respond. For information about enabling GuardDuty, see [Enable Amazon GuardDuty](#enable-guardduty).

## Requirements and considerations

Cloud Insight Essentials and Cloud Insight deployments have different requirements and configurations to consider before you create a deployment.

### Cloud Insight Essentials requirements and considerations

Cloud Insight Essentials requires that you create an AWS IAM policy and role to allow Alert Logic access to your AWS assets to monitor them. For more information about creating our policy document, see [Why do I need an IAM policy?](#why-policy)

Consider enabling Amazon GuardDuty, which you can integrate into your Cloud Insight Essentials deployments to display security findings on the Incidents page. For information about enabling GuardDuty, see [Enable Amazon GuardDuty](#enable-guardduty).

For more information about deployments, and creation of a Cloud Insight Essentials deployment, see [Set up and manage deployments](#ci-deployments).

### Cloud Insight requirements and considerations

Cloud Insight has the same requirements as Cloud Insight Essentials, and also requires that you:

* Ensure an available /28 subnet.
* Configure security groups.
* Add host credentials.

Cloud Insight deployment creation also requires that you select one of two deployment modes. The two deployment modes allow different levels of control over the creation of scanning instances and subnets, but your choice could affect how you manage and maintain aspects of your security infrastructure.

* **Select Automatic Mode** (recommended) if you want Alert Logic to deploy and maintain much of your security infrastructure. If you use Automatic Mode to create a deployment, Alert Logic creates a subnet in which to deploy a security appliance in each VPC within the deployment scope. In addition, Alert Logic:
   * Manages routing for the subnet.
   * Manages network ACLs for that subnet and other subnets in the VPC.
* **Select Guided Mode** if Automatic Mode is not possible, because:
   * You have VPCs with no available space to create a subnet in which to deploy scanning instances.
   * Your corporate or IT policies do not allow a third party to perform some of the actions permitted with Automatic Mode, such as subnet creation and routing management.
   * Your network layout requires that components of security infrastructure, such as a management subnet used by multiple tools, reside in an existing subnet.
   * Any situation in which Alert Logic cannot create and manage a dedicated security subnet in all your VPCs.

Consider enabling Amazon GuardDuty, which you can integrate into your Cloud Insight deployments to display security findings on the Incidents page. For information about enabling GuardDuty, see [Enable Amazon GuardDuty](#enable-guardduty).

For more information about deployments, and creation of a Cloud Insight deployment, see [Set up and manage deployments](#ci-deployments).

## Subnet Information  

                Not required for Cloud Insight Essentials deployments.    
Regardless of the deployment mode used to create a Cloud Insight deployment, you must ensure each VPC in a deployment scope has an available, properly configured subnet in which to deploy a scanning instance.

### Automatic Mode

When you set the scope for a Cloud Insight deployment, Cloud Insight automatically chooses and utilizes a /28 subnet (16 IP addresses) for each VPC in an AWS deployment. The chosen subnet is the first available /28 in the VPC.

If you planned a subnet IP addressing scheme, but have not yet deployed it in your AWS VPC, you should create desired subnets before you create a Cloud Insight deployment. Doing so ensures Cloud Insight does not consume IP addesses planned for your addressing scheme. For more information about subnets in AWS VPCs, see  [AWS subnet documentation](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Subnets.html).

If you discover the need to reserve a subnet range after you create a Cloud Insight deployment, log into the Alert Logic console, and then edit the scope of this deployment to remove the VPC that contains the subnet from the protected scope. Doing so triggers Cloud Insight to remove all the changes made for this VPC. After you create or modify the subnets in this VPC, you can log into the Alert Logic console, edit the deployment scope to add the VPC to the deployment, and then initiate deployment.

### Guided Mode

If you use Guided Mode to create a deployment, you must select the subnet in each VPC within the deployment scope in which to deploy a security appliance. Guided Mode requires that you manage routing and the network ACLs for the subnets in which you deploy a scanning appliance. Specifically:

* The chosen subnet must allow outbound communication on port 22, port 80, and port 443.
* Subnet routing must allow communication with the DNS servers for each subnet VPC.
* The network ACLs must be compatible with the above.

For more information about management of VPC security groups, network ACLs, and flow logs, see [AWS VPC security documentation](https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Security.html).

## Set up and manage deployments

The  Deployments page allows you to specify the assets you want to monitor. Use the Deployments page to manage and create your deployments, and to watch the initial scan and deployment progress.

When you create a deployment, you must choose between the following two levels of assessment:

* **Create a **Cloud Insight Essentials** deployment**
Cloud Insight Essentials provides access to the library of AWS Configuration best practices checks, which are continuously tested on your  environment to help you detect and remediate exposures.  Cloud Insight Essentials also includes the option to integrate with AWS services like Amazon GuardDuty, which displays threat findings and guidance on how to address these findings on the Incidents page.

* **Create a **Cloud Insight** deployment**
Cloud Insight deployments provide all the capabilities from Cloud Insight Essentials, plus vulnerability assessments on the workloads you are running in your deployment. This adds visibility to vulnerabilities on your EC2 instance workloads.

When you add your first Cloud Insight or Cloud Insight Essentials deployment, you must create an AWS policy and role, which allows Alert Logic access to your hosts. All the information you need to create a policy and role appears on your screen when you add a deployment.

Policy and role creation is required only once for each type of deployment. You can use the AWS role and the External ID created for each deployment type to create as many deployments of that type as you need.

    Cloud Insight Essentials and Cloud Insight deployments use different policies to create their respective roles. Be sure you are using the correct policy and role for the deployment you create.    ### Why do I need an IAM policy?

An IAM policy is a document that specifies the permissions assigned to the IAM role you create for Cloud Insight to access to your AWS account. Without a policy, you cannot create a role to allow Cloud Insight to access and monitor your AWS assets. The policy document grants only the permissions required to monitor your deployments.

**What our policy document does not allow*** Retrieve secret keys or credentials from IAM
* Retrieve data from data stores other than S3
* Perform these actions from any other AWS account
* Grant access			 to the protected account to any other AWS account or user
* Modify IAM credentials or policies

**What our policy document allows**
Our policy document allows Alert Logic to use IAM delegation (third-party access) by a single Alert LogicAWS account to:

* Use read-only access to enumerate and discover the configuration of the following services:
   * Auto Scaling Groups
   * CloudFormation
   * CloudFront
   * CloudWatch
   * Direct Connect
   * DynamoDB
   * EC2
   * Elastic Beanstalk
   * Elastic Load Balancer (ELB)
   * Elastic MapReduce (EMR)
   * ElasticCache
   * Glacier
   * GuardDuty
   * IAM
   * Kinesis
   * Lambda
   * Relational Database Service (RDS)
   * Redshift
   * Route53
   * SimpleDB (SDB)
   * S3
* Enable CloudTrail logging by performing the following actions:
   * Enable the logging, if not already enabled
   * Create an S3 bucket with a name starting with "outcomesbucket"
   * Create a Simple Notification Service (SNS) topic with a name starting with "outcomesbucket"
   * Select "Create your own policy" from the available options
* Disable CloudTrail logging by performing the following actions:
   * Disable the logging, if we enabled it
   * Remove the S3 bucket, SNS topic, and SQS queue created when logging was enabled
* Read S3 objects
* Create new scanning infrastructure, comprising the following, in each protected VPC (where possible, tagged with <kbd>AlertLogic:Security</kbd>):Alert Logic does not create, modify, or delete route tables, Internet gateways or network ACLs for Cloud Insight deployments created through Guided Mode.
   * Tags
   * Subnets
   * Internet gateway
   * Route tables (and associated routes)
   * Security groups
   * SSH private keys
   * Network ACLs
   * Auto Scaling groups
   * Launch configurations
   * EC2 instances (from AMIs shared by Alert Logic)
* Modify the following resources, if tagged as <kbd>AlertLogic:Security</kbd>, to permit scanning:
   * Security groups
   * Network ACLs
   * Route tables
* Delete the following infrastructure, if tagged as <kbd>AlertLogic:Security</kbd>, when undeploying:
   * Subnets
   * Route tables
   * Network ACLs
   * Auto scaling groups
   * Launch configurations
* Start, stop, and then terminate EC2 instances tagged as <kbd>AlertLogic:Security</kbd>

### Create your first deployment

To create your first deployment, you must log into both the Alert Logic console and the AWS Console. Doing so allows you to follow the interactive workflow for creating the AWS policy and role while you create your first deployment. When you create a deployment, you must choose to create either a Cloud Insight deployment, or a Cloud Insight Essentials deployment.

If you choose to create a Cloud Insight deployment, Alert Logic presents two options: Automatic Mode and Guided Mode.

* **Automatic Mode** — If you use Automatic Mode to create a deployment, Alert Logic creates a subnet in which to deploy a security appliance in each VPC within the deployment scope. For more information, click [here](#subnet-auto-mode).
* **Guided Mode** — If you use Guided Mode to create a deployment, you must select the subnet in each VPC within the deployment scope in which to deploy a security appliance. For more information, click [Guided Mode](#subnet-guided-mode).

**To create your first  Cloud Insight Essentials deployment:**
Alert Logic recommends you use our CloudFormation template for quick, convenient IAM policy and role creation.

**To use the CloudFormation template to create a deployment:**

1. Log into the AWS Console.
2. Log into the Alert Logic console.
3. From the   Deployments page, click the ![](../Resources/Images/Icons/cdAddPlus.png) icon.
4. Select Amazon Web Services (AWS).
5. Type a name for your deployment, and then click **SAVE AND CONTINUE**.
6. Under Cloud Insight Essentials, click **SELECT**, and then click **CONTINUE**.
7. Click **CLOUDFORMATION SETUP** to use the Alert Logic CloudFormation template to create the AWS role needed for deployment creation.
8. Follow the on-screen procedure to access the AWS CloudFormation Create Stack page and generate the role ARN you need to create your deployment.
9. Under Cloud Insight Essentials, click **SELECT**, and then click **CONTINUE**.
10. When prompted, paste the  role ARN you copied from the AWS CloudFormation Create Stack page.
11. Click **CONTINUE**.
12. Select your scope, and then click **DEPLOY**. For more information about scope selection, see [Set deployment scope](#set-scope).

You can also choose to employ manual setup in which you log into the AWS console and create your IAM policy and role.

**To create a **Cloud Insight Essentials** deployment through manual setup:**

1. Log into the AWS Console.
2. Log into the Alert Logic console.
3. From the   Deployments page, click the ![](../Resources/Images/Icons/cdAddPlus.png) icon.
4. Select Amazon Web Services (AWS).
5. Type a name for your deployment, and then click **SAVE AND CONTINUE**.
6. Under Cloud Insight Essentials, click **SELECT**, and then click **CONTINUE**.
7. Click **Or proceed with manual setup**.
8. Follow the procedure in the displayed tutorial, which guides you through IAM policy and role creation and then returns you to the deployment creation form.
9. In the deployment creation form, enter the AWS role and External ID you acquired in the previous step.
10. Click **CONTINUE**.
11. After the discovery process completes, select your deployment scope, and then click **DEPLOY**. For more information about scope selection, see [Set deployment scope](#set-scope).

**To create your first **Cloud Insight** deployment:**1. Log into the AWS Console.
2. Log into the Alert Logic console.
3. From the  Deployments page, click the ![](../Resources/Images/Icons/cdAddPlus.png) icon.
4. Select Amazon Web Services (AWS).
5. Type a name for your deployment, and then click **SAVE AND CONTINUE**
6. Under Cloud Insight, click **SELECT**, and then click **CONTINUE**
7. On the Create a Policy page, choose to create a deployment using Automatic Mode or Guided Mode, and then click **CONTINUE**.
8. Click **CLOUDFORMATION SETUP** to use the Alert Logic CloudFormation template to create the AWS role needed for deployment creation.
9. Follow the on-screen procedure to access the AWS CloudFormation Create Stack page and generate the role ARN you need to create your deployment.
10. When prompted, paste the  role ARN you copied from the AWS CloudFormation Create Stack page.
11. Click **CONTINUE**.
12. Select your scope, and then click **DEPLOY**. For more information about scope selection, see [Set deployment scope](#set-scope).
13. (Guided Mode) Select the subnet in each VPC in which you want to deploy a scanning appliance, click **SAVE**, and then click **DEPLOY**.

You can also choose to employ manual setup in which you log into the AWS console and create your IAM policy and role.

**To create a **Cloud Insight** deployment through manual setup:**

1. Log into the AWS Console.
2. Log into the Alert Logic console.
3. From the  Deployments page, click the ![](../Resources/Images/Icons/cdAddPlus_29x29.png) icon.
4. Select Amazon Web Services (AWS).
5. Type a name for your deployment, and then click **SAVE AND CONTINUE**
6. Under Cloud Insight, click **SELECT**, and then click **CONTINUE**
7. On the Create a Policy page, choose to create a deployment using Automatic Mode or Guided Mode, and then click **CONTINUE**.
8. Click **Or proceed with manual setup**.
9. In the Alert Logic console, follow the procedure in the "Set Up an IAM Role and Policy with Vulnerability Scanning" tutorial, which contains the procedure for AWS policy and role creation, including the Account ID, External ID, and the policy document required, and then returns you to the deployment creation form.

If you want to create a policy with restricted permissions for your CloudTrail S3 bucket.
The procedure in the "Set Up an IAM Role and Policy with Vulnerability Scanning" tutorial includes the default policy document to copy and then paste within the AWS console. If you want to create a policy with restricted permissions for your S3 bucket, use [this policy document](../pdf-files/ci-policy-min.txt) in Step 2 of the tutorial.

1. In the AWS console, click **IAM** > **Policies** > **Create policy**.
2. Click the JSON tab.
3. Copy the policy document in the link above, and then paste the document into the JSON window.
4. In the JSON window, locate the policy document line <kbd>"Resource": "arn:aws:s3:::CLOUDTRAIL_S3_BUCKET_NAME*"</kbd>, and then replace <kbd>CLOUDTRAIL_S3_BUCKET_NAME</kbd> with the name of your S3 bucket.
5. Follow the remaining steps of the "Set Up an IAM Role and Policy with Vulnerability Scanning" tutorial.

1. Click **CONTINUE**.
2. Select your scope, and then click **DEPLOY**. For more information about scope selection, see [Set deployment scope](#set-scope).
3. (Guided Mode) Select the subnet in each VPC in which you want to deploy a scanning appliance, click **SAVE**, and then click **DEPLOY**.

If you want to change the assessment level of any deployment you create, Alert Logic allows you to do so quickly through the Cloud Insight Essentials console. For more information see [Change the Assessment Level of a Cloud Insight Deployment](../product-guides/cloud-insight/cloud-insight-upgrade-downgrade.md).

### Set deployment scope

After deployment discovery, Alert Logic displays the Scope Selection page to allow you to select the regions you want to monitor. By default, Alert Logic monitors all the AWS assets in your deployment, but you can specify regions or VPCs to monitor. Click **Select Entire Deployment** to remove the entire deployment from, or add it to, the scope. Select **Custom Selection** to specify regions and VPCs to monitor.

Scope selection considerations and available options differ, depending on the type of deployment you created.

* Cloud Insight Essentials allows you to select regions and VPCs to monitor. No scanning occurs for this deployment type, so it does not require deployment of appliances to subnets in selected VPCs. Therefore subnet size or availability is not a consideration for scope selection.
* Cloud Insight
   * Automatic Mode allows Alert Logic to create a subnet in which to deploy a security appliance in each VPC within the deployment scope. Alert Logic manages subnet routing, and the network ACLs of that subnet and other subnets in the VPC.
   * Guided Mode requires that you select the subnet in each VPC within the deployment scope in which to deploy a security appliance. In addition, you must manage routing and network ACLs for the subnets in which you deploy a scanning appliance. For more information about management of VPC security groups, network ACLs, and flow logs, see [AWS VPC security documentation](https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Security.html).

### Set up and enable centralized  CloudTrail log collection

AWS allows you to use a separate, dedicated account with CloudTrail enabled to centralize your CloudTrail collection. If you use a separate AWS account for CloudTrail collection, you can enter a second  role when you create or edit a deployment to allow Alert Logic to access the AWS receiving account that collects CloudTrail data.

If you have AWS CloudTrail configured to write log data to an S3 bucket in an account other than the account protected by Cloud Insight Essentials, and if you want Cloud Insight Essentials to access this data, you must perform additional configuration during deployment creation or management to provide Alert Logic with cross-account CloudTrail access.

If you provide cross-account access to the separate AWS account with CloudTrail enabled, you will get near real-time updates about your assets. Without cross-account access to CloudTrail, Cloud Insight refreshes information about your assets every 12 hours.

This scenario involves the following:

* Protected deployment—The deployment monitored  by Alert Logic, and for which you created an IAM policy and role when you added the deployment.
* Receiving account—The account that owns the S3 bucket where you configured CloudTrail to store the log files.

When the AWS CloudTrail service writes CloudTrail log files to S3, that service account owns the objects, and the bucket owner is granted access to the objects. An IAM role is required for each of these accounts to access the respective objects.

The first time you set up Cloud Insight to access the objects in the receiving account, you must log into both the Alert Logic console and the AWS Console. Doing so allows you to follow the interactive workflow for creating the policy and IAM role for the receiving account.

To set up and enable centralized  CloudTrail log collection:

1. Log into the AWS Console.
2. Log into the Alert Logic console.
3. From the Cloud Insight Essentials Deployments page, click the ![](../Resources/Images/Icons/cdAddPlus_29x29.png) icon, or click **EDIT** on any Cloud Insight or Cloud Insight Essentials deployment tile.
4. On the left navigation pane, click AWS** Role**.
5. Select "I want this deployment to use centralized CloudTrail log collection."
6. Click the information icon (![](../Resources/Images/ci/ciInfoIcon.png)).
7. In the appropriate fields, enter the ARN and External ID you acquired in the previous step.
8. Click **CONTINUE**.

## Enable Amazon GuardDuty

If you enable Amazon GuardDuty in AWS, you can then configure both Cloud Insight and Cloud Insight Essentials to display security findings on the Incidents page. The Incidents page includes information about incidents, and how to manage and close incidents to secure the AWS assets in your deployments.

To integrate GuardDuty into your Cloud Insight or Cloud Insight Essentials deployments:

1. Log into the AWS console and enable Amazon GuardDuty. For information about how to enable Amazon GuardDuty, see the [GuardDuty documentation](https://aws.amazon.com/documentation/guardduty).
2. Deploy the Alert Logic CloudFormation template (CFT) collector to each AWS region in your selected scope. The Alert Logic collector is an AWS lambda function that collects and forwards GuardDuty findings to Cloud Insight.  For information about how to deploy collectors for GuardDuty findings, see [Integrate Amazon GuardDuty Findings into Alert Logic Incidents](../configure/integrate-guard-duty-findings.md#integrate-gd-findings).

## Set up authenticated scanning

    Not required for Cloud Insight Essentials deployments.     
Alert Logic allows you to use credentials to perform host-level scanning. Using Windows or SSH credentials as part of your scans allows for more accurate vulnerability scans and lowers the number of false positive results. Choose a region, VPC, or subnet to manage credentials at the region or specific asset level.

For authenticated scans to work properly in your deployment, you must set your AWS security groups to allow full communication inside the group. Doing so allows a Cloud Insight appliance to communicate with client hosts, and the authenticated scan to run without errors.

For more information, see .

To add or manage asset credentials:

1. From the  Topology page, select an asset at any level.                
Cloud Insight allows inherited credentials. You can provide credentials at the level most appropriate for those assigned in your AWS account, and those credentials will apply to all child assets.
2. At the top of the asset information pane, click the key icon (![](../Resources/Images/Icons/ciCredentialIcon.png)).
3. Select the one of the following credential types to add or manage for the selected asset:
   * Windows—Requires the Windows domain and username for the selected asset. Before you can run a credentialed scan, you must set up parameters on the Windows asset to be scanned. For more information about Windows authenticated scans, see .
   * SSH—Requires the user name and password for the selected asset.
   * SSH with key—Requires the user name and generated SSH key information generated and assigned to you by AWS during host deployment.
5. Provide the requested credential information.
6. Click **add credential**.

# Web Security Manager AWS V5 Auto Scaling Upgrade with CloudFormation Template

Web Security Manager must upgrade auto scaling to version 5 in the AWS console. Alert Logic no longer supports CentOS version 6. This requires you to upgrade your Web Security Manager auto scaling for AWS to the latest operating version. This document provides instructions for customers who want to create a new CloudFormation template. For instructions on how to upgrade with an existing CloudFormation template, see [Web Security Manager AWS V5  Auto Scaling Upgrade  with an Existing Stack](WSM5-aws-autoscaling-upgrade.md).

You must first request the latest version of the Alert Logic Managed Web Application Firewall (WAF) Amazon Machine Image (AMI) and the CloudFormation template from [WSM Alert Logic support](mailto:support@alertlogic.com). In the email, make sure you include your AWS Account ID.

After you have the latest AMI, you must ensure your AMI is set to the region you are using and predetermine your VPCs and subnets.

## Configure upgrade to WSM v5 for AWS Auto Scaling AMI replacement

**Upgrade WSM v5 for **AWS** auto scaling AMI replacement**:

1. Save the Alert Logic CloudFormation template to your local drive.
2. Log in to the [AWS console](https://console.aws.amazon.com/ec2/).
3. Go to the **CloudFormation** section.
4. Click **Create stack**, and then select **With new resources (standard)**.
5. Under **Specify template**, click **Upload a template file**, and then click **Choose file** to upload the Alert Logic CloudFormation template you saved earlier.
6. Click **Next**.
7. Under **Stack name**, in the **AlertLogic Data Center** field, enter a name for your stack.
8. Under **Network Configuration**, in the **AlertLogic Data Center** field, select the Data Center you are using.
9. In the **WSM license** field, enter your Alert Logic Unique Registration Key.                
**To access your license key**:
   1. Go to the Alert Logic console.
   2. Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click the support icon (![](../Resources/Images/Icons/support-icon.png)).
   3. Copy the key under **Unique Registration Key**.
11. In the **VPC** field, select the VPC where you want to deploy the stack.
12. Under **Master WSM Configuration**, in the **azMaster** field, select the region for the subnet you want to use.
13. In the **subnetMaster** field, select the subnet you want to use.
14. In the **subnetMasterELB** field, select the public subnet you want to use.
15. Under **Worker WSM Configuration**, in the **azWorkerlist** field, select the regions for the subnets you want to use. You can deploy two or more subnets.
16. In the **subnetWorker** field, select the subnets you want to use.
17. In the **subnetWorkerELBList** field, select the public subnets you want to use.
18. (Optional) **Under Autoscaling Configuration**,  modify your auto scaling settings. Otherwise, you can leave the default settings.
19. Under **Other parameters**, in the **wsmMasterInstanceType** field, select the instance type you want to use.
20. In the **wsmPassword** field, enter a password to set up.
21. In the **wsmUser** field, enter a username to set up.
22. In the **wsmWorkerInstanceType** field, select the instance type you want to use.
23. In the **wsmWorkerInstanceVolumeSize** field, enter the GB size (at least 100 GB) of worker EBS volume.
24. Click **Next**.
25. Under **Tags**, enter unique tags, and then enter values for those tags.
26. Under **Permissions**, select the IAM role name.
27. Click **Next Step** to review your stack.
28. If you need to change any values, click **Edit**.
29. Click **Create stack** to launch the new stack.

# Web Security Manager AWS V5  Auto Scaling Upgrade  with an Existing Stack

Web Security Manager must upgrade auto scaling to version 5 in the AWS console. Alert Logic no longer supports CentOS version 6. This requires you to upgrade your Web Security Manager auto scaling for AWS to the latest operating version. This document provides instructions for customers who want to update an existing CloudFormation template. For instructions on how to upgrade with a new CloudFormation template, see [Web Security Manager AWS V5 Auto Scaling Upgrade with CloudFormation Template](WSM5-aws-autoscaling-upgrade-cloudformation.md).

You must first request the latest version of the Alert Logic Managed Web Application Firewall (WAF) Amazon Machine Image (AMI) from [WSM Alert Logic support](mailto:support@alertlogic.com). In the email, make sure you include your AWS Account ID.

After you have the latest AMI, you must ensure your AMI is set to the region you are using and predetermine your VPCs and subnets.

## Configure upgrade to WSM v5 for AWS Auto Scaling AMI replacement

**Upgrade WSM v5 for **AWS** auto scaling AMI replacement**:

1. Log in to the [AWS console](https://console.aws.amazon.com/ec2/).
2. On the navigation pane, under **AUTO SCALING**, choose **Launch Configurations**.
3. In the new copied launch configuration for WSM lcmaster shared with your AWS account, change **AMI** to **WSM 5 AMI**, and then **save**.
4. Copy **Launch Config for WSM lcMaster**, and then add **WSM5copy** to the end of the name.
5. In the new copied launch configuration for WSM lcWorker, change the WSM 5 AMI, and then click **save**.
6. Go to the **Auto Scaling Groups** section.
7. Select **Master Auto Scaling Group** for the stack you are upgrading.
8. In the **Launch configuration** section, select **Edit**, and then change the **Launch configuration** to the new copied **WSM5copy** version.
You should see the new AMI listed under **AMI ID**.
9. Click **Update**. 
This update deploys the new launch configuration. There are no physical changes to the instances yet.
10. In **Auto Scaling Groups**, select **Worker Autoscaling groups**.
11. Under **Launch Configuration**, select **Edit**, and then change **Launch Configuration** to the new copied WSM5copy version.
You should see the new AMI listed under AMI ID.
12. Click **Update**. 
This update deploys the new launch configuration. There are no physical changes to the instances yet.
13. Move to EC2 instances in the AWS console.
14. Find and terminate the current **Master EC2** instance for that WSM lcmaster stack.
15. A new instance spins up automatically with the new WSM 5 AMI. 
To reduce the amount of work and wait time, you can reduce your auto scaling worker count to two. Terminate each worker one at a time, and then increase the worker count later.
16. Wait three to five minutes for the new Master instance to run before continuing to worker EC2.Ensure the new instance shows as healthy in service after it is running.
17. Terminate any current worker EC2 instances  for that WSM lcworker stack one at a time. You must allow for new ones to spin up before terminating the next worker. Wait takes three to five minutes.

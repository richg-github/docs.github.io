# Configure AWS Full Permission Deployment

Alert Logic recommends full permission deployment, which requires the use of the recommended policy available within the Alert Logic console. This set of permissions allows Alert Logic to discover your AWS environment and  automate the setup of the required AWS services.

To use full permission deployment, you must grant Alert Logic permissions to make changes to your environment (enable/modify AWS CloudTrail settings, create an Amazon SQS queue and an Amazon SNS topic, and modify permissions).

Full permission deployment allows you to set up CloudTrail in either the AWS account you want Alert Logic to protect, or in a separate account in which CloudTrail is configured for centralized log collection.

You can also employ a minimal permission deployment, which provides limited privileges that still allow  Alert Logic to work properly in AWS. To learn more about minimal permission deployment, see [Configure  AWS Minimal Permission Deployment in Manual Mode](aws-minimal-permission-deployment.md).

If you deploy using the minimum-permissions policy, Alert Logic will not be able to facilitate the discovery of your AWS environment or automate required AWS services, which can affect your experience. Alert Logic recommends deploying with the full-permissions deployment policy.

## Configure full permission                    deployment 

To configure full permission deployment, you must log into your AWS account and create a policy and IAM role, and then log into the Alert Logic console and provide your role information. AWS role creation requires that you provide an AWS policy, a document that specifies the permissions assigned to the AWS role you create for Alert Logic to access to your AWS account.

    The policy document grants only the permissions required to monitor your AWS account.    ### Create an IAM policy and role for full permission deployment with a CloudFormation template

Alert Logic recommends you use its CloudFormation template for quick, convenient IAM policy and role creation.

**To use the CloudFormation template to create a deployment:**

1. Log into the Alert Logic console.
2. From the   Deployments page, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
3. Select Amazon Web Services (AWS).
4. Type a name for your deployment, and then click **SAVE AND CONTINUE**.
5. Under Cloud Defender, click **SELECT**, and then click **CONTINUE**.
6. Leave Automatic Mode selected, and then click **SAVE &amp; CONTINUE**.
7. Click **CLOUDFORMATION SETUP** to use the Alert Logic CloudFormation template to create the AWS role needed for deployment creation.
8. Follow the on-screen procedure to access the AWS CloudFormation Create Stack page and generate the role ARN you need to create your deployment.
9. When prompted, paste the  role ARN you copied from the AWS CloudFormation Create Stack page.
10. Click **CONTINUE**.

### Create a manual IAM policy and role for full permission deployment

Click this link to access [the policy document for the full permission deployment (github link)](https://algithub.pd.alertlogic.net/defender/themis/blob/integration/priv/policies/aws/defender/2019-07-04/full.json). Keep the link open so you can copy and paste the information during IAM role creation. To create a cross-account access role, see[Create a cross-account access role](iam-role-creation.md#top).

### Complete full permission deployment configuration 

To complete configuration of a full permission deployment, you must log into the Alert Logic console, and then enter the AWS role information created above.

To configure this deployment in the Alert Logic console:

1. Browse to the Deployments page.
2. Click the tile for the AWS deployment you want to configure.
3. Enter the Role ARN and External ID you created above.
4. Click **CREATE**.

## Configure full permission deployment with centralized log collection                

### Create a cross-account access role

To configure full permission deployment with centralized log collection, you must log into your AWS account and create a policy and IAM role for the account you want to protect and for the account you want to use for centralized log collection.

The policy document for the protected account grants only the permissions required to monitor your environments. The policy document for the receiving account grants only read-only access.

**To create a policy and IAM role**:

1. Download and open [this policy document for the protected account](../pdf-files/defender-collection_account-full.txt). Keep the document open so you can copy and paste the information during IAM role creation.
2. Download and open [this policy document for the receiving account](../pdf-files/defender-collection_account-full.txt). Keep the document open so you can copy and paste the information during IAM role creation for centralized log collection.
3. To create a cross-account access role, see [Create a cross-account access role](iam-role-creation.md#top).
      You must perform this procedure for the protected account, and then for the receiving account. Be sure you use the correct policy document for each role you create. 
6. Then you must log into the Alert Logic console and provide the role information for both accounts:
   * **Protected account**—The account protected by Alert Logic.
   * **Receiving account**—The account that owns the S3 bucket where CloudTrail is configured to store its log files.

### Complete configuration of full permission deployment with centralized log collection

To complete configuration of a full permission deployment with centralized log collection, you must log into the Alert Logic console, and then enter the AWS role information created above. To learn more about AWS deployments, see [AWS Deployments](../get-started/about-deployment-types.md#aws-deployments).

To configure this deployment in the Alert Logic console:

1. Browse to the Deployments page.
2. Click the tile for the AWS deployment you want to configure.
3. Enter the Role ARN and External ID for the protected account.
4. Select **I want this environment to use cross-account CloudTrail to centralize CloudTrail log collection**.
5. Enter the Role ARN and External ID for the receiving account.
6. Click **CREATE**.

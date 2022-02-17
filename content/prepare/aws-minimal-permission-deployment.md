# Configure  AWS Minimal Permission Deployment in Manual Mode

Alert Logic strongly recommends deploying with full permissions to facilitate the discovery of your AWS environment and allow Alert Logic to automate required AWS services. To learn more about full permission deployment, see [Configure AWS Full Permission Deployment](aws-full-permission-deployment.md).

Minimal permission deployment employs the most limited privileges that still allow  Alert Logic to work properly in AWS.

Minimal permission deployment allows you to set up CloudTrail in either the AWS account you want protected by Alert Logic or in a separate account with an S3 bucket to which CloudTrail is configured for centralized log collection.

## Configure minimal                        permission deployment

To perform minimal permission cross-account role configuration, you must log into your AWS account and create an IAM role. AWS role creation requires that you provide an AWS policy, a document that specifies the permissions assigned to the AWS role you create for Alert Logic to access your AWS account. The policy document grants only the permissions required to monitor your environments.

**To deploy minimal permissions for your AWS implementation:**

1. [Set up AWS CloudTrail](#set-up-aws-cloudtrail). Choose to:
   * [Create a CloudTrail and SNS topic](#enable-cloudtrail), or
   * [Use an existing CloudTrail and SNS topic](#configure-existing-cloudtrail)
3. [Create an IAM policy and role for minimal permission deployment](#create-iam-policy-role).
4. [Configure Amazon S3 bucket policies for CloudTrail log collection](#configure-s3-bucket-policies)

### Set up AWS CloudTrail

For minimal permission deployment to work properly, you must set up your AWS CloudTrail manually. The process to set up AWS CloudTrail depends on whether you need to create an SNS topic or edit an existing SNS topic for CloudTrail.

#### **Create a CloudTrail and SNS topic**

If AWS CloudTrail is not yet enabled for your account, you must create a new trail, with an S3 bucket and SNS topic, and configure it for use with Alert Logic.

To set up CloudTrail with a new SNS topic:

1. Log into the AWS protected account.
2. Select the **CloudTrail** service.
3. Click **Create a trail**, and then click **Create trail** to open the full workflow.
4. In **Trail name**, type a name for your trail.
5. Click **Create a new S3 bucket**.
6. In **Trail log bucket and folder**, type the name of the S3 bucket in which to store your CloudTrail logs in your account.
7. In **AWS KMS alias**, type a KMS alias to enable log file encryption.
8. For **SNS notification delivery**, select **Enabled**.
9. For **Create a new SNS topic**, select **New**.
10. Click **Next**, click **Next**, and then click **Create trail**.

#### **Use an existing CloudTrail and SNS topic**

If you already enabled AWS CloudTrail for your account, the trail likely has the "multi-region" flag enabled. If you set up more than one trail with this flag enabled, Alert Logic selects the trail that appears first in alphabetical order. The existing trail you use must be configured with SNS delivery enabled, as described in the steps below.

To configure an existing SNS Topic:

1. From the AWS CloudTrail console, click **Trails**, and then select your existing trail.
2. For **SNS notification delivery**, select **Enabled**.
3. For **Create a new SNS topic**, select **New** . Note the ARN of the SNS topic; you will need it when defining the IAM policy.
4. Click **Save changes**.

### Create an IAM policy and role for minimal permission deployment

20. Click this link to download [the policy document for the minimal permission deployment (JSON file)](../pdf-files/manual-min.json). Keep the link open so you can copy and paste the information during IAM role creation. To create a cross-account access role, see [Configure  IAM Role for Amazon Web Services (AWS) ](iam-role-creation.md).
### Configure Amazon S3 bucket policies for CloudTrail log collection

For Alert Logic to collect CloudTrail logs from your S3 buckets, you must allow permission for the IAM role you created above to access the ListObjects and GetObject APIs for the bucket and prefix where you store the logs.

The process to configure the S3 bucket policy depends on your current configuration. Use one of the following procedures:

#### Create an Amazon S3 bucket policy

You must create an S3 bucket policy if your CloudTrail does not have that policy set up.

To create an Amazon S3 bucket policy:

1. From the IAM Console click **Roles**, select the role you created above, and then note the IAM **Role ARN** value to ensure that the correct policy is applied to your bucket.
2. From the Amazon S3 console, find the bucket that stores the logs to be collected.
If the logs are stored under one or more prefixes (which appear as folders in the console), note the prefix but stop at the top-level bucket, because bucket policies can only be edited from this level.
3. Click **Properties**, and then expand the Permissions section and click **Add Bucket Policy**.
4. Define the policy as follows:
   1. Download and open [this policy document](../pdf-files/bucket_policy_new.txt), copy the contents, and then paste them into the bucket policy window.
   2. Where indicated, replace <kbd>BUCKET_NAME/PREFIX</kbd> with the name of your bucket.
   3. Where indicated, replace <kbd>YOUR_IAM_ROLE_ARN</kbd> with the account number of the protected account.
6. Click **Save**.

#### Edit an existing Amazon S3 bucket policy

If the Amazon S3 bucket where you store logs has an existing bucket policy, you must make the following changes to your policy to allow the IAM role created forAlert Logic to collect logs.

To update an existing Amazon S3 bucket policy:

1. From the Amazon S3 console, find the bucket that stores collected logs.
If the logs are stored under one or more prefixes (which appear as folders in the console), note the prefix but stop at the top-level bucket, because bucket policies can only be edited from this level.
2. Click **Properties**, expand the **Permissions** section, and then click **Edit Bucket Policy**.
3. Make the following changes to your policy:
   1. [Download the bucket policy block (.txt)](../pdf-files/bucket_policy_update.txt) and copy the contents.
   2. Where indicated, replace <kbd>BUCKET_NAME/PREFIX</kbd> with the name of your bucket.
   3. Where indicated, replace <kbd>YOUR_IAM_ROLE_ARN</kbd> with the account number of the protected account.
   4. After the last permissions statement in the bucket policy window, paste the bucket policy block contents.
5. Click **Save**.

### Complete minimal permission deployment configuration

To complete configuration of a minimal permission deployment, you must log into the Alert Logic console, and then enter the AWS role information created above.

To configure this deployment in the Alert Logic console:

1. Browse to the Deployments page.
2. Click the tile for the AWS deployment you want to configure.
3. Enter the Role ARN and External ID you created above.
4. Click **CREATE**.

## Configure minimal                        permission                    deployment with centralized log collection                    

Minimal permission deployment with centralized log collection requires you to log into the AWS console to set up and configure both S3 and SNS in the receiving account (the AWS account in which you want to centralize log collection), and then log into the protected account (the AWS account you want  to protect) to set up CloudTrail and an IAM role.

**To deploy minimal permission deployment with centralized log collection:**

1. **In the receiving account:**
   1. [Configure Amazon S3 bucket policies for CloudTrail log collection for the receiving account](#set-up-s3-receiving). Choose to:
      * [Create a new SNS topic for the receiving account](#enable-sns-receiving), or
      * [Edit an existing S3 bucket policy in the receiving account](#edit-s3-receiving).
   3. [Configure SNS topic for the receiving account](#set-up-sns-receiving). Choose to:
      * [Create a new SNS topic for the receiving account](#enable-sns-receiving), or
      * [Edit an existing SNS topic for the receiving account](#Edit).
   5. [Create a minimal permissions IAM policy and role for the receiving account](#set-up-iam-policy-min-receiving)
3. **In the protected account:**
   1. [Set up CloudTrail in the protected account](#set-up-ct-protected)
   2. [Create a minimal permission IAM policy and role for the protected account](#set-up-iam-policy-min-protected)
5. **In the Alert Logic console:**
   * [Complete minimal permission deployment configuration with centralized log collection ](#configure-min-permission-cd)

### Configure Amazon S3 bucket policies for CloudTrail log collection for the receiving account

For Alert Logic to collect CloudTrail logs from your S3 buckets, you must allow permission for the IAM role you create to access the ListObjects and GetObject APIs for the bucket and prefix where you store the logs.

The process to configure the S3 bucket policy depends on your current configuration. Use one of the following procedures:

#### Enable a new S3 bucket policy in the receiving account

If S3 is not enabled for the receiving account, you must enable it, and then configure it for use with Alert Logic.

To create an Amazon S3 bucket policy:

1. Log into the receiving account.
2. From the AWS console, click **S3**, and then click **Create bucket**.
3. Complete the appropriate fields in the **Create bucket** window.
4. Click **Next ** to accept the default settings for properties and permissions.
5. Click **Create**.
6. From the AWS S3 console, select the bucket you just created.
7. Click the **Permissions** tab, and then click **Bucket Policy**.
8. Create the bucket policy as follows:
   1. Download the [[bucket policy (.txt)](../pdf-files/defender-s3-bucket-policy-new.txt)](../pdf-files/defender-collection_account-full.txt) and paste the contents into the bucket policy window.
   2. Where indicated, replace <kbd>ReceivingAccountBucketName</kbd> with the name of your bucket.
   3. Where indicated, replace <kbd>ProtectedAccountID</kbd> with the account number of the protected account.
10. Click **Save**.

#### Edit an existing S3 bucket policy in the receiving account

If you enabled S3 for the receiving account, you must configure S3 for use with Alert Logic.

1. Log into the receiving account.
2. From the IAM Console, click **S3**, and then find the bucket that stores collected logs.
3. Click **Properties**, expand the **Permissions** section, and then click **Edit Bucket Policy**.
4. Perform the following actions:
   1. [Download the bucket policy block (.txt)](../pdf-files/defender-s3-bucket-policy-update.txt) and copy the contents.
   2. After the last permissions statement in the bucket policy window, paste the bucket policy block contents.
   3. Where indicated, replace <kbd>ReceivingAccountBucketName</kbd> with the name of your bucket.
   4. Where indicated, replace <kbd>ProtectedAccountID</kbd> with the account number of the protected account.
6. Click **Save**.

### Configure SNS topic for the receiving account

For minimal permission deployment to work properly, you must set up your AWS CloudTrail manually in the receiving account. The process to set up AWS CloudTrail depends on whether you need to create an SNS topic or edit an existing SNS topic for CloudTrail.

#### Create a new SNS topic for the receiving account

You must create an Simple Notification Service (SNS) topic in the receiving account and configure it for use with Alert Logic.

To create an SNS topic:

1. Log into the receiving account.
2. From the AWS console, click **Simple Notification Service**.
3. From the SNS dashboard, click **Create topic**, and then provide a topic name. 
The **Display name** is optional in this case.
4. Click **Create topic**.
5. On the Topics page, make note of the ARN for the new SNS topic.
6. Select **Other topic actions** > **Edit topic policy**.
7. Click **Advanced view**.
8. Make the following changes to your topic policy:
   1. After the last permissions statement, add a comma (,).
   2. Download the [SNS topic policy text block (.txt)](../pdf-files/defender-sns-policy-new.txt) and paste it into the policy after the comma.
   3. Replace <kbd>SNS_TOPIC_ARN</kbd> with the Topic ARN.
10. Click **Update policy**.

#### Edit an existing SNS topic for the receiving account

If you have an existing Simple Notification Service (SNS) topic enabled in the receiving account, you must edit the existing topic policy.

To edit an existing SNS topic:

1. Log into the receiving account.
2. From the AWS console, click **Simple Notification Service**.
3. From the SNS dashboard, click **Topics**, and then select the topic you want to edit.
4. Select **Other topic actions** > **Edit topic policy**.
5. Click **Advanced view**.
6. Make the following changes to your topic policy:
   1. After the last permissions statement, add a comma (,).
   2. Download the [SNS topic policy text block (.txt)](../pdf-files/defender-sns-policy-new.txt) and paste it into the policy after the comma.
   3. Replace <kbd>SNS_TOPIC_ARN</kbd> with the Topic ARN.
8. Click **Update policy**.

### Create a minimal permissions IAM policy and role for the receiving account

To perform cross-account role configuration with centralized log collection, you must log into your AWS account and create an IAM role for the account you want to use for centralized log collection.

AWS role creation requires that you provide an AWS policy, a document that specifies the permissions assigned to the AWS role you create for Alert Logic to access your AWS account.  The policy document for the receiving account grants only read-only access.

Download and open [this policy document for the receiving account (.txt)](../pdf-files/defender-collection_account-full.txt). Keep the document open so you can copy and paste the information during IAM role creation for centralized log collection. To create a cross-account access role, see [Create a cross-account access role](iam-role-creation.md#top).

### Set up CloudTrail in the protected account

1. Log into the AWS protected account.
2. Click **CloudTrail** >**Trails**.
3. Click **Create trail**.
4. In **Trail name**, type a name for your trail.
5. For **Apply trail to all regions**, click **Yes**.
6. For **Create a new S3 bucket**, select **No** .
7. In **S3 bucket**, type the name of the S3 bucket you created in the receiving account to store your CloudTrail logs.
8. Click **Advanced**.
9. For **Send SNS notification for every log file delivery**, select **Yes**.
10. For **Create a new SNS topic**, select **No**, and then enter the topic ARN for the SNS topic you created in the receiving account.
11. Click **Save**.
12. Click **Create**.

### Create a minimal permission IAM policy and role for the protected account

To perform cross-account role configuration with centralized log collection, you must log into your AWS account and create an IAM role for the account you want to protect. The policy document for the protected account grants only the permissions required to monitor your environments.

Download and open this [policy document for the protected account (JSON file)](../pdf-files/manual-min.json). Keep the document open so you can copy and paste the information during IAM role creation for the protected account. To create a cross-account access role, see [Configure  IAM Role for Amazon Web Services (AWS) ](iam-role-creation.md)

### Complete minimal permission deployment configuration with centralized log collection 

To complete configuration of a minimal permission deployment with centralized log collection, you must log into the Alert Logic console, and then enter the AWS role information created above. To learn more about AWS deployments, see [AWS Deployments](../get-started/about-deployment-types.md#aws-deployments).

To configure this deployment in the Alert Logic console:

1. Browse to the Deployments page.
2. Click the tile for the AWS deployment you want to configure.
3. Enter the Role ARN and External ID for the protected account.
4. Select **I want this environment to use cross-account CloudTrail to centralize CloudTrail log collection**.
5. Enter the Role ARN and External ID for the receiving account.
6. Click **CREATE**.

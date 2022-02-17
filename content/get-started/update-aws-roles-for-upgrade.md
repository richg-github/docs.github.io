# Update AWS IAM Roles to Prepare for Upgrade

    This document is intended for customers with Alert Logic Cloud Insight, Alert Logic Cloud Insight Essentials, and Alert Logic Cloud Defender entitlements who are preparing to upgrade to Managed Detection and Response.    
Periodically, Alert Logic updates the policy documents used for the IAM roles that are required for  Amazon Web Services (AWS) deployments. These updates, which Alert Logic announces in [Alert Logic Console Release Notes](../release-notes/alert-logic-console.md), support new features and ensure  your deployments continue to monitor your AWS assets.

Prior to your upgrade to Managed Detection and Response, ensure your deployments use IAM roles created with the most current policy documents.

## How to check for an outdated IAM role policy document

If you have AWS Cloud Insight or Cloud Insight Essentials deployments, check the Remediations page  in the Alert Logic console for each deployment to ensure your policy documents are current.  If you see the High threat level remediation "Update policy document for the associated IAM role" in the list, you must update the policy document for the IAM role associated with the deployment.

## Copy the current policy document from the Alert Logic console

If an IAM role policy document needs to be updated, complete this procedure to copy the current one from the Alert Logic console.

**To copy the current policy document:**

1. In the Alert Logic console, browse to the Deployments page, click the relevant deployment tile, and then click **AWS Instructions**.
2. Under Step 2e, click **Copy Policy**.

## Update your IAM role in the AWS console

After you copy the policy document, the last step is to update the IAM role in the AWS console.

**To update an IAM role:**

1. In the AWS IAM Management Console, click **Roles**.This step specifies that you select Roles instead of Policies in case you set up the IAM role policy with a CloudFormation template. If you used the CloudFormation template, the IAM role policy is an inline policy accessed from Roles only.
2. From the list of your roles, click the role you want to update. If you do not know the name of the role, you can find it in the Alert Logic console. Access the deployment, and then click AWS** Role** in the left navigation area. The role name is the portion of the ARN after the string "role/". For example, if the ARN is “arn:aws:iam::123456789012:role/cloud-insight”, the role name is “cloud-insight”.
3. Click the policy you want to update.
4. Click **Edit policy**.
5. Click the **JSON** tab.
6. Paste the updated policy document, which you copied from the Alert Logic console,   into the JSON window to replace the old information.
7. Click **Review policy** to verify no errors are detected.
8. Click **Save changes**.

Perform this procedure for every IAM role you need to update.

# Configure  IAM Role for Amazon Web Services (AWS) 

Alert Logic supports Amazon Web Services (AWS) cross-account roles, which allow you to grant Alert Logic third-party access to your AWS accounts. In the AWS console, you can create multiple IAM roles, which grant different permissions based on the policy document you use to create the role.

## Create a cross-account access role

Alert Logic recommends that you configure your deployment with full permissions,  which allows Alert Logic to discover your AWS environment and  automate the setup of the required AWS services. However, you can choose from the following levels of permissions:

* [Configure AWS Full Permission Deployment](aws-full-permission-deployment.md#Configur)—Allows Alert Logic to make all the necessary changes to your AWS account.
* [Configure  AWS Minimal Permission Deployment in Manual Mode](aws-minimal-permission-deployment.md)—Allows you to maintain control over the changes in your deployment, and it requires you to perform any necessary actions manually.

The full permission policy document does not allow Alert Logic to:

* Retrieve secret keys or credentials from IAM
* Retrieve data from data stores other than S3
* Perform these actions from any other AWS account
* Grant access to the protected account to any other AWS account or user
* Modify IAM credentials or policies.

    If you create a deployment with one level of permissions, and then want to switch to another level of permissions, you can create another IAM role with the appropriate level of permissions (if you do not already have that role configured). Then, click **edit** on the deployment tile to change your deployment configuration to use the appropriate role.     
**To create a cross-account access role:**

1. In the AWS Console, click **IAM**, located under **Security, Identity &amp; Compliance**.
2. From the IAM Management Console, click **Policies**, and then click **Create Policy**.
3. Click the **JSON** tab.
4. Copy and paste the contents of your policy document into the JSON window.
5. Click **Review policy**.
6. On the Review Policy page, type a **Policy Name** and **Description** for the policy.
7. Click **Create policy**.
8. From the IAM Management Console, click **Roles**, and then click **Create role**.
9. On the Create role page, click **Another AWS account**.
10. Enter the following information for Alert Logic:
   * **Account ID (IAM role creation for CloudTrail and S3 log collection only): **
      * <kbd>239734009475</kbd>
   * **Account ID (all other IAM role creation scenarios):**
      * If you are using the US data center: <kbd>733251395267</kbd>
      * If you are using the EU data center: <kbd>857795874556</kbd>
   * Select **Require external ID**.
   * **External ID**—Use your Alert Logic Customer ID.  Note this value; you will need to provide it when you create the AWS credentials in the Alert Logic console.
   * **Require MFA**—Make sure the option is not selected.
12. Click **Next: Permissions**.
13. Select the policy you created above, and then click **Next: Review**.
14. Type a **Role Name** and **Role description**, and then click **Create Role**.
15. In the list of IAM roles, click the name of the role you created, and then note the **Role ARN** value, which you will need when you create the AWS credentials in the Alert Logic console.

## Update an IAM role

Periodically, Alert Logic updates the policy documents used for the IAM roles required for AWS deployments. These updates, which Alert Logic announces in [Alert Logic Console Release Notes](../release-notes/alert-logic-console.md), ensure you can successfully create deployments, and they ensure your existing deployments continue to monitor your AWS assets.

You can download the policies in the Alert Logic console.

**To update an IAM role:**

1. In the AWS Console, click **IAM**, located under **Security, Identity &amp; Compliance**.
2. From the IAM Management Console, click **Roles**.
3. From the list of your roles, click the role you want to update.
4. Click the policy you want to update.
5. Click **Edit policy**.
6. Click the **JSON** tab.
7. Copy the contents of the updated policy document.
8. Paste the updated policy document  into the JSON window to replace the old information.
9. Click **Review policy**.
10. Click **Save changes**.

Perform this procedure for every IAM role you need to update.

# Change the Assessment Level of a Cloud Insight Deployment 

If you want to enable scanning for a Cloud Insight Essentials deployment, or disable scanning for a Cloud Insight deployment, Alert Logic allows you to do so quickly through the Deployments page.

## Upgrade from Cloud Insight Essentials to Cloud Insight

To enable scanning for a Cloud Insight Essentials deployment, you can edit the security policy in AWS. Then, in Cloud Insight Essentials, edit the deployment and change the level of assessment to Cloud Insight.

A Cloud Insight deployment allows Alert Logic to spin up AWS subnets and instances in your AWS infrastructure, which incurs additional costs from Alert Logic for scanning per host, and additional costs from AWS for the instances Alert Logic creates.

**To upgrade a deployment to **Cloud Insight**:**

1. Log into the AWS console.
2. Log into the Alert Logic console.
3. On the Deployments page, click **EDIT** on the deployment tile for the Cloud Insight Essentials deployment you want to upgrade.
4. In the left navigation area, click **Choose an Assessment Level**.
5. Under Cloud Insight, click **SELECT**, and then click **SAVE**.
6. On the Create a Policy page, choose  Automatic Mode or Guided Mode for your deployment, and then click **CONTINUE**.
7. On the IAM Role Setup page, click **Or proceed with manual setup** to create the AWS policy for the role with the upgraded permissions for your Cloud Insight Essentials deployment.

    Do not use CloudFormation Setup to create an IAM role when you upgrade a deployment from Cloud Insight Essentials to Cloud Insight.    1. Click **CONTINUE**.
2. Click **SAVE**.

## Downgrade from Cloud Insight to Cloud Insight Essentials

To disable scanning for a Cloud Insight deployment, you must change the deployment from Cloud Insight to Cloud Insight Essentials.

Any vulnerabilities discovered in a Cloud Insight deployment prior to a downgrade to a Cloud Insight Essentials deployment remain in your list of Remediations. 
**To downgrade a deployment to **Cloud Insight Essentials**:**

1. Log into Cloud Insight Essentials.
2. On the Deployments page, click **EDIT** on the deployment tile for the Cloud Insight deployment you want to downgrade.
3. In the left navigation area, click **Choose an Assessment level**.
4. Under Cloud Insight Essentials, click **SELECT**, and then click **SAVE**.

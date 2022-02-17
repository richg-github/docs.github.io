# Integrate Amazon GuardDuty Findings into Alert Logic Incidents

Amazon GuardDuty is a continuous security monitoring service that requires no customer-managed hardware or software. GuardDuty analyzes and processes VPC Flow Logs and AWS CloudTrail event logs. GuardDuty uses security logic and AWS usage statistics techniques to identify unexpected and potentially unauthorized and malicious activity, like escalations of privileges, uses of exposed credentials, or communication with malicious IPs, URLs, or domains.

Alert Logic provides a CloudFormation template that deploys a CloudWatch Events collector and a Lambda function that integrates GuardDuty findings into the Alert Logic console for display as threats on the Incidents page.

## Before you begin

Before you perform the procedures required to integrate GuardDuty findings into the Incidents page, ensure you have the proper permissions to do so and the correct command line interfaces to generate access keys.

### Verify administrative permissions

To perform the procedures necessary to integrate GuardDuty findings into the Incidents page, your Alert Logic user account and your AWS account must have administrative permissions.

**To verify your** Alert Logic **permissions:**

1. Log in to the Alert Logic console.
2. Click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu.
3. Click the ![](../Resources/Images/dashboard/manage-icon.png)Manage menu item, and then select **Users**.
4. At the top of the list of users, select your user name.
5. In the **Account Details** panel, verify the selected user role is **Administrator**.

**To verify your **AWS** permissions:**

1. Log in to the AWS console.
2. Click **IAM**, under **Security, Identity &amp; Compliance**.
3. Ensure "AdministratorAccess" appears as one of the policies in the list of policy names.

### Ensure access to a command line interface (CLI) 

GuardDuty integration with Alert Logic requires you use a command line interface (CLI) appropriate to your operating system to generate the access keys and secret keys required to allow Alert Logic to issue API calls on your behalf. You need the following CLI, depending on your operating system:

* Microsoft Windows requires [PowerShell 3.0 or later](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell).
* Unix and Linux require [cURL](https://curl.haxx.se/cURL) and [jq](https://stedolan.github.io/jq/).

### Enable Amazon GuardDuty

Before you can integrate GuardDuty findings into the Incidents page, you must log in to AWS and enable GuardDuty. For more information, see  [Setting Up Amazon GuardDuty](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_settingup.html).

## Create an Alert Logic access key and secret key

To support GuardDuty integration, Alert Logic uses your customer identification, in the form of access keys and secret keys, to issue API calls on your behalf. You need these keys to launch a CloudFormation template that deploys a CloudWatch Events collector and a Lambda function that integrates GuardDuty findings into the Alert Logic system for display as threats on the Incidents page.

You can create an access key through the Alert Logic console, or by using a Unix or Linux bash command line. For more information about access key creation in the Alert Logic console,  see [Create and Manage Alert Logic Access Keys ](../prepare/access-key-management.md).

**To create an access key and a secret key through the Unix or Linux bash command line:**
1. From the bash command line, type the following command, where <kbd>&amp;lt;email address&amp;gt;</kbd> is your Alert Logic user name.

<kbd>export AL_USERNAME='&amp;lt;email address&amp;gt;'</kbd>

2. Copy, and then paste, the following command into the command line:

<kbd>auth=$(curl -X POST -s -u $AL_USERNAME https://api.global-services.global.alertlogic.com/aims/v1/authenticate); export AL_ERROR=$(echo $auth | jq -r '.error // ""'); export AL_ACCOUNT_ID=$(echo $auth | jq -r '.authentication.account.id'); export AL_USER_ID=$(echo $auth | jq -r '.authentication.user.id'); export AL_TOKEN=$(echo $auth | jq -r '.authentication.token'); if [ -n "$AL_ERROR" -o -z "$AL_TOKEN" ]; then echo "Authentication failure - $AL_ERROR "; else roles=$(curl -s -X GET -H "x-aims-auth-token: $AL_TOKEN" https://api.global-services.global.alertlogic.com/aims/v1/$AL_ACCOUNT_ID/users/$AL_USER_ID/roles | jq -r '.roles[].name'); if [ "$roles" != "Administrator" ]; then echo "The $AL_USERNAME doesn’t have Administrator role. Assigned role is '$roles'"; else curl -s -X POST -H "x-aims-auth-token: $AL_TOKEN" https://api.global-services.global.alertlogic.com/aims/v1/$AL_ACCOUNT_ID/users/$AL_USER_ID/access_keys | jq .; fi; fi; unset AL_USERNAME;</kbd>

3. When prompted, enter your Alert Logic user account password.

    Successful response example:
<kbd>{
 "access_key_id": "712c0b413eef41f6",
 "secret_key": "1234567890b3eea8880d292fb31aa96902242a076d3d0e320cc036eb51bf25ad"
}</kbd>

Note the  <kbd>access_key_id</kbd> and <kbd>secret_key</kbd> values, which you need to deploy the CloudFormation template to your AWS account.

### Necessary role error

If the command returns an error about not having the necessary role, verify that your Alert Logic account has administrator permissions. For more information about AIMS APIs, see the [Alert Logic AIMS Account Resources](https://console.account.alertlogic.com/users/api/aims/).

### Limit exceeded error

Each user can create only five access keys. If a limit exceeded error appears, you must delete one or more access keys before you can create new keys.

1. Type the following command to list access keys:                    curl -s -X GET -H "x-aims-auth-token: $AL_TOKEN" https://api.global-services.global.alertlogic.com/aims/v1/$AL_ACCOUNT_ID/users/$AL_USER_ID/access_keys | jq
2. Use the selected <kbd>access_key_id </kbd>in the following command to delete the key:                    curl -X DELETE -H "x-aims-auth-token: $AL_TOKEN" https://api.global-services.global.alertlogic.com/aims/v1/$AL_ACCOUNT_I

**To create an access key and a secret key through Windows PowerShell:**
1. In the Windows PowerShell console, copy and paste the following command:

<kbd>[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; $creds = Get-Credential -Message "Please enter your Alert Logic Cloud Insight email address and password"; $unsecureCreds = $creds.GetNetworkCredential(); $base64AuthInfo = [Convert]::ToBase64String([Text.Encoding]::ASCII.GetBytes(("{0}:{1}" -f $unsecureCreds.UserName,$unsecureCreds.Password))); Remove-Variable unsecureCreds; $AUTH = Invoke-RestMethod -Method Post -Headers @{"Authorization"=("Basic {0}" -f $base64AuthInfo)} -Uri https://api.global-services.global.alertlogic.com/aims/v1/authenticate ; Remove-Variable base64AuthInfo; $AL_ACCOUNT_ID = $AUTH.authentication.account.id; $AL_USER_ID = $AUTH.authentication.user.id; $AL_TOKEN = $AUTH.authentication.token; if (!$AL_TOKEN) { Write-Host "Authentication failure"} else { $ROLES_RESP = Invoke-RestMethod -Method Get -Headers @{"x-aims-auth-token"=$AL_TOKEN} -Uri https://api.global-services.global.alertlogic.com/aims/v1/$AL_ACCOUNT_ID/users/$AL_USER_ID/roles ; $ROLES = $ROLES_RESP.roles.name; if ($ROLES -ne "Administrator" ) { Write-Host "Your user doesn’t have Administrator role. Assigned role is '$ROLES'" } else { $ACCESS_KEY = Invoke-RestMethod -Method Post -Headers @{"x-aims-auth-token"=$AL_TOKEN} -Uri https://api.global-services.global.alertlogic.com/aims/v1/$AL_ACCOUNT_ID/users/$AL_USER_ID/access_keys ; Write-Host $ACCESS_KEY } }</kbd>

2. When prompted, enter your Alert Logic user name and password.

    Successful response example:
<kbd>@{access_key_id=712c0b413eef41f6; secret_key=1234567890b3eea8880d292fb31aa96902242a076d3d0e320cc036eb51bf25ad}</kbd>
Note the  <kbd>access_key_id</kbd> and <kbd>secret_key</kbd> values, which you need to deploy the CloudFormation template to your AWS account.

### Necessary role error

If the command returns an error about not having the necessary role, verify your Alert Logic account has administrator permissions. For more information about AIMS APIs, see the [Alert Logic AIMS Account Resources](https://console.account.alertlogic.com/users/api/aims/).

### Limit exceeded error

Each user can create only five access keys. If a limit exceeded response appears, you must delete one or more access keys before you can create new keys.

1. Type the following command to list access keys:                        Invoke-RestMethod -Method Get -Headers @{"x-aims-auth-token"=$AL_TOKEN} -Uri https://api.global-services.global.alertlogic.com/aims/v1/$AL_ACCOUNT_ID/users/$AL_USER_ID/access_keys
2. Use the selected <kbd>access_key_id </kbd>in the following command to delete the key:						Invoke-RestMethod -Method Delete -Headers @{"x-aims-auth-token"=$AL_TOKEN} -Uri https://api.global-services.global

## Deploy the CloudWatch Events collector from the CloudFormation template

This CloudFormation template deploys the Alert Logic CloudWatch Events collector and Lambda function to a single AWS region for GuardDuty integration. The CloudWatch Events collector collects CloudWatch Events associated with GuardDuty findings, and the Lambda function forwards those events to the Alert Logic console to display as incidents.

If you want to collect events from multiple AWS regions, you must either install the CloudWatch Events collector in each region from which you want to collect events or set up a GuardDuty Master Account. For more information, see [Managing AWS Accounts in Amazon GuardDuty](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_accounts.html).

### Use the AWS console to deploy 

**To deploy the CloudWatch Events collector from the CloudFormation template:**

1. Log in to the [AWS Console](http://aws.amazon.com/) with an AWS account that has AWS administrator privileges.
2. Click the region in which you want to deploy the CloudFormation template.
3. Click **Services**, and then click **CloudFormation**.
4. Click **Create Stack**.
5. Under Choose a template section, select **Specify an Amazon S3 template URL**, and then enter the following URL: <kbd>https://s3.amazonaws.com/alertlogic-collectors-us-east-1/cfn/guardduty.template</kbd>
6. Click **Next**.
7. In the **Specify Details** window, provide the following required parameters:
   * **Stack name**—Accept the default, or use any preferred name
   * **AccessKeyId**—<kbd>access_key_id</kbd> you created in [Create an Alert Logic access key and secret key](#create-al-access-key)
   * **AlApiEndpoint**—Accept the default (<kbd>api.global-services.global.alertlogic.com</kbd>)
   * **AlDataResidency**—Usually <kbd>default</kbd>
   * **SecretKey**—<kbd>secret_key</kbd> you created in [Create an Alert Logic access key and secret key](#create-al-access-key)
9. Click **Next**.
10. On the **Options** panel, click **Next**.
11. In the **Review** panel, perform a predeployment check.
12. Select **I acknowledge that AWS CloudFormation might create IAM resources**, and then click **Create**.
13. On the CloudFormation Stacks panel, filter results based on the stack name you created, and then select your stack.

A successful deployment returns a status of <kbd>CREATE_COMPLETE</kbd>.

You must repeat the collector installation procedure for each region in which you want to install the CloudWatch Events collector.You may install only one collector in each AWS region. If you try to deploy the template multiple times in the same region, you will receive an error. ### Use the AWS CLI to deploy 

To use the command line to deploy the Alert Logic custom template, see the instructions in the Alert Logic [github readme](https://github.com/alertlogic/cwe-collector/blob/integration/cfn/README-GD.md#use-a-command-line-to-deploy).

## Verify the CloudFormation template launched successfully

If the CloudFormation template launched successfully, the  Incident List will include recent GuardDuty findings that also appear in the GuardDuty console.

1. Log in to the Alert Logic console with an account that has administrator permissions.
   * Use the [US Alert Logic console](https://console.account.alertlogic.com/#/login) for regions in the United States and associated geographical regions.
   * Use the [UK Alert Logic console](https://console.account.alertlogic.co.uk/#/login) for regions in Europe and other regions not in the US.
3. Click the navigation menu icon (![](../Resources/Images/dashboard/menu-icon.png)), click ![](../Resources/Images/dashboard/respond-icon.png)**Respond**, and then click **Incidents**.
4. Verify that GuardDuty findings appear as incidents in the Incident List.

## Troubleshooting installation issues

### AWS console troubleshooting

If installation through the AWS console is not successful, you can see the  detailed error messages in the AWS CloudWatch Log Stream.

**To access the error messages**:

1. Click **CloudFormation**, and then click **Stacks**.
2. Click **Stack Detail**, and then select your stack name from the list.
3. Click **Logs**, and then filter by<kbd> /aws/lambda/my-new-stack</kbd> (where <kbd>my-new-stack</kbd> is the name you gave your stack).

### AWS CLI troubleshooting

If installation through the AWS CLI is not successful, issue the following command for more information:

<kbd>aws cloudformation describe-stack-events --stack-name my-new-stack</kbd>

### Lambda function troubleshooting

If <kbd>GetEndpointsLambdaFunction</kbd> fails, an issue could exist with the <kbd>access_key_id</kbd> or the <kbd>secret_key</kbd> you provided. Be sure the <kbd>access_key_id</kbd> is correct, your <kbd>secret_key</kbd> is valid, and your user account has administrative permissions for the Alert Logic console.

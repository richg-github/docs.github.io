# Configure Amazon WorkSpaces Collector

You can deploy the Alert Logic agent to your Amazon WorkSpaces instances to collect logs and network traffic. To protect environments that use Amazon WorkSpaces, the required method is to deploy the Alert Logic agent on each  that you want to protect. The Alert Logic agent enables collections of network traffic and log messages from each of the Amazon WorkSpaces instances. Collection of data is configured transparently for new and existing deployments. You can find Amazon WorkSpaces data with keyword search in the Alert Logic console [Search: Log Messages](../../analyze/log-message-search.md) page.

You must complete the following to successfully configure your Amazon WorkSpaces  collector:

1. Access the Amazon WorkSpaces instances through the AWS console.
2. Install the Alert Logic agent on any Amazon WorkSpaces host agent. To install the latest Alert Logic agent, see [Install the Alert Logic Agent for Windows](../../prepare/alert-logic-agent-windows.md) or [Install the Alert Logic Agent for Linux](../../prepare/alert-logic-agent-linux.md).To install the latest Alert Logic agent, see [Install the Alert Logic Agent for Linux](../../prepare/alert-logic-agent-linux.md), [Install the Alert Logic Agent for Windows](../../prepare/alert-logic-agent-windows.md), or [Automate Alert Logic Agent Installation with AWS Systems Manager Distributor](../../prepare/agent-install-automated-aws.md).
3. Ensure the latest IAM Policy is applied to the Alert Logic role in your AWS environment. To update an existing IAM role, see [Update an IAM role](../../prepare/iam-role-creation.md#UpdateanIAMrole).
4. After the agent is installed and the IAM policy is updated to the latest version, Alert Logic will claim the agent automatically.
5. After the claim is complete, you will start collecting network traffic and log data.

To successfully configure the Amazon WorkSpaces collector, you must also have the following:

* The latest version of the Alert Logic agent
* The latest version of IAM policy version for AWS
* Have access to the AWS console and Amazon WorkSpaces
* An Alert Logic Professional or Enterprise subscription.

## New Deployments

For new deployments, your AWS deployment must already be configured. If you do not have your AWS deployment set up, see [AWS Deployments](../../get-started/about-deployment-types.md#aws-deployments). For new AWS deployments, you must the following steps to activate protection of your Amazon WorkSpaces instances:

1. Access your AWS console account to find your Amazon WorkSpaces instances.
2. Install the latest version of the Alert Logic agent on your Amazon WorkSpaces instances.  To install the latest Alert Logic Protected Host agent, see [Install the Alert Logic Agent for Windows](../../prepare/alert-logic-agent-windows.md) or [Install the Alert Logic Agent for Linux](../../prepare/alert-logic-agent-linux.md).
3. After the agent is installed, it will automatically claim and bind to the appropriate account and protection will begin for your Amazon WorkSpaces instances.

This configuration is an account-level integration, which means you can configure more than one instance of Amazon WorkSpaces log collection. This capability is useful when  more than one instance of the application exists.

## Existing Deployments

For existing deployments, the process is very similar. The primary difference is that you may be using older versions of the IAM policy and Alert Logic agent. You must ensure that you are using the latest versions of both components.

To update an existing IAM role, see [Update an IAM role](../../prepare/iam-role-creation.md#UpdateanIAMrole). To install the latest Alert Logic Protected Host agent, see [Install the Alert Logic Agent for Windows](../../prepare/alert-logic-agent-windows.md) or [Install the Alert Logic Agent for Linux](../../prepare/alert-logic-agent-linux.md).

## Verify collection in the Alert Logic console

After you set up the Amazon WorkSpaces, you can verify if the instance is collecting. You can check the Application Registry and the Health page in the Alert Logic console.

To access the Application Registry page, click the menu icon (![](../../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Application Registry**.
In the Applications List tab, if you configured your application correctly, within approximately 10 minutes you will see Configured next to the application. In the Configured Applications tab, if you configured your application correctly, within approximately 10 minutes you will see the application listed. For more information about how to add instances or manage existing collecting applications, see [Manage your configured applications](../application-registry.md#Configur).
The Health console also indicates whether the application collector  is healthy or unhealthy. For more information, see [Health](../../analyze/health.md).

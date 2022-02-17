# Configure Slack Connection Target

A Slack connection target securely stores reusable authentication credential and URL path information for integrations with Slack.

Complete the following steps to  configure a connection target for Slack:

1. [Configure Slack Connection Target](#GeneratethetargetURL)
2. [Use the connection target in connectors and playbooks](#Usetheconnectiontargetinconnectorsandplaybooks)

## Generate your Slack base target URL

The base URL for Slack connection targets must be generated from Slack .To generate the base target URL, complete the instructions in the [Slack documentation](https://api.slack.com/messaging/webhooks). Copy the generated URL, which you must paste into the base URL field in the Alert Logic console later.

## Create the Slack connection target from the Alert Logic console

1. In the Alert Logic console, click the navigation menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.
2. Click on the **Connection Targets** tab.
3. On the Connection Targets page, click the add icon (![](../../../Resources/Images/Icons/cdAddPlus.png)), and then click **Slack**.
4. On the Create a Slack Connection Target page, type a descriptive name for the connection target —for example, "Slack Connection Target".
5. In  **Base URL**, use the URL you identified earlier.
6. Activate the connection target if you want to use it, or leave it inactive to save the connection target for later.
7. Click **SAVE**.

## Use the connection target in connectors and playbooks

After you save the connection target, the last step is to set up a connector or automated response playbook. For more information on connectors, see [Connectors Configuration Guide](../../../Z-Sandbox/bbaskin/connectors-beta/connectors.md). For more information on automated response, see [Get Started with Automated Response (Beta)](../../../respond/automated-response.md).

## Manage connection targets

You can view the list of connection targets and edit or delete an existing one. For more information, see [Manage Connection Targets](../../../Z-Sandbox/bbaskin/connectors-beta/connection-targets/manage-connection-targets.md).

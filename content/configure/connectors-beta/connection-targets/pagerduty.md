# Configure PagerDuty Connection Target

A PagerDuty connection target securely stores reusable authentication credential and URL path information for integrations with PagerDuty.

Complete the following steps to  configure a connection target for PagerDuty:

1. [Generate your PagerDuty routing key](#GenerateyourPagerDutyroutingkey)
2. [Use the connection target in connectors and playbooks](#Usetheconnectiontargetinconnectorsandplaybooks)

## Generate your PagerDuty routing key

To  generate the PagerDuty integration service routing key, see the [PagerDuty documentation](https://support.pagerduty.com/docs/services-and-integrations#section-events-api-v2).

## Create the PagerDuty connection target from the Alert Logic console

1. In the Alert Logic console, click the navigation menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.
2. Click on the **Connection Targets** tab.
3. On the Connection Targets page, click the add icon (![](../../../Resources/Images/Icons/cdAddPlus.png)), and then click ****.
4. On the Create a  Connection Target page, type a descriptive name for the connection target —for example, " Connection Target".
5. In  **Base URL**, use the default Base URL.
6. In **Routing Key**, paste the routing key you generated.
7. Activate the connection target if you want to use it, or leave it inactive to save the connection target for later.
8. Click **SAVE**.

## Use the connection target in connectors and playbooks

After you save the connection target, the last step is to set up a connector or automated response playbook. For more information on connectors, see [Connectors Configuration Guide](../../../Z-Sandbox/bbaskin/connectors-beta/connectors.md). For more information on automated response, see [Get Started with Automated Response (Beta)](../../../respond/automated-response.md).

## Manage connection targets

You can view the list of connection targets and edit or delete an existing one. For more information, see [Manage Connection Targets](../../../Z-Sandbox/bbaskin/connectors-beta/connection-targets/manage-connection-targets.md).

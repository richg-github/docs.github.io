# Configure Zendesk Connection Target

A Zendesk connection target securely stores reusable authentication credential and URL path information for integrations with Zendesk.

Complete the following steps to  configure a connection target for Zendesk:

1. [Identify your Zendesk subdomain name](#IdentifyyourJirabasetargetURL)
2. [Create a Zendesk API token](#CreateaZendeskAPItoken)
3. [Use the connection target in connectors and playbooks](#Usetheconnectiontargetinconnectorsandplaybooks)

## Identify your Zendesk subdomain name

Identify your Zendesk instance name. In the Base URL field, you must replace "<myinstance>" in the default URL provided in the Alert Logic console with the Zendesk instance  you want to target.

## Create a Zendesk API token

The API token must be generated from the  same account you are using for user email in the connection target. For directions on how to generate and use an API token from your Zendesk account, see [Generating a new API token in Zendesk](https://support.zendesk.com/hc/en-us/articles/226022787-Generating-a-new-API-token-).

## Use the connection target in connectors and playbooks

After you save the connection target, the last step is to set up a connector or automated response playbook. For more information on connectors, see [Connectors Configuration Guide](../../../Z-Sandbox/bbaskin/connectors-beta/connectors.md). For more information on automated response, see [Get Started with Automated Response (Beta)](../../../respond/automated-response.md).

## Manage connection targets

You can view the list of connection targets and edit or delete an existing one. For more information, see [Manage Connection Targets](../../../Z-Sandbox/bbaskin/connectors-beta/connection-targets/manage-connection-targets.md).

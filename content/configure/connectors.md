# Webhook and Email Connectors

You can configure a  connector in the Alert Logic console  to send [notifications](notifications.md) to  any public-facing HTTP endpoint. Connectors  allow you to send security data directly to a third-party application in near real time. When  you set up a notification and subscribe a webhook or email connector, the connector sends the event to the target URL (as an HTTP POST request) or email address you configured and can send a message or generate an IT service management (ITSM) ticket  automatically.

Connectors to your third-party applications increase efficiency by enabling you to automate your workflows. Faster awareness of security events can decrease response teams and improve your security posture.

## Access the Connectors feature

To access the Connectors feature, from the navigation menu, click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.

## Connector configuration

The process for connecting to a third-party application involves these main steps:

1. Create the connector in the Alert Logic console.
2. Subscribe your connector to receive Alert Logic security notifications.

Application requirements vary and often require different information. For instructions on how to configure a specific connector, see the [Connectors Configuration Guide](connectors/connectors.md).

## Connector types

Alert Logic offers connectors in several business categories: Ticketing Webhook, Messaging Webhook, and Universal.

### Ticketing Webhook

Several choices are available for creating a webhook that can generate ITSM tickets automatically from Alert Logic security notifications:

* **Jira**—Webhook connector for Atlassian Jira Software
* **Jira Service Desk**—Webhook connector for Atlassian Jira Service Desk
* **ServiceNow**—Webhook connector for ServiceNow

If you need to create a webhook connector for a different ticketing system, an experienced DevOps professional can configure the universal webhook or email connector by using information in the ticketing system documentation.

### Messaging Webhook

You can configure a webhook to receive Alert Logic security notifications as messages by selecting one of these connectors:

* **Microsoft Teams**—Webhook connector for Microsoft Teams
* **Slack**—Webhook connector for Slack
* **PagerDuty**—Webhook connector for PagerDuty

If you need to create a webhook connector for a different messaging or team collaboration system,  an experienced DevOps professional can configure the universal webhook or email connector by using information in the messaging system documentation.

### Universal

To create a webhook connector for an external system that is not listed or an email connector, an experienced DevOps professional  can configure one of the universal connectors:

* **Webhook**—You can configure this type of connector to send security notifications to any HTTP endpoint. Alert Logic provides a sample payload that you can customize for compatibility with the external system  and your security goals.
* **Email**—You can configure this type of connector to send incident notifications to any web server configured to accept email requests. With this option, the incident payload that Alert Logic sends is not customizable, but you can customize the email subject.

    Alert Logic provides several fully supported webhook connectors for commonly used messaging and ticketing systems. Customers are responsible for correctly configuring a universal connector for other applications. To assist your experienced DevOps professional with troubleshooting, Alert Logic passes through all error messages sent by the target application.    ## Connector management

You can view a list of connectors created in your account from the Connectors page. You can also delete and edit existing connectors. For more information, see [Manage Connectors](connectors/manage-connectors.md).

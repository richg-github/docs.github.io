# Manage Connectors

The Connectors page, listed under ![](../../Resources/Images/dashboard/configure-icon.png)**Configure** in the Alert Logic console, offers a consolidated view of your connectors to third-party applications. The list includes all connectors created in your account. You can create and manage connectors of all types from this page.

Connectors increase efficiency and reduce response times. You can subscribe them to receive security notifications or generate service tickets  automatically. For more information about connectors, see [Webhook and Email Connectors](../connectors.md).

## Connector creation

You can create connectors of all types from the Connectors page. Click  the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)), and then choose the type of connector.

Application requirements vary and often require different information. For instructions on how to configure a specific connector, see the [Connectors Configuration Guide](connectors.md).

## Filter the connectors list

The Connectors page displays all connectors for your accounts and the accounts you manage. You can filter the list by connector type or payload type.

### Connector Type filters

Filters in the Connector Type category include all the choices available when you click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)) on the Connectors page.

Filters for specific applications include these webhook connectors:

* Jira
* Jira Service Desk
* ServiceNow
* Microsoft Teams
* Slack
* PagerDuty

The list also includes the following universal connectors.

* **Webhook**—A webhook created for a third-party application not listed above. This type of connector sends security information to a target URL.
* **Email**—A connector that sends security incidents to a target email address of a  third-party application

The number of connectors of that type appears next to the filter name.

### Payload Type filters

The Payload Type filters include the  types of Alert Logic security information supported by webhook connectors:

* Incident
* Observation (of a log correlation)
* Scheduled Report Notification

The number of connectors configured with that payload type appears next to the filter name. For more information about the payload types and  sample JSON, see:

* [Incident Schema](incident.md)
* [Observation Schema](observation.md)
* [Health Schema](health.md)
* [Scheduled Report Notification Schema](scheduled-report-notification-payload.md)

    Email connectors support only the Incident payload type.    
To filter the connectors list:

1. In the left navigation, click one or more filters in the Connector Type and/or Payload Type category to narrow the list. The active filter is in bold format.
2. To search for a filter, type a filter value in **search filters**.
3. To clear filters and start over, click one or more of the active filters to remove them, delete text typed in **search filters** (if applicable), or click **CLEAR ALL FILTERS**.

## Group and sort the connectors list

Alert Logic groups your connectors by the following business categories and sorts them by name within each grouping:

* Ticketing Webhook
* Messaging Webhook
* Universal

To change the grouping,  click **Group by**, and then click the option you want:

* Business Category
* Connector Type
* Payload Type

## Edit a connector

You can change the details in an existing connector.

    Do not change the payload type in a saved connector. Although webhook connectors support multiple payload types you must create another specific webhook connector to avoid conflicts with existing notifications .    
To edit  a connector:

1. In the list of connectors, find the connector you want to edit, and then click the **EDIT** icon.
2. Change any of the available settings.
3. Click **TEST** to verify the connector is valid, and then click **SAVE**.

## Delete a connector

In the list of connectors, find the connector you want to delete, and then click the **DELETE** icon.

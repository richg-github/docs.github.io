# Connectors Configuration Guide

You can configure a  connector in the Alert Logic console  to send [notifications](../notifications.md) to  any public-facing HTTP endpoint. Connectors  allow you to send security data directly to a third-party application in near real time. When  you set up a notification and subscribe a webhook or email connector, the connector sends the event to the target URL or email address you configured and can generate a message or IT service management (ITSM) ticket  automatically.

The following guides for configuring Alert Logic connectors are available. The list is organized by business category. The universal connectors allow experienced DevOps professionals to configure an email connector or a webhook for which an application-specific webhook is not available.

## Ticketing webhook

* [Configure Jira Webhook Connector](jira.md)
* [Configure Jira Service Desk Webhook Connector](jsd.md)
* [Configure ServiceNow Webhook Connector](servicenow.md)

## Messaging webhook

* [Configure Microsoft Teams Webhook Connector](teams.md)
* [Configure PagerDuty Webhook Connector](pagerduty.md)
* [Configure Slack Webhook Connector](slack.md)

## Universal

* [Configure a Universal Webhook Connector](webhooks.md)
* [Configure a Universal Email Connector](email.md)

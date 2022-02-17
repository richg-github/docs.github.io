Notes/scraps

Language for app-specific: prepopulated with required information, predefined content

Major questions that need to be socialized in the next scrum of scrums:

1. Are we doing the base64 encoding for the Authorization header or do we need it to already be encoded for us by the customer? It would be friendlier and likely result in fewer support calls if we handle the encoding. Preferred approach is to add fields to get the needed components, and then we should build the Authorization header.
2. Are the components needed to build the Authorization header the same for each authenticated webhook? If not, Kim needs the list of instructions for each.
3. Which payload types are supported? Earlier it seemed that the payload did not change dynamically when the user selected a type other than Incident.
**Note:** For unauthenticated webhooks, customers could already subscribe incident, observation, and scheduled report notifications. For more info, see [Webhooks](https://docs.alertlogic.com/configure/webhooks.htm).
4. Payloads: seem to have too much data in them
5. Authenticated vs Unauthenticated: Universal template will contain all possible fields (determined through the native integrations we support) but none are required. Payload empty save curly braces. Documentation to specify universal template is unsupported, outside of the error messages we pass through from the target system [KH: maybe wording such as for experienced Dev Ops personnel. ] Alert Logic provides several webhoook connectors for commonly used messaging and ticketing systems. Customers are responsible for the correct configuration of any universal webhooks created. Alert Logic does, however,

* **Incident**—An incident includes one or more suspicious events that require attention to maintain your security posture, achieve regulatory compliance, or both. The incident payload includes a description of the incident, threat level, recommended actions, a link to the incident in the Alert Logic console, and more.
* **Observation**—An observation indicates that Alert Logic observed an occurrence of a [log correlation](../notifications/log-correlation.md). The observation payload
* **Scheduled Report**—You can schedule a report and receive a notification when  the report is available. The scheduled report payload includes information such as the report name, description, and a link to the report in the Alert Logic console.

* **Ticketing Webhook**—An application-specific webhook connector such as for ServiceNow that you can configure to generate IT service management (ITSM) tickets automatically from Alert Logic security notifications
* **Messaging Webhook**—An application-specific webhook such as for Microsoft Teams that you can configure to send Alert Logic security notifications as messages
* **Universal**—A custom webhook connector for which an application-specific connector is not available or an email connector for any third-party application

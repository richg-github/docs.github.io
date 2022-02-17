# Authentication Application Security Incidents

Alert Logic can detect and generate security incidents from log data collected from third-party authentication application resources. Alert Logic collects log data through API-based integration with these applications. Authentication security incidents  enhances your security content by providing greater visibility into threats in your environment.

Security incidents are generated when  suspicious events are detected  that require attention to maintain your security posture, achieve regulatory compliance, or both. Alert Logic organizes the incidents by threat level and classification type on your Incidents page. To learn more about the Incidents page, see [Incidents](incidents.md).

Alert Logic also identifies relevant security information derived from one or multiple sources from the log data collected, which are referred to as observations. For more information, see [Security observations](#Security).

For Managed Detection and Response customers, you can also  view your security incident analytics in the [Authentication Management Summary](dashboard/authentication-management-summary.md) and [Authentication Management Security](dashboard/authentication-management-security.md) dashboards.

## About security incidents

Alert Logic generates security incidents related specifically to administrative actions, user logins, and user behavior, which are classified as authentication:activity and admin:activity in the  [Incidents](incidents.md) page in the Alert Logic console. Alert Logic can generate security incidents from the following authentication applications:

* Auth0
* Cisco Duo
* Azure/Office 365 AD
* Okta
* Salesforce

For information about how to configure one of these authentication applications, see [Security log configuration](#Security2).

### Security incident examples

Alert Logic generates and classifies the following security incidents from authentication application log data if detected in the [Incidents](incidents.md) page:

| Name | Description | Classification |
|---|---|---|
| Brute force activity ​ | When brute force activity is detected from an IP address. An incident is triggered at a threshold of 250 log events for a single user, and at a threshold of 60 log events for multiple users. | authentication:activity​ |
| MFA disabled​ | Disabled MFA of a user from the sign-in logs | authentication:activity​ |
| Sign-in attempt from risky IP​ | Login failure from a risky IP address and sign-in attempts from a malicious IP address. | authentication:activity​ |
| User granted admin privileges | User granted administrator privileges to another user. | admin:activity​ |
| User attempted to access admin application | User attempted to access an admin application. | admin:activity​ |
| Multiple countries, single day | Logins detected from multiple countries in one day. | authentication:activity |
| Credential stuffing activity | A type of brute force activity where an attacker obtains leaked credentials from an unrelated breach and attempts to gain access to other accounts through credential reuse. | authentication:activity |
| Successful login from risky IP | Successful login from a risky IPs. A user from an IP address associated with malicious activity has successfully logged in. | authentication:activity |

## Security observations

Alert Logic also performs observations of relevant security information that is derived from one or multiple sources from the authentication application log data. Observations do not always meet the criteria for Alert Logic to generate an incident, but can demonstrate security value. Observations can identify security patterns and allow you to conduct threat hunting, and manually raise incidents as necessary. Examples of observations that Alert Logic can perform if detected from authentication application log data are the following:

## Security log configuration

You  must configure log collection for the authentication application in the [Application Registry](../configure/application-registry.md) page in the Alert Logic console for Alert Logic to collect log data and generate incidents. The Application Registry page is a catalog with all of the available applications from which Alert Logic can receive log data. You can add multiple log collection instances to each application.

### Configure an authentication application log collection instance

The instructions below provide a basic workflow for configuring an application. However, application requirements vary and often require different information. See the guide specific to the application you want to configure:

* [Configure Auth0 Log Collector ](../configure/collectors/auth0.md)
* [Configure Cisco Duo Log Collector ](../configure/collectors/ciscoduo.md)
* [Configure Microsoft Office 365 Log Collector](../configure/collectors/o365.md)
* [Configure Okta Log Collector ](../configure/collectors/okta.md)
* [Configure Salesforce Log Collector](../configure/collectors/salesforce.md)

To see the full list of log collection instructions available, see [Log Collectors Configuration Guide](../configure/collectors/log-applications.md).

**To add a new application collection**:

1. In the Alert Logic console,  click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page to access the Application Registry page.
2. Click ![](../Resources/Images/dashboard/configure-icon.png) **Configure**, and then click **Application Registry**.
3. On the Application List tab, use the drop-down menu to select the application type you want to see.
4. Click **GET STARTED** from the available application you want to configure.
5. Depending on the application, the required fields and options will vary. The general configuration requirements are the following:
   * Under Details, type a name for the application.
   * Under Collection Method and Policy, specify a location from where to collect log data, and provide the required credentials associated with your application account.
7. Click **ADD**.
8. In the Application List tab, if you have configured your application correctly, the application tile will say Configured.

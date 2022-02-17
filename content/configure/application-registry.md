# Application Registry

Application Registry provides an intuitive and efficient way to integrate multiple third-party applications that can generate logs. Application Registry is a repository of platform integrations in your Configuration group in the Alert Logic console. Integration with third-party applications adds administrative and security value to your organization.  Application Registry is only available for Professional and EnterpriseManaged Detection and Response customers.

To access the Application Registry page, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page. Click **Configure**, and then click **Application Registry**.

## Supported applications

Alert Logic offers integration with applications in multiple ways, including API-based integration with applications and passive log collecting through syslog forwarding  with most firewall platforms. Alert Logic works to continuously release more applications.

Application requirements vary and often require different information. For instructions on how to integrate a specific application, see the [Log Collectors Configuration Guide](collectors/log-applications.md).

### Authentication Applications

Alert Logic supports log collection from many single sign-on and multi-factor authentication applications.In addition to log parsing, Alert Logic generates security incidents for some of the authentication applications that are supported for collection. Incidents generated relate to administrative actions, user login, and user behavior. To learn more about the security incidents Alert Logic generates from log data collected from the authentication applications, see [Authentication Application Security Incidents](../analyze/security-incidents.md).

### Customer Relationship Management (CRM) Products

Alert Logic supports log collection from many customer relationship management (CRM) products. In addition to log parsing, Alert Logic generates security incidents for some of the CRM applications that are supported for collection. Incidents generated relate to administrative actions, user login, and user behavior.

### AWS CloudTrail

Alert Logic supports log collection from AWS CloudTrail. Alert Logic supports parsing for many types of CloudTrail log messages but does not currently generate security incidents from those messages. To learn how to configure your own rules for triggering incidents, observations, and notifications using [Search: Log Messages](../analyze/log-message-search.md), see [Correlations and Notifications](notifications/log-correlation.md).

### Container Environments

Alert Logic supports log collection from many types of container environments. Alert Logic supports parsing for many types of container log messages  but does not currently generate security incidents from those messages. To learn how to configure your own rules for triggering incidents, observations, and notifications using [Search: Log Messages](../analyze/log-message-search.md), see [Correlations and Notifications](notifications/log-correlation.md).

### Endpoint Products

Alert Logic supports log collection from many endpoint protection products. In addition to log parsing, Alert Logic generates security incidents for some of the endpoint products that are supported for collection.

### Firewall Products

Alert Logic supports log collection from many firewall products. You must configure the applications to send logs to the IP address of the Alert Logic syslog remote collector on port 1515. Alert Logic generates security incidents for some of the firewall applications listed above based on log data. Incidents generated relate to suspicious and malicious behavior, exposures, and new service resource discovery. To learn more about the security incidents Alert Logic generates from log data collected from the firewall application, see [Firewall Incidents and Log Configuration](../analyze/firewall-incidents.md).

### Flat File Logs Collection

### Microsoft Azure Integrations

### Productivity Applications

### Protected hosts

### S3

Applications include products for authentication, productivity, management and more. Alert Logic serves as a remote collector to receive log data from the application related to different incident types, depending on the product type. Alert Logic collects logs related to administrative actions, anomaly detection for user logins, user behavior, resource access, system compromise, attack outbreak, and others. Applications available include the following:

* Amazon Web Services (AWS)
* Auth0
* Carbon Black
* Cisco Duo
* Google Cloud Platform
* G Suite
* Microsoft Office 365
* Okta
* Salesforce

Alert Logic generates security incidents for some of the authentication applications listed above based on log data. Incidents generated relate to administrative actions, user login, and user behavior. To learn more about the security incidents Alert Logic generates from log data collected from the authentication applications, see [Authentication Application Security Incidents](../analyze/security-incidents.md).

For Firewall logs, the Alert Logic syslog remote collector receives log data. You must configure the applications to send logs to the IP address of the Alert Logic syslog remote collector on port 1515. Firewall applications available include the following:

* Cisco Adaptive Security Appliance (ASA)
* Cisco Firepower
* Fortinet
* Palo Alto
* Checkpoint
* Cylance

Alert Logic generates security incidents for some of the firewall applications listed above based on log data. Incidents generated relate to suspicious and malicious behavior, exposures, and new service resource discovery. To learn more about the security incidents Alert Logic generates from log data collected from the firewall application, see [Firewall Incidents and Log Configuration](../analyze/firewall-incidents.md).

### Coming soon

Alert Logic is expanding the Application Registry page to include the capability to collect log data from a wide range  of applications. For a preview of applications in progress, see the Coming Soon section from the Application Registry page. To learn more about an application, click **LEARN MORE** in the tile.

## Configure your applications

The instructions below provide a basic workflow for configuring an application. Application requirements vary and often require different information. For instructions on how to integrate a specific application, see the [Log Collectors Configuration Guide](collectors/log-applications.md).

**To add a new application collection**:

1. On the Application List tab, use the drop-down menu to select the application type you want to see.
2. Click on the tile for the corresponding integration you want to configure. If there are several options, click the specific integration type you are looking for.
3. Depending on the application, the required fields and options will vary. The general configuration requirements are the following:
   * Under Details, type a name for the application.
   * Under Collection Method and Policy, specify a location from where to collect log data, and provide the required credentials associated with your application account.
5. Click **ADD**.
6. In the Application List tab, if you have configured your application correctly, the application tile will say Configured.

### Add new

You can add multiple log collection instances to each application. To add a new log collection to one you previously configured, click **ADD NEW**. Fill out the required fields, and then click **ADD**.

## Manage your configured applications

You can view a list of your configured applications and access an application's metadata. Click the **Configured Applications** tab. On the left panel, you can filter which application type you want to see, and on the page, you can sort the applications by name, applications last created, or applications last modified.

The page lists the application and the log collection instances you created. Click **View** on the specific log collection instance to see details.

### Details page

The details page provides more information of the application, including metadata for creation and modification, timestamps (if any), and collection method and policies. Click **VIEW LOGS** to quickly access the Search page already filtered  with the log data for that log collection instance.

### Edit an application collection instance

In the application collection instance you want to edit, click **View**, and then click the edit icon (![](../Resources/Images/pencil icon.png)). Make any necessary changes to the fields, and then click **SAVE**.

### Delete an application collection instance

In the application collection instance you want to delete, click **View**, and then click the delete icon (![](../Resources/Images/Icons/trash icon.png)). Click **DELETE**.

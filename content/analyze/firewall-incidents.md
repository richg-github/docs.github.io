# Firewall Incidents and Log Configuration

Alert Logic can detect and generate firewall security incidents and observations from log data collected from third-party firewall application resources. Alert Logic collects log data through passive syslog forwarding from the firewall application. Firewall security incidents and observations enhances your security content value for greater visibility into threats in your environment.

Firewall security incidents are generated when  suspicious events are detected  that require attention to maintain your security posture, achieve regulatory compliance, or both. Alert Logic organizes the incidents by threat level and classification type on your Incidents page. To learn more about the Incidents page, see [Incidents](incidents.md).

Alert Logic also identifies relevant security information derived from one or multiple sources from the log data collected, which are referred to as observations. For more information, see [Firewall observations](#Firewall-observations).

You must have an Alert Logic syslog remote collector configured and have an active firewall application to detect firewall incidents and collect log data in the Alert Logic console. For more information, see [Firewall log configuration](#Firewall).

For Managed Detection and Response customers, you can also  view your firewall incident analytics in the three dashboards: [Firewall Log Volume Analysis Dashboard](dashboard/firewall-log-volume-dashboard.md), [Firewall Log Security Analysis Dashboard](dashboard/firewall-log-security-dashboard.md), and [Firewall Log Traffic Analysis Dashboard](dashboard/firewall-log-traffic-analysis-dashboard.md).

## Firewall log configuration

You must already have configured an Alert Logic syslog remote collector, and a firewall  application. To learn how to configure the Alert Logic remote collector, see [Install the  Remote Collector for Linux](../prepare/remote-log-collector-linux.md) or [Install the Remote Collector for Windows](../prepare/remote-log-collector-windows.md).

You must configure the third-party firewall application resources to forward firewall logs to the Alert Logic syslog remote collector on port 1515. To learn how to forward the firewall logs, reference the documentation of the third-party firewall application from which you want incidents generated.

For Managed Detection and Response customers, you also have access to the Application Registry page, which is a catalog of all the available applications from which Alert Logic can receive log data. For more information about Application Registry, see [Application Registry](../configure/application-registry.md).

## Firewall incidents

Alert Logic specifically generates security incidents related to suspicious and malicious behavior, exposures, and new service resource discovery.  Firewall security incidents that Alert Logic can generate include the following:

* Cisco Adaptive Security Appliance (ASA)
* Cisco Firepower
* Fortinet
* Palo Alto

### Firewall incident examples

Examples of security incidents that Alert Logic generates  if detected from firewall application log data are the following:

* A new created service in the environment that is being used by a customer or external systems.
* Blacklisted IP addresses creating successful connections to most popularly exploited services in the network of a customer.
* A blacklisted IP address successfully probed a new internal resource.

## Firewall observations

Alert Logic also performs observations of relevant security information that is derived from one or multiple sources from the firewall application log data. Observations do not always meet the criteria for Alert Logic to generate an incident, but can demonstrate security value. Observations can identify security patterns and allow you to conduct threat hunting, and manually raise incidents as necessary. Examples of observations that Alert Logic can perform if detected from firewall application log data are the following:

* An IP addresses in logs matches with a listed blacklisted IP addresses.
* Brute force password guessing for a user for a certain amount of time.
* An anomalous number of resource downloads for a user deviated from normal activity.

You can view data related to observations in the [Firewall Log Volume Analysis Dashboard](dashboard/firewall-log-volume-dashboard.md).

# Endpoint Security Incidents

Alert Logic can detect and generate endpoint incidents from log data collected from third-party endpoint application resources. Alert Logic collects log data through endpoint integrations. Endpoint security incidents  enhances your security content by providing greater visibility into threats in your environment.

Security incidents are generated when  suspicious events are detected  that require attention to maintain your security posture, achieve regulatory compliance, or both. Alert Logic organizes the incidents by threat level and classification type on your Incidents page. To learn more about the Incidents page, see [Incidents](incidents.md).

Alert Logic also identifies relevant security information derived from one or multiple sources from the log data collected, which are referred to as observations. For more information, see [Security observations](#Security).

## About endpoint incidents

Alert Logic generates endpoint incidents related specifically to:

* Endpoints for ransomware detected
* Audit and remediation (potential new malware or suspicious event detected)
* Outbreak of non-mitigated suspicious threats
* Non-mitigated malicious threats across multiple hosts
* Outbreak of malicious threats mitigated across multiple hosts
* Agent that failed to remediate
* Agent with a high severity alert  (malicious and non-mitigated)

You can view these endpoint incidents in the  [Incidents](incidents.md) page in the Alert Logic console. Alert Logic can generate security incidents from the following endpoint applications:

* Carbon Black
* SentinelOne
* Cisco Endpoint (formerly Cisco AMP)
* CrowdStrike
* Cylance
* Sophos

For information about how to configure one of these endpoint applications, see [Endpoint log configuration](#Security2).

### Endpoint incident examples

Alert Logic generates the following endpoint incidents  in the [Incidents](incidents.md) page from endpoint log data at the indicated threshold.

#### Carbon Black endpoint incidents 

| Name | Description | Threshold  | Classification |
|---|---|---|---|
| Carbon Black Endpoint: Known malware detected | Known Malware file(s) Detected on %destination_host% | Single-host: One or more events in five minutes | endpoint:activity​ |
| Carbon BlackEndpoint: Ransomware detected | Ransomware file(s) Detected on %destination_host% | Single-host: One or more events in five minutes | endpoint:activity​ |
| Carbon Black Endpoint Outbreak: Potential new malware or suspicious event detected | New or Suspicious malware file Detected on multiple hosts | Multi-host: Five or more hosts in 15 minutes | endpoint:activity​ |

#### SentinelOne endpoint incidents

| Name | Description | Threshold  | Classification |
|---|---|---|---|
| SentinelOne Outbreak: Non-Mitigated Suspicious Threat across Multiple Hosts | Triggers when SentinelOne has not mitigated the same suspicious threat across multiple hosts in a 30-minute period | Five or fewer unique hosts in 30 minutes | endpoint:activity​ |
| SentinelOne Outbreak: Non-Mitigated Malicious Threat across Multiple Hosts | Triggers when SentinelOne has not mitigated the same malicious threat across multiple hosts in a 30-minute period | Five or fewer  unique hosts in 30 minutes | endpoint:activity​ |
| SentinelOne Outbreak: Malicious Threat Mitigated across Multiple Hosts | Triggers when SentinelOne has mitigated the same malicious threat across multiple hosts in a 30-minute period | Five or fewer  unique hosts in 30 minutes | endpoint:activity​ |
| SentinelOne: Agent Failed to Remediate | SentinelOne: Failed Remediation of Threat(s) Detected on %destination_host% | Single-host: One or more events in five minutes | endpoint:activity |
| SentinelOne: High severity alert (malicious) (non-mitigated) | SentinelOne: Non-Mitigated Malicious Threat(s) Detected on %destination_host% | Single-host: One or more events in five minutes | endpoint:activity |

#### Cisco Endpoint incidents

| Name | Description | Threshold  | Classification |
|---|---|---|---|
| Cisco Endpoint: Exploit Prevented | Cisco Endpoint: Exploit file(s) Prevented on $destination_host | One event in five minutes | endpoint:activity |
| Cisco Endpoint: Possible Ransomware TTPs detected | Cisco Endpoint: Possible Ransomware file(s) Detected on %destination_host% | Single-host: One or more events in five minutes | endpoint:activity |

#### Cylance Endpoint incidents

| Name | Description | Threshold  | Classification |
|---|---|---|---|
| Cylance: Known hacktool detected | Cylance: Ransomware file(s) Detected on %destination_host% | Single-host: One or more events in five minutes | endpoint:activity |
| Cylance: Ransomware detected | Cylance: Ransomware file(s) Detected on %destination_host% | Single-host: One or more events in five minutes | endpoint:activity |
| Cylance: Exploit Attempt | Cylance: Exploit Attempt(s) Detected on $destination_host | One event in five minutes | endpoint:activity |

#### Sophos Endpoint Incidents

| Name | Description | Threshold  | Classification |
|---|---|---|---|
| Sophos Endpoint - Ransomware detected | Possible Ransomware file(s) Detected on $destination_host | One event in five minutes | endpoint:activity |

## Security observations

Alert Logic also performs observations of relevant security information that is derived from one or multiple sources from the authentication application log data. Observations do not always meet the criteria for Alert Logic to generate an incident, but can demonstrate security value. Observations can identify security patterns and allow you to conduct threat hunting, and manually raise incidents as necessary. Examples of observations that Alert Logic can perform if detected from authentication application log data are the following:

## Endpoint log configuration

You  must configure log collection for the endpoint application in the [Application Registry](../configure/application-registry.md) page in the Alert Logic console for Alert Logic to collect log data and generate incidents except for Cylance. The Application Registry page is a catalog with all of the available applications from which Alert Logic can receive log data. You can add multiple log collection instances to each application.

### Configure an endpoint log collection instance

The instructions below provide a basic workflow for configuring an application. However, application requirements vary and often require different information. See the guide specific to the application you want to configure:

* [Configure Carbon Black Log Collector ](../configure/collectors/carbonblack.md#Create)
* [Configure SentinelOne Log Collector ](../configure/collectors/sentinelone.md)
* [Configure Cisco AMP Log Collector ](../configure/collectors/ciscoamp.md)
* [Cylance endpoint log collection configuration](#Cylance)
* [Configure Sophos Log Collector ](../configure/collectors/sophos.md)
* CrowdStrike

To see the full list of log collection instructions available, see [Log Collectors Configuration Guide](../configure/collectors/log-applications.md).

**To add a new application collection**:

1. In the Alert Logic console,  click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) from the Dashboards page.
2. Click ![](../Resources/Images/dashboard/configure-icon.png) **Configure**, and then click **Application Registry**.
3. On the Application List tab, use the drop-down menu to select the application type you want to see.
4. Click **GET STARTED** from the available application you want to configure.
5. Depending on the application, the required fields and options vary. The general configuration requirements are the following:
   * Under Details, type a name for the application.
   * Under Collection Method and Policy, specify a location from where to collect log data, and provide the required credentials associated with your application account.
7. Click **ADD**.

In the Application List tab, if you configured your application correctly, "Configured" appears on the application tile.

### Cylance endpoint log collection configuration

You must already have configured an Alert Logic syslog remote collector and a Cylance application. To learn how to configure the Alert Logic remote collector, see [Install the  Remote Collector for Linux](../prepare/remote-log-collector-linux.md) or [Install the Remote Collector for Windows](../prepare/remote-log-collector-windows.md).

The Cylance application resources must be forwarding logs to the Alert Logic syslog remote collector on port 1514. To learn how to forward the logs, see the Cylance documentation.

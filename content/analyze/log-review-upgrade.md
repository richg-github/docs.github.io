# Machine Learning Log Review Upgrade

Alert Logic is upgrading the Log Review process with new machine learning algorithms, which allows Alert Logic to deliver a higher level of security value. The Machine Learning Log Review algorithms can automatically detect many log-based anomaly types based on unique patterns and trends learned from your organization.

The Machine Learning Log Review output consist of anomalies generated from the machine learning based detection that are delivered as information-level incidents in the [Incidents](incidents.md) page. Alert Logic offers detailed reports of your anomalies generated with the machine learning Log Review algorithms in the evidence tab of the incident investigation report. For more information about the investigation report, see [Investigation Report](../get-started/incidents-upgrade.md#investigationReport).

Log Review incidents are listed in the [Monthly Log Review Report](reports/threats/log-review-analysis/monthly-log-review.md) report. You can also use the [Incident Daily Digest](reports/threats/incident-analysis/incident-daily-digest.md) report to evaluate daily incidents by threat level, classification, top attackers, and top targets.

Alert Logic analysts continue to oversee Log Review  incidents, and the Machine Learning Log Review feature will continue to meet your log review compliance requirements.

## About  machine learning based on Log Review process

The machine learning model-based Log Review is fast, efficient and accurate, which increases the likelihood of detecting most anomalies through log data. The Machine Learning Log Review model can detect more than 100 anomaly scenarios based on time series, location, and unusual names. The machine learning models are computed based on specific logs customers sent to Alert Logic and are based on at least 90 days worth of data. Rule-based analytics can also trigger anomaly detections, which allows anomalies to be detected automatically and reliably, based on your patterns and trends.

Machine Learning Log Review examines security-related logs that alert you to potential security issues, and assists with compliance mandates. Log anomalies are automatically raised based on:

* Unusual counts of certain events
* Unique users accessing a host
* Unusual or suspicious user names
* Blacklists
* User preference

Examples of log data that Alert Logic reviews are:

* **Windows**: Failed logins, changes to privileges, changes to accounts, Active Directory global catalog changes, and others
* **Linux**: Sudo access, SSH failed logins, switched user common success/fails, and others
* AWS: MFA, security group changes, IAM, EC2, S3 changes, user account and access changes, network control changes, and others
* Azure: Backup,  user file access, user login activity, user network security events, OAuth2 grant activity, object access, user role modification activity, service principal activity, user file access, user group modification

The Machine Learning Log Review algorithm then observes and learns  patterns and trends, and it automatically tunes itself  for more accurate security content.

## Machine Learning Log Review models and outcomes

The Machine Learning Log Review is based on two models:

* Customer model: Tracks and learns from log data related to customer activity
* Host model: Tracks and learns from log data related to host changes
* User model: Tracks and learns from log data related to user activity

The Machine Learning Log Review outcomes include anomalies based on user trends and anomalies based on host trends. The following are anomalies that Alert Logic uses the following anomalies to generate incidents for all machine learning models:

| Anomaly | Description |
|---|---|
| high-message-count | A spike in the number of log messages of a given type. |
| high-sourceuser-count | A spike in the number of unique source users for a given message type and host. |
| high-targetuser-count | A spike in the number of unique target users for a given message type and host. |
| high-sourcehost-count | A spike in the number of unique source hosts for a given message type and host or user. |
| high-targethost-count | A spike in the number of unique target hosts for a given message type and host or user. |
| unusual-name | A user name is different from the normal names encountered. |
| unusual-location | A host location is different from the normal locations encountered. |

Alert Logic analysts also generate incidents based on pattern matching and rule-based detection based on your preferences. These include the following Windows activities:

* High log message count for Windows failed login
* High log message count for Windows account changed
* Total message count for Windows account changed
* Windows Account Lockouts

Incidents are also generated for the following Linux-based log administrator activities:

* High log message count for failed UNIX SSH Failed login
* Suspicious Unix Sudo Access
* Unix Switch User Command Success
* Network Device Failed Logins (i.e. Cisco ASA, PAN, etc.)
* Unix Administrator Failed Logins
* Unix Administrator Account Group Changes

### Observations

Alert Logic can  note observations in the incident investigation reports which provide other relevant security information. Observations identify security patterns and allow you to conduct threat hunting for activity that does not meet the criteria to become an incident, but can still demonstrate security value. The two types of observations are anomaly and suspicious pattern observations.

For anomaly observations, Alert Logic uses the following criteria to make note  of this observation:

* For high-message-count and high-user-count anomalies, the properties are:
   * Expected-count: the count of messages that the anomaly detector expected to see based on the machine learning modes for users and hosts
   * Actual-count: the count of messages that the anomaly detector actually saw during the review for users and hosts
* For an unusual-location anomaly, the properties are:
   * Location: the anomalous location
   * Message-count: number of messages with anomalous location
* For an unusual-name anomaly, the properties are:
   * Name: the anomalous name
   * Message-count: number of messages with anomalous location

For suspicious pattern observations, Alert Logic uses the following properties to make note  of this observation:

* Message-count: the number of messages that matched the pattern
* Matched-patterns: the values that matched the pattern

### Download evidence

For Log Review incidents, the **Investigation and Recommendation** tab also includes the Overview of Log Alerts and Anomalies section. The Overview of Log Alerts and Anomalies section is a briefing of the evidence. You can review the evidence in more detail from the **Evidence** tab, which includes a table-style list view for evidence. From the Evidence tab, you can dive deeper into your investigation and download CSV files of observations and facts from event groupings.

You can also use the aggregator summary section which groups observation findings and evidence for different log message types. For compliance needs, you can download evidence for specific aggregator types to a CSV file. The file contains information fields from observations or facts from all of the log messages associated with the anomaly findings.

#### Download observations

You can download a CSV file of the observations for a specific event under an activity.  Click the drop-down arrow (![](../Resources/Images/incidents/drop-down-arrow.png)) next to the event grouping to expand details, and then click **Download Observations**. To download additional data associated with the observations, click **Download Observation Evidence**. The CSV file for observations contains the following fields:

* Summary
* Date
* Description
* Severity
* Customer name
* Caller user
* Log source
* Maximum time
* Message type
* Minimum time
* Terminal time
* Total messages
* Aggregator	entity type
* User

#### Download facts

You can investigate further and download the facts of an observation event under the Log Review activity. Click the drop-down arrow (![](../Resources/Images/incidents/drop-down-arrow.png)) to expand the details of an observation, and then click **Download Facts**. The CSV file for the observation facts includes the following fields:

* Description
* Date
* Message
* User
* Facility and priority
* Syslog fields PID
* UID
* User name

### Customer model

The Machine Learning Log Review customer model includes anomalies based on  customer trends of log message types for high overall count.

| Model | Anomaly | Included details |
|---|---|---|
| Customer | high-message-count | Customer Target Time range Log source Customer ID and name Message type (parser) Implicated hosts Implicated users Expected count Actual count |

### Host model

The Machine Learning Log Review host model includes anomalies based on host trends of  log message types for high count, unusual location, and unique users.

| Model | Anomaly | Included details |
|---|---|---|
| Host | high-message-count | Time range Log source Customer ID and name Message type Host IP/name Implicated users Implicated event details Expected count Actual count |
| Host | high-sourceuser-count high-targetuser-count | Time range Log source Customer ID and name Message type Host IP/name Implicated users Implicated event details Expected count Actual count |
| Host | unusual-location | Time range Log source Customer ID and name Message type Host IP/name Implicated users Implicated event details Location |

### User model

The Machine Learning Log Review user host model includes anomalies based on  user trends of log message types for a high overall count, and it includes anomalies regarding unusual names.

| Model | Anomaly | Included details |
|---|---|---|
| User | unusual-name | Time range Log source Customer ID and name Message type User name Implicated hosts Implicated event details |
| User | high-message-count | Time range Log source Customer ID and name Message type User name Implicated hosts Implicated event details Expected count Actual count |
| User | high-sourcehost-count high-targethost-count | Time range Log source Customer ID and name Message type User name Implicated hosts Implicated event details Expected count Actual count |

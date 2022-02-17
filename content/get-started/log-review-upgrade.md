# Log Review Upgrade

Alert Logic is upgrading Log Review incidents with a new machine learning algorithms which allows Alert Logic to deliver a higher level of security value.

The Log Review machine learning algorithms can automatically detect many log-based incident types based on unique patterns and trends learned from your organization. Alert Logic analysts will still be involved in overseeing Log Review  incidents, and the Log Review feature will continue to meet your log review compliance requirements. You will also  receive the following detailed reports of your log anomalies and log review incidents with the Log Review machine learning algorithms:

* [Daily Log Anomaly Analysis](../analyze/reports/threats/log-anomaly-analysis/daily-log-anomaly-analysis.md)
* Monthly Log Anomalies
* [Monthly Log Review Report](../analyze/reports/threats/log-review-analysis/monthly-log-review.md)

The Log Review machine learning capability allows cases and log-based incidents to be automatically created. The Log Review machine learning capabilities observe and become familiar with unique patterns and trends, which is then automatically tuned for more accurate security content. To learn more about Log Review incidents, see [About incident classification types](../analyze/incidents.md#aboutIncidentClasses).

## Log Review process

Alert Logic analysts have examined security-related logs to inform you of potential security issues, and assist with compliance mandates. Alert Logic analysts review log messages and their counts, and then generate incidents  based unusual counts of certain events, or unique user accessing a host, unusual or suspicious user names, blacklists, and user preference. The Alert Logic analyst  then consults with the representative of your organization for fine-tuning. Anomalies are then computed based on spikes observed manually.

Logs Alert Logic analysts reviews the following types of logs daily:

* **Windows**: Failed logins, changes to privileges, changes to accounts, AD global catalog changes, and others
* **Linux**: Sudo access, SSH failed logins, switched user common success/fails, and others
* AWS: MFA, Security group changes, IAM, EC2, S3 changes, user account and access changes, network control changes

Log Review has been upgraded to automatically review significantly more logs.

## About machine learning based on Log Review

The machine learning model based on Log Review is fast, efficient, and accurate which increases the likelihood of detecting most anomalies through log data. The Log Review machine learning model can detect more than 100 anomaly scenarios based time series, location, and unusual names. It is also a rule-base analytics which allows anomalies to be detected automatically and reliably—on your patterns and trends.

### Log Review models and outcomes

The Log Review machine learning is based on three models:

* Customer model
* Host model
* User model

The Log Review machine learning outcomes includes anomaly detections based on customer trends, anomalies based on user trends, and anomalies based on host trends.

* **Customer**: Anomalies regarding a high overall count for log message types 'Unix SSH Log Failed' and 'Windows Login Failed'.
* **Host **: Anomalies for a host regarding high count  for log message type 'Windows Login Failed', unusual location for log message type 'Windows Login Failed', and high number of unique users with log messages type ‘Unix SSH Login Failed’.
* **User**: Anomalies regarding a high overall count for log message type 'Windows Login Failed'  for a host, and anomalies regarding unusual names of a user with log messages type ‘Windows Login Failed.

Pattern matching and rule-based detection which are Windows administrator activities include the following:* High log message count for Windows failed login
* High log message count for Windows account changed
* Total message count for Windows account changed

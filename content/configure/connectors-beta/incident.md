# Incident Schema

You can refer to this incident schema to configure the payload template for a third-party webhook connector.

## Schema

JSON

| 1 | { |
| 2 | "accountId": number, |
| 3 | "asset_deployment_type": "string" |
| 4 | "asset_host_name": "string" |
| 5 | "asset_native_account_id": "string" |
| 6 | "assets": {}, |
| 7 | "attacker": { |
| 8 | "account": "string", |
| 9 | "instanceId": "string", |
| 10 | "ip": "string", |
| 11 | "port": number, |
| 12 | "region": "string" |
| 13 | }, |
| 14 | "attacker_country_code": "string", |
| 15 | "attacker_country_name": "string", |
| 16 | "attacker_lset": [ |
| 17 | { |
| 18 | "ip": "string" |
| 19 | }, |
| 20 | { |
| 21 | "value": "string" |
| 22 | } |
| 23 | ], |
| 24 | "closed_time": "string", |
| 25 | "correlation_id": "string", |
| 26 | "correlation_name": "string", |
| 27 | "createTime": number, |
| 28 | "createtime_str": "string, |
| 29 | "customer": "string", |
| 30 | "customer_feedback": { |
| 31 | "feedback": "string", |
| 32 | "feedback_datetime": "string", |
| 33 | "feedback_reason": "string", |
| 34 | "feedback_uid": "string", |
| 35 | "feedback_user": "string" |
| 36 | }, |
| 37 | "customer_status": { |
| 38 | "notes": "string", |
| 39 | "reason_code": "string", |
| 40 | "status": "string", |
| 41 | "status_change_time": "string" |
| 42 | }, |
| 43 | "customer_status_status": "string", |
| 44 | "defaultThreatRating": "string", |
| 45 | "deployment,": "string", |
| 46 | "deployment_subnet": "string", |
| 47 | "deployment_vpc": "string", |
| 48 | "detection_source": "string", |
| 49 | "first_closed_time": "string", |
| 50 | "geo_ip_map": { |
| 51 | "string": { |
| 52 | "city": "string", |
| 53 | "continentcode": "string", |
| 54 | "country": "string", |
| 55 | "countryname": "string", |
| 56 | "ip": "string", |
| 57 | "latitude": number, |
| 58 | "longitude": number, |
| 59 | "postcode": "string", |
| 60 | "regioncode": "string", |
| 61 | "regionname": "string" |
| 62 | } |
| 63 | }, |
| 64 | "humanFriendlyId": "string", |
| 65 | "incident": { |
| 66 | "attackClassId": number, |
| 67 | "attackClassId_str": "string", |
| 68 | "description": "string", |
| 69 | "escalated": "string", |
| 70 | "recommendations": "string", |
| 71 | "summary": "string", |
| 72 | "threatRating": "string" |
| 73 | }, |
| 74 | "incidentId": "string", |
| 75 | "incident_attack_class": "string", |
| 76 | "incident_class": "string", |
| 77 | "incident_escalated": "string", |
| 78 | "incident_threat_rating": "string", |
| 79 | "incident_type": string, |
| 80 | "notes": { |
| 81 | "otherNotes": [ |
| 82 | { |
| 83 | "date": "string", |
| 84 | "note": "string", |
| 85 | "who": "string" |
| 86 | } |
| 87 | ] |
| 88 | }, |
| 89 | "path": "string", |
| 90 | "recommendations": "string", |
| 91 | "scope_type": "string", |
| 92 | "snooze_status": { |
| 93 | "expiration": number, |
| 94 | "expiration_str": "string", |
| 95 | "notes": "string", |
| 96 | "period_ms": number, |
| 97 | "reactivates_at": string, |
| 98 | "reason_code": "string", |
| 99 | "snooze_by": "string", |
| 100 | "snooze_by_uid": "string", |
| 101 | "snoozed": boolean |
| 102 | }, |
| 103 | "snooze_status_snoozed": false, |
| 104 | "sources": [ |
| 105 | "string" |
| 106 | ], |
| 107 | "stack_region": "string", |
| 108 | "updateTime": number, |
| 109 | "updatetime_str": "string", |
| 110 | "victim": { |
| 111 | "value": "['string']" |
| 112 | }, |
| 113 | "victim_lset": [ |
| 114 | { |
| 115 | "value": "['string']" |
| 116 | } |
| 117 | ], |
| 118 | "extra": { |
| 119 | "incidentUrl": "string", |
| 120 | "class": "string", |
| 121 | "analyst_notes": [{ |
| 122 | "date": "string", |
| 123 | "note": "string" |
| 124 | }], |
| 125 | "status": "string", |
| 126 | "tld": "string", |
| 127 | "is_escalated": boolean, |
| 128 | "investigation_report": "string", |
| 129 | "recommendations": "string", |
| 130 | "location_ip": ["string"], |
| 131 | "target_host": ["string"] |
| 132 | } |
| 133 | } |

## Definitions

* **accountId** (*number*) – Alert Logic customer account identifier (example: 12345678)
* **asset_deployment_type** (*string*) – Deployment type of the asset on which the incident occurred
*Valid values: *`datacenter`, `aws`, `saas`, `azure`
* **asset_host_name** (*string*) – Host name of the asset on which the incident occurred (example: 10.1.2.3)
* **asset_native_account_id** (*string*) – Native account identifier of the asset on which the incident occurred, such as the AWS or Azure account ID (example: 123456789012)
* **assets** (*object*) - Used internally
* **attacker** (*object*) – Information about the attacker, if it can be determined
   * **account** (*string*) – Cloud native account identifier (example: 123456789012)
   * **instanceId** (*string*) – Cloud instance identifier of the attacker (example: i-0a159b2a553285ebb)
   * **ip** (*string*) – IP address of the attacker for the incident (example: 10.10.10.12)
   * **port** (*number*) - Port number of the attacker for the incident (example: 40814)
   * **region** (*string*) – Cloud region of the attacker (example: us-east-2)
   * **value** (*string*) - User name, applies to attacks originating from a user instead of an IP address  (example: SomeAttacker)
* **attacker_country_code** (*string*) – ISO two-digit code of the country where the attacker is located, if it can be determined (example: BR)
* **attacker_country_name** (*string*) – Name of the country where the attacker is located, if it can be determined (example: Brazil)
* **attacker_lset** (*array*) - List of information for multiple attackers
   * **ip** (*string*) – List of attacker IP addresses for the incident (example: 203.0.113.1)
   * **value** (*string*) – List of attacker user names for the incident, applies to attacks originating from a user instead of an IP address (example: SomeAttacker)
* **closed_time** (*string*) – ISO date and time in UTC when an Alert Logic Security Operations Center (SOC) analyst closed the incident (example: 2020-08-10T11:24:27.765796+00:00)
* **correlation_id** (*string*) – Uppercase full UUID of an incident generated by a [correlation](../notifications/log-correlation.md) (example:  5F36660A-0015-0120-0002-104300000000)
* **correlation_name** (*string*) – Name of the [correlation](../notifications/log-correlation.md) for an incident generated by a correlation rule (example: Admin Failed Login Correlation)
* **createTime** (*number*) – Epoch time when the incident arrived in the Alert Logic server (example: 1597058547)
* **createtime_str** (*string*) –  ISO date and time in UTC when the incident arrived in the Alert Logic server  (example: 2020-08-10T11:22:27.799796+00:00)
* **customer** (*string*) – Customer name of the Alert Logic account affected by the incident (example: XYZ Corporation)
* **customer_feedback** (*object*) - Customer feedback information about the incident
   * **feedback** (*string*) – Text of the customer feedback (example: The wiggle probe server 10.123.10.57 is making multiple failed login attempts to the James MSSQL servers at INC001DB03G, INC001DB06G,  inc001db04g and inc001db05g. This is expected activity in the James environment. \nINC076660)
   * **feedback_datetime** (*string*) – ISO date and time in UTC when the customer entered feedback (example: 2020-08-14T09:57:35.535995+00:00)
   * **feedback_reason** (*string*) – Feedback assessment (example: threat_not_valid)
   * **feedback_uid** (*string*) – User ID of the user who entered the feedback (example: 423A54CE-105F-4089-B713-10A303DE0938)
   * **feedback_user** (*string*) – Name and email address of the user who entered the feedback (example: CustomerFirstName CustomerLastName username@xyz.com)
* **customer_status**  (*object*) - Incident status information set by the customer
   * **notes** (*string*) – Incident assessment notes written by the customer (example: The wiggle probe server 10.123.10.57 is making multiple failed login attempts to the James MSSQL servers at INC001DB03G, INC001DB06G,  inc001db04g and inc001db05g. This is expected activity in the James environment. \nINC076660)
   * **reason_code** (*string*) – Reason for the incident status change (example: threat_not_valid)
   * **status** (*string*) – Incident status set by the customer
   *Valid values: *`open`, `completed`
   * **status_change_time** (*string*) – ISO date and time in UTC when the customer changed the incident status (example: 2020-08-10T11:22:27.799796+00:00)
* **customer_status_status** (*string*) – Incident status set by the customer
*Valid values: *`open`, `completed`
* **defaultThreatRating** (*string*) – Initially assigned threat level
*Valid values:* `critical`, `high`, `medium`, `low`, `info`
* **deployment** (*string*) – Name of the deployment affected by the incident (example: AWS Production Deployment)
* **deployment_subnet** (*string*) – Name of the subnet affected by the incident (example: subnet-a412345g)
* **deployment_vpc** (*string*) – Name of the virtual private cloud (VPC) affected by the incident (example: vpc-12345678)
* **detection_source** (*string*) – Detection source of the incident
*Valid values: *`Correlation Rules`, `Network IDS`, `Web Log Analytics`, `Log Mgmt`, `Firewall`, `Manual`, `Log Review`
* **first_closed_time** (*string*) – ISO date and time in UTC when an Alert Logic SOC analyst closed the  incident for the first time (example: 2020-09-11T13:22:27.799796+00:00)
* **geo_ip_map** (*object array*) – Geographical information for a list of IP addresses
   * **city** (*string*) – City in which the IP address is located (example: Palmares do Sul)
   * **continentcode** (*string*) – Two-letter ISO code of the continent in which the IP address is located (example: SA)
   * **country** (*string*) – Two-letter ISO code of the country in which the IP address is located (example: BR)
   * **countryname** (*string*) – Name of the country in which the IP address is located (example: Brazil)
   * **ip** (*string*) – IP address (example: 86.34.222.99)
   * **latitude** (*number*) – Latitude in which the IP address is located (example: -30.3465)
   * **longitude** (*number*) – Longitude in which the IP address is located (example: -50.5482)
   * **postcode** (*string*) – Postal code in which the IP address is located (example: 95540)
   * **regioncode** (*string*) – ISO region code in which the IP address is located (example: RS)
   * **regionname** (*string*) – Name of the region in which the IP address is located (example: Rio Grande do Sul)
* **humanFriendlyId** (*string*) – Short incident ID (example: ww1k39)
* **incident** (*object*) – Information about the incident
   * **attackClassId_str** (*string*)
   * **description** (*string*) – Incident explanation (example: **Attack Detail**:  \n**Attacker:** 172.31.37.117, local_ip \n**Targets:** 122.99.34.111, 172.31.37.90, and 172.31.39.79 \n We have detected a recon attack targeting a number of common server vulnerabilities. This is a vulnerability scan however we are unable to determine the specific tool or company performing this attack.)
   * **escalated** (*string*) – Whether an Alert Logic SOC analyst escalated the incident
   *Valid values: *`true`, `false`
   * **recommendations** (*string*) – Recommended actions in response to the incident (example: A compromised host should be isolated from the network and cleaned. Remove the back doors installed and check the system logs for other actions taken. Once a system is compromised, usually one of the first things done by an attacker is creating a secondary access channel. Assume that additional modifications have been made to the system beyond the initial breach.)
   * **summary** (*string*) –  Brief description of the incident that is suitable as a title or message subject (example: Brute force attempt from 1.2.3.4)
   * **threatRating** (string)  Incident threat level after analysis (example: Medium)
* **incident_attack_class** (*string*) – Attack classification type (Cloud Defender) (examples: suspicious-activity, log-review, application-attack, brute-force)
* **incident_class** (*string*) – Attack classification type (examples: authentication:activity, firewall:activity, correl:activity)
* **incident_escalated** (*string*) –   Whether an Alert LogicSOC analyst escalated the incident
*Valid values: *`true`, `false`
* **incident_threat_rating** (*string*) –    Incident threat level after analysis
*Valid values:*`Critical`, `High`, `Medium`, `Low`, `Info`
* **incident_type** (*string*) – Incident threat type (examples: webapp_attack, log-review, config_change, bf, log_correlation, scan, activerules, web_tool, bf_aggressive, policy)
* **incidentId** (*string*) – Unique incident identifier. For Managed Detection and Response incidents, the value is the full uppercase UUID. For Cloud Defender incidents, the value is a hex 64-bit UUID. (Examples: 5F36660A-0015-0120-0002-104300000000 or ea1118de147187ba)
* **notes** (*array*) - List of notes added by Alert LogicSOC analysts
   * **OtherNotes** (*object*) - Note added by an Alert Logic analyst
      * **date** (*string*) - ISO date and time in UTC when the analyst added the note (example: 2020-08-10T11:22.27.799796+00:00)
      * **note** (*string*) - Text of the note added by the analyst (example: Normal Activity:\nThere was 1 AWS EC2 Run Instances event with 1 User Type AssumedRole, 1 userName null, 1 sourceIPAddress autoscaling.amazonaws.com, 1 errorCode null, 1 errorMessage null, 1 ARN arn:aws:sts::261161298046:assumed-role/AWSServiceRoleForAutoScaling/AutoScaling, and 1 eventVersion 1.05.\nThis activity occurred on August 13, 2020 between 6:33:00pm and 6:33:00pm EDT.\nCaptured by 1 Log Source US-West-2-OpsTrail.\n\nThere is no unusual activity.)
      * **who** (*string*) - Name and email address of the analyst who added the note (example: AnalystFirstName AnalystLastName <username@alertlogic.com>)
* **snooze_status** (*object*) - Information about an incident temporarily removed from the incident list with the snooze feature
   * **expiration** (*number*) - Epoch time with milliseconds when snooze is set to expire (1597737611.136183)
   * **expiration_str** (*string*) - ISO date and time in UTC when snooze expires (example: 2020-08-10T11:22:27.799796+00:00)
   * **notes** (*string*) - Notes added when the incident was snoozed (example: Check with Sally tomorrow)
   * **period_ms** (*number*) - Snooze time period in milliseconds (example: 60000)
   * **reactivates_at** (*string*) - Time when the incident reactivates and snooze ends (example: 2020-08-10T11:22:27.799796+00:00)
   * **reason_code** (*string*) - Snooze duration selected
   *Valid values: *`tomorrow`, `in couple of days`, `next week`, `in two weeks`
   * **snooze_by** (*string*) - Name and email address of the user who snoozed the incident (example: CustomerFirstName CustomerLastName username@xyz.com)
   * **snooze_by_uid** (*string*) - User ID of the user who snoozed the incident (example: CBAA2703-B7F6-43E6-8B17-F75A04A5423E)
   * **snoozed** (*Boolean*) - Whether the incident is snoozed
   *Valid values: *`true`, `false`
* **snooze_status_snoozed** (*Boolean*) - Whether the incident is snoozed, extracted from `snooze_status`
*Valid values: *`true`, `false`
* **sources** (*array*) -  List that contains one entry that indicates the telemetry source of the incident (examples: `logreview`, `IDS`, `LOG`, `CLOG`, `FW`)
* **stack_region** (*string*) - Internal value that refers to the Alert Logic region of the customer account in which the incident occurred
*Valid values:*`cd-us-production`, `cd-uk-production`
* **updateTime** (*number*) - Epoch time of the last update to the incident  (example: 1597348547)
* **updatetime_str** (*string*) - ISO date and time in UTC of the last update to the incident  (example: 2020-09-11T16:23:47.734796+00:00)
* **victim** (*object*) - Information about the target of the incident, if it can be determined
   * **ip** (*string*)  – IP address of the target for the incident (example: 203.0.113.1)
   * **port** (*number*) - Port number of the target for the incident (example: 40814)
   * **protocol** (*string*) - Network protocol of the target for the incident (example: TCP)
   * **value** (*string*) - User name, applies to attacks that target a user instead of an IP address (example: SomeTarget)
* **victim_lset** (*array*) - List of target IP addresses of the incident or targeted users, if they could be determined
   * **ip** (*string*)  – List of target IP addresses of the incident (example: 203.0.113.1)
   * **value** (*string*) - List of target user names, applies to attacks that target a user instead of an IP address (example: SomeTarget)
* **extra**
   * **incidentUrl** (*string*) - URL that links to the incident in the Alert Logic console
   * **class** (*string*) - Incident classification
   * **analyst_notes** (*list*)  - All the analyst notes for the incident
      * **date** (*string*)
      * **note** (*string*)
   * **status** (*string*) - Whether the customer closed the incident in the Alert Logic console
   * **tld** (*string*)  - Top-level Alert Logic domain of the customer based on the region in which the data resides
   *Valid values: *`uk`, `us`
   * **is_escalated** (*Boolean*)  - Escalation status. Customers can subscribe to receive notifications about escalated incidents.
   * **investigation_report** (*string*)  - Incident description  that may contain  HTML formatting elements
   * **recommendations** (*string*)  - Text of the recommendations from the incident investigation report, if any, that may contain  HTML formatting elements
   * **location_ip** (*array*)  - One or more IP addresses, if determined, of the attacker for an incident
   * **target_host** (*array*)   - One or more IP addresses, if determined, of the target affected by the incident

## Sample JSON

Alert Logic uses this JSON  object to test connectors with an Incident payload type.

JSON

| 1 | { |
| 2 | "accountId": 2, |
| 3 | "asset_deployment_type": "aws", |
| 4 | "asset_host_name": "10.1.2.3", |
| 5 | "asset_native_account_id": "2", |
| 6 | "assets": {}, |
| 7 | "attacker": { |
| 8 | "account": "2", |
| 9 | "instanceId": "i-0a159b2a553285ebb", |
| 10 | "ip": "10.10.10.12", |
| 11 | "port": 40814, |
| 12 | "region": "us-east-2" |
| 13 | }, |
| 14 | "attacker_country_code": "BR", |
| 15 | "attacker_country_name": "Brazil", |
| 16 | "attacker_lset": [ |
| 17 | { |
| 18 | "ip": "86.34.222.99" |
| 19 | }, |
| 20 | { |
| 21 | "value": "SomeAttacker" |
| 22 | } |
| 23 | ], |
| 24 | "closed_time": "2020-08-10T11:24:27.765796+00:00", |
| 25 | "correlation_id": "5F36660A-0015-0120-0002-104300000000", |
| 26 | "correlation_name": "Admin Failed Login Correlation", |
| 27 | "createTime": 1594153092.2202642, |
| 28 | "createtime_str": "2020-07-07T20:18:12.220264+00:00", |
| 29 | "customer": "XYZ Corporation", |
| 30 | "customer_feedback": { |
| 31 | "feedback": "The wiggle probe server 10.123.10.57 is making multiple failed login attempts to the James MSSQL servers at INC001DB03G, INC001DB06G,  inc001db04g and inc001db05g. This is expected activity in the James environment. \nINC0766607", |
| 32 | "feedback_datetime": "2020-08-14T09:57:35.535995+00:00", |
| 33 | "feedback_reason": "threat_not_valid", |
| 34 | "feedback_uid": "423A54CE-105F-4089-B713-10A303DE0938", |
| 35 | "feedback_user": "CustomerFirstName CustomerLastName username@xyz.com" |
| 36 | }, |
| 37 | "customer_status": { |
| 38 | "notes": null, |
| 39 | "reason_code": "threat_not_valid", |
| 40 | "status": "completed", |
| 41 | "status_change_time": "2020-08-14T09:58:03.137831+00:00" |
| 42 | }, |
| 43 | "customer_status_status": "open", |
| 44 | "defaultThreatRating": "medium", |
| 45 | "deployment,": "AWS Production Deployment", |
| 46 | "deployment_subnet": "subnet-a412345g", |
| 47 | "deployment_vpc": "vpc-12345678", |
| 48 | "detection_source": "Log Mgmt", |
| 49 | "first_closed_time": "2020-09-10T13:22:27.799796+00:00", |
| 50 | "geo_ip_map": { |
| 51 | "86.34.222.99": { |
| 52 | "city": "Palmares do Sul", |
| 53 | "continentcode": "SA", |
| 54 | "country": "BR", |
| 55 | "countryname": "Brazil", |
| 56 | "ip": "86.34.222.99", |
| 57 | "latitude": -30.3465, |
| 58 | "longitude": -50.5482, |
| 59 | "postcode": "95540", |
| 60 | "regioncode": "RS", |
| 61 | "regionname": "Rio Grande do Sul" |
| 62 | } |
| 63 | }, |
| 64 | "humanFriendlyId": "ww1k39", |
| 65 | "incident": { |
| 66 | "attackClassId": 19, |
| 67 | "attackClassId_str": "authentication:activity", |
| 68 | "description": "**Attack Detail**:  \n**Attacker:** 172.31.37.117, local_ip \n**Targets:** 122.99.34.111, 172.31.37.90, and 172.31.39.79 \n We have detected a recon attack targeting a number of common server vulnerabilities. This is a vulnerability scan however we are unable to determine the specific tool or company performing this attack.", |
| 69 | "escalated": true, |
| 70 | "recommendations": "A compromised host should be isolated from the network and cleaned. You will want to remove the back doors installed and check the system logs for other actions taken. Once a system is compromised, usually one of the first things done by an attacker is creating a secondary access channel. Assume that additional modifications have been made to the system beyond the initial breach.", |
| 71 | "summary": "Brute force attempt from 1.2.3.4", |
| 72 | "threatRating": "Medium" |
| 73 | }, |
| 74 | "incidentId": "5F04D7E3-000A-8420-0002-757900000000", |
| 75 | "incident_attack_class": "authentication:activity", |
| 76 | "incident_class": "authentication:activity", |
| 77 | "incident_escalated": "true", |
| 78 | "incident_threat_rating": "Medium", |
| 79 | "incident_type": null, |
| 80 | "notes": { |
| 81 | "otherNotes": [ |
| 82 | { |
| 83 | "date": "2020-08-13T07:22:23+00:00", |
| 84 | "note": "Normal Activity:\nThere was 1 AWS EC2 Run Instances event with 1 User Type AssumedRole, 1 userName null, 1 sourceIPAddress autoscaling.amazonaws.com, 1 errorCode null, 1 errorMessage null, 1 ARN arn:aws:sts::261161298046:assumed-role/AWSServiceRoleForAutoScaling/AutoScaling, and 1 eventVersion 1.05.\nThis activity occurred on August 13, 2020 between 6:33:00pm and 6:33:00pm EDT.\nCaptured by 1 Log Source US-West-2-OpsTrail.\n\nThere is no unusual activity.", |
| 85 | "who": "AnalystFirstName AnalystLastName <username@alertlogic.com>" |
| 86 | } |
| 87 | ] |
| 88 | }, |
| 89 | "path": "Authentication/UserLoginFailures", |
| 90 | "recommendations": "<p>A compromised host should be isolated from the network and cleaned. You will want to remove the back doors installed and check the system logs for other actions taken. Once a system is compromised, usually one of the first things done by an attacker is creating a secondary access channel. Assume that additional modifications have been made to the system beyond the initial breach.</p>", |
| 91 | "scope_type": "host_uuid", |
| 92 | "snooze_status": { |
| 93 | "expiration": 1597737611.136183, |
| 94 | "expiration_str": "2020-08-18T08:00:11.136183+00:00", |
| 95 | "notes": "Check with Sally tomorrow", |
| 96 | "period_ms": 67124867, |
| 97 | "reactivates_at": "2020-08-18 08:00:11.136183", |
| 98 | "reason_code": "tomorrow", |
| 99 | "snooze_by": "CustomerFirstName CustomerLastName <username@xyz.com>", |
| 100 | "snooze_by_uid": "CBAA2703-B7F6-43E6-8B17-F75A04A5423E", |
| 101 | "snoozed": true |
| 102 | }, |
| 103 | "snooze_status_snoozed": false, |
| 104 | "sources": [ |
| 105 | "LOG" |
| 106 | ], |
| 107 | "stack_region": "cd-us-production", |
| 108 | "updateTime": 1594153098, |
| 109 | "updatetime_str": "2020-07-07T20:18:18+00:00", |
| 110 | "victim": { |
| 111 | "value": "['username1', 'username2']" |
| 112 | }, |
| 113 | "victim_lset": [ |
| 114 | { |
| 115 | "value": "['username1', 'username2']" |
| 116 | } |
| 117 | ], |
| 118 | "extra": { |
| 119 | "incidentUrl": "https://console.alertlogic.com/fake/incident/url", |
| 120 | "class": "authentication:activity", |
| 121 | "analyst_notes": [{ |
| 122 | "date": "15th Mar 2020 10:21:00 GMT", |
| 123 | "note": "This looks suspicious" |
| 124 | }], |
| 125 | "status": "closed", |
| 126 | "tld": "us", |
| 127 | "is_escalated": false, |
| 128 | "investigation_report": "<p><strong>Attack Detail</strong>:<br><strong>Attacker:</strong> 172.31.37.117, local_ip <strong>Targets:</strong> 122.99.34.111, 172.31.37.90, and 172.31.39.79 We have detected a recon attack targeting a number of common server vulnerabilities. This is a vulnerability scan however we are unable to determine the specific tool or company performing this attack.</p>", |
| 129 | "recommendations": "<p>A compromised host should be isolated from the network and cleaned. You will want to remove the back doors installed and check the system logs for other actions taken. Once a system is compromised, usually one of the first things done by an attacker is creating a secondary access channel. Assume that additional modifications have been made to the system beyond the initial breach.</p>", |
| 130 | "location_ip": ["10.10.10.12"], |
| 131 | "target_host": ["10.1.2.3"] |
| 132 | } |
| 133 | } |

# Health Schema

You can refer to this health schema to configure the payload template for a third-party webhook connector.

## Schema

JSON

| 1 | { |
| 2 | "cid": "string", |
| 3 | "report_description": "string", |
| 4 | "exposure_impact": "string", |
| 5 | "remediation_id": "string" |
| 6 | "customer_account_name": "string", |
| 7 | "deployment_name": "string", |
| 8 | "target_asset_type": "string", |
| 9 | } |

JSON

| 1 | { |
| 2 | "alert_description": "string", |
| 3 | "alert_summary": "string" |
| 4 | "alert_type": "string" |
| 5 | "asset_key": "string" |
| 6 | "asset_name": "string" |
| 7 | "asset_type": "string", |
| 8 | "cid": "string", |
| 9 | "configuration_remediation_name": "string", |
| 10 | "create_date": number, |
| 11 | "customer_account_name": "string", |
| 12 | "deployment_name": "string", |
| 13 | "exposure_impact": "string, |
| 14 | "host_id": "string", |
| 15 | "remediation_id": "string" |
| 16 | "status_timestamp": number |
| 17 | } |

## Definitions

* **alert_description** (*string*) – A brief description of the health exposure (example: “The Alert Logic agent is offline.”)
* **alert_summary** (*string*) – A summary of the health exposure.
* **alert_type** (*string*) – The type of health exposure for the notification rule.
*Valid values: *`offline`, `not collecting`, `error`
* **asset_key** (*string*) – Target URL identifier for the collection asset (example: /aws/eu-east-1/host/i-0000000001)
* **asset_name** (*string*) – The name of the collection asset (example: Alert Logic Network IDS security appliance)
* **asset_type** (*string*) – The type of collection asset for the notification rule.
*Valid values: *`agent`, `appliance`, `collector`
* **cid**(*number*) – Alert Logic customer account identifier (example: 12345678)
* **report_description** (*string*)			- A brief description of the health exposure (example: “The Alert Logic agent is offline.”)
* **exposure_impact** (*string*) – Summary of the security impact caused by the health exposure.
* **resolution** (*string*) – The resolution actions for the remediation associated with the health exposure.
* **remediation_id** (*string*) - Backend identification for the remediation associated with the health exposure.
* **configuration_remediation_name** (*string*) - Name of the remediation associated with the health exposure notification.
* **create_date** (*number*) – Epoch time when the incident arrived in the Alert Logic server (example: 1597058547)

* **customer_account_name** (*string*) – Name of the Alert Logic customer account (example: Alert Logic Internal)
* **deployment_name** (*string*) - Name of the deployment that the affected collection asset is in.
* **target_asset_type** (*string*) – The type of collection asset for the notification rule.
*Valid values: *`agent`, `appliance`, `collector`
* **host_id** (*string*) – Alphanumeric identification code for the hosts impacted by the health exposure on the collection asset(s).
* **status_timestamp**  (*number*) – Epoch time when the incident arrived in the Alert Logic server (example: 1597058547)

## Sample JSON

Alert Logic uses this JSON  object to test connectors with a Health payload type.

JSON

| 1 | { |
| 2 | "cid": "12345678", |
| 3 | "report_description": "The Alert Logic appliance is offline or unable to reach Alert Logic.", |
| 4 | "exposure_impact": "The Alert Logic appliance associated has either stopped or is unable to check in with Alert Logic. Ensure that the host is running and is able to reach Alert Logic", |
| 5 | "remediation_id": "appliance_restart_appliance" |
| 6 | "customer_account_name": "Alert Logic Internal Test Account", |
| 7 | "deployment_name": "AWS Test Deployment", |
| 8 | "target_asset_type": "appliance", |
| 9 | } |

JSON

| 1 | { |
| 2 | "alert_description": "The Alert Logic appliance is offline or unable to reach Alert Logic.", |
| 3 | "alert_summary": "appliance is offline" |
| 4 | "alert_type": "offline" |
| 5 | "asset_key": "/aws/eu-east-1/host/i-0000000001" |
| 6 | "asset_name": "AlertLogic IDS Security Appliance" |
| 7 | "asset_type": "appliance", |
| 8 | "cid": "12345678", |
| 9 | "configuration_remediation_name": "Re-enable this appliance"", |
| 10 | "create_date": 1628002258505, |
| 11 | "customer_account_name": "Alert Logic Internal Test Account", |
| 12 | "deployment_name": "AWS Test Deployment", |
| 13 | "exposure_impact": "The Alert Logic appliance associated has either stopped or is unable to check in with Alert Logic. Ensure that the host is running and is able to reach Alert Logic", |
| 14 | "host_id": "011150B8-3371-E615-543F-10FEFB64DB22", |
| 15 | "remediation_id": "appliance_restart_appliance" |
| 16 | "status_timestamp": 1628002257523 |
| 17 | } |

First example schema have from 2/17/2022.

"alert_description": "The Alert Logic appliance is offline or unable to reach Alert Logic.",

"alert_summary": "appliance is offline",

"alert_type": "offline",

"asset_key": "/aws/eu-west-1/host/i-002621cb53326130c",

"asset_name": "AlertLogic IDS Security Appliance",

"asset_type": "host",

"cid": "134249236",

"configuration_remediation_name": "Re-enable this appliance",

"create_date": 1628002258505,

"customer_account_name": "Respond Only Account",

"deployment_name": "AWS E2E (DO NOT DELETE) ",

"exposure_impact": "The Alert Logic appliance associated has either stopped or is unable to check in with Alert Logic. Ensure that the host is running and is able to reach Alert Logic.",

"host_id": "063150B8-3371-E685-543F-10FEFB64DB17",

"remediation_id": "appliance_restart_appliance",

"status_timestamp": 1628002257523,

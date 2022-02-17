# Scheduled Report Notification Schema

You can refer to this scheduled report notification schema to configure the payload template for a third-party webhook connector.

## Schema

JSON

| 1 | { |
| 2 | "type": "string", |
| 3 | "status": "string", |
| 4 | "scheduled_time": number, |
| 5 | "schedule_id": "string", |
| 6 | "schedule": { |
| 7 | "daily": { |
| 8 | "hour": number, |
| 9 | "minute": number |
| 10 | } |
| 11 | }, |
| 12 | "run_once": boolean, |
| 13 | "published": boolean, |
| 14 | "publish_result": { |
| 15 | "timestamp": number, |
| 16 | "status": "string" |
| 17 | }, |
| 18 | "notify_behavior": "string", |
| 19 | "name": "string", |
| 20 | "modified": { |
| 21 | "by": string, |
| 22 | "at": number |
| 23 | }, |
| 24 | "id": string, |
| 25 | "delete_empty_result": boolean, |
| 26 | }, |
| 27 | "created": { |
| 28 | "by": "string", |
| 29 | "at": number |
| 30 | }, |
| 31 | "artifact_data": { |
| 32 | "result_id": "string", |
| 33 | "result_count": number, |
| 34 | "metadata": { |
| 35 | "scheduled_report_name": "string", |
| 36 | "schedule_id": "string", |
| 37 | "result_count": number, |
| 38 | "report_type": "string", |
| 39 | "report_id": "string", |
| 40 | "report_description": "string", |
| 41 | "customer_name": "string", |
| 42 | "cadence": "string", |
| 43 | "artifact_create_date": "string" |
| 44 | }, |
| 45 | "create_time": number, |
| 46 | "attachments": [ |
| 47 | { |
| 48 | "url": "string", |
| 49 | "name": "string" |
| 50 | } |
| 51 | ] |
| 52 | }, |
| 53 | "account_id": "string", |
| 54 | "extra": { |
| 55 | "tld": "string", |
| 56 | "ui_url": "string", |
| 57 | "download_url": "string" |
| 58 | } |
| 59 | } |

## Definitions

* **type** (*string*) – Schedule type
*Value for a report schedule:*`tableau`
* **status** (*string*) – Current state of the scheduled report execution
*Valid values:*`scheduled`, `running`, `completed`, `failed`, `canceled`, `deleted`
* **scheduled_time** (*number*) – Epoch time when the report is or was scheduled to run
* **schedule_id** (*string*) – Schedule identifier
* **schedule** (*object*) – Schedule frequency and time when report is scheduled to run
*Valid values:*`every_15_minutes`, `daily`, `weekly`, `monthly`
   * **daily**	(*object*)
      * **minute** (*number*) - Minute portion of time when report is scheduled to run
      * **hour** (*number*) - GMT hour when the report is scheduled to run in 24-hour clock format
   * **weekly**	(*object*)
      * **day** (*string*) - Day of the week when the report is scheduled to run
      *Valid values: *`sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`
      * **hour** (*number*) - GMT hour when the report is scheduled to run in 24-hour clock format
      * **minute** (*number*) - Minute portion of time when report is scheduled to run
   * **monthly**	(*object*)
      * **day** (*number*) - Day of the month (1-31) when the report is scheduled to run
      * **hour** (*number*) - GMT hour when the report is scheduled to run in 24-hour clock format
      * **minute** (*number*) - Minute portion of time when report is scheduled to run
* **run_once** (*Boolean*) - Whether the report was scheduled to be run only once. Schedule frequency is ignored if "true" is the value.
* **published** (*Boolean*)  - Whether a notification was sent
* **publish_result** (*object* or *string*)  - Result of sending the notification. A value of `null ` means that the user does not  request sending a notification; see **notify_behavior**.
   * **timestamp** (*number*)  - Epoch time stamp indicating when the notification was sent
   * **status** (*string*)  - Notification status
   *Valid values:*`ok` or an error
* **notify_behavior** (*string*)  - Choice of when to send notifications
*Valid values:*`always`, `never`, `ifnotempty`  -  send a notification only if execution returns  results that are not empty; see **result_count**
* **name** (*string*)  - Schedule name
* **modified** (*object*)
   * **by** (*string*)  - User ID that changed the schedule
   * **at** (*number*)   - Epoch time of the schedule change
* **id** (*string*)  - Scheduled report execution ID
* **delete_empty_result** (*Boolean*)  - Whether the notification and report are deleted automatically if results are empty
* **created** (*object*)
   * **by** (*string*)  - User ID that created the schedule
   * **at** (*number*)   - Epoch time of schedule creation
* **artifact_data** (*object*)   - Information about the scheduled report
   * **result_id** (*string*)   - Generated report identifier
   * **result_count**   (*number*) - Whether the execution result is empty
   *Valid values:*`0` (empty),`1` (if one or more)
   * **metadata** (*object*) - Information in the email notification sent to the customer when the scheduled report is generated
      * **scheduled_report_name** (*string*) - Name of the report schedule
      * **schedule_id** (*string*) - Schedule identifier
      * **result_count** (*number*) - Whether result of running the scheduled report is empty or not
      *Valid values:*`0` (empty), `1` (if one or more)
      * **report_type** (*string*) - Name of scheduled report as displayed in the Alert Logic console
      * **report_id** (*string*) - Report execution identifier
      * **report_description** (*string*) - Description of the report that appears in the Alert Logic console
      * **customer_name** (*string*) - Customer name of the Alert Logic account where the report was scheduled
      * **cadence** (*string*) - Schedule frequency and time when report is scheduled to run in human-readable format
      * **artifact_create_date** (*string*) - Date and time the scheduled report was generated in the format YYYY-MM-DD HH:MM GMT
   * **create_time** (*number*) -  Epoch time when the report was generated
   * **attachments** (*object*) - Information used internally to attach the scheduled report to the notification email
      * **url** (*string*) - URL to download the report
      * **name** (*string*) - Name of the report as specified in the schedule with the report generation date appended
* **account_id** (*string*) - Customer account identifier
* **extra** (*object*) - Additional information about the scheduled report notification
   * **tld** (*string*) - Top-level Alert Logic domain of the customer based on the region in which the data resides
   *Valid values: *`uk`, `us`
   * **ui_url** (*string*) - URL that links to the scheduled report in the Alert Logic console
   * **download_url** (*string*) - URL for downloading the scheduled report from the Alert Logic console

## Sample JSON

Alert Logic uses this JSON  object to test connectors with a Scheduled Report Notification payload type.

| 1 | { |
| 2 | "type": "tableau", |
| 3 | "status": "completed", |
| 4 | "scheduled_time": 1596488400, |
| 5 | "schedule_id": "8915CB92-A75C-1005-8001-0242AC110004", |
| 6 | "schedule": { |
| 7 | "daily": { |
| 8 | "hour": 21 |
| 9 | "minute": 0, |
| 10 | } |
| 11 | }, |
| 12 | "run_once": false, |
| 13 | "published": true, |
| 14 | "publish_result": { |
| 15 | "timestamp": 1596488406, |
| 16 | "status": "ok" |
| 17 | }, |
| 18 | "notify_behavior": "always", |
| 19 | "name": "XYZ Corporation Azure Multi-Tenant CIS Benchmark", |
| 20 | "modified": { |
| 21 | "by": "A3CBF982-2FED-4E4B-9168-9E28F22FEEF3", |
| 22 | "at": 1596488406 |
| 23 | }, |
| 24 | "id": "20200803-210000-8915CB92-A75C-1005-8001-0242AC110004", |
| 25 | "delete_empty_result": false, |
| 26 | }, |
| 27 | "created": { |
| 28 | "by": "A3CBF982-2FED-4E4B-9168-9E28F22FEEF3", |
| 29 | "at": 1596488400 |
| 30 | }, |
| 31 | "artifact_data": { |
| 32 | "result_id": "6C3A6383-ABFF-1005-8001-0242AC110016", |
| 33 | "result_count": 1, |
| 34 | "metadata": { |
| 35 | "scheduled_report_name": "XYZ Corporation Azure Multi-Tenant CIS Benchmark", |
| 36 | "schedule_id": "8915CB92-A75C-1005-8001-0242AC110004", |
| 37 | "result_count": 1, |
| 38 | "report_type": "CIS Microsoft Azure Foundations Benchmark", |
| 39 | "report_id": "20200803-210000-8915CB92-A75C-1005-8001-0242AC110004", |
| 40 | "report_description": "This report displays the status of your environment to the CIS Microsoft Azure Foundations Benchmark Level 1 and 2.", |
| 41 | "customer_name": "XYZ Corporation", |
| 42 | "cadence": "Daily, 21:00 GMT", |
| 43 | "artifact_create_date": "2020-08-03 21:00 GMT" |
| 44 | }, |
| 45 | "create_time": 1596488404, |
| 46 | "attachments": [ |
| 47 | { |
| 48 | "url": "https://api.cloudinsight.alertlogic.com/cargo/v2/12345678/execution_record/20200803-210000-8915CB92-A75C-1005-8001-0242AC110004/result", |
| 49 | "name": "XYZ Corporation Azure Multi-Tenant CIS Benchmark 2020-08-03 21:00 GMT.pdf" |
| 50 | } |
| 51 | ] |
| 52 | }, |
| 53 | "account_id": "12345678", |
| 54 | "extra": { |
| 55 | "tld": "us", |
| 56 | "ui_url": "https://console.alertlogic.com/fake/scheduled/report/url", |
| 57 | "download_url": "https://console.alertlogic.com/fake/scheduled/report/url" |
| 58 | } |
| 59 | } |

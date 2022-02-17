# Observation Schema

You can refer to this observation schema to configure the payload template for a third-party webhook connector.

Alert Logic generates an observation when it detects an occurrence of a log correlation rule. For more information, see [Correlations and Notifications](../notifications/log-correlation.md).

## Schema

JSON

| 1 | { |
| 2 | "fields": { |
| 3 | "authority": "string", |
| 4 | "class": "string", |
| 5 | "confidence": number, |
| 6 | "desc": "string, |
| 7 | "end_ts": number, |
| 8 | "ingest_id": "binary", |
| 9 | "ingest_ts": number, |
| 10 | "keys": { |
| 11 | "message": "string", |
| 12 | "time_recv": number |
| 13 | }, |
| 14 | "parents": [ |
| 15 | "string" |
| 16 | ], |
| 17 | "path": "string", |
| 18 | "properties": {}, |
| 19 | "recommendations": "string", |
| 20 | "severity": "string", |
| 21 | "start_ts": number, |
| 22 | "subclass": "string", |
| 23 | "summary": "string", |
| 24 | "tactic": "string", |
| 25 | "technique": "string", |
| 26 | "ts": number, |
| 27 | "visibility": "string" |
| 28 | }, |
| 29 | "id": { |
| 30 | "account": number, |
| 31 | "aid": number, |
| 32 | "msgid": "string" |
| 33 | }, |
| 34 | "extra": { |
| 35 | "customer_name": "string", |
| 36 | "observation_description": "string", |
| 37 | "correlation_rule_id": "string", |
| 38 | "correlation_rule_name": "string", |
| 39 | "observation_id": "string", |
| 40 | "deployment_name": "string", |
| 41 | "tld": "string" |
| 42 | } |
| 43 | } |

## Definitions

* **fields** (*object*)
   * **keys** (*object*)  - Set of token-type values that uniquely identify an instance of this observation type
      * **message** (*string*)  - Details about the observation instance
      * **time_recv** (*number*)  - Epoch time  when Alert Logic detected the observation instance
   * **ingest_ts** (*number*) - Epoch time stamp (GMT) indicating when Alert Logic processed the log message
   * **ingest_id** (*binary*) - Unique log message identifier
   * **end_ts**	(*number*) - Epoch time stamp when the last log message triggering this correlation observation occurred
   * **desc** (*string*) – Observation description
   * **confidence** (*number*) – True positive detection confidence expressed as a number between 0 and 100, representing a rounded whole number percentage. A value of 100 equals 100 percent true positive detection.
   * **class** (*string*) – Major classification of the observation, the value of which depends on the taxonomy selected for the observation
   * **authority** (*string*) – Alert Logic subsystem and component that generated the observation

> * **parents** (*array of strings*)  - References to data records that contributed to the generation of this observation  and can be used to navigate to the log search used for the log correlation rule
* **path** (*string*)  - Unique logical name and path of the observation in the Alert Logic console
* **properties** (*object*)  - Set of token-type values that capture additional information about the observation
* **recommendations** (*string*)   - Full text of the recommended actions for this observation or incident
* **severity** (*string*)  - Importance of this observation with respect to the risk to the customer's environment
*Valid values*: `critical`, `high`, `medium`, `low`, `info`
* **start_ts** (*number*)  - Epoch time stamp when the first log message triggering this correlation observation occurred
* **sub_technique** (*string*)   - Determined MITRE ATT&amp;CK sub-technique of the enclosing object based on its detection within the customer's environment
* **subclass** (*string*)   - Minor classification of the observation, the value of which depends on the taxonomy selected for the observation
* **summary** (*string*)   -  Summary of the observation
* **tactic**   (*string*) - Determined MITRE ATT&amp;CK tactic based on its detection within the customer's environment
* **technique** (*string*) - Determined MITRE ATT&amp;CK technique based on its detection within the customer's environment
* **ts** (*number*) - Epoch time stamp (GMT) indicating when the observation was generated
* **visibility** (*string*) - Defines who can see the observation in the system and is used for notification and incident generation

* **id** (*object*) - Information about the observation returned by the search service
   * **account** (*number*) - Customer account identifier
   * **aid** (*number*) - Internal audit ID
   * **msgid** (*string*) - Observation message identifier
* **extra** (*object*) - Additional information about the observation
   * **customer_name** (*string*) - Customer name of the Alert Logic account where the observation was generated
   * **observation_description** (*string*) - Observation description in HTML format
   * **correlation_rule_id** (*string*) - Unique identifier of the log correlation rule that generated the observation
   * **correlation_rule_name** (*string*) - Name of the log correlation rule that generated the observation
   * **observation_id** (*string*) - Identifier of the observation
   * **deployment_name** (*string*) - Name of the deployment in which the observation occurred
   * **tld** (*string*) - Top-level Alert Logic domain for the customer based on the region in which the data resides.
   *Valid values:* `uk`, `us`

## Sample JSON

Alert Logic uses this JSON  object to test connectors with an Observation payload type.

JSON

| 1 | { |
| 2 | "fields": { |
| 3 | "authority": "alertlogic/ae/trigger_eng/1.0", |
| 4 | "class": "correl:activity", |
| 5 | "confidence": null, |
| 6 | "desc": "# Test", |
| 7 | "end_ts": 1586062782, |
| 8 | "ingest_id": "XollvQAOASAAAplnAAAAAA==", |
| 9 | "ingest_ts": 1586062782, |
| 10 | "keys": { |
| 11 | "message": "{\"CreationTime\":\"2020-04-05T04:38:02\",\"Id\":\"fdd05f68-fa83-4386-a364-dd7378006cb8\",\"Operation\":\"UserLoginFailed\",\"OrganizationId\":\"bf8d32d3-1c13-4487-af02-80dba2236488\",\"RecordType\":15,\"ResultStatus\":\"Failed\",\"UserKey\":\"11110000AD6EA715@alazurealertlogic.onmicrosoft.com\",\"UserType\":0,\"Version\":1,\"Workload\":\"AzureActiveDirectory\",\"ClientIP\":\"52.2.16.16\",\"ObjectId\":\"797f4846-ba00-4fd7-ba43-dac1f8f63013\",\"UserId\":\"azure_valid@alazurealertlogic.onmicrosoft.com\",\"AzureActiveDirectoryEventType\":1,\"ExtendedProperties\":[{\"Name\":\"RequestType\",\"Value\":\"OAuth2:Token\"},{\"Name\":\"ResultStatusDetail\",\"Value\":\"UserError\"}],\"ModifiedProperties\":[],\"Actor\":[{\"ID\":\"76ea01ce-6f1c-4001-aba5-ba32dcd283dd\",\"Type\":0},{\"ID\":\"azure_valid@alazurealertlogic.onmicrosoft.com\",\"Type\":5},{\"ID\":\"11110000AD6EA715\",\"Type\":3}],\"ActorContextId\":\"bf8d32d3-1c13-4487-af02-80dba2236488\",\"ActorIpAddress\":\"52.2.16.16\",\"InterSystemsId\":\"469c2728-ffa1-41aa-aeca-02d0fd0b93c0\",\"IntraSystemId\":\"af113cf1-8ce1-46c7-9cde-91fb0b471901\",\"SupportTicketId\":\"\",\"Target\":[{\"ID\":\"797f4846-ba00-4fd7-ba43-dac1f8f63013\",\"Type\":0}],\"TargetContextId\":\"bf8d32d3-1c13-4487-af02-80dba2236488\",\"ApplicationId\":\"04b07795-8ddb-461a-bbee-02f9e1bf7b47\",\"LogonError\":\"InvalidUserNameOrPassword\"}", |
| 12 | "time_recv": 1586061482 |
| 13 | }, |
| 14 | "parents": [ |
| 15 | "arn:iws:ingest:us-west-2:2:logmsgs/5E895FF3-0002-E920-0002-AA3500000000" |
| 16 | ], |
| 17 | "path": "correlation/12345678/22526B99-30B3-46EE-A270-8140052511FF", |
| 18 | "properties": {}, |
| 19 | "recommendations": null, |
| 20 | "severity": "critical", |
| 21 | "start_ts": 1586062782, |
| 22 | "subclass": "suspicious-activity", |
| 23 | "summary": "test", |
| 24 | "tactic": null, |
| 25 | "technique": null, |
| 26 | "ts": 1586062782, |
| 27 | "visibility": "notification" |
| 28 | }, |
| 29 | "id": { |
| 30 | "account": 12345678, |
| 31 | "aid": 0, |
| 32 | "msgid": "QU1JNAAAAAIAAAAAXollvV6JZb4AAplnAA4AImFwcGxpY2F0aW9uL3gtYWxwYWNrZXQtb2JzZXJ2YXRpb24ACmZha2VTdHJlYW0=" |
| 33 | }, |
| 34 | "extra": { |
| 35 | "customer_name": "XYZ Corporation", |
| 36 | "observation_description": "<h1>Test</h1>", |
| 37 | "correlation_rule_id": "22526B99-30B3-46EE-A270-8140052511FF", |
| 38 | "correlation_rule_name": "Failed Login Correlation", |
| 39 | "observation_id": "25257372-AC77-47CE-A00B-2F0BD35AA3D8", |
| 40 | "deployment_name": "Azure Production Deployment", |
| 41 | "tld": "us" |
| 42 | } |
| 43 | } |

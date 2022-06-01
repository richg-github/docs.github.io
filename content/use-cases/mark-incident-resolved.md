# Mark an Incident as Resolved

<p>To ensure that your infrastructure remains secure, <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> provides you with alerts and reports whenever a security incident takes place. To organize these alerts, you may wish to submit a response, taking notes on lessons learned and creating follow up tasks for your operations teams to reduce the risk of similar incidents in the future. This guide provides details on how to implement such a process using the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />.</p>

<MadCap:snippetBlock src="../Resources/Snippets/sub-types-pro.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:snippetBlock src="../Resources/Snippets/req-cli-installed.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />## Technical Details

Incidents are created and managed via the IRIS web service.

## List Incidents by Time

<p>The incidents_by_time command in the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> can be used to retrieve a list of incidents for a given <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account. It takes the following parameters:</p>

<table style="width: 100%;">
  <col />
  <col />
  <col />
  <tbody>
    <tr>
      <th>Parameter</th>
      <th>Type</th>
      <th>Definition</th>
    </tr>
    <tr>
      <td>
        <kbd>account_id</kbd>
      </td>
      <td>string</td>
      <td>
        <p>  the UUID of the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account to retrieve incidents from</p>
      </td>
    </tr>
    <tr>
      <td>
        <kbd>start_time </kbd>
      </td>
      <td>string</td>
      <td>the minimum time of retrieved incidents. Can be UNIX epoch timestamp or ISO8601 date</td>
    </tr>
    <tr>
      <td>
        <kbd>end_time </kbd>
      </td>
      <td>string</td>
      <td>the time of retrieved incidents. Can be UNIX epoch timestamp or ISO8601 date</td>
    </tr>
  </tbody>
</table>
The following example retrieves a list of incidents for account with UUID 123456789 from the past week (at time of writing):

```

$ alcli iris incidents_by_time --account_id 123456789 --start_time 1595241349 --end_time 1595244949
```

Response:

```

[
	{
		"account_id": "134235158",
		"aggregations": [],
		…
		"incidentId": "5F152BD4-0000-0020-0002-4C4000000000",
		"incident_attack_class": "authentication:activity",
		"incident_class": "authentication:activity",
		"incident_escalated": true,
		"incident_threat_rating": "Medium",
		"incident_type": null,
		"visibility": "incident",
	}
]
```

## Mark Incidents as Completed

After reviewing an incident and performing the recommended steps to mitigate future occurrences, you may close the incident by marking it as completed. This removes it from the list of open incidents that require your attention.

The complete_incident command can achieve this and requires the following parameters:

<table style="width: 100%;">
  <col />
  <col />
  <col />
  <tbody>
    <tr>
      <th>Parameter</th>
      <th>Type</th>
      <th>Definition</th>
    </tr>
    <tr>
      <td>
        <kbd>account_id</kbd>
      </td>
      <td>string</td>
      <td>
        <p>  the UUID of the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account to retrieve incidents from</p>
      </td>
    </tr>
    <tr>
      <td>
        <kbd>incident_id </kbd>
      </td>
      <td>string</td>
      <td>the UUID of the incident you wish to close</td>
    </tr>
    <tr>
      <td>
        <kbd>notes </kbd>
      </td>
      <td>string</td>
      <td>a description of the reasoning for closing the incident</td>
    </tr>
    <tr>
      <td>
        <kbd>reason_code </kbd>
      </td>
      <td>string</td>
      <td>Reason for marking the incident as completed. Valid values are <kbd>further_action</kbd>, <kbd>acceptable_risk</kbd>, <kbd>compensating_control</kbd>, <kbd>threat_not_valid</kbd>, <kbd>not_concluded </kbd>, and <kbd>other</kbd></td>
    </tr>
  </tbody>
</table>
The following example retrieves a list of incidents for account with UUID 123456789 from the past week:

```

$ alcli iris complete_incident --account_id 134235158 --incident_id 5F156451-0000-0020-0002-07DC00000000 --notes "User forgot their password and failed to login" --reason_code "threat_not_valid"
```

Response

```

{
	"new": {
		"notes": " User forgot their password and failed to login",
		"reason_code": "threat_not_valid",
		"status": "completed",
		"status_change_time": "2020-07-20T12:37:54.437261+00:00"
	},
	"old": {
		"status": "open",
		"status_change_time": "2020-07-20T09:31:31.441959+00:00"
		}
	}
}
```

# CLI Examples

<p>This section describes a few short example commands that will work with any <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account.</p>

## Determine your account ID

<p>Each <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Account (or customer) is identified by a numeric ID, which is a common parameter to many commands. To determine the account ID that your user is associated with, execute:</p>

```

alcli --query authentication.account.id aims authenticate
```

Sample output:

```

$ alcli --query authentication.account.id aims authenticate
"12345678"
```

## List your managed (child) accounts

If your account manages multiple other accounts, you can list information about them by executing:

alcli aims list_accounts_by_relationship --account_id accountID --relationship managed

For example:

```

alcli aims list_accounts_by_relationship --account_id 12345678 --relationship managed
```

Sample output:

```

$ alcli aims list_accounts_by_relationship --account_id 12345678 --relationship managed
{
"accounts": [
{
"accessible_locations": [
"defender-us-denver",
"esb-us-1",
"insight-us-virginia"
],
"active": true,
"created": {
"at": 1540933023,
"by": "702DDB3B-BEE0-4565-93D6-D525034C9DFD"
},
"default_esb_location": "esb-us-1",
"default_location": "defender-us-denver",
"id": "123456790",
"modified": {
"at": 1591118357,
"by": "1097041F-EC03-4EEC-8575-316F8988204C"
},
"name": "Child 1",
"version": 12
},
{
"accessible_locations": [
"insight-us-virginia"
],
"active": true,
"created": {
"at": 1522177283,
"by": "702DDB3B-BEE0-4565-93D6-D525034C9DFD"
},
"default_location": "insight-us-virginia",
"id": "134257145",
"modified": {
"at": 1522177283,
"by": "702DDB3B-BEE0-4565-93D6-D525034C9DFD"
},
"name": "Child 2",
"version": 1
}
]
}
```

## List the users in your account

To list information about the users in your account, execute:

alcli aims list_users --account_id accountID

For example:

```

alcli aims list_users --account_id 12345678
```

Sample output:

```

$ alcli aims list_users --account_id 12345678
{
"users": [
{
"account_id": "12345678",
"active": true,
"created": {
"at": 1583530408,
"by": "76C9AC72-97E7-4DEC-92F6-04F4CC2E7895"
},
"email": "user@example.com",
"id": "3F29E7F8-9BAD-4007-8E51-E8A3073C6B5A",
"locked": false,
"modified": {
"at": 1583862229,
"by": "76C9AC72-97E7-4DEC-92F6-04F4CC2E7895"
},
"name": "User 1",
"username": "user@example.com",
"version": 3
},
{
"account_id": "12345678",
"active": true,
"created": {
"at": 1583530408,
"by": "76C9AC72-97E7-4DEC-92F6-04F4CC2E7895"
},
"email": "user2@example.com",
"id": "72AC57F4-DBAE-4044-91F8-357DACEE2E7F",
"locked": false,
"modified": {
"at": 1583862229,
"by": "76C9AC72-97E7-4DEC-92F6-04F4CC2E7895"
},
"name": "User 2",
"username": "user2@example.com",
"version": 5
},
[…]
```

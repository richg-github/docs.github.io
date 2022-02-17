# Alert Logic Payloads

You can use the following annotated payload JSON to customize the payload templates for third-party webhook connectors.

* [Incident JSON payload](#IncidentJSONpayload)
* [Observation JSON payload](#ObservationJSONpayload)
* [Scheduled Report JSON payload](#ScheduledReportJSONpayload)
* [Scheduled FIM Search JSON payload](#ScheduledFIMSearchJSONpayload)

## Incident JSON payload

This  code is the incident JSON that Alert Logic generates. Configure your webhook payload template using the JSON output and descriptions below:

Old Incident JSON

| 1 | { |
| 2 | "accountId": 68530684, |
| 3 | "all_assets": [], |
| 4 | "apex": true, |
| 5 | "appliance_info": [], |
| 6 | "appliance_ip_set": [ |
| 7 | { |
| 8 | "appliance_id": "2EEBAFAF-88DF-1005-ADBA-005056B03F5C", |
| 9 | "match_host_uuid": false, |
| 10 | "private_ips": [ |
| 11 | "172.21.210.45", |
| 12 | "fe80::250:56ff:feb2:6732", |
| 13 | "fe80::250:56ff:feb2:73b3" |
| 14 | ], |
| 15 | "scope_agent_local_ipv4_net": [ |
| 16 | "172.21.210.0/24" |
| 17 | ], |
| 18 | "scope_agent_local_ipv6": [ |
| 19 | "fe80::250:56ff:feb2:6732", |
| 20 | "fe80::250:56ff:feb2:73b3" |
| 21 | ] |
| 22 | }, |
| 23 | { |
| 24 | "appliance_id": "3023EF1F-7C60-1005-B722-005056B03F5C", |
| 25 | "match_host_uuid": false, |
| 26 | "private_ips": [ |
| 27 | "172.21.210.50", |
| 28 | "172.21.215.50", |
| 29 | "fe80::250:56ff:feb2:d6a3", |
| 30 | "fe80::250:56ff:feb2:fbd6" |
| 31 | ], |
| 32 | "scope_agent_local_ipv4_net": [ |
| 33 | "172.21.0.0/16", |
| 34 | "172.21.215.0/24" |
| 35 | ], |
| 36 | "scope_agent_local_ipv6": [ |
| 37 | "fe80::250:56ff:feb2:d6a3", |
| 38 | "fe80::250:56ff:feb2:fbd6" |
| 39 | ] |
| 40 | }, |
| 41 | { |
| 42 | "appliance_id": "17901CBC-7A3D-1005-B722-005056B03F5C", |
| 43 | "match_host_uuid": false, |
| 44 | "private_ips": [ |
| 45 | "192.168.100.60", |
| 46 | "fe80::250:56ff:feb2:b687" |
| 47 | ], |
| 48 | "scope_agent_local_ipv4_net": [ |
| 49 | "192.168.100.0/24" |
| 50 | ], |
| 51 | "scope_agent_local_ipv6": [ |
| 52 | "fe80::250:56ff:feb2:b687" |
| 53 | ] |
| 54 | } |
| 55 | ], |
| 56 | "appliances": [], |
| 57 | "assets": { |
| 58 | "al__deployment": "Manual deployment" |
| 59 | }, |
| 60 | "associatedEventCount": 0, |
| 61 | "associatedEventSignatures": [], |
| 62 | "associatedLogCount": 0, |
| 63 | "category": [ |
| 64 | "log-review" |
| 65 | ], |
| 66 | "createTime": 1590740818.399811, |
| 67 | "createtime_str": "2020-05-29T08:26:58.399811+00:00", |
| 68 | "customer": "Elips Life AG", |
| 69 | "customer_status": { |
| 70 | "status": "open", |
| 71 | "status_change_time": "2020-05-29T08:26:58.370932+00:00" |
| 72 | }, |
| 73 | "customer_status_status": "open", |
| 74 | "dedup_hint": "cid68530684case3068dcnewport", |
| 75 | "defaultThreatRating": "info", |
| 76 | "detection_source": "Log Review", |
| 77 | "entitled_products": [ |
| 78 | "beta_navigation", |
| 79 | "detect", |
| 80 | "endpoints_enabled", |
| 81 | "exposures_enabled", |
| 82 | "herald_v2", |
| 83 | "phoenix_migrated" |
| 84 | ], |
| 85 | "events_from_fusionvm": 0, |
| 86 | "findingCount": 0, |
| 87 | "flaggedEventCount": 1, |
| 88 | "guardduty_sec_group": [], |
| 89 | "has_assets": false, |
| 90 | "humanFriendlyId": "qumsro", |
| 91 | "incident": { |
| 92 | "attackClass": "log-review", |
| 93 | "attackClassId": 17, |
| 94 | "attackClassId_str": "log-review", |
| 95 | "begin_time": 1590740818, |
| 96 | "begin_time_str": "2020-05-29T08:26:58+00:00", |
| 97 | "case_id": 3068, |
| 98 | "description": "Alert Logic detected suspicious activity in logs from 05-28-2020 for the customer Elips Life AG. This activity was escalated for further review and remediation.\n", |
| 99 | "end_time": 1590740818, |
| 100 | "end_time_str": "2020-05-29T08:26:58+00:00", |
| 101 | "escalated": "true", |
| 102 | "escalatedBy": "Nicolaus Abbott-Davies <nicolaus.davies@alertlogic.com>", |
| 103 | "escalationTime": "2020-05-29T08:27:33.710833+00:00", |
| 104 | "evolution": { |
| 105 | "tree": { |
| 106 | "escalated": true, |
| 107 | "escalatedBy": null, |
| 108 | "evolved_from": [], |
| 109 | "incidentId": "ea1186a134f29b29", |
| 110 | "summary": "Log Review Windows Account Changes", |
| 111 | "threatRating": "Info" |
| 112 | } |
| 113 | }, |
| 114 | "soc_review": "None Needed", |
| 115 | "subType": "case", |
| 116 | "summary": "Log Review Windows Account Changes", |
| 117 | "threatRating": "Info", |
| 118 | "type": "log-review" |
| 119 | }, |
| 120 | "incidentId": "ea1186a134f29b29", |
| 121 | "incident_attack_class": "log-review", |
| 122 | "incident_escalated": "true", |
| 123 | "incident_soc_review": "None Needed", |
| 124 | "incident_sub_type": "case", |
| 125 | "incident_threat_rating": "Info", |
| 126 | "incident_type": "log-review", |
| 127 | "iris_incident_version": 2, |
| 128 | "iris_notifications": true, |
| 129 | "logical_sort": {}, |
| 130 | "notes": { |
| 131 | "otherNotes": [ |
| 132 | { |
| 133 | "date": "2020-05-29T08:26:54+00:00", |
| 134 | "note": "Normal Activity:\nThere were 107 Windows User Account Created events with 5 Caller Security IDs NT AUTHORITY\\SYSTEM, NT-AUTORITÄT\\SYSTEM, ELIPS\\PZH2VGSMEXC003$, ELIPS\\axcom, and ELIPS\\axvia, 1 Caller Domain ELIPS, 106 User Security IDs NT-AUTORITÄT\\SYSTEM , S-1-5-21-3491657726-477697566-1788752327-9505, NT AUTHORITY\\SYSTEM , S-1-5-21-3837148881-2502805429-2409722269-9754, NT AUTHORITY\\SYSTEM , S-1-5-21-4075259480-3462529160-292815839-9386, NT AUTHORITY\\SYSTEM , S-1-5-21-4075259480-3462529160-292815839-9387, and NT AUTHORITY\\SYSTEM , S-1-5-21-3837148881-2502805429-2409722269-9746, 1 User Logged In Unknown, 5 SAM Users elipsadmin, epmadminpro, epmadminpro1, epm_adminpro, and scz, 1 Group ID 513, 1 User Account Control Account Disabled      'Password Not Required' - Enabled      'Normal Account' - Enabled, 1 Password Set <never>, 1 Password Expires in Days <never>, and 10 Host Names vdccgn0001.elips.local , <value not set>, vdczh20001.elips.local , <value not set>, VDCORD0002.elips.local , <value not set>, vdcdub0001.elips.local , <value not set>, and VDCZRH0012.elips.local , <value not set>.\nThis activity occurred on May 28, 2020 between 12:09:00am and 11:48:00pm BST.\nCaptured by 10 Log Sources vdccgn0001, vdczh20001, vdcord0002, vdcdub001, and vdczrh0012.\n\nThere were 105 Windows User Account Deleted events with 4 Caller Security IDs NT AUTHORITY\\SYSTEM, NT-AUTORITÄT\\SYSTEM, ELIPS\\axvia, and ELIPS\\PZH2VGSMEXC003$, 1 Caller Domain ELIPS, 105 User Security IDs NT-AUTORITÄT\\SYSTEM , S-1-5-21-3491657726-477697566-1788752327-9505, NT AUTHORITY\\SYSTEM , S-1-5-21-3837148881-2502805429-2409722269-9753, NT AUTHORITY\\SYSTEM , S-1-5-21-4075259480-3462529160-292815839-9385, NT AUTHORITY\\SYSTEM , S-1-5-21-4075259480-3462529160-292815839-9386, and NT AUTHORITY\\SYSTEM , S-1-5-21-4075259480-3462529160-292815839-9387, 8 Target Domains VDCCGN0001, VDCZH20001, VDCORD0002, VDCDUB0001, and VDCZRH0012, 3 Target Users elipsadmin, epmadminpro, and epm_adminpro, 1 User Logged In Unknown, and 9 Host Names vdccgn0001.elips.local, vdczh20001.elips.local, VDCORD0002.elips.local, vdcdub0001.elips.local, and VDCZRH0012.elips.local.\nThis activity occurred on May 28, 2020 between 12:09:00am and 11:48:00pm BST.\nCaptured by 9 Log Sources vdccgn0001, vdczh20001, vdcord0002, vdcdub001, and vdczrh0012.\n\nThere were 71 Windows User Account Changed events with 5 Caller Security IDs ELIPS\\axvia, ELIPS\\PZH2VGSMEXC003$, NT AUTHORITY\\ANONYMOUS LOGON, ELIPS\\axcom, and NT AUTHORITY\\SYSTEM, 2 Caller Domains ELIPS, and NT AUTHORITY, 15 User Security IDs ELIPS\\axcom , ELIPS\\scz, ELIPS\\PZH2VGSMEXC003$ , ELIPS\\epmadminpro1, ELIPS\\PZH2VGSMEXC003$ , ELIPS\\epm_adminpro, ELIPS\\axvia , ELIPS\\epmadminpro1, and ELIPS\\axvia , ELIPS\\epmadminpro, 1 User Logged In Unknown, 4 SAM Users -, elipsadmin, and epmadminpro, 3 Group IDs -, and 513, 6 User Account Controls -, 'Password Not Required' - Disabled      'Don't Expire Password' - Enabled, Account Enabled, 'Password Not Required' - Disabled, and Account Disabled, 16 Password Sets -, 11/15/2018 10:43:59 PM, 28.05.2020 09:22:55, 28.05.2020 09:29:03, and 28.05.2020 12:11:40, 3 Password Expires in Dayss -, and <never>, and 7 Host Names izrhvgsmdom001.elips.local , -, pzh2vgsmdom002.elips.local , -, izh2vgsmdom001.elips.local , -, pzh2vgsmdom001.elips.local , -, and VDCZRH0034.elips.local , <value not set>.\nThis activity occurred on May 28, 2020 between 12:32:00am and 11:24:00pm BST.\nCaptured by 6 Log Sources izrhvgsmdom001, pzh2vgsmdom002, izh2vgsmdom001, pzh2vgsmdom001, and vdczrh0034.\n\nThere were 26 Active Directory Computer Account Changed events with 2 Caller Security IDs NT AUTHORITY\\ANONYMOUS LOGON, and ELIPS\\sxESXAutomation, 2 Caller Domains ELIPS, and ELIPSEXT, 19 User Security IDs ELIPS\\sxESXAutomation , ELIPS\\pzhxvmsmaut003$, NT AUTHORITY\\ANONYMOUS LOGON , ELIPS\\pzh2vgsmctx206$, NT AUTHORITY\\ANONYMOUS LOGON , ELIPS\\LAPORD0038$, NT AUTHORITY\\ANONYMOUS LOGON , ELIPS\\LAPZRH0228$, and NT AUTHORITY\\ANONYMOUS LOGON , ELIPS\\LAPZRH0285$, 2 Target Domains NT AUTHORITY, and ELIPS, 1 User Logged In Unknown, 1 SAM User -, 1 Group ID -, 2 User Account Controls -, and Account Enabled, 23 Password Sets 28.05.2020 13:42:38, 28.05.2020 02:32:56, 28.05.2020 10:09:55, 28.05.2020 07:50:58, and 28.05.2020 07:54:10, 1 Password Expires in Days -, and 6 Host Names pzh2vgsmdom002.elips.local , -, izrhvgsmdom001.elips.local , -, izh2vgsmdom001.elips.local , -, pzh2vgsmiam002.elips.external , -, and pzh2vgsmdom001.elips.local , -.\nThis activity occurred on May 28, 2020 between 12:52:00am and 11:55:00pm BST.\nCaptured by 6 Log Sources pzh2vgsmdom002, izrhvgsmdom001, izh2vgsmdom001, pzh2vgsmiam002, and pzh2vgsmdom001.\n\nThere were 9 Windows User Account Enabled events with 3 Caller Security IDs ELIPS\\axvia, ELIPS\\sxESXAutomation, and ELIPS\\axcom, 1 Caller Domain ELIPS, 5 User Security IDs ELIPS\\sxESXAutomation , ELIPS\\pzhxvmsmaut003$, ELIPS\\axcom , ELIPS\\scz, ELIPS\\axvia , ELIPS\\epmadminpro1, ELIPS\\axvia , ELIPS\\epmadminpro, and ELIPS\\axvia , ELIPS\\epm_adminpro, 1 Target Domain ELIPS, 5 Target Users pzhxvmsmaut003$, scz, epmadminpro1, epmadminpro, and epm_adminpro, 1 User Logged In Unknown, and 3 Host Names izrhvgsmdom001.elips.local, pzh2vgsmdom002.elips.local, and izh2vgsmdom001.elips.local.\nThis activity occurred on May 28, 2020 between 8:22:00am and 11:55:00pm BST.\nCaptured by 3 Log Sources izrhvgsmdom001, pzh2vgsmdom002, and izh2vgsmdom001.\n\nThere was 1 Windows User Account Disabled events with 1 Caller Security ID ELIPS\\axvia, 1 Caller Domain ELIPS, 1 User Security ID ELIPS\\axvia , ELIPS\\epm_adminpro, 1 Target Domain ELIPS, 1 Target User epm_adminpro, 1 User Logged In Unknown, and 1 Host Name izrhvgsmdom001.elips.local.\nThis activity occurred on May 28, 2020 between 12:17:00pm and 12:17:00pm BST.\nCaptured by 1 Log Source izrhvgsmdom001.\n\nEscalated Activity:\nEscalation 1: There were 4 Active Directory Computer Account Deleted events with 1 Caller Security ID ELIPS\\sxESXAutomation, 1 Caller Domain ELIPS, 1 User Security ID ELIPS\\sxESXAutomation , ELIPS\\pzhxvmsmaut003$, 1 Target Domain ELIPS, 1 User Logged In Unknown, and 1 Host Name pzh2vgsmdom002.elips.local.\nThis activity occurred on May 28, 2020 between 11:24:00pm and 11:55:00pm BST.\nCaptured by 1 Log Source pzh2vgsmdom002.\n\nEscalation 2: There were 4 Active Directory Computer Account Created events with 1 Caller Security ID ELIPS\\sxESXAutomation, 1 Caller Domain ELIPS, 1 User Security ID ELIPS\\sxESXAutomation , ELIPS\\pzhxvmsmaut003$, 1 Target Domain ELIPS, 1 User Logged In Unknown, 1 SAM User pzhxvmsmaut003$, 1 Group ID 515, 1 User Account Control Account Disabled      'Workstation Trust Account' - Enabled, 1 Password Set <never>, 1 Password Expires in Days <never>, and 1 Host Name pzh2vgsmdom002.elips.local , -.\nThis activity occurred on May 28, 2020 between 11:24:00pm and 11:55:00pm BST.\nCaptured by 1 Log Source pzh2vgsmdom002.", |
| 135 | "who": "Nicolaus Abbott-Davies <nicolaus.davies@alertlogic.com>" |
| 136 | }, |
| 137 | { |
| 138 | "date": "2020-05-29T08:26:56+00:00", |
| 139 | "note": "Analyst note:\nEscalating this activity as per your preference to be notified of any account creations or deletions that to do not follow your administrative naming scheme.\n\nPlease be aware we are not alerted to notes you place in the Cloud Defender User Interface. If you have any queries regarding this escalation, please create a ticket for the Log Review team using logreview@alertlogic.com or call 713.484.8383 for Log Review to speak with an analyst. If you are a UK customer, please call +44 (0) 203 011 5533, to speak with an analyst.\n\nThis activity is being escalated.", |
| 140 | "who": "Nicolaus Abbott-Davies <nicolaus.davies@alertlogic.com>" |
| 141 | } |
| 142 | ] |
| 143 | }, |
| 144 | "snooze_status": { |
| 145 | "period_ms": 0, |
| 146 | "reason_code": "immediately", |
| 147 | "snoozed": false |
| 148 | }, |
| 149 | "snooze_status_snoozed": false, |
| 150 | "source_keyword": "logreview", |
| 151 | "sources": [ |
| 152 | "logreview" |
| 153 | ], |
| 154 | "updateTime": 1590740856, |
| 155 | "updatetime_str": "2020-05-29T08:27:36+00:00" |
| 156 | } |
| 157 |  |

Line numbers in the table below correspond to line items in the JSON code.

| Line | Element | Description | Data Type | Required? | Comments |
|---|---|---|---|---|---|
| 2 | accountId | Alert Logic customer account identifier | Number | Required | [Comments if any, date formats for example Assume the example will be in the code, so not planning to add an example column] |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |

## Observation JSON payload

## Scheduled Report JSON payload

## Scheduled FIM Search JSON payload

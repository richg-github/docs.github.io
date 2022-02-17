# Investigate an Extended Endpoint Protection Event

Alert Logic Extended Endpoint Protection enables you to easily triage, investigate, and take action on event alerts.Alert Logic groups similar events based on common path or common hash, to avoid individually triaging events.

### Event blocking and detection

Extended Endpoint Protection constantly monitors your endpoints for suspicious activity, and blocks suspicious processes when it identifies them. This identified suspicious activity is called an event. When an event is blocked, Extended Endpoint Protection automatically stops the process. All events are automatically blocked when Extended Endpoint Protection is on. If protection is turned off for an endpoint, the event appears as a detection. When an event is detected, Extended Endpoint Protection generates an alert, but does not stop the process. Any event that is detected with protection off appears in red in the event list.

### Event groups and patterns

Event grouping allows you to view the history of a particular event within your organization. If you are triaging a new event that is part of a group, you can see how many times Extended Endpoint Protection previously detected that event within your organization, when those prior detections occurred, and on which devices. Here are a few common patterns and what they can mean:

* Multiple new events in a short time frame on a single device can indicate that the device owner has made multiple attempts to execute the offending program.
* Multiple new events in a short time frame across multiple devices can indicate a targeted attack, such as a phishing campaign that has been sent to multiple users in your organization.
* A single new event that matches previously seen events can indicate a new outbreak of malware that has been seen before in your organization.

## Events page

The Events page lists groups of events, with the number of events in the group indicated in parentheses. New events appear in bold text, and events that have been opened are not bolded.

On the left side of the page, you can choose to view events by type:

* All events
* Unread events only
* Read events only
* Events over 30 days old
* Events over 60 minutes old
* Events created within the last 60 minutes
* Quarantined events
* Overridden events (default selection)

From the Events list, you can mark an event as unread or [add an override](../../configure/extended-endpoint-protection/apply-override.md). Click the check box next to the event listing, and then select **MARK UNREAD** or **ADD OVERRIDE** at the top of the page.

Click on the event listing to go to the Event Detail page for the event group.

## Event Details

Extended Endpoint Protection provides detailed data on each event to aid in your investigation. Click an event listing to see the event details.

The Event Detail page shows information about the event(s).

Click the links at the top to [override the event](../../configure/extended-endpoint-protection/apply-override.md), add the files to quarantine, isolate the endpoint, or view audit logs.

The summary box at the top of the page shows basic information about the events and why they were grouped together.

**Grouped Events** lists all the events in the group. Click an item to see more details about it.

For each event, the console lists:

* **Process Name**
* **Endpoint**
* **User**: the user logged into the device at the time of the event, or the most recent logged-in user before the event
* **Date and Time**: date and time of the event in the time zone of the administrator
* **Process Path**: the location of the process on the device
* **Hash**: Alert Logic provides the SHA1 and MD5 hashes for the event, along with a link to look up the SHA1 hash in VirusTotal for more information.
* Process information
* Process ancestry
* Network interface
* IP address
* MAC Address

Reported User Feedback

This field will only appear when you have enabled the event feedback questionnaire and the device user has submitted a response. The questionnaire prompts the user to input information on what they were doing at the time of the attack. You can use this response to identify the root cause of the event. For example, if the user reports that they opened an email attachment at the time of the event, it is likely that they fell victim to a phishing scam.

Event Path Visualization

The Event Path Visualization graphically displays running processes on the system at the time of the event, and traces the path of the potentially malicious process back to its origins. You can use this information to formulate a hypothesis to the root cause of the event. For example, if the visualization shows a Microsoft Office document with the parent process outlook.exe, it is possible that the event stemmed from a phishing attack.

You can also use the Event Path Visualization to explore other processes running at the time of the attack and identify anything that looks suspicious. The visualization is automatically centered on the malicious event path, but you can drag the image and use the zoom function to browse the full process tree.

# About IDS Signatures in the Threat Intelligence Center

The Threat Intelligence Center provides a tabular list for the properties of each IDS signature available from Alert Logic.  Use the IDS signatures view in the Threat Intelligence Center to learn about IDS signature content. To learn more about the Threat Intelligence Center, see [Threat Intelligence Center (Beta)](../threat-intelligence-center.md).

## Learn about IDS signatures

Network traffic is the machine-to-machine  activity to and from your environment, and it is monitored by the Network IDS appliance. Network activity, unlike activity logs, is governed by internet standards, including TCP/IP, HTTP, HTTPS, DNS, and many others. Therefore, suspicious activity can be identified by looking for patterns in the traffic, commonly known as "signature" network patterns. IDS signatures recognize a specific type of activity to generate events. Analytics can evaluate these events to generate incidents and observations.

To learn how to install and configure a physical Network IDS, see [Install and Configure the  Physical Appliance](../../prepare/alert-logic-physical-appliance.md).

To learn how to install and configure a virtual Network IDS, see [Install and Configure the  Virtual Appliance](../../prepare/virtual-appliance.md).

## Validate IDS Signature Event coverage

The Threat Intelligence Center provides details for content covered by Alert Logic, not content that is necessarily covered in your environment. Use the  content table  to validate that specific IDS events are covered by Alert Logic. For more information about how to control filters and viewing specific threats, see [About IDS Signatures in the Threat Intelligence Center](#Threat).

## IDS signature properties details and use cases

Using the Threat Intelligence Center, you can review the properties of each IDS signature.

| Property | Description  | Use Cases | Examples |
|---|---|---|---|
| Signature ID | Unique identification code for the signature. | Verify the release date of a log parser cross-reference with your security posture history. | 1103000 |
| Description | Description of the network activity that the IDS signature detects to create an event. | Determine the type of activity being detected. | AL TELEM - DNS AXFR Zone Transfer Request |
| Signature Source | Name of the vendor for the signature being used to detect activity. | Verify the threat intelligence sourcing for activity signatures. | Alert Logic Emerging Threat |
| Date Added | Date that Alert Logic released the signature. | Verify the release date of a signature or cross-reference with your security posture history. | 3rd May 2017 20:07:32 GMT-5 |
| Last Updated | Date that Alert Logic last updated the signature . | Verify that Alert Logic signatures are kept up to date or cross-reference updates with your security posture history. | 3rd Jun 2021 20:07:32 GMT-5 |
| Revision | Version of the IDS signature. | Verify the version of a signature or cross-reference versions with your security posture history. | 1.x 2.x |
| Threshold | Network IDS threshold for seeing the pattern before triggering an event. | Determine and tune the signature rule for firing an event notification to analytics. | Alert once every 300 seconds after 1 occurrence(s), tracked by destination |
| CVE | Common Vulnerabilities and Exposures ID. | Validate which CVEs  an IDS signature covers. | CVE-1999-0532 |
| CWE | The Common Weakness Enumeration ID. | Validate which CWEs are being covered by an IDS signature. | cve,1999-0532 |

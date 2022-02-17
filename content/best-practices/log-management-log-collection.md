# Log Management—Which Logs to Collect

To meet regulatory compliance standards, all logs must be collected—not just the security logs. For example, operating system logs and application logs often contain security-related information and information about events that may not initially appear security related. Organizations must consider the potential value of each possible log source. Consider the following log types for collection:

* Anti-malware software logs include indicators that malware was detected, disinfection attempt results, file quarantines, when file-system scans were last performed, when anti-virus signature files were last updated, and when software upgrades have taken place.
* Authentication server logs store every authentication attempt and include:
   * Originating user ID
   * Destination system or application
   * Date and time information
   * Success and failure details
* Firewall logs are detailed and informative, because firewalls not only block activity based on policy, and they inspect content and ensure the state and integrity of permitted connections.
* Intrusion prevention systems record detailed information about suspicious behavior and detected attacks as well as actions taken to halt malicious activity in progress. Some intrusion protection systems, such as file integrity systems, run periodically instead of continuously, so they generate logs in batches rather than an ongoing basis.
* Network access control servers control access to the network from both internal and external hosts NACs determine the hosts’ security posture, and hosts failing to adhere to the defined policy are quarantined onto a separate VLAN (Virtual Local Area Network) segment. NAC servers log a great deal of useful information about both permitted and unsuccessful (quarantined) network connections.
* Network devices, like routers and switches, produce logs that contain informative network communication activity.
* Operating system logs can help identify suspicious activity involving a specific host, because these logs contain information about:
   * Service starts and stops
   * Authentication attempts
   * File accesses
   * Security policy changes
   * Account changes
   * Permission and privilege changes
   * Use of privileges
   * Information from security software and system applications.
* Remote access logs store 			successful and failed connection attempts. They record details such as the date and time each user connects			and disconnects, as well as the types and amount of data sent and received during the connected session.
* Vulnerability management software...Included here are both vulnerability scanning and patch management software. These typically run on an				occasional basis and log batches of log entries that include information about scanned hosts/devices including:				configuration, missing software updates, vulnerabilities identified, and patch/scan currency downloads, among			other things.
* Web proxy logs record user			activity and URLs accessed by specified users.

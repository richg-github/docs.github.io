# About Alert Logic Scans

A scan detects and identifies network and host vulnerabilities in your environment. Scans can perform external attack simulations as well as comprehensive vulnerability checks including registry evaluation. In Data Center deployments, discovery scans detect new assets or asset changes. Alert Logic scans can also help you meet PCI compliance requirements. To learn more about scans for PCI compliance requirements, see [Manage PCI Scans](../configure/pci-scans.md).

This topic describes the types of scans that are supported,  best practices for running successful scans, and how to configure and manage scan definitions and results.

## Scan types

The following table describes the types of supported scans:

| Scan Type | Description  |
|---|---|
| Internal | An *internal scan* runs from an Alert Logic appliance or agent in your environment. **Internal scan with no credentials or agent-based scan:** If you do not provide credentials or enable agent-based scanning, Alert Logic scans your network without logging on to each host and performs as many vulnerability as possible. **Internal scan with credentials and no agent-based scan:** When you define a scan, you can specify credentials to use with the internal scan. If you provide credentials, Alert Logic can log on to each host on your network and collect information about the host while it performs comprehensive vulnerability checks including registry setting evaluation. To learn how to provide credentials, see [Manage your credentials](../analyze/manage-scans-and-results/adjust-settings.md#Manageyourcredentials). **Internal scan with agent-based scan:** You can enable agent-based scanning by deployment. Agent-based scans and credentialed network scans provide similar  internal vulnerability assessment.  When the network scan begins an internal assessment of a host, it checks with that host for the presence of agent-based scan configuration. The network scan will not run redundant vulnerability assessments for the host. For more information, see [Agent-Based Scanning](../analyze/manage-scans-and-results/agent-based-scan.md). **Note:** Your appliance must be enabled for internal scanning. For more information, see "../userGuides/threat-manager-detection.htm#enableScans". |
| External | An *external scan* runs from the Alert Logic data centers against your environment. This type of scan simulates attacks from outside your network and identifies potential issues from these attack types. |
| Discovery | A *discovery scan* applies to Data Center deployments only. It scans for new assets or asset changes on your networks. |
| PCI | A *PCI scan* is a special type of external scan that is used specifically for Payment Card Industry (PCI) compliance requirements. |

## Vulnerability Scanning

| Scan Type | Vulnerability Assessment Type | Use Case | Description  |
|---|---|---|---|
| Unauthenticated Network Scan | Internal (Limited) External |  | An *internal scan* runs from an Alert Logic appliance in your environment. When you define a scan, you can specify credentials to use with the internal scan. If you provide credentials, Alert Logic can log on to each host on your network and collect information about the host while it performs comprehensive vulnerability checks including registry setting evaluation. If you do not provide credentials, Alert Logic scans your network without logging on to each host and performs as many checks as possible. To learn how to provide credentials, see [Manage your credentials](../analyze/manage-scans-and-results/adjust-settings.md#Manageyourcredentials). **Note:** Your appliance must be enabled for internal scanning. For more information, see "../userGuides/threat-manager-detection.htm#enableScans". |
| Authenticated Network Scan | Internal External |  | An *external scan* runs from the Alert Logic data centers against your environment. This type of scan simulates attacks from outside your network and identifies potential issues from these attack types. |
| Agent-Based Scan | Internal |  | A *discovery scan* applies to Data Center deployments only. It scans for new assets or asset changes on your networks. |

## Scanning best practices

Alert Logic creates default scan schedules when you create a deployment. You can edit the default schedules and create additional schedules for all or selected assets and ports as explained in [Manage Scan Schedules](../analyze/manage-scans-and-results/schedules.md). When configuring your scans, use the following guidelines to create successful scans and scan results.

### Specific considerations for scanning in Azure environments

While Azure does not require pre-approval for scanning, clients must comply with their terms and are encouraged to fill out and submit a penetration testing notification form.

The terms and notification form from Microsoft are located  [here](https://portal.msrc.microsoft.com/en-us/engage/pentest#pentestterms).

### Be smart when scheduling scans

Schedule your scans to be both effective and efficient.

* **Scan your servers, firewalls, and routers during off-peak times.** To effectively balance scanning resources across your enterprise, configure scanning of data center assets to occur during off-peak times.
* **Do not scan during service windows.** Service windows are the times when you do backups, hardware maintenance, or apply patches.  Valid scan results require that the server is powered on and not in the middle of a reboot. For best results, scan *after* you apply patches and not *while* applying patches.
* **Scan your workstations during working hours.** At night, laptops go home and workstations get powered off. Scan laptops and workstations when they are available on your network.
* **Scan new computers before use.** Scan new servers before you plug in to the Internet. Time to infection for an unpatched, unprotected server can be less than an hour.
* **Scan often.** Security is a moving target that you cannot hit in three-month scan intervals. Establish a reasonable schedule that scans as frequently as possible and can be adhered to. Alert Logic automatically creates default scan schedules.

### Make sure your scans have time to complete

An incomplete scan yields incomplete results. If your scans cannot finish, you may have undetected vulnerabilities. To get a comprehensive vulnerability assessment, it is imperative that all scans—no matter how lengthy—run to completion. You can affect your scanning throughput by either modifying scan schedules or by increasing scanning capability, as follows:

* **Run open-ended scans.** When scheduling your scan, consider leaving the scan end time blank.
* **Split up long scans.** Rather than a single, comprehensive scan, schedule multiple scans. Set several smaller scopes and spread the load across multiple appliances.
* **Run scans in parallel.** If you have multiple appliances, you can run scans in parallel. Running scans in parallel requires spreading scans across multiple appliances.
* **Adjust scan performance.** You can increase the number of IPs scanned simultaneously  to complete scans faster. For more information, see [Adjust scan performance](../analyze/manage-scans-and-results/adjust-settings.md#Adjustscanperformance).

If scans are taking an unusually long time to complete,  other local factors may be involved:

* Back-end database speed
* Network connection or infrastructure issues
* Number of simultaneous connections by the appliance
* Number of vulnerability checks
* Client computer/server performance and response time

### Know what to scan

Consider what to scan and how often to scan it. Your scanning strategy might require multiple scan definitions with different schedules and frequencies.

* **Scan frequency recommendations:** Alert Logic creates default scan schedules when you create a deployment. The default schedules reflect the recommended scan frequencies. For Data Center deployments, Alert Logic recommends scheduling discovery, internal, and external scans once a week. For AWS and Azure deployments, Alert Logic recommends  setting internal and external scans to run as often as necessary, which scans asset scope for vulnerabilities up to twice a day or when significant changes are detected.
* **Scan common ports often, and all ports less often.** Use the following recommendations:        As a general best practice, on external systems, disable all UDP ports at the host level, the firewall level, and the router level. Unless you have a specific reason, do not open UDP ports on your internet-facing systems.        
For a summary of port scan frequency recommendations for each port group, see [Port scan frequency recommendations](#Portscanfrequencyrecommendations).
   * Scan common TCP and UDP ports often, at least once a week. Almost all new vulnerabilities appear on common TCP and UDP ports.
   * Use [authenticated scanning](../prepare/authenticated-scanning.md) on common ports. This is the best way to lower scan times, reduce false positives, and detect the latest vulnerabilities.
   * Scan all TCP ports infrequently. Scanning all TCP ports  is time-consuming and has minimal benefit over scanning common TCP  ports.
* **Do not scan "all ports open" configurations commonly found on firewalls.**  To improve security posture, some users implement firewall or router configurations that are designed to slow scans. These configurations are designed specifically to slow down an attacker but will slow down your scans as well. Scanning targets with these types of configurations should not be done as part of regular scanning, but they should be scanned individually using an outside vendor tool to assess the effectiveness of the protection mechanism. If you decide to use this protection mechanism, ensure that Alert Logic appliances and external scanners are whitelisted  and not affected by the protection mechanism.
* **Configure personal firewalls to allow access by the appliance.** Where personal firewalls are used for desktops or workstations, credential-based scans are not possible without configuration setting changes. Configure Windows firewalls to allow appliance access on Windows Management Instrumentation (WMI), configure your Linux box to allow access via SSH, and then run a credentialed scan.
* **Define reasonable, non-overlapping scopes.**
   * Scan a range of 256–1024 IP addresses at a time. Scanning large IP address ranges (for example,  10.0.0.0/9) will send large amounts of unnecessary traffic to your network which might cause the scan to fail.
   * Avoid configuring multiple scans that overlap IP address ranges. This creates redundant results and extends scan times.
   * Scan DMZ, internal servers, and workstations separately, as they will likely need different levels of attention. Also, consider limiting scope by role (for example, database, web, application, QA, test, development, production).

### Port scan frequency recommendations

| Scan frequency | Common TCP and UDP ports | Typically Vulnerable TCP and UDP ports | All TCP ports |
|---|---|---|---|
| Internal scan | External scan | Internal scan | External scan | Internal scan | External scan |
|---|---|---|---|---|---|
| Daily |  | x |  |  |  |  |
| Weekly | x |  |  | x |  |  |
| Monthly |  |  | x |  |  | x |
| Quarterly |  |  |  |  | x |  |
| After configuration change |  |  |  |  | x | x |
| Suspicion of break or infection |  |  |  |  | x | x |

#### Port groups

| Port group name | Ports |
|---|---|
| Common TCP Ports (1000) | 1, 3, 4, 6, 7, 9, 13, 17, 19, 20, 21, 22, 23, 24, 25, 26, 30, 32, 33, 37, 42, 43, 49, 53, 70, 79, 80, 81, 82, 83, 84, 85, 88, 89, 90, 99, 100, 106, 109, 110, 111, 113, 119, 125, 135, 139, 143, 144, 146, 161, 163, 179, 199, 211, 212, 222, 254, 255, 256, 259, 264, 280, 301, 306, 311, 340, 366, 389, 406, 407, 416, 417, 425, 427, 443, 444, 445, 458, 464, 465, 481, 497, 500, 512, 513, 514, 515, 524, 541, 543, 544, 545, 548, 554, 555, 563, 587, 593, 616, 617, 625, 631, 636, 646, 648, 666, 667, 668, 683, 687, 691, 700, 705, 711, 714, 720, 722, 726, 749, 765, 777, 783, 787, 800, 801, 808, 843, 873, 880, 888, 898, 900, 901, 902, 903, 911, 912, 981, 987, 990, 992, 993, 995, 999, 1000, 1001, 1002, 1007, 1009, 1010, 1011, 1021, 1022, 1023, 1024, 1025, 1026, 1027, 1028, 1029, 1030, 1031, 1032, 1033, 1034, 1035, 1036, 1037, 1038, 1039, 1040, 1041, 1042, 1043, 1044, 1045, 1046, 1047, 1048, 1049, 1050, 1051, 1052, 1053, 1054, 1055, 1056, 1057, 1058, 1059, 1060, 1061, 1062, 1063, 1064, 1065, 1066, 1067, 1068, 1069, 1070, 1071, 1072, 1073, 1074, 1075, 1076, 1077, 1078, 1079, 1080, 1081, 1082, 1083, 1084, 1085, 1086, 1087, 1088, 1089, 1090, 1091, 1092, 1093, 1094, 1095, 1096, 1097, 1098, 1099, 1100, 1102, 1104, 1105, 1106, 1107, 1108, 1110, 1111, 1112, 1113, 1114, 1117, 1119, 1121, 1122, 1123, 1124, 1126, 1130, 1131, 1132, 1137, 1138, 1141, 1145, 1147, 1148, 1149, 1151, 1152, 1154, 1163, 1164, 1165, 1166, 1169, 1174, 1175, 1183, 1185, 1186, 1187, 1192, 1198, 1199, 1201, 1213, 1216, 1217, 1218, 1233, 1234, 1236, 1244, 1247, 1248, 1259, 1271, 1272, 1277, 1287, 1296, 1300, 1301, 1309, 1310, 1311, 1322, 1328, 1334, 1352, 1417, 1433, 1434, 1443, 1455, 1461, 1494, 1500, 1501, 1503, 1521, 1524, 1533, 1556, 1580, 1583, 1594, 1600, 1641, 1658, 1666, 1687, 1688, 1700, 1717, 1718, 1719, 1720, 1721, 1723, 1755, 1761, 1782, 1783, 1801, 1805, 1812, 1839, 1840, 1862, 1863, 1864, 1875, 1900, 1914, 1935, 1947, 1971, 1972, 1974, 1984, 1998, 1999, 2000, 2001, 2002, 2003, 2004, 2005, 2006, 2007, 2008, 2009, 2010, 2013, 2020, 2021, 2022, 2030, 2033, 2034, 2035, 2038, 2040, 2041, 2042, 2043, 2045, 2046, 2047, 2048, 2049, 2065, 2068, 2099, 2100, 2103, 2105, 2106, 2107, 2111, 2119, 2121, 2126, 2135, 2144, 2160, 2161, 2170, 2179, 2190, 2191, 2196, 2200, 2222, 2251, 2260, 2288, 2301, 2323, 2366, 2381, 2382, 2383, 2393, 2394, 2399, 2401, 2492, 2500, 2522, 2525, 2557, 2601, 2602, 2604, 2605, 2607, 2608, 2638, 2701, 2702, 2710, 2717, 2718, 2725, 2800, 2809, 2811, 2869, 2875, 2909, 2910, 2920, 2967, 2968, 2998, 3000, 3001, 3003, 3005, 3006, 3007, 3011, 3013, 3017, 3030, 3031, 3052, 3071, 3077, 3128, 3168, 3211, 3221, 3260, 3261, 3268, 3269, 3283, 3300, 3301, 3306, 3322, 3323, 3324, 3325, 3333, 3351, 3367, 3369, 3370, 3371, 3372, 3389, 3390, 3404, 3476, 3493, 3517, 3527, 3546, 3551, 3580, 3659, 3689, 3690, 3703, 3737, 3766, 3784, 3800, 3801, 3809, 3814, 3826, 3827, 3828, 3851, 3869, 3871, 3878, 3880, 3889, 3905, 3914, 3918, 3920, 3945, 3971, 3986, 3995, 3998, 4000, 4001, 4002, 4003, 4004, 4005, 4006, 4045, 4111, 4125, 4126, 4129, 4224, 4242, 4279, 4321, 4343, 4443, 4444, 4445, 4446, 4449, 4550, 4567, 4662, 4848, 4899, 4900, 4998, 5000, 5001, 5002, 5003, 5004, 5009, 5030, 5033, 5050, 5051, 5054, 5060, 5061, 5080, 5087, 5100, 5101, 5102, 5120, 5190, 5200, 5214, 5221, 5222, 5225, 5226, 5269, 5280, 5298, 5357, 5405, 5414, 5431, 5432, 5440, 5500, 5510, 5544, 5550, 5555, 5560, 5566, 5631, 5633, 5666, 5678, 5679, 5718, 5730, 5800, 5801, 5802, 5810, 5811, 5815, 5822, 5825, 5850, 5859, 5862, 5877, 5900, 5901, 5902, 5903, 5904, 5906, 5907, 5910, 5911, 5915, 5922, 5925, 5950, 5952, 5959, 5960, 5961, 5962, 5963, 5987, 5988, 5989, 5998, 5999, 6000, 6001, 6002, 6003, 6004, 6005, 6006, 6007, 6009, 6025, 6059, 6100, 6101, 6106, 6112, 6123, 6129, 6156, 6346, 6389, 6502, 6510, 6543, 6547, 6565, 6566, 6567, 6580, 6646, 6666, 6667, 6668, 6669, 6689, 6692, 6699, 6779, 6788, 6789, 6792, 6839, 6881, 6901, 6969, 7000, 7001, 7002, 7004, 7007, 7019, 7025, 7070, 7100, 7103, 7106, 7200, 7201, 7402, 7435, 7443, 7496, 7512, 7625, 7627, 7676, 7741, 7777, 7778, 7800, 7911, 7920, 7921, 7937, 7938, 7999, 8000, 8001, 8002, 8007, 8008, 8009, 8010, 8011, 8021, 8022, 8031, 8042, 8045, 8080, 8081, 8082, 8083, 8084, 8085, 8086, 8087, 8088, 8089, 8090, 8093, 8099, 8100, 8180, 8181, 8192, 8193, 8194, 8200, 8222, 8254, 8290, 8291, 8292, 8300, 8333, 8383, 8400, 8402, 8443, 8500, 8600, 8649, 8651, 8652, 8654, 8701, 8800, 8873, 8888, 8899, 8994, 9000, 9001, 9002, 9003, 9009, 9010, 9011, 9040, 9050, 9071, 9080, 9081, 9090, 9091, 9099, 9100, 9101, 9102, 9103, 9110, 9111, 9200, 9207, 9220, 9290, 9415, 9418, 9485, 9500, 9502, 9503, 9535, 9575, 9593, 9594, 9595, 9618, 9666, 9876, 9877, 9878, 9898, 9900, 9917, 9929, 9943, 9944, 9968, 9998, 9999, 10000, 10001, 10002, 10003, 10004, 10009, 10010, 10012, 10024, 10025, 10082, 10180, 10215, 10243, 10566, 10616, 10617, 10621, 10626, 10628, 10629, 10778, 11110, 11111, 11967, 12000, 12174, 12265, 12345, 13456, 13722, 13782, 13783, 14000, 14238, 14441, 14442, 15000, 15002, 15003, 15004, 15660, 15742, 16000, 16001, 16012, 16016, 16018, 16080, 16113, 16992, 16993, 17877, 17988, 18040, 18101, 18988, 19101, 19283, 19315, 19350, 19780, 19801, 19842, 20000, 20005, 20031, 20221, 20222, 20828, 21571, 22939, 23502, 24444, 24800, 25734, 25735, 26214, 27000, 27352, 27353, 27355, 27356, 27715, 28201, 30000, 30718, 30951, 31038, 31337, 32768, 32769, 32770, 32771, 32772, 32773, 32774, 32775, 32776, 32777, 32778, 32779, 32780, 32781, 32782, 32783, 32784, 32785, 33354, 33899, 34571, 34572, 34573, 35500, 38292, 40193, 40911, 41511, 42510, 44176, 44442, 44443, 44501, 45100, 48080, 49152, 49153, 49154, 49155, 49156, 49157, 49158, 49159, 49160, 49161, 49163, 49165, 49167, 49175, 49176, 49400, 49999, 50000, 50001, 50002, 50003, 50006, 50300, 50389, 50500, 50636, 50800, 51103, 51493, 52673, 52822, 52848, 52869, 54045, 54328, 55055, 55056, 55555, 55600, 56737, 56738, 57294, 57797, 58080, 60020, 60443, 61532, 61900, 62078, 63331, 64623, 64680, 65000, 65129, 65389 |
| Common UDP Ports (108) | 7, 9, 17, 19, 49, 53, 67, 68, 69, 80, 88, 103, 104, 105, 111, 120, 123, 135, 136, 137, 138, 139,158, 161, 162, 177, 427, 443, 445, 497, 500, 514, 515, 518, 520, 593, 601, 623, 626, 631, 660996, 997, 998, 999, 1022, 1023, 1025, 1026, 1027, 1028, 1029, 1030, 1433, 1434, 1645,1646, 1701, 1718, 1719, 1812, 1813, 1900, 2000, 2048, 2049, 2222, 2223, 3283, 3456,3703, 4444, 4500, 5000, 5060, 5353, 5632, 9200, 10000, 17185, 20031, 30718, 31337,32768, 32769, 32771, 32815, 33281, 49152, 49153, 49154, 49156, 49181, 49182, 49185,49186, 49188, 49190, 49191, 49192, 49193, 49194, 49200, 49201, 50924, 51704, 52768, 65024 |
| Typically Vulnerable TCP Ports (10,071) | 1-10001, 10008, 10110, 10202-10203, 11234, 11311, 12000, 12010, 12168, 12174, 12221, 12345, 12397, 12401, 12754, 13701, 13722, 13724, 13782, 13838, 14206, 14247, 14942, 15104, 16102, 16388, 16660, 17000, 17781, 18264, 18302, 19300, 20031, 20101, 20222, 20432, 21700, 23472, 25072, 27017, 27374, 27665, 28017, 29005, 32982, 33270, 33567-33568, 34443-34444, 36010, 36794, 36890, 37452, 38292, 40080, 40180, 41002, 4 1080, 41443, 41523, 42800, 50000-50001, 51100, 54345, 55555, 57772, 60008, 62078 |
| Typically Vulnerable UDP Ports (108) | 7, 9, 17, 19, 49, 53, 67, 68, 69, 80, 88, 103, 104, 105, 111, 120, 123, 135, 136, 137, 138, 139,158, 161, 162, 177, 427, 443, 445, 497, 500, 514, 515, 518, 520, 593, 601, 623, 626, 631, 660996, 997, 998, 999, 1022, 1023, 1025, 1026, 1027, 1028, 1029, 1030, 1433, 1434, 1645,1646, 1701, 1718, 1719, 1812, 1813, 1900, 2000, 2048, 2049, 2222, 2223, 3283, 3456,3703, 4444, 4500, 5000, 5060, 5353, 5632, 9200, 10000, 17185, 20031, 30718, 31337,32768, 32769, 32771, 32815, 33281, 49152, 49153, 49154, 49156, 49181, 49182, 49185,49186, 49188, 49190, 49191, 49192, 49193, 49194, 49200, 49201, 50924, 51704, 52768, 65024 |
| All TCP Ports | 1-65535 |

### Optimize your scans

When setting up your scans, consider your strategy. Develop an implementation that is particular to your scanning targets and environment.

* **Establish your initial scan window.** The time required to complete a scan is greatly dependent on the types of scans you run as well as environmental factors like hosts and bandwidth. If you must set an end time and want to determine the scan window requirements, run a one-off scan without an end time to establish the initial duration, and then add 20-30 percent more time to accommodate future growth. If the scan takes longer than you want, consider reducing scan scope and spreading scans across multiple appliances to reduce time.
* **Be mindful of what you are scanning.** In terms of length, not all types of scans are equal. Windows-credentialed scanning takes longer than all other credentialed or non-credentialed scans. Under test scenarios, Windows-credentialed scans have taken up to four times as long as other scans. The web application scanning component used in Alert Logic PCI scans can also run long due to the amount of web pages present and the number of fields on each page, multiplied by the number of sites being scanned. Consider these factors when defining your scans and determining scan windows.
* **Multitask.** Scan your servers and workstations separately in a staggered schedule to allow remediation in stages. For example, you can perform remediation on servers while scans on workstations continue to run.
* **Try not to scan over WAN links or VPN.** The traffic between the appliance and the scan target is high compared to the relatively low traffic between the appliance and Alert Logic. Place the appliance on the same side of the VPN or WAN link as the scan target for the best use of your bandwidth.
* **Use un-credentialed scans as fallback.** Credentialed scans produce the most accurate results and should be used on all servers and workstations. Un-credentialed scans should be used only for devices where credentialed scanning is not available, for example, routers, switches, and printers.

## Originating IP addresses for scanning

The following table contains the broad range of IP addresses owned by Alert Logic for existing and future use. Alert Logic scanning technologies use a specific subset of these IP addresses for scan origination. Make sure that your active protective mechanisms, such as IDS, IPS, WAFs, and firewalls that can send shun/block requests, allow scanning traffic from all the following IP addresses.

| IP/CIDR | Number of addresses | Included addresses |
|---|---|---|
| 204.110.218.0/23 | 512 | 204.110.218.0 — 204.110.219.255 |
| 208.71.208.0/22 | 1024 | 208.71.208.0 — 208.71.211.255 |
| 185.54.124.0/22 | 1024 | 185.54.124.0 — 185.54.127.255 |

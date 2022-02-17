# Get Started with Alert Logic   Subscriptions and Add-ons

Alert Logic MDR Essentials, Alert Logic MDR Professional, and Alert Logic MDR Enterprise are subscriptions for your Alert Logic customer account. Each subscription provides different levels of vulnerability and threat management services and capabilities for your on-premise, public cloud, or hosted data centers.

## Alert Logic subscription levels

Your subscription determines the level of protection you can assign for the assets in your deployments. A deployment is a defined set of assets that you want to monitor and protect. Assets can be found from your appliances, agents, hosts, and collectors from your Amazon Web Services (AWS), Microsoft Azure, and other cloud-based or physical data center environments.

During deployment creation, Alert Logic discovers the assets in your networks and allows you to select the desired subscription level for each network individually. You can use the Alert Logic console or an API to assign a subscribed level of protection to any discovered network or asset. Available levels of coverage for each asset include:

* Unprotected
* Essentials coverage
* Professional coverage
* Enterprise coverage

Your coverage includes at least one of these subscription options. For more information about assigning coverage levels, see [Get Started with Alert Logic Deployments](deployments.md). For a summary of your entitlements and usage, see [Entitlement Summary](../analyze/reports/service/entitlement/entitlement-summary.md).

## Alert Logic MDR Essentials

An Essentials subscription provides visibility to assets and vulnerabilities across your environments.

**Security features**:

* Asset discovery
* Vulnerability scanning
* Cloud security configuration checks
* Cloud CIS Benchmarks
* PCI Scanning
* Extended Endpoint Protection
* Threat Risk Index (TRI)

**Support services**:

* 24/7 platform support
* Vulnerability remediation support
* PCI compliance support

### Essentials security features

An Essentials subscription includes security features to monitor and protect your deployments.

#### Asset discovery

Discover and visualize assets in a deployment based on a recurring discovery process for on-premise data centers, hosted environments, AWS and Azure public cloud environments, and container infrastructures.

#### Vulnerability scanning 

Discover and visualize weaknesses in deployed assets and cloud configuration through internal network scans, external network scans, and PCI scans. You can prioritize the vulnerabilities to remediate based on various criteria.

#### Cloud security configuration checks

Alert Logic detects configuration changes and conducts a continuous exposure assessment, providing prioritized remediation steps.

#### Cloud CIS Benchmarks

The CIS Amazon Web Services and Microsoft Azure Foundation Benchmark reports provide an assessment of how your environment conforms to configuration guidelines developed by Center for Internet Security (CIS) experts. Alert Logic performs a series of benchmark checks on your Azure deployments to display the statuses of the checks for each section.

For more information about CIS Benchmarks for Amazon Web Services, see [CIS AWS Foundation Benchmark](../analyze/reports/compliance/CIS-AWS-foundation-benchmark.md). For more information about CIS Benchmarks for Microsoft Azure, see [CIS Microsoft Azure Foundation Benchmark](../analyze/reports/compliance/azure-foundation-benchmark.md).

#### PCI Scanning

In the Alert Logic console, you can schedule   scans that are required for Payment Card Industry (PCI) compliance. Using scan results, you can view, export, and work  to resolve vulnerabilities to prove compliance to auditors.  The scans provide information for meeting PCI compliance and report mandates, including vulnerability details, impacted hosts, risk level, and remediation tips. For more information, see [Manage PCI Scans](../configure/pci-scans.md).

#### Extended Endpoint Protection

The Extended Endpoint Protection functionality  helps you control threats and manage incidents from employee workstations, points of sale, servers, and more. For more information, see [About Alert Logic Extended Endpoint Protection](about-extended-endpoint-protection.md) and [Get Started with Alert Logic Extended Endpoint Protection](endpoint-protection.md).

#### Threat Risk Index (TRI)

The TRI groups the discovered exposures in your deployments and helps pinpoint networks with highly vulnerable assets.

Alert Logic ranks vulnerabilities based on their vulnerability scores, their proximity to the internet, and whether an active exploit for the vulnerability is in the wild. For more information, see [Threat Risk Index Score Factors](../analyze/TRI-score-factors.md).

### Essentials support services

An Essentials subscription provides  support services for implementation, security operations, and support of the Managed Detection and Response platform.

#### 24/7 platform support

Alert Logic provides customer support for implementation,  deployments, user interface, and general product queries, such as console support, agent installation, alert configuration, appliance management, vulnerability scanning configuration, and report scheduling.

#### Vulnerability remediation support

Alert Logic groups and prioritizes remediations based on greatest risk reduction impact (for example, proximity to internet gateways or proximity to databases). Remediations are designed to be highly actionable and drive a consistent approach to resolution.

You can use the Alert Logic console or Alert Logic APIs to mark a remediation as either completed or disposed. For more information about remediating security exposures, see [Exposures](../analyze/exposures.md).

#### PCI compliance support

The Alert Logic Security Operations Center (SOC) helps with scheduling scans, interpreting PCI accredited scan vendor results, and working through the remediation and exception processes to reach scan PCI compliance. For more information, see [PCI DSS Audit](../analyze/reports/compliance/reports.md#PCI_DSS_Audit).

A PCI scan sometimes reports findings that you may want to dispute. After you submit a dispute, a PCI accredited, Alert Logic ASV Security Analyst reviews your request. For more information, see [PCI Scan Disputes](../configure/pci-scan-dispute.md).

## Alert Logic MDR Professional

A Professional subscription provides the coverage of an Essentials subscription, plus threat management capabilities and additional support services.

**Security features**:

* Threat visibility
* File Integrity Monitoring (FIM)
* Web Log Analytics (WLA)
* Log management, storage, and search
* Compliance readiness

**Support services**:

* Customer Service Manager
* 24/7 threat management support
* 15 minute escalation SLA
* Expert Log Review
* Emerging threat hunting

### Professional security features

A Professional subscription includes additional security features for Threat Management.

#### Threat visibility

Network IDS, incident detection and generation, and log collection and log analytics provide information on active threats in your environments.

The Incidents page in the Alert Logic console displays information about incidents and how to use that information to manage and close incidents to secure your environments. For more information, see [Incidents](../analyze/incidents.md).

#### File Integrity Monitoring (FIM)

FIM allows you to monitor changes to files and directories of assets in your deployments. You can configure monitoring or exclusions for specific file paths or entire directories  in your Windows and Linux systems.

The FIM feature also helps you demonstrate compliance with PCI Requirement 10.5.5 and PCI Requirement 11.5. Alert Logic provides guidance on how to use and access FIM features to demonstrate compliance in the and [PCI Requirement 10.5.5](../analyze/reports/compliance/PCI-requirement-10.5.5.md) and [PCI Requirement 11.5](../analyze/reports/compliance/PCI-requirement-11.5.md). For more information, see [File Integrity Monitoring ](../configure/file-integrity-monitoring.md).

#### Web Log Analytics (WLA)

WLA is a log-based application attack detection solution that protects your web applications from common application vulnerabilities. WLA analyzes web server access logs for threats and attacks with a combination of pattern-matching signatures, and an anomaly detection and machine-learning engine. For more information, see [About Alert Logic Web Log Analytics (WLA)](about-wla.md).

#### Log management, storage, and search 

Alert Logic leverages log sources for threat detection. Logs can provide additional information and support for incident response efforts, operational support, and compliance efforts.  Alert Logic stores log data for 12 months by default, although add-ons are available for [Extended log data retention](#extended-log-data-retention).

Alert Logic supports the following log collection methods:

* Windows event log collection
* Syslog-based log collection
* Cloud-specific API based log collection
* Flat-file log collection

You can search flat-file and syslog sourced log data. For more information about Log Search, see [Search: Log Messages](../analyze/log-message-search.md). For more information about log sources and log collection, see [Log Sources](../deploy/log-sources.md)[Log Management Policies](../configure/log-management-policies.md), and [Application Registry](../configure/application-registry.md). and [Log Management Collection Schedules](../configure/schedule-log-collection.md).

#### Compliance readiness 

Professional embedded security capabilities help to meet key compliance mandates and support compliance audit processes. For more information about supported compliance mandates, see [Compliance Reports](../analyze/reports/compliance/reports.md).

### Professional support services

A Professional subscription provides  support services for implementation, security operations, and support of the Managed Detection and Response platform.

#### MDR Concierge

The MDR Concierge serves as a single point of contact for business planning and service management activities. The concierge provides assistance with account planning, network environment health, business, roadmap, and security posture reviews. The MDR Concierge  keeps a close relationship with customers to ensure value and service needs are being met and to organize on-demand customer requests.

#### 24/7 Threat Management Support

The Alert Logic SOC performs additional analysis, triage, and escalation for verified incidents to provide guidance and suggested actions.

#### 15-minute escalation Service Level Ageement

Security analysts triage and analyze detected high or critical threat incidents for legitimacy. Legitimate high and critical threat incidents are escalated verbally to designated customer contacts. Additionally, analysts determine whether the attack was successful. The analyst  adds supporting evidence and analysis to the incident in the Alert Logic console. The analyst also provides recommendations to the customer for preventing further similar attacks.

#### Emerging Threat Hunting

The Alert Logic SOC threat intelligence team combines telemetry and emerging security research to investigate  new types of threats that automation cannot detect. When Alert Logic confirms signatures for new threats, it applies the information to develop global automated detection.

#### On-demand tuning and sensor optimization

Alert Logic works with customers to tune sensors  to reduce excessive incidents, notifications, and escalations caused in some environments.

#### Expert Log Review

Security analysts review daily reports generated from customer log sources and escalate any anomalous, suspicious, or malicious activity that is observed by automated detection. Analysts also review where data contained within the logs may breach rules or thresholds set by the customer. Expert Log Review also helps customers meet [PCI Requirement 10.6.1](../analyze/reports/compliance/PCI-requirement-10.6.1.md).

## Alert Logic MDR Enterprise

An Enterprise subscription provides the coverage of the Essentials and Professional subscriptions, plus a designated Enterprise Security Expert.

### Enterprise Security Expert

A designated security analyst provides personalized technical account management, weekly security posture review, active threat hunting, and on-site evaluation. This expert works closely with the customer, and adds additional layers of technical security support, including:

* Security posture optimization
* Weekly security calls
* Active threat hunting
* Annual on-site consultation

#### Security posture optimization

The Enterprise security expert becomes an integral part of your security program by collaborating as a member of your team to make you more secure in a measurable way. The security expert optimizes your use of Alert Logic services, tunes sensors and exclusions, recommends steps for long-term security efficiency and compliance, and keeps you updated on relevant threat intelligence for business operations planning.

#### Weekly security calls

The designated security expert hosts a weekly call or web-conference with the customer to review recent activity and provide recommendations for prioritizing and remediating security risks. The expert discusses current security news and events that are relevant to your line of business. Any other security projects can also be discussed, and the security expert offers guidance and assistance.

#### Active threat hunting

The designated security expert uses all subscribed Alert Logic services, threat intelligence feeds, and threat intelligence tools to continuously evaluate and analyze your environment for threats and activity that may not normally trigger an alert. Your dedicated security expert identifies this anomalous activity or trend,  correlates the data to determine if the threat is legitimate, and then makes recommendations on how to best remediate the threat. When Alert Logic confirms signatures for new threats, it applies the information to develop global automated detection.

#### Annual on-site consultation

The designated security expert  schedules an annual visit to your facility. The  consultation is dedicated to ensuring that you are getting maximized value from the Enterprise subscription for your specific needs. The security expert can also facilitate talks and presentations on relevant security topics.

    If circumstances do not allow in-person meetings, the security expert hosts a special  video conference to cover topics that are normally discussed during the on-site consultation.    ## Add-ons to Alert Logic Subscriptions

Add-ons are available based on subscription levels and node coverage.

### Alert Logic Managed Web Application Firewall (WAF)

You can implement the Alert LogicWAF regardless of subscription level. WAF is implemented per website as a filtering gateway to validate all requests to  web systems. WAF defends against all OWASP Top 10 vulnerabilities, URL tampering, web scraping, buffer overflow attacks, Zero-Day web application threats, and DoS attacks.

WAF also provides full compliance with [PCI Requirement 6.6](../analyze/reports/compliance/PCI-requirement-6.6.md) and  an audit  report  of your WAF deployments, traffic, incidents, and attacks. For more information, see [About Alert Logic Managed Web Application Firewall (WAF)](../configure/inline-waf/manual/about_profense_waf.md).

### Excess log data traffic

Professional and Enterprise subscriptions include the Network IDS for threat management, which ingests log data. Excessive log volume  requires a log data add-on. Log data allowance is based on node entitlement.  To learn how to review your node entitlement, see [Entitlement Summary](../analyze/reports/service/entitlement/entitlement-summary.md). To learn how to review your log data usage, see [Log Collection](../analyze/reports/service/capability-usage/log-collection.md).

### Extended log data retention

Professional and Enterprise subscriptions include the Network IDS for threat management, which ingests log data. Alert Logic retains log data for 12 months by default. Extended retention is available as an add-on.

### Physical appliances

Alert Logic physical appliances are servers that are preconfigured to meet deployment specifications. Your conversations with Alert Logic representatives determine if your deployment requires a physical appliance and which physical appliance  best serves the goals of your organization.  For more information, see [Install and Configure the  Physical Appliance](../prepare/alert-logic-physical-appliance.md).

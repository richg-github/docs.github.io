# Compliance Reports

The **REPORTS** page in the Alert Logic console provides access to data related to exposures and incidents Alert Logic found within your deployments. You can also view data related to your product usage within your accounts. For information on all the available report groups, see [Reports Guide](../reports.md).

The Compliance report group provide convenient access to analysis, statistics, and trending data related to compliance assessment status and audit preparedness from your subscribed products and services. Alert Logic provides Compliance reports within the following categories:

* [CIS Benchmarks ](#CIS)—Provide assessments of how your environment conforms to configuration guidelines developed by security experts.
* [PCI DSS Audit](#PCI_DSS_Audit)—Provide available documentation and compliance artifacts that help you demonstrate compliance with requirements of the Payment Card Industry Data Security Standard (PCI DSS).
* [HIPAA-HITECH Security Audit](#HIPAASecurityAudit)—Provide documentation to help demonstrate compliance with requirements of the Health Insurance Portability and Accountability Act (HIPAA) and Health Information Technology for Economic and Clinical Health (HITECH) security audit.
* [HITRUST CSF ](#HITRUST)—Provide documentation to help demonstrate compliance with HITRUST Common Security Framework (CSF) control categories, as outlined in the HITRUST Risk Management Framework.
* [SOC 2 Audit](#SOC)—Provide documentation to help demonstrate compliance with the Trust Services Criteria controls established the American Institute of Certified Public Accountants (AICPA).
* [GDPR Audit](#GDPR)—Provide  documentation and compliance artifacts that help you demonstrate compliance with requirements outlined by  the General Data Protection Regulation (GDPR).
* [NIST 800-171 Audit](#NIST800-171Audit)—Provide documentation and compliance artifacts that help you demonstrate compliance with the requirements outlined by the National Institute of Standards and Technology (NIST) Special Publication 800-171.

To access the Compliance reports, in the Alert Logic console,  click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**. Click **Reports**, and then click **Compliance**.

Each report allows you to share its data by email, or download the report as an image, data, crosstab, PDF, or PowerPoint files. To learn how to download reports, see [Report Download Option](../download-option.md).

You can also schedule a report to run periodically and subscribe users or an integration (such as a webhook) to receive a notification when the report is generated.   From the Downloads tab on the Reports page, you can download and manage reports generated from your schedules. For more information, see [Scheduled Reports and Notifications](../../../configure/notifications/report.md).

## Filtering reports

You can filter your reports quickly to refine your results and generate relevant information you need. Each report has a set of filters located at the top that you can select or clear for the filters you want to see. Alert Logic also allows you to add or remove some or all values in a filter you want to see.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

### CIS Benchmarks 

You can run the following report that provides information on assessments of how your environment conforms to Center for Internet Security (CIS) Foundations Benchmark:

* **CIS **Amazon Web Services (AWS)** Foundation Benchmark**: Provides an assessment of how your environment conforms to configuration guidelines developed by CIS experts.
* **CIS **Microsoft Azure** Foundation Benchmark**: Provides an assessment of how your environment conforms to configuration guidelines developed by CIS experts.

For more information about CIS Benchmarks, see the [CIS Benchmarks FAQ](https://www.cisecurity.org/cis-benchmarks/cis-benchmarks-faq/).

### PCI DSS Audit

You can run the following reports that demonstrate compliance to specific requirements of the Payment Card Industry Data Security Standard (PCI DSS):

* **PCI Requirement 6.6:** Shows Alert Logic Managed Web Application Firewall (WAF) deployments, traffic, incidents, and attacks to help you demonstrate compliance to Requirement 6.6. To learn more about this report, see [PCI Requirement 6.6](PCI-requirement-6.6.md).
* **PCI Requirement 10.2.2**: Provides guidance for performing log searches that help you demonstrate compliance with Requirement 10.2.2. To learn more about this report, see [PCI Requirement 10.2.2](PCI-requirement-10.2.2.md).
* **PCI Requirement 10.2.4**: Provides guidance for performing log searches that help you demonstrate compliance with Requirement 10.2.4. To learn more about this report, see [PCI Requirement 10.2.4](PCI-requirement-10.2.4.md).
* **PCI Requirement 10.2.5**: Provides guidance for performing log searches that help you demonstrate compliance with Requirement 10.2.5. To learn more about this report, see [PCI Requirement 10.2.5](PCI-requirement-10.2.5.md).
* **PCI Requirement 10.2.6**: Describes, and provides access to, log searches in the Alert Logic console that help demonstrate compliance with Requirement 10.2.6.To learn more about this report, see [PCI Requirement 10.2.6](PCI-requirement-10.2.6.md).
* **PCI Requirement 10.2.7**: Provides guidance for performing log searches that help you demonstrate compliance with Requirement 10.2.7. To learn more about this report, see [PCI Requirement 10.2.7](PCI-requirement-10.2.7.md).
* **PCI Requirement 10.5.1 Report**: Shows a list of the current log management users,  which helps you demonstrate compliance with Requirement 10.5.1. To learn more about this report, see [PCI Requirement 10.5.1](PCI-requirement-10.5.1.md).
* **PCI Requirement 10.5.5 Report**: Provides guidance for how to access File Integrity Monitoring features that help you demonstrate compliance with  Requirement 10.5.5. To learn more about this report, see [PCI Requirement 10.5.5](PCI-requirement-10.5.5.md).
* **PCI Requirement 10.6.1 Report:** Shows Log Review incidents and Log Management incidents that help you demonstrate compliance with Requirement 10.6.1. To learn more about this report, see [PCI Requirement 10.6.1](PCI-requirement-10.6.1.md).
* **PCI Requirement 10.7 Report**: Provides guidance for performing log searches that help you demonstrate compliance with Requirement 10.7. To learn more about this report, see [PCI Requirement 10.7](PCI-requirement-10.7.md).
* **PCI Requirement 10.8 Report**: Provides guidance to demonstrate you have implemented a process for the timely detection and reporting failures of critical security control systems, in compliance with Requirement 10.8. To learn more about this report, see [PCI Requirement 10.8](PCI-requirement-10.8.md).
* **PCI Requirement 11.2.1 Report**: Provides guidance to demonstrate  that quarterly internal vulnerability scans, "high-risk" vulnerabilities are rescanned, and performed by qualified personnel, in compliance with Requirement 11.2.1. To learn more about this report, see [PCI Requirement 11.2.1](PCI-requirement-11.2.1.md).
* **PCI Requirement 11.2.2 Report**: Provides guidance to demonstrate that quarterly external vulnerability scans and rescans are performed, in compliance with Requirement 11.2.2. To learn more about this report, see [PCI Requirement 11.2.2](PCI-requirement-11.2.2.md).
* **PCI Requirement 11.4**: Shows Network IDS incidents and customer escalation contacts to help you demonstrate compliance to Requirement 11.4 To learn more about this report, see [PCI Requirement 11.4](PCI-requirement-11.4.md).
* **PCI Requirement 11.5**: Provides guidance on how to access File Integrity Monitoring features that help you demonstrate compliance with Requirement 11.5. To learn more about this report, see [PCI Requirement 11.5](PCI-requirement-11.5.md).

### HIPAA-HITECH Security Audit

You can run the following reports that demonstrate compliance with specific requirements of the HIPAA security audit:

* **HIPAA 164.308(a)(1)(ii)(B)—Risk Management**: Provides information on security measures that reduce risk and vulnerabilities to a reasonable and appropriate level to help you demonstrate compliance with HIPAA 164.308(a)(1)(ii)(B). To learn more about this report, see [HIPAA 164.308(a)(1)(ii)(B)—Risk Management](HIPAA-164.308-risk-management.md).
* **HIPAA 164.308(a)(5)(ii)(B)—Protection from Malicious Software**:  Provides  information on guarding against, detecting, and reporting malicious software to help you demonstrate compliance with HIPAA 164.308(a)(5)(ii)(B). To learn more about this report, see [HIPAA 164.308(a)(5)(ii)(B)—Protection from Malicious Software](HIPAA-164.308-protection-from-malicious-software.md).
* **HIPAA 164.308(a)(1)(ii)(D)—Information System Activity Review**: Shows available documentation and compliance artifacts that help you demonstrate compliance with requirements of 164.308(a)(1)(ii)(D). To learn more about this report, see [HIPAA 164.308(a)(1)(ii)(D)—Information System Activity Review](HIPAA-164.308-is-activity-review.md).
* **HIPAA 164.308(a)(5)(ii)(C)—Login Monitoring**: Shows available documentation and compliance artifacts that help you demonstrate compliance with requirements of HIPAA 164.308(a)(5)(ii)(C). To learn more about this report, see [HIPAA 164.308(a)(5)(ii)(C)—Login Monitoring](HIPAA-164.308-login-monitoring.md).
* **HIPAA 164.308(a)(6)(ii)—Response and Reporting**: Shows available documentation and compliance artifacts that help you demonstrate compliance with requirements of HIPAA 164.308(a)(6)(ii). To learn more about this report, see [HIPAA 164.308(a)(6)(ii)—Response and Reporting](HIPAA-164.308-response-reporting.md).
* **HIPAA 164.312(b)—Audit Controls**: Provides information on the implemented software or procedural mechanisms that record and examine activity in information systems to help you demonstrate compliance with HIPAA 164.312(b). To learn more about this report, see [HIPAA 164.312(b)—Audit Controls](HIPAA-164.312-audit-controls.md).
* **HIPAA 164.312(c)(1)—Integrity Controls**: provides guidance on how to use and access your file integrity monitoring features to help you demonstrate compliance with HIPAA 164.312(c)(1).  To learn more about this report, see [HIPAA 164.312(c)(1)—Integrity Controls](HIPAA-164.312-integrity-controls.md).

### HITRUST CSF 

You can run the following reports that demonstrate compliance with specific control categories of HITRUST CSF:

* **HITRUST CSF 01.0 Access Control**:  Describes how to use and access log searches and the list of users with access to security functions and access logs  in the Alert Logic console that help demonstrate compliance with Control Category 01.0.To learn more about this report, see [HITRUST CSF 01.0 Access Control](HITRUST-CSF-01.md).
* **HITRUST CSF 03.0 Risk Management**: Describes how to  use and access vulnerability, threat risk index, and threat response reporting features in the Alert Logic console that help demonstrate compliance with Control Category 03.0.To learn more about this report, see [HITRUST CSF 03.0 Risk Management](HITRUST-CSF-03.0.md).
* **HITRUST CSF 06.0 Compliance**:Provides guidance on how to access configuration features in the Alert Logic console that help you demonstrate compliance with Control Category 6.0. To learn more about this report, see [HITRUST CSF 06.0 Compliance](HITRUST-CSF-06.0.md).
* **HITRUST CSF 09.0 Communications and Operations Management**: Provides guidance on how to access configuration features in the Alert Logic consoleto that help you demonstrate compliance with Control Category 09.0.To learn more about this report, see [HITRUST CSF 09.0 Communications and Operations Management](HITRUST-CSF-09.0.md).
* **HITRUST CSF 10.0 Information Systems Acquisition, Development, and Maintenance**: Describes how to access web application protection and vulnerability management features in the Alert Logic console that help demonstrate compliance with Control Category 10.0. To learn more about this report, see [HITRUST CSF 10.0 Information Systems Acquisition, Development, and Maintenance](HITRUST-CSF-10.0.md).
* **HITRUST CSF 11.0 Information Security Incident Management**: Describes how to access security event and incident reporting features in the Alert Logic console that  help demonstrate compliance with Control Category 11.0.To learn more about this report, see [HITRUST CSF 11.0 Information Security Incident Management](HITRUST-CSF-11.0.md).

## SOC 2 Audit

You can run the following reports that demonstrate compliance with specific common criteria (CC) of SOC 2:

* **SOC 2 CC6.2 User Registration**:  Describes how to use and access log searches   in the Alert Logic console that help demonstrate compliance with CC6.2.To learn more about this report, see [SOC 2 Common Criteria 6.2 User Registration](SOC2-CC-6.2-user-registration.md).
* **SOC 2 CC6.3 Access Modification and Removal**: Describes how to  use and access log searches and the list of users with access to security functions and access logs  in the Alert Logic console that help demonstrate compliance with CC6.3.To learn more about this report, see [SOC 2 Common Criteria 6.3 Access Modification and Removal](SOC2-CC-6.3-access-modification-and-removal.md).
* **SOC 2 CC6.6 Boundary Protection**:Describes how to  use and access threat detection, scanning, and web application protection features in the Alert Logic console that help demonstrate compliance with CC6.6. To learn more about this report, see [SOC 2 Common Criteria 6.6 Boundary Protection](SOC2-CC-6.6-boundary-protection.md).
* **SOC 2 CC6.8 Unauthorized and Malicious Code Protection**: Describes how to access file integrity monitoring and endpoint protection features in the Alert Logic console to that help you demonstrate compliance with CC6.8.To learn more about this report, see [SOC 2 Common Criteria 6.8 Unauthorized and Malicious Code Protection](SOC2-CC-6.8-unauthorized-and-malicious-code-protection.md).
* **SOC 2 CC7.1 Configuration and Vulnerability Management**: Describes how to access file integrity monitoring, scan scheduling, and vulnerability reporting features in the Alert Logic console that help demonstrate compliance with CC7.1. To learn more about this report, see [SOC 2 Common Criteria 7.1 Configuration and Vulnerability Management](SOC2-CC-7.1-configuration-and-vulnerability-management.md).
* **SOC 2 CC7.2 Security Event and Anomaly Detection**: Describes how to access security event and threat response reporting features in the Alert Logic console that help demonstrate compliance with CC7.2. To learn more about this report, see [SOC 2 Common Criteria 7.2 Security Event and Anomaly Detection](SOC2-CC-7.2-security-event-anomaly-detection.md).
* **SOC 2 CC7.3 Incident Detection and Response**: Describes how to access security event and threat response reporting features in the Alert Logic console that help demonstrate compliance with CC7.3. To learn more about this report, see [SOC 2 Common Criteria 7.3 Incident Detection and Response](SOC2-CC-7.3-incident-detection-reponse.md).
* **SOC 2 CC7.4 Incident Containment and Remediation**: Describes how to access how to access vulnerability and threat response reporting features in the Alert Logic console that help demonstrate compliance with CC7.4. To learn more about this report, see [SOC 2 Common Criteria 7.4 Incident Containment and Remediation](SOC2-CC-7.4-incident-containment-remediation.md).

## GDPR Audit

You can run the following reports that help demonstrate compliance with the General Data Protection Regulation (GDPR):

* **GDPR Article 25: Data Protection by Design and By Default**:  Describes and provides access to features in the Alert Logic console that help demonstrate compliance with GDPR Article 25. To learn more about this report, see [GDPR Article 25: Data Protection by Design and by Default](GDPR-article-25-data-protection.md).
* **GDPR Article 32: Security of Processing**: Describes and provides access to features in the Alert Logic console that help demonstrate compliance with GDPR Article 32.To learn more about this report, see [GDPR Article 32: Security of Processing](GDPR-article-32-security-of-processing.md).
* **GDPR Article 33: Notification of Personal Data Breach**:Describes and provides access to features in the Alert Logic console that help demonstrate compliance with GDPR Article 33. To learn more about this report, see [GDPR Article 33: Notification of Personal Data Breach](GDPR-article-33-notification-personal-data-breach.md).
* **GDPR Article 34: Communication of a Personal Data Breach**:Describes and provides access to features in the Alert Logic console that help demonstrate compliance with GDPR Article 34. To learn more about this report, see [GDPR Article 34: Communication of a Personal Data Breach](GDPR-article-34-comm-data-breach.md).
* **GDPR Article 35: Data Protection by Design and By Default**:Describes and provides access to features in the Alert Logic console that help demonstrate compliance with GDPR Article 35. To learn more about this report, see [GDPR Article 35: Data Protection Impact Assessment](GDPR-article-35-data-protection-impact-assessment.md).

## NIST 800-171 Audit

You can run the following reports that help demonstrate compliance National Institute of Standards and Technology (NIST) Special Publication 800-171:

* **NIST 800-171 3.1 - Access Control**:  Provides links to log searches in the Alert Logic console that help demonstrate compliance with NIST 800-171 3.1   Derived Security Requirements 3.1.7, 3.1.8, 3.1.11, and 3.1.12. To learn more about this report, see [NIST 800-171 3.1 - Access Control](NIST-800-171-3.1-access-control.md).
* **NIST 800-171 3.3 - Audit and Accountability**: Provides links to log search, notifications, log review and event analysis reporting, file integrity monitoring, dashboards, and incident response features in the Alert Logic console that help demonstrate compliance with  NIST 800-171  Basic Security Requirements 3.3.1 and 3.3.2 and Derived Security Requirements 3.3.3, 3.3.4, 3.3.5, and 3.3.8. To learn more about this report, see [NIST 800-171 3.3 - Audit and Accountability](NIST-800-171-3.3-audit-and-accountability.md).
* **NIST 800-171 3.4 - Configuration Management**:Provides links to the exposures and endpoint protection features in the Alert Logic console that help demonstrate compliance with NIST 800-171    Derived security requirements 3.4.7 and 3.4.8. To learn more about this report, see [NIST 800-171 3.4 - Configuration Management](NIST-800-171-3.4-configuration-management.md).
* **NIST 800-171 3.5 - Identification and Authentication**: Provides links to log searches in the Alert Logic console that help demonstrate compliance with the NIST 800-171    Basic Security Requirements 3.5. To learn more about this report, see [NIST 800-171 3.5 - Identification and Authentication](NIST-800-171-3.5-identification-and-authentication.md).
* **NIST 800-171 3.6 - Incident Response**:Provides links to incident response and event analysis reporting features in the Alert Logic console that help demonstrate compliance with NIST 800-171 3.1  Basic Security Requirements 3.6.1 and 3.6.2.. To learn more about this report, see [NIST 800-171 3.6 - Incident Response](NIST-800-171-3.6-incident-response.md).
* **NIST 800-171 3.11 - Risk Assessment**:Provides links to vulnerability scanning and vulnerability variance reporting features in the Alert Logic console that help demonstrate compliance with NIST 800-171 Derived Security Requirements 3.11.2 and 3.11.3. To learn more about this report, see [NIST 800-171 3.11 - Risk Assessment](NIST-800-171-3.11-risk-assessment.md).
* **NIST 800-171 3.12 - Security Assessment**:Provides links to vulnerability assessment and threat risk index reporting features in the Alert Logic console that help demonstrate compliance with NIST 800-171 Derived Security Requirement 3.12.3. To learn more about this report, see [NIST 800-171 3.12 - Security Assessment](NIST-800-171-3.12-security-assessment.md).
* **NIST 800-171 3.13 - System and Communications Protection**:Provides links to network IDS, vulnerability scan, and web application protection features in the Alert Logic console that help demonstrate compliance with NIST 800-171  Basic Security Requirement 3.13.1 and Derived Security Requirement 3.13.6. To learn more about this report, see [NIST 800-171 3.13 - System and Communications Protection](NIST-800-171-3.13-system-and-communications.md).
* **NIST 800-171 3.14 - System and Information Integrity**:The NIST 800-171 3.14 - System and Information Integrity report provides links to endpoint protection, web application protection, and log search features in the Alert Logic console that help demonstrate compliance  with NIST 800-171 Basic Security Requirements 3.14.1 and 3.14.2, and Derived Security Requirements 3.14.4 through 3.14.7. To learn more about this report, see [NIST 800-171 3.14 - System and Information Integrity](NIST-800-171-3.14-system-and-information-integrity.md).

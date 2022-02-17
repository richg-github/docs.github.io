# Manage PCI Scans

Through the Alert Logic console, you can schedule  quarterly external scans that are required for Payment Card Industry (PCI) compliance. You can quickly and easily view the results of those scans in the Alert Logic console, and then work with Alert Logic, as needed, to resolve vulnerabilities and prove compliance to auditors.

Working with PCI compliance requires documents available from the [PCI Security Standards Council](https://www.pcisecuritystandards.org/) (PCI SSC). Documents include the *Payment Card Industry  Data Security Standard* (DSS) and the current release of the *ASV Program Guide*.

Alert Logic also offers PCI compliance reports in the Reports page of the Alert Logic console. The PCI compliance reports provide convenient access to analysis, statistics, and trending data related to compliance assessment status and audit preparedness from your subscribed products and services.  To learn more about the PCI compliance reports, see [PCI DSS Audit](../analyze/reports/compliance/reports.md#PCI_DSS_Audit).

### Review the recommended process

The following procedure outlines the suggested workflow to use Alert Logic vulnerability scans for your PCI compliance requirements.

To use Alert Logic scans for PCI compliance:

1. [Schedule a PCI scan](#scheduleScan).			
When you run a PCI scan, Alert Logic generates a preliminary PCI compliance report and sends an email to the configured devices.
2. [View PCI compliance status and history](#viewStatusHistory).
3. If your preliminary PCI compliance report indicates that you are compliant, then [complete your final PCI compliance documentation](#complete-final-PCI-documentation).
4. If your preliminary PCI compliance report indicates that you are not compliant, or if you need to scan again, complete the following actions:
   * [Address PCI compliance vulnerabilities](#addressCompVulnerabilities).
   * If you have a vulnerability that you believe contains a false positive, you can submit a dispute. For more information about how to submit a dispute, see [PCI Scan Disputes](pci-scan-dispute.md). You can also contact Technical Support to discuss the vulnerability.
   * If you have a vulnerability that you cannot address due to a business or technological constraint, you can submit a dispute. For more information about how to submit a dispute, see [PCI Scan Disputes](pci-scan-dispute.md). You can also contact Technical Support to discuss the vulnerability and any compensating controls in your environment that reduce the risk associated with the vulnerability.
   
   Technical Support (US:(877) 484-8383, EU: +44 (0) 203 011 5533) requires specific information for PCI scan disputes. Before you contact Technical Support, have the following information ready:   * The PCI compliance report ID number, which you can find in the heading of the PCI compliance report
      * The date and time when the PCI compliance report was generated, which you can find in the heading of the PCI compliance report
      * Any compensating control documentation associated with the vulnerability before you contact the Alert Logic Security Operations Center (SOC)
   * After you address all vulnerabilities and resolve disputes, then [complete final PCI compliance documentation](#complete-final-PCI-documentation).

### Schedule a PCI scan

When you schedule a PCI scan, Alert Logic runs the scan as specified in the schedule, and then displays the results of the scan in the PCI Compliance tab.

When you schedule a PCI scan, you attest that, at a minimum:

* You are responsible for proper scoping of the scans, and the scan includes all required components for a  PCI DSS scope.
* You implemented network segmentation if you excluded any components from PCI DSS scope.

For more information about attestations, see the *ASV Program Guide*.

To schedule a PCI scan:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu, and then click the ![](../Resources/Images/dashboard/configure-icon.png)**Configure** menu item.
2. Click **PCI Scanning** to access the PCI Scanning page.
3. Click **Schedule New Scan**.
4. On the New PCI Scan page, in the **Scan Title** field, enter a descriptive title for the scan.
5. Select the check box if you want to create a case when the scan completes.
6. In **All Targets (domain names of your web sites to distinguish multiple websites on the same IP address) and IP addresses to scan**, enter all targets. PCI DSS requires customers to supply FQDNs in addition to external-facing IP addresses and other unique entryways into applications for the entire in-scope infrastructure. This includes, but is not limited to:                
To include multiple domains, enter each domain on a separate line. Do not use commas, semicolons, or other separators.
The box also uses what you enter to seed the scanner. Seed entries include hidden URLs that cannot be reached from the homepage. These seed URLs allow the scanner to reach more of your application, ensuring the most thorough possible scan.
   * Discrete IP addresses
   * IP address ranges
   * Domains for all web servers
   * Domains for mail servers
   * Domains used in name-based virtual hosting
   * Web-server URLs to directories that cannot be reached by crawling the website from the home page
   * Any other public-facing domains or domain aliases
8. In **Addresses to exclude**, enter the TCP/IP addresses of the hosts you want to exclude from the scan operation, if applicable.
9. In **Your top level domains for scoping suggestions**, enter top-level domains to help the PCI scanner find more scan targets that you want to include in the scan.
10. Under **Scan Schedule**, specify how often to run the scan, the start time, and your time zone.
11. Under **Notification Settings**, type the email address where you want to receive notifications when the scan is finished.
12. Click **Submit PCI scan job**.

### View PCI compliance status and history

Alert Logic simplifies tracking, analyzing, and documenting your PCI compliance. You can view your current and historical PCI compliance status in the PCI Scanning page.

By default, your PCI compliance status is "Non-Compliant." The status changes to "Compliant" only after you generate your final PCI compliance report. For more information, see [Complete final PCI compliance documentation](#complete-final-PCI-documentation).

To view your PCI compliance status and history:

1. Access the PCI Scanning page in the Alert Logic console.
2. Under** Latest 25 Reports**, click the name of the report you want to view.

#### Legacy scan results and archived reports

If you were subscribed to legacy products, you can view your legacy scan results from the Settings menu. Click the Settings icon (![](../Resources/Images/supportThreeDots.png)), and then click **Legacy Scan Results**. You can also access the legacy scan results from the Reports page.

**To access legacy scan results**:

1. Click **REPORTS**, and then click **Scheduled**.
2. Click **Saved Scheduled Reports**, and then click **Archived Reports**.

### Address PCI compliance vulnerabilities

After viewing the results of a PCI compliance scan, if the status displays "Non-compliant," you must address vulnerabilities.

A scan retains its non-compliant status until you generate a final report.

To address PCI compliance vulnerabilities:

1. Access the PCI Scanning page in the Alert Logic console.
2. Under **Latest 25 Reports**, click the name of the non-compliant results that contain the vulnerabilities to address.
3. In the **PCI Scan Result** report, click the name of the vulnerability you want to address to view information about the vulnerability, including the CVE number, a brief description of the vulnerability, and possible solutions.
4. Review the information for the vulnerability and address as necessary. If you cannot address the vulnerability due to a business or technical constraint, you can dispute the vulnerability. For more information, see [Dispute scan results](pci-scan-dispute.md#Dispute).
5. After you address each vulnerability identified in the PCI Scan Result report, run the scan again to verify you addressed the vulnerability. See [Re-scan  a non-compliant PCI scan](#rescan).

### Disable weak and anonymous ciphers

PCI-DSS requires websites to use strong cryptography and security protocols such as Secure Socket Layer/Transport Layer Security (SSL/TLS) or Internet Protocol Security (IPsec) to safeguard sensitive cardholder data during transmission over open public networks. In addition, you must disable insecure protocols like SSL 2.0 and weak ciphers, or you will fail a PCI compliance scan.

    Apache    
Most versions of Apache have SSL 2.0 enabled by default. To disable SSL 2.0 and weak ciphers:

1. Open the httpd.conf or ssl.conf file, and then search for the SSLCipherSuite directive. If you do not have the directive, add it.
2. Replace the contents with the following:
<kbd>SSLProtocol -ALL +SSLv3 +TLSv1</kbd>
<kbd>SSLCipherSuite ALL:!ADH:RC4+RSA:+HIGH:+MEDIUM:!LOW:!SSLv2:!EXPORT</kbd>
3. Save the file.
4. Restart Apache.

More resources:

[mod_ssl documentation for disabling SSL 2.0 and weak ciphers](http://httpd.apache.org/docs/2.0/mod/mod_ssl.html#sslproxyciphersuite)

    Windows    
The following registry settings can help secure ciphers and encryption settings for Microsoft Internet Information Server (IIS).

Alert Logic makes no warranty as to the efficacy of the script. Many services on a Windows computer may use SSL/TLS such as Remote Desktop, LDAP, HTTPs, SMTPs, or Windows remote management ports.  Changing the encryption settings may affect other services.  This script may need to be customized for your environment. Use this script at your own risk, and try it on a development environment first. Before you edit the registry, export the keys in the registry that you plan to edit, or back up the whole registry.

Restart the server after implementing the registry changes.

<kbd>Windows Registry Editor Version 5.00
                    [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders]
“SecurityProviders”=”msapsspc.dll, schannel.dll, digest.dll, msnsspc.dll”
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SaslProfiles]
“GSSAPI”=”Kerberos”
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL]
“EventLogging”=dword:00000001
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL]
“AllowInsecureRenegoServers”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\DES 56/56]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\NULL]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC2 128/128]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC2 40/128]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC2 56/128]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC4 128/128]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC4 40/128]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC4 56/128]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC4 64/128]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\Triple DES 168/168]
“Enabled”=dword:ffffffff
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Hashes\MD5]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Hashes\SHA]
“Enabled”=dword:ffffffff
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\KeyExchangeAlgorithms\PKCS]
“Enabled”=dword:ffffffff
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\PCT 1.0\Client]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\PCT 1.0\Server]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Client]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 3.0\Client]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 3.0\Server]
“Enabled”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Client]
“Enabled”=dword:00000001
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Server]
“Enabled”=dword:00000001
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client]
“Enabled”=dword:00000001
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server]
“Enabled”=dword:00000001
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest]
“Negotiate”=dword:00000000
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest]
“UTF8HTTP”=dword:00000001
                [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest]
“UTF8SASL”=dword:00000001</kbd>### Re-scan  a non-compliant PCI scan

You can run a PCI scan between scheduled scan times. If a scheduled PCI scan result is "Non-compliant," and you have addressed the vulnerabilities discovered by the scan, you can use the re-scan feature to determine compliance.

**To re-scan a scheduled PCI scan policy:**

1. Access the PCI Scanning page in the Alert Logic console.
2. Under **Latest 25 Reports**, click the PCI Scan Result with a status of "Non-compliant."
3. Click **Re-scan**.

### Dispute failing vulnerabilities

A PCI scan can report findings that you want to dispute. For example, the scan can identify a vulnerability in your environment that may be a false positive. Another example is that the scan can identify a vulnerability that you cannot address due to a business or technological constraint, but you can resolve through the use of a compensating control. In these and similar situations, you can dispute the vulnerability through an official dispute process. To learn how to dispute a vulnerability, see [PCI Scan Disputes](pci-scan-dispute.md).

### Complete final PCI compliance documentation

After you address all your PCI vulnerabilities, you need to prepare required PCI compliance documentation and submit it to your *acquirer*. Required PCI compliance documentation includes:

* Final PCI scan reports
* Self-Assessment Questionnaire (SAQ) and Attestation of Compliance

An *acquirer* is typically the entity, such as a credit card processor, that provides credit card processing services.

To complete final PCI compliance documentation:

1. [Prepare final PCI scan reports](#prepare-final-pci-scan-reports).
2. [Prepare Self-Assessment Questionnaire and Attestation of Compliance](#prepare-saq-and-attestation-of-compliance).
3. Submit final PCI scan reports, SAQ, and Attestation of Compliance to your acquirer.

#### Prepare final PCI scan reports

When your PCI scan results are compliant, you can generate your final reports for submission to an acquirer.

To prepare final PCI scan reports:

1. Access the PCI Scanning page in the Alert Logic console.
2. Under **Latest 25 Reports**, click the name of the scan results to submit to your acquirer. *The scan results must have a status of compliant.*
3. Under **Report Downloads**, click each of the following reports to generate and download: 
The **Vulnerability Details** report is available as a CSV file in addition to the PDF download. The CSV file includes less detail than the PDF, but the information is easy to view and analyze in a spreadsheet.
   * **Executive Summary**
   * **Vulnerability Details**
   * **Attestation of scan compliance**

If you want to send feedback to the PCI SSC regarding your scanning experience, your experience with Alert Logic, or any other aspects of PCI scans, click the **PCI ASV Feedback Form** link below the list of reports.

#### Prepare Self-Assessment Questionnaire and Attestation of Compliance

To validate compliance with PCI DSS, you must submit a Self-Assessment Questionnaire and Attestation of Compliance with your final PCI scan reports. You can obtain the required documents from the PCI SSC, as described in the following procedure.

To prepare the Self-Assessment Questionnaire and Attestation of Compliance:

1. Use the guidelines provided in the table on the [PCI SSC website](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment) to determine the appropriate questionnaire for your company. Note the letter code for the questionnaire.
2. Referencing the letter code, locate and download the appropriate questionnaire from the [PCI SSC document library](https://www.pcisecuritystandards.org/document_library?category=saqs#results). You can choose DOC or PDF format.
3. Complete the questionnaire.

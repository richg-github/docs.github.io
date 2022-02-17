# PCI Scan Disputes

A PCI scan will sometimes report findings that you may want to dispute. For example, if a scan identifies a false positive vulnerability. Other examples of when you may want to dispute findings in the PCI scan results are the following:

* Vulnerability has a disputed CVSS Base score.
* Vulnerability cannot be addressed in your environment, but there is a compensating control in place.
* Exceptions exist in the report.

In these and similar situations, you can file a dispute in the PCI Scan Disputes page. The most common workflow for disputing a vulnerability is the following:

1. Determine the scan policy that contains the vulnerabilities you need to address, and then access the PCI Scan Results for that scan policy. See [Dispute scan results](#Dispute) for more information.
2. Address and enter a dispute statement for each vulnerability to submit for review. See [Dispute a vulnerability](#how-to-submit-dispute) for more information.
3. After you submit your dispute, an Alert Logic ASV Security Analyst reviews your request. See [Review or update a submitted dispute](#how-to-update-submitted-request) for more information.

For more information about  PCI scan vulnerability disputes and compensating controls, see [PCI Security Standards Council.](https://www.pcisecuritystandards.org/)

## Guidelines and examples for disputing 

When you dispute a vulnerability finding, you provide the type of dispute and an explanation for your dispute. If an issue appears with a PCI assessment, the only way to pass the check is to provide an acceptable dispute. PCI does not recognize a justification of the presence of the issue alone as a valid dispute.

**Use the following general guidelines when developing your dispute statement**:

* Provide detailed, specific information about the reasons you believe the scan result is a false positive.
* Provide proof that you have resolved the scan vulnerability.
* Provide specific information about the operating system, service, or patch level if the issue under dispute is version-specific.
* Do not address a configuration issue by simply claiming to be patched against the issue.
* Do not claim the software in use is the latest version without including evidence that the version in use does not include the same risk.
* Do not claim a detected plug-in or product version is incorrect without providing evidence of the difference.
* Make sure the dispute statement is correct and complete before you submit it. Once you file a dispute, the statement cannot be modified. You can only add evidence that addresses the statement.

### **Examples**

**The following list provides specific examples that can help  when developing your dispute statement**:

* If the issue under dispute is version specific, provide specific information about the operating system, service or patch level :
**Incorrect:** This does not affect our version of Windows.
**Correct:** The discovered vulnerability (MS06-057) does not apply to the version of the operating system that we run (MS Windows 2008 R2).
* If the assessment reveals a version of .NET 2.0.xxxx, and you do not use this version of .NET, you must include evidence that .NET 2.0 is not in use.
* If the scan detects a version of a service considered vulnerable, and you use a different version of the service, you must include the version of the service in use.
* If you operate multiple versions of a given daemon on some systems, and a version of a web server is shown as a vulnerable version, you must provide a statement that the version reported by the server itself to the scanner is wrong. Also, you must provide documentation that the service bound to the port is the correct version.

## Dispute scan results

You must first determine the scan policy that contains the vulnerabilities you need to address, and then access the PCI Scan Results for that scan policy. From the PCI Scan Results, you can access the  PCI Scan Disputes page, which lists all of the failing vulnerabilities identified in that PCI Scan.

**To dispute scan results from the PCI Compliance tab**:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu, and then click the ![](../Resources/Images/dashboard/configure-icon.png)**Configure** menu item.
2. Click **PCI Scanning** to access the PCI Scanning page.
3. In the PCI Compliance tab, under **Latest 25 Reports**, click the name of the non-compliant scan policy that contain the vulnerabilities you need to address.
4. Under **PCI Scan Results**, click **Dispute Results**.

You can also access a non-compliant scan policy in the Scans tab of the PCI Scanning page.

**To dispute scan results from the Scans tab**:

1. In the PCI Scanning page, click **Scans**, and then locate  the non-compliant scan policy that contains the vulnerabilities you need to address.
2. Click **Results** to see details on the scan policy, and then click **PCI Scan Results**.
3. Under **PCI Scan Results**, click **Dispute Results**.

### PCI Scan Disputes page overview 

The following list highlights some of the features of the PCI Scan Disputes page:

* **Vulnerability description**: A detailed description is provided for each vulnerability under the Vulnerability column.
* **Previously disputed**: An exposure that was previously disputed  is identified with an arrow icon (![](../Resources/Images/Cloud Defender/Scanning/PCIDisputePrefillArrow.png)). For these items, you can prefill information from the previous disputes. To learn how to prefill information, see [Prefill information from previous disputes](#prefill-info-from-previous-disputes).
* **Vulnerability information**: You can view more information for each vulnerability. Click the vulnerability for more details and additional resources.  For similar vulnerabilities, you can address them in bulk. To learn how to address vulnerabilities in bulk, see [Address multiple exposures in bulk](#address-multiple-exposures-in-bulk).
* **Supporting evidence**: Vulnerabilities that are ready to be submitted have a check icon (![](../Resources/Images/Cloud Defender/Scanning/PCIDisputeCheck.png)) next to them.
* **Vulnerabilities remaining**: The number of vulnerabilities you have yet to address is reflected in the upper right corner. All vulnerabilities must be addressed before you can submit your dispute request.

#### Sort and search content in the PCI Scan Disputes page

You can sort the list of vulnerabilities by various parameters, by ascending or descending order, and search content. You can perform searches to find a specific vulnerability. In the search bar on the top right of the page, search for all or part of the name of the vulnerability, a specific port or protocol, host information, or any partial string of text that is part of the vulnerability text.

To sort the list of vulnerabilities, use the Sort fields or click a column name. You can sort by the following values:

* **Status**
* **Host Name**
* **Host IP Address**
* **FQDN**
* **Vulnerability (ID)**
* **Service Protocol**
* **Service Port**
* **Selection Status**
* **Last Modified**
* **Dispute Type**

### Dispute a vulnerability

To dispute a vulnerability, you must provide an explanation for the disputed findings, and submit the information for review by an Alert Logic PCI ASV Analyst. After you submit your dispute request, the engineer, with whom you can communicate through the PCI Scan Disputes page, reviews the submitted evidence and makes a decision.

In the PCI Scan Disputes page, if a vulnerability was previously disputed, you can use the Prefill option to reuse comments and evidence. To learn more about the prefill option, see [Prefill information from previous disputes](#prefill-info-from-previous-disputes).

To dispute a vulnerability:

1. In the PCI Scan Disputes page, complete the following for each identified vulnerability listed:
   1. Select the check box next to the vulnerability.
   2. Select a dispute type from the drop-down list. The following options are available:
      * **Dispute Score**
      * **Compensating Control**
      * **False Positive**
      * **Scan Exception**
   4. In the **Notes** box, type your dispute statement. Review [PCI Scan Disputes](#dispute-statement-guidelines) for guidance when developing your dispute statement.
   5. To upload supporting files, click **ADD NEW** and locate the files to upload, or click **USE EXISTING EVIDENCE** to attach a file previously uploaded. This step is optional.
               You can address vulnerabilities in bulk. To learn how to address vulnerabilities in bulk, see [Address multiple exposures in bulk](#address-multiple-exposures-in-bulk).
3. Review your dispute content. Make sure each dispute statement is correct and complete. Once you submit a dispute, you can only add evidence that addresses the statement. You cannot edit the dispute statement.
4. After you have addressed and reviewed each vulnerability, click **SUBMIT FOR REVIEW**.
5. In the slideout panel,  enter your contact information.
6. Click **START DISPUTE**. The dispute contact will receive an email confirmation of the dispute request.

If you need assistance, call Technical Support (US: (877) 484-8383, EU: +44 (0) 203 011 5533), or email support@alertlogic.com.

After your dispute has been submitted, an  Alert Logic ASV Security Analyst reviews your dispute. When they either complete it or request further information, you will receive an email notification. To review and communicate with the ASV Security Analyst, see [Review or update a submitted dispute](#how-to-update-submitted-request).

After you submit a dispute, the statement cannot be modified. You can only add evidence that addresses the statement.

#### Prefill information from previous disputes

If you have already disputed some of your vulnerabilities, you can submit the comments from your previous dispute. An arrow icon (![](../Resources/Images/Cloud Defender/Scanning/PCIDisputePrefillArrow.png)) appears next to each of the previously disputed vulnerabilities. You can prefill these vulnerabilities individually, or you can prefill all of them at the same time. **Prefill** at the top displays the number of previously disputed vulnerabilities.

To prefill information for a single previously disputed vulnerability, click the arrow icon (![](../Resources/Images/Cloud Defender/Scanning/PCIDisputePrefillArrow.png)) next to the vulnerability. To prefill information for all previously disputed vulnerabilities, click **Prefill**.

If you manually enter comments for a previously disputed vulnerability rather than using **Prefill**, the action is reflected with both the arrow and check icons (![](../Resources/Images/Cloud Defender/Scanning/PCIDisputePrefillArrow.png),![](../Resources/Images/Cloud Defender/Scanning/PCIDisputeCheck.png)).

#### Address multiple exposures in bulk

For vulnerabilities that share the same dispute types and supporting documentation, you can address multiple exposures in bulk.

To address exposures in bulk, first select the vulnerabilities to address. There are several way to select multiple vulnerabilities. You can:

* Select all listed vulnerabilities
* Select all unhandled vulnerabilities
* Select individual vulnerabilities. To organize related vulnerabilities together, you can sort the list by clicking one of the column names: **Asset**, **Vulnerability**, **Protocol/Port**, or **Dispute Type/Commentary**.
* Click on a particular asset or protocol/port link to select all vulnerabilities related to that asset, or related to that protocol or port.

When you make your selection of multiple vulnerabilities, the **Bulk Operations** slideout panel appears, displaying the number of exposures selected. To hide the **Bulk Operations**, click **CANCEL**.

To apply bulk operations:

1. In the Bulk Operations slideout panel, select a dispute type from the drop-down list.
2. In the **Notes**, type your dispute statement. Review [PCI Scan Disputes](#dispute-statement-guidelines) for guidance when developing your dispute statement.
3. You can upload supporting files, although this step is not required. To upload supporting files, click **ADD NEW** and locate the files to upload, or click **USE EXISTING EVIDENCE** to attach a file previously uploaded.
4. Click **APPLY** to enter this information for each selected vulnerability.

### Review or update a submitted dispute

After you submit your dispute, an Alert Logic ASV Security Analyst reviews your request. After the engineer makes a decision, you will receive an email notification. At that time, you can review the dispute and add further comments.

To review or update a submitted dispute, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu, and then click the ![](../Resources/Images/dashboard/validate-icon.png)Validate menu item. Click **PCI Scan Disputes**. On the PCI Scan Disputes page, you can view existing disputes, review comments, provide updates, and communicate with the Alert Logic ASV Security Analyst.

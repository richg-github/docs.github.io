# SOC 2 Common Criteria 6.2 User Registration

The SOC 2 Audit Reports provide documentation to help demonstrate compliance with the Trust Services Criteria established  by the American Institute of Certified Public Accountants (AICPA). The SOC 2 CC6.2 User Registration report describes how to  use and access log searches   in the Alert Logic console that help demonstrate compliance with Common Criteria (CC) 6.2.

**To access the SOC 2 CC6.2 User Registration report:**

1. In the Alert Logic console, click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click **Compliance**.
3. Under **SOC 2 Audit**, click **VIEW**.
4. Click **SOC 2 CC6.2 User Registration**.

## Filter the report

To refine your findings, you can filter your report by  date range and customer account.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

The report summary page displays two columns. **Points of Focus** lists points of focus, specifically related to all engagements using the trust services criteria, that highlight important characteristics relating to CC6.2. **Available Documentation and Artifacts** describes, and contains links to, the documentation and compliance artifacts that can demonstrate compliance with each point of focus.

## Available Documentation and Artifacts

This report provides access to the Log Search page to help you demonstrate  compliance with CC6.2. This criteria requires that prior to issuing system credentials and granting system access, the entity registers and authorizes new internal and external users whose access is administered by the entity. For those users whose access is administered by the entity, user system credentials are removed when user access is no longer authorized.

## Controls Access Credentials to Protected Assets 

The Controls Access Credentials to Protected Assets point of focus requires you to demonstrate that information asset access credentials are created based on an authorization from the system's asset owner or authorized custodian.

This section  provides you with a link to the Alert Logic [Search: Log Messages](../../log-message-search.md) page, where you can search logs for message types related to creating user accounts and groups.  You can use this information  to  demonstrate that credentials are created based on authorization.

The report page includes a link to an Alert Logic Knowledge Base article that contains the recommended log search statements you can use on the Alert Logic Log Search page. You can use the log search statements  to gather the supporting documentation that illustrates compliance with CC6.2 Control Access Credentials to Protected Assets point of focus.

## Removes Access to Protected Assets When Appropriate

The Removes Access to Protected Assets When Appropriate point of focus requires you to demonstrate that processes are in place to remove credential access when an individual no longer requires such access.

This section  provides you with a link to the Alert Logic [Search: Log Messages](../../log-message-search.md) page where you can search logs for message types related to removing user accounts and groups.  You can use this information  to  demonstrate that there is a process for remove credential access.

The report page includes a link to an Alert Logic Knowledge Base article that contains the recommended log search statements you can use on the Alert Logic Log Search page. You can use the log search statements  to gather the supporting documentation that illustrates compliance with CC6.2 Removes Access to Protected Assets When Appropriate point of focus.

## Reviews Appropriateness of Access Credentials

The Reviews Appropriateness of Access Credentials point of focus requires you to demonstrate that the appropriateness of access credentials is reviewed on a periodic basis for unnecessary and inappropriate individuals with credentials.

Alert Logic does not provide data for this point of focus. You must provide the policy and procedure documents for this audit.

# Threat Risk Index Score Factors

The Threat Risk Index (TRI) is a Alert Logic vulnerability rating system designed to help you determine which of your deployments, VPCs, or networks are most exposed and susceptible to a security attack or breach.

There are five main ways the TRI score is used in the Alert Logic console:

* Per Host – A TRI score is calculated for each host, which is then used to calculate the TRI score for each VPC/network and each deployment.
* Per VPC/Network – The TRI score for the VPC/network is calculated based on the TRI score for each host within the VPC/network.
* Per Deployment – The TRI score for the deployment is calculated based on the TRI score for each host within the deployment. The deployment TRI scores are then used to create the overall score for the customer account.
* Overall Score (per customer account) – This score is calculated based on the TRI scores for each deployment within the customer account.

## Host TRI score components

A TRI score is calculated for every host. The following components are used to calculate the TRI score for a host:

* Alert Logic weighted CVSS v2 vulnerability score
* The number of external-facing vulnerabilities found in external scans
* The number of vulnerabilities with known exploit code available
* Time elapsed since the last scan on the host

Alert Logic weighs the CVSS vulnerability scores  to elevate the high and critical vulnerabilities.

### VPC/network and deployment TRI score

This score is calculated by determining the tri-mean of the host TRI scores within the VPC/network or deployment.

### Overall TRI score

This score is calculated by weighing the average of the TRI scores for all of the deployments in the customer account.

### TRI severity levels

TRI scores are assigned severity levels when referred to in the Alert Logic console. Severity levels are assigned as follows:

* Critical: TRI >= 9.0
* High: TRI >= 7.0 and < 9.0
* Medium: TRI >= 4.0 and < 7.0
* Low: TRI >= 1.0 and TRI < 4.0
* Minimal: TRI < 1.0

## TRI scores in the Alert Logic console

The TRI scores are incorporated in several pages of the Alert Logic console:

* [Threat Risk Index Summary Dashboard](#TRIDash)
* [Monthly Security Posture report](#Security)
* [TRI Summary report](#TRI)
* [Top 10 TRI Lists](#TRI2)
* [TRI Trends report](#TRI3)

### Threat Risk Index Summary Dashboard

The Threat Risk Index (TRI) Summary dashboard provides insights into the recent TRI scores of your environment, including the average TRI score and trends, vulnerabilities changes, last scanned asset changes, and TRI scores by assets. Use this dashboard to help you determine which of your deployments, VPCs, or networks are most exposed and susceptible to a security attack or breach.

To access the Threat Risk Index Summary Dashboard, in the Dashboards page, click the drop-down menu on the top left to see the list of available dashboards, and then click **TRI Summary**.

To learn more about this dashboard, see [Threat Risk Index Summary](dashboard/tri-summary.md).

### Monthly Security Posture report

The Monthly Security Posture report provides the current and historic monthly security risk and health posture of your environment, including configuration and security remediations, risk posture overviews, vulnerability assessments, and threat analysis.

To access the Monthly Security Posture report:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click   **Risk**.
3. Click **Security Posture**, and then click **Monthly Security Posture**.

To learn more about this report, see [Monthly Security Posture Report](reports/risk/monthly-security-posture.md).

### TRI Summary report

The TRI Summary report provides a summary of the recent TRI scores of your environment, including the overall TRI score and trends, score details, risk index asset distribution charts, and top ten lists.

To access the TRI Summary report:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click   **Risk**.
3. Under **Threat Risk Index**, click **VIEW**.
4. Click **TRI Summary**.

To learn more about this report, see [TRI Summary](reports/risk/tri-summary.md).

### Top 10 TRI Lists

The Top 10 TRI Lists report provides  top 10 lists of your most vulnerable hosts by TRI score, and the top 10 vulnerabilities by TRI Score.

To access the Top 10 TRI Lists report:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click   **Risk**.
3. Under **Threat Risk Index**, click **VIEW**.
4. Click **Top 10 TRI Lists**.

### TRI Trends report

The Threat Risk Index Trends report provides insights into TRI scores and trends in reducing risks, including average TRI scores, total vulnerability and host counts, internet-facing vulnerabilities, exploit availability, and last scanned age.

To access the TRI Summary report:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)), and then click ![](../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click   **Risk**.
3. Under **Threat Risk Index**, click **VIEW**.
4. Click **TRI Trends**.

To learn more about this report, see [TRI Trends Report](reports/risk/tri-trends.md).

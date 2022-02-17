# Missing Agent Digest

The Missing Agent Digest report provides insight into the daily issues related to hosts that are missing agents, including a comparison of missing agent statuses, top ten lists, and a list of hosts with missing agents.

To access Missing Agent Digest report:

1. In the Alert Logic console, click the menu icon (![](../../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click **Service**.
3. Under **Health**, click **VIEW**.
4. Click **Missing Agent Digest**.

## Filter the report

To refine your findings, filter your report by  customer account, deployment name, platform, and date.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

## Missing Agent Status section

This section provides  a color-coded donut chart with the total host count, and the counts and percentages for hosts with agents installed and for hosts with agents missing for the selected date.

![](../../../../Resources/Images/Reports/missing-agent-digest/missing-agent-status.png)

## Missing Agent Change section

This section provides the count of missing agent change for the selected date and the day before, and the percentage change between the two dates.

![](../../../../Resources/Images/Reports/missing-agent-digest/missing-agent-change.png)

## Top Impacted Deployments section

This section displays the top ten impacted deployments with the most hosts missing agents on the selected date. The section lists the customer account, deployment name, missing agent counts, and percentages of total missing agents, along with a percentage bar, for the selected date.

![](../../../../Resources/Images/Reports/missing-agent-digest/top-impacted-deployments.png)

## Platforms section

The section lists the platform, missing agent counts, and percentages of total missing agents, along with a percentage bar, for the selected date.

![](../../../../Resources/Images/Reports/missing-agent-digest/platform.png)

## List of Hosts with Missing Agent section

This list displays the hosts with the missing agents for the selected date. The list is organized by customer account, deployment name, VPC or network name, host, and status.

![](../../../../Resources/Images/Reports/missing-agent-digest/missing-agent-list.png)

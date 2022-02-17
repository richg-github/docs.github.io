# Upgrade Scans with Agent-based scanning

    This document is intended for early-access customers, and it is updated as agent-based scanning features are enhanced.     
Alert Logic is upgrading vulnerability scanning by adding OSQuery and OVAL scan components to the existing Alert Logic agent.

## Upgrades to Scanning Experience

The agent-based scan will improve the efficacy and usability of Alert Logic vulnerability scanning features:

**Credential Management**: Users of credentialed network scans had to manage credentials for assets and networks. The agent is deployed within the host itself, and does not require authentication to scan accurately.

**Network Traffic**: The amount of information being sent over the network is reduced because the agent is able to process some information directly.

**Network and Host Impact**: Authenticated and unauthenticated network scans have adverse impacts on some networks and hosts. The agent-based scan has less impact on networks and hosts.

**Asset-Target Availability**: The agent can be deployed on assets that are impossible or impractical to network scan.

**Vulnerability Accuracy**: The agent-based scan dramatically increases the fidelity accuracy of vulnerability scan results. The agent is able to assess false positives. The agent also provides better OS, application, patch, and kernel level vulnerability assessment. For more information, see [Scan-based Vulnerability assessment technical details](#Scan-bas).

## Beta Details

In order to provide Alert Logic with the best information possible for general release,  the full authenticated network scan, unauthenticated network scan, and agent-based scan will all run during a scan schedule. This will result in slightly increased network traffic and host impact instead of a reduction. Since the authenticated network scan will still be in use, credentials will still need to be managed.

## Prerequisites

A host must meet the following criteria to be scanned by an agent.

### Node subscription level

The host node must have a professional or enterprise subscription. You can verify or change the subscription levels using [Change Protection Level of an Asset](../deploy/change-protection.md) or [Entitlement Summary](../analyze/reports/service/entitlement/entitlement-summary.md).

### Host Operating System

The host must be Windows or Linux. The scanning components of the agent will not work in an agent container configuration.

| Alert Logic agent Operating System | Installation Guide | Agent-based Scan Support |
|---|---|---|
| Windows | [Install the Alert Logic Agent for Windows](../prepare/alert-logic-agent-windows.md) | Yes |
| Linux | [Install the Alert Logic Agent for Linux](../prepare/alert-logic-agent-linux.md) | Yes |
| Container | [Install the Alert Logic Agent Container](../prepare/alert-logic-agent-container.md) | No |

### Agent Health

The health status of the agent will affect agent-based scanning. You can verify the health status of agents from the [Health Console](../analyze/health.md) and the [Missing Agent Digest](../analyze/reports/service/health/missing-agent-digest.md) report.

## Scan using Alert Logic agents

Any successful scan of a host that meets the [Prerequisites](#Prerequisites) will automatically recognize and trigger the agent-based scan for that host. You can complete an agent-based scan on an asset using two methods:

**Scan Schedule Scope**: Complete a scheduled scan with the host that you would like the agent to scan in scope. For more information on asset scopes in scan schedules, see [Define the scope of the assets to scan](../analyze/manage-scans-and-results/schedules.md#Definethescopeoftheassetstoscan).

**Successful use example**: A scan schedule has 30 assets in scope. 18 have Professional subscriptions. 10 of those 18 have correctly configured agents. The agent-based scan will automatically trigger for the 10 assets that meet the prerequisites. The network scan will  run for all 30 scoped assets.
**Scan Now**: You can use the **Scan Now** feature from the Topology page of the Alert Logic console to scan individual hosts as soon as possible. For more information on the **Scan Now** feature, see [Scan Now](../analyze/topology.md#ScanNow).

**Successful use example**:  From the Topology page, you click the host you want to scan. In the side panel, you navigate to the actions tab, and then click **Scan Now**. If the host meets the prerequisites, then the scan will automatically trigger the agent-based scan in addition to the network scan and update results for that host as soon as possible.## Scan-based Vulnerability assessment technical details

| Asset Enumeration - Inferred Vulnerabilities | Host-based Agent (Osquery) | Network Scan (Unauthenticated) | Network Scan (Authenticated) |
|---|---|---|---|
| System-level vulnerabilities (kernal - Windows OS) | Yes | No | Yes |
| Application-level exposures (RHEL) | Yes | No | Yes |
| Application-level exposures (Debian) | Yes | No | Yes |
| Application-level exposures (Windows Programs) | Partial | No | Partial |

| Active Assessment - Deterministic | Host-based Agent (OVAL) | Network Scan (Unauthenticated) | Network Scan (Authenticated) |
|---|---|---|---|
| System-level vulnerabilities (kernal - Windows OS) | Yes | Partial | Yes |
| Application-level exposures (RHEL) | Yes |  | Yes |
| Application-level exposures (Debian) | Yes |  | Yes |
| Application-level exposures (Windows Programs) | Yes |  | Yes |
| Configuration Check (TLS/Certificates, Common U/P) | No | Yes | Yes |
| Web Application Testing | No | Partial | Partial |
| Active Exploits/ SQL Injections/ Etc | No | Partial | Partial |

### Comparison of Vulnerability Assessment Results

This section is a placeholder for a technical description of before and after results from unauth network scan or credentialed network scan to the agent-based scan addition, with some explanation.

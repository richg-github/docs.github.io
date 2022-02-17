# Manage Endpoints

All your endpoints are listed on the **Endpoints** page. To access the page, click the ![](../../Resources/Images/dashboard/configure-icon.png)**Configure** menu item, click **Endpoints**, and then click the **Endpoints** tab. The list includes all active endpoints, archived endpoints, and endpoints that had the agent uninstalled.

## Add endpoints

Click the **ADD ENDPOINTS** button to download the Alert Logic Extended Endpoint Protection installer. Follow the instructions here to install: [Deploy Alert Logic Extended Endpoint Protection](../../deploy/endpoint-installer.md)

## Sort and filter endpoints

Extended Endpoint Protection has several built-in ways to sort and filter your endpoints.

To sort endpoints, click the heading of the column you want to sort.

To filter endpoints, browse to the **Endpoints** page in the Alert Logic console, and then click the options on the left.

| Filter option | Endpoints |
|---|---|
| **All Endpoints** | This is the default view. It shows every endpoint that is not archived. |
| **Servers** | Endpoints that are running server operating systems. These endpoints also appear under **All Endpoints**, with the Server icon to the left of the machine name. |
| **Archived** | Endpoints that you have archived. These endpoints are not billable, do not show up in the default **All Endpoints** filter or any other filter, and are not counted towards totals on the **Status** page. |
| **Protection off** | Endpoints that are not archived and have protection turned off. They appear in red in the list. To turn on protection, click the endpoint, click **Protection**, and then click **Turn on**. |
| **Protection on** | Endpoints that are not archived that have protection turned on. To turn off protection, click the endpoint, click **Protection**, and then click **Turn off**. |
| **Errors** | Endpoints that require remediation in order to activate Extended Endpoint Protection. In most cases, restarting the service on the endpoint or rebooting the machine resolves the error. |
| **Up-to-date** | Endpoints that are on the latest version of the agent. Alert Logic upgrades the agent over the cloud automatically. |
| **Out-of-date** | Endpoints that are awaiting upgrade to the latest version of the agent. They are still protected, but they either have not checked in to Extended Endpoint Protection since the upgrade became available, or they have checked in, but are queued behind other endpoints to download the latest version. |
| **VT mode off** |  |
| **VT mode on** |  |
| **Offline** | These endpoints are offline and not communicating with Alert Logic. Protection is still active on these endpoints, but you cannot view them in realtime until they are online again. |

## Endpoint list

After you filter the list to your desired view, you have several actions available.

Use the search bar to search in the list of endpoints.

Click **Export CSV** to export a list of either the current filtered view or the full list of endpoints.

Click the check box to select one or more endpoints in the list. Several options appear at the top of the page:

* **Protection**: Turn protection on or off for the selected endpoint(s).
* **Tags**: Add or remove tags from the selected endpoint(s).
* **Isolation**: View and change isolation status of the selected endpoint(s).
* **Archive**: Archive or unarchive the selected endpoint(s).

## Protection on devices

If protection was on when an endpoint last checked in, Alert Logic continues to protect the endpoint, even if the endpoint never checks in again.Endpoints that display inactive have not checked into the portal for more than 30 days and are not billed. Because the Extended Endpoint Protection agent is still installed on the endpoint, it will continue to block attacks (though it cannot upgrade and cannot report those attacks to the portal). When the endpoint checks back in, the endpoint will automatically display active and become billable again.

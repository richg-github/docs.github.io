# Geo IP Blocking

Alert Logic provides Geo IP blocking to restrict access to your website from certain regions based on the geographic location of the incoming request. The Alert Logic Managed Web Application Firewall (WAF) product checks incoming IP addresses against a blacklist or whitelist account, and determines whether to approve or deny access to the request. You can configure which countries you want WAF to block.

**To access the Geo IP blocking option**:

1. In the Alert Logic console, click **CONFIGURATION**, and then click WAF.
2. In the left navigation pane, click **Appliances**.
3. In the item row of your appliance, click **Manage Appliance**.
4. In the left navigation pane, under **Services**, click **Websites**.
5. Select the website you want to view.
6. Under WAF, click **Policy**.
7. Click **Source IP tracking and access control** to expand the section.
8. Under Geo location IP access control, select **Enable GeoIP access control**.
9. Select the country you want to either blacklist or whitelist. You can also select more than one country.

Single-clicking  will deselect all other countries if you previously had other countries selected. You must select the countries you previously had selected again, and any new ones you want to add. To select more than one country, click and hold the control key on your keyboard as you click to select countries.11. Select **Whitelist** or **Blacklist**.
12. In the lower right corner of the page, click **Save**.
13. At the top of the page, click **Apply Settings**.

To ensure the Geo IP database in Alert Logic Managed Web Application Firewall (WAF) is up to date, refer to [https://www.maxmind.com/en/geoip-demo](https://www.maxmind.com/en/geoip-demo) regularly.

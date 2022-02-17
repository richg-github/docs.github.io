# Proxy Protocol

Alert Logic allows you to enable proxy protocol, which is designed to safely transport connection information without losing any information. Enabling proxy protocol allows Alert Logic Managed Web Application Firewall (WAF) to work with multiple layers of NAT or TCP proxy protocols, does not require infrastructure changes, has no impact on NAT firewalls, and is scalable.

Enabling proxy protocol on the WAF is not necessary unless you are configuring both communicating endpoints. If you have configured the other communicating endpoint to proxy protocol, you can enable proxy protocol in the WAF.

You must configure proxy protocol on both endpoints of the connection. If one endpoint connection is not configured to use proxy protocol, the websites stop communicating, and WAF will not function properly.

**To access the Proxy Protocol option**:

1. In the Alert Logic console, click **CONFIGURATION**, and then click WAF.
2. In the left navigation pane, click **Appliances**.
3. In the item row of your appliance, click **Manage Appliance**.
4. In the left navigation pane, under **Services**, click **Websites**.
5. Select the website you want to view.
6. Under ADC, click **Virtual Host**.
7. Under Client Source IP, select **Enable proxy protocol**.
8. Click **Save Settings** in the lower right corner of the page.
9. Click **Apply Settings** at the top of the page.

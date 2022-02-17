# Blocking Configuration

Blocking Configuration is a Network IDS configuration that allows you to set up blocks to prevent attackers from accessing your network. This functionality requires a physical appliance.

To access Blocking Configuration, click **CONFIGURATION** and **Network IDS**. Blocking Configuration appears in the left navigation area.

## Items to configure before you set up automated blocking policies

Automated blocking policies require the following configurations.

Complete these configuration items in the order provided.

### Select a zone

Before you set up blocking policies, you must determine and select the zone(s) in which you want to use the blocking functions. The default behavior of Threat Manager is to apply the blocking settings to all zones. If you do not want to apply blocking settings to all zones, you can select a specific zone.

Before you can select which zone(s) to use, you must first create the zones.

**To set Threat Manager to use blocking features in specific zones:**

1. Access the Blocking Configuration page.
2. Under **Apply these settings to**, click **Edit**.
3. In the **Select zone** drop-down menu, select the zone on which you want to use blocking features, and then click **Select**.

### Set up a whitelist

A whitelist is an approved list of IP addresses allowed to communicate with hosts protected by Threat Manager. Using a whitelist as part of your defense strategy makes it harder for threats to infiltrate your network and remain there.

Whitelist all important infrastructure devices before configuring an automatic blocking policy. Failure to do so may result in unwanted downtime of these systems or unintentional Denial of Service.

To add a whitelist:

1. Access the Blocking Configuration page.
2. Select the **Whitelist** tab, and then click **Add Host**.
3. In the appropriate fields, type your information as follows:
   * **To add a single host***, *in the **IPv4/IPv6 Address** and **Netmask/Prefix** boxes, enter the appropriate information.
   * **To add multiple hosts**, in the **Add Multiple Hosts** box, enter the IP addresses, separated by commas. A range of hosts can be specified using slash notation, for example, 192.168.1.0/24.

### Add a firewall and associated credentials

After you have selected which zones you want to use blocking functions on, you need to set up and test the communications between Threat Manager and the firewall. This is accomplished by adding a firewall and associated credentials.

**To add a firewall and associated credentials:**

1. Access the Blocking Configuration page.
2. Select the **Configuration** tab.
3. Under **Add a Blocking Firewall**, enter and select the appropriate credentials, and then click **Save**.
   * **Appliance**—Select the Threat Manager appliance connected to the firewall where you want the rule implemented.
   * **Name**—Enter a name to help identify the firewall or rule you want to add (Example: *ASA-01-port8080*).
   * **Firewall and Connection Type**—Choose the firewall and connection type used by your firewall. The fields displayed in the Alert Logic console vary depending on the firewall type selected. Enter the appropriate information in the fields displayed.
      * **IPv4/IPv6 Address**—Enter the IPv4 or IPv6 address of the firewall where you want to implement the blocking configuration rule.
      * **Username**—Enter a user name to have access to the firewall where you want to implement the blocking configuration rule.
      * **Password/Confirm Password**—Enter a password to be associated with the user name you selected.
      * **IPv4/IPv6 Group Name**—If applicable, enter the IPv4/IPv6 group name.
      * **Group Name**—If applicable, enter the group name.
      * **Enable Password/Confirm Enable Password**—Use this password for privileged mode access.
      * **Port**—Specify the port to be used to connect to the firewall.

### Test the firewall configuration

After saving your firewall and associated credentials, test the configuration.

**To test the firewall configuration:**

Next to the firewall configuration you set up, click **test credentials**. A successful test displays "Success" in the **Credential Test** column of the firewall you tested.

If the credential test remains in progress and does not end, remove the firewall test entry and contact Alert Logic at (US: (877) 484-8383, EU: +44 (0) 203 011 5533).

## Define an automatic blocking policy

You can define your blocking policies to provide automated protection and response for detected threats. Blocking policy rules can be based off signatures of detected threats, incident classes, or both.

You can use either signature-based blocking or incident class blocking, but in general, Alert Logic recommends you use both. A combination of reactionary signature-based blocking and incident class prevention blocking ensures you cover any gaps in your security process.

In addition to automated blocking, Threat Manager customers can manually block specified incidents and events.

### Reasons to use signature-based blocking

If you have specific technologies or concerns that you want to actively protect against, you can use signature-based blocking. Signature-based blocking employs a targeted approach and benefits you by making your product more efficient.

This approach, however, is difficult to manage due to the manual process of signature selection. Also, signature-based blocking does not provide any defensive protection against unforeseen threats.

You receive an alert from Alert Logic stating you have a Trojan outbreak of netsky. You log into the portal and add each of the roughly 15 individual specific netsky-related signatures.

### Reasons to use incident class blocking

Incident classes are logical groupings of all the signatures in the product. If you want to block an entire set of signatures, you would use incident class blocking. This approach employs a broader coverage, which is easier to manage and enables you to potentially keep a wider range of exploits/compromises from occurring on the network.

This approach could lead you to block legitimate traffic, though doing so can be mitigated by whitelisting IP addresses you do not want to block.

### Define blocking policies

Before you define your blocking policies, there are a few things you must do. If you have not selected a zone, added a firewall and associated credentials, or tested the firewall configuration, please complete these steps before continuing.

Please whitelist all important infrastructure devices before configuring an automatic blocking policy. Failure to do so may result in unwanted downtime of these systems or unintentional denial of service.

**To define your blocking policies:**

1. Access the Blocking Configuration page.
2. Select the **Policies** tab, select the appropriate policy values, and then click **Configure**.
   * **To set signature-based blocking**, in the **Available Signatures** drop-down menu, select a classification, select one or more signatures, and then click **Add**.
   * **To set incident class blocking**, in **Available Incident Classes**, select the appropriate check boxes.
4. Under **Configure Settings**, in the **Signature **and** Incident Class** areas, specify how you want blocking to occur, then click **Save**.
   * You can block the **Source**, **Destination**, or **Both**.
   * A **Severity** rating of 0 (the default) instantly blocks the source and/or destination. A **Severity** rating other than 0 will cause the event to be rated before blocking occurs.
   * The block will stay in place for the amount of time entered in the **Duration** field.

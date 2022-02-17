# Network

The Service Network page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Services, see [Global](ref_services_http_global.md). To go to  the documentation for next section in the  manual, see [Application Delivery Controller (ADC)](ch_adc.md).

To manage website security profiles, under Services  on the left panel, click **Network**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

Alert Logic Managed Web Application Firewall (WAF) can block hostile IP addresses at the network level. Addresses can be learned and automatically blocked in four ways:

* **DoS Mitigation**: If DoS Mitigation is enabled, source IPs exceeding configurable request limits are automatically blocked for a configurable number of seconds (i.e. 86400 - 24 hours).
* **Attack source auto blocking**: If Attack source auto blocking is enabled, source IPs are tracked across all website deny logs. If a number requests above a certain risk level are recorded within a certain time span, the source IP is automatically blocked for a configurable number of seconds.
* **Immediate source blocking**: Each website can be configured to immediately block a source IP if a log event above a certain risk level is recorded.
* **Manual entry**: IP addresses can be added manually to the list of blocked source IPs.

Only traffic to inbound interfaces is blocked. Management interfaces are not blocked unless the management role has been bound to an interface which is also responding to inbound requests - typically the interface facing the Internet.

Blocking a source IP does not keep a determined attacker from accessing your website. Positive filtering at the application level, which is the core functionality of WAF, is more effective at stopping unauthorized intrusion attempts. This forces the attacker to change IP every time he triggers an attack signature  especially if immediate source blocking is enabled.

Settings like blacklisting and DoS mitigation controls that work on the client IP are only effective when WAF is terminating the original request as received from the Internet. These settings must not be enabled when WAF is deployed behind a Layer 7 device which hides the client IP at the network layer.

### Blacklisted Source IPs

The table shows which source IPs are currently blocked.

<colgroup></colgroup>| **              Source IP            ** | Source IP |
| **              Violation            ** | The reason for / type of blocking can be:<dl><dt>                DoS              </dt><dd>The source IP has triggered the DoS mitigation by issuing too many requests within a too short time span.</dd><dt>                Policy              </dt><dd>The source IP has either triggered the general attack source auto blocking or a website specific block-IP policy.</dd><dt>                Permanent              </dt><dd>The source IP has been added to the list manually.</dd></dl> |
| **              Del            ** Button | Remove IP from the list. |
| **Add Blocked IP** Input field |  |

### Network blocking bypass

The table shows IP addresses which are allowed to bypass network protection like blacklisting and DoS mitigation controls.

<colgroup></colgroup>| **                Trusted Client Source IP              ** | The IP address which will bypass network controls. |
| **                In packets              ** | Number of incoming packets from the source IP |
| **                In bytes              ** | Number of incoming bytes from the source IP |
| **                Out packets              ** | Number of outgoing packets to the source IP |
| **                Out bytes              ** | Number of outgoing bytes to the source IP |

#### Allowing  IPs to bypass network controls

The network blocking bypass whitelist is compiled of:

* website Trusted Client IPs
* website trusted proxy IPs,
* the default gateway IP

<colgroup></colgroup>| **                Allow website Trusted Client IPs to bypass network protection              ** Check box | Enable / disable network blocking bypass for trusted clients. Default: `<disabled>` |
| **                Allow trusted proxy IPs to bypass network protection              ** Check box | Enable / disable network blocking bypass for trusted proxies. Default: `<disabled>` |
| **                Allow gateway IP to bypass network protection              ** Check box | Enable / disable network blocking bypass for the default gateway. Note that this will not allow requests passing through the default gateway but only requests with the default gateway as source. Default: `<enabled>` |

#####       Website Trusted Client lists    

You can manage Trusted Client IP addresses in the Website global policy section of the Policy page.

**To manage Trusted Client IP addresses**:

1. In the left panel, under Services, click **Websites** to go to the Website page, and then click on the website for which you want to manage.
2. Under WAF, click **Policy**, and scroll down to the Website global policy section.
3. On the right of the Website global policy section, next to Display, ensure the drop-down option is on **Advance**.
4. Click **+ Trusted clients - IP whitelisting** to expand the options in this feature.
5. In the Whitelist box, enter or remove any IP addresses with net mask (IP/mask) in CIDR notation separated by newline.
6. Select the **Enable IP network blocking bypass for trusted client** check box.

You must also enable network blocking bypass for trusted clients. Select the **Allow website Trusted Client IPs to bypass network protection** check box.

#####       Website trusted proxies    

You can add trusted proxies in the Client Source IP section of the Virtual host page.

**To add trusted proxies**:

1. From Websites page, click on the website you want to manage.
2. Under ADC, click **Virtual host**, and scroll to the Client Source IP Section.
3. Under the Trusted Proxy, select **Use trusted proxy - extract client source IP from X-Forwarded-For header**.
4. In the List of trusted proxies, enter or remove IP addresses with net mask (IP/mask) in CIDR notation separated by newline.

You must also enable network blocking bypass for trusted proxies. Select the **Allow trusted proxy IPs to bypass network protection** check box.

##### The default gateway

The default gateway is enabled by default.

This feature is only available on Alert Logic Managed Web Application Firewall (WAF) licenses.

### DoS mitigation

When enabled the DoS mitigation system tracks source IP connections to inbound interfaces. If an IP exceeds the configurable limits it is added to the list of blocked IPs and further connection attempts are silently dropped at the network level.

<colgroup></colgroup>| **                Enable DoS mitigation              ** Check box | Enable / disable DoS mitigation. Default: `<disabled>` |
| **                Max src conn rate              ** Two input fields: number and seconds. | Limit the rate of new connections to a certain amount per time interval.<dl><dt>                  Valid input                </dt><dd>Both fields take an integer as valid input.</dd><dt>                  Input example                </dt><dd>50 / 5 - 50 connections in 5 seconds</dd><dt>                  Default value                </dt><dd>`&amp;amp;lt;60 / 10&amp;amp;gt;`</dd></dl> |
| **                Blacklist IPs for              ** | How long time IPs should be blacklisted in seconds.<dl><dt>                  Valid input                </dt><dd>An integer</dd><dt>                  Input example                </dt><dd>``&amp;amp;lt;36000&amp;amp;gt;`` - 10 hours</dd><dt>                  Default value                </dt><dd>`&amp;amp;lt;86400&amp;amp;gt;` - 24 hours</dd></dl> IPs are automatically removed from the list when the blacklist period has ended. |

### Attack source auto blocking

Attack source auto blocking tracks denied source IPs at the application level and blocks an IP at the network level if they reach configurable limits.

<colgroup></colgroup>| **              Enable Attack Source Auto Blocking            ** Check box | Enable / disable Enable Attack Source Auto Blocking. Default: `<disabled>` |
| **              Attack threshold            ** Input field | Sets the maximum number of denied requests across all websites within a certain time frame (below). Only websites with source tracking enabled contribute to the attack threshold number and for each website a risk threshold is configured above which denied requests are added to this global counter.<dl><dt>                Valid input              </dt><dd>Any integer</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;5&amp;amp;gt;`</dd></dl> |
| **              Time threshold            ** Input field | Sets the time frame within `attack threshold` (above) is accepted.<dl><dt>                Valid input              </dt><dd>Any integer</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;86400&amp;amp;gt;`</dd></dl> |
| **              Blacklist IPs for            ** | How long time IPs trigging the Attack source Auto blocking should be blacklisted in seconds.<dl><dt>                Valid input              </dt><dd>An integer</dd><dt>                Input example              </dt><dd>`&amp;amp;lt;86400&amp;amp;gt;` - 24 hours</dd><dt>                Default value              </dt><dd>`&amp;amp;lt;604800&amp;amp;gt;` - 1 week</dd></dl> IPs are automatically removed from the list when the blacklist period has ended. |

### Network routing

In some network deployments, you may want to have WAF perform routing functions by forwarding IP packets not destined for its own IP addresses. This allows these packets to pass between its interfaces. You must enable IP forwarding as a prerequisite when websites are deployed in `routing proxy` mode.

A segmentation matrix allows for configuring policy rules for forwarding IP packets between network interfaces.

<colgroup></colgroup>| **                Enable IP forwarding              ** Check box | Enable / disable IP forwarding. You must enable IP forwarding when websites are deployed in routing proxy mode. Default: `<disabled>` |
| **                Enforce network segmentation when routing              ** Check box | Enable / disable network segmentation. When enabled, network segmentation rules as specified in the segmentation policy matrix are enforced. Segmentation has no effect unless IP forwarding is enabled. Default: `<enabled>` |
| **                Network segmentation              ** | The network segmentation matrix defines policy rules for traffic to travel across the WAF network interfaces. Policy rules are defined as *allow from* interfaces in the leftmost column *to* interfaces in the upper horizontal row. The segmentation matrix only shows physical interfaces. Cluster (VRRP) interfaces and virtual IP addresses inherit the policy rules applying to the physical interfaces to which they are bound.<dl><dt>                  Example                </dt><dd>If a system has the interfaces em0, em1 and em2, to allow packets to travel from em0 to em1 check the cell em0,em1.</dd><dt>                  Default value                </dt><dd>Traffic is not allowed to travel across interfaces.</dd></dl> |

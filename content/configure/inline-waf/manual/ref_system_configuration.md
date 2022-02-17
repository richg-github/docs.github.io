# Configuration

The System Configuration page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of System, see [Clustering](ref_system_clustering.md). To go to  the documentation for next subsection in the System section, see [Information](ref_system_information.md).

To access the Configuration page in the **WAF** management interface, on the left panel, under System, click **Configuration**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

### Network

Basic network configuration is performed in this section. Any changes made to this section are applied and saved by clicking on the Save" button.

<colgroup></colgroup>| **              Hostname            ** Input field | Domain name of the Web Security Manager Alert Logic Managed Web Application Firewall (WAF).<dl><dt>                Valid input              </dt><dd>Fully qualified domain name.</dd><dt>                Input example              </dt><dd>`proxy.mydomain.com`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **              Default gateway            ** Input field | IP address of the default gateway.<dl><dt>                Valid input              </dt><dd>IP address assigned must be in the same network subnet as the IP address of one of the physical network interfaces.</dd><dt>                Input example              </dt><dd>`192.168.0.1`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **              DNS server(s)            ** Input field | IP address of one or more DNS servers.<dl><dt>                Valid input              </dt><dd>IP addresses
Use space to separate multiple hosts (only one required).</dd><dt>                Input example              </dt><dd>`192.168.0.2`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **              SMTP server            ** Input field | SMTP server hostname or IP address. SMTP server is used for sending alert e-mails to the contact e-mail address specified.<dl><dt>                Valid input              </dt><dd>IP address or fully qualified domain name</dd><dt>                Input example              </dt><dd>`smtp.mydomain.com`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **              Syslog server            ** Input field | External syslog server hostname or IP address. Proxies with external syslog alert enabled will send syslog alerts to the specified server. Syslog messages are sent to `user` facility and `informational level` (criticality) is configurable for each proxy.<dl><dt>                Valid input              </dt><dd>IP address or fully qualified domain name</dd><dt>                Input example              </dt><dd>`syslog.mydomain.com`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |

### Static routes

Define static routes.

Click **Add new route** and enter route information for each route you want to add.

When routes are entered click **Save settings** in lower button bar to save.

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              Destination            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>The route destination.</p>
        <p>Enter first IP address of destination network.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A valid ip address.</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <ol>
              <li>
                <p>
                  <code>192.168.5.0</code>
                </p>
              </li>
              <li>
                <p>
                  <code>192.168.6.8</code>
                </p>
              </li>
              <li>
                <p>
                  <code>192.168.7.10</code>
                </p>
              </li>
            </ol>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>None</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Subnet            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>Network mask of the destination IP address.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>A valid network mask</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <ol>
              <li>
                <p>
                  <code>255.255.255.0</code>
                </p>
              </li>
              <li>
                <p>
                  <code>255.255.255.248</code>
                </p>
              </li>
              <li>
                <p>
                  <code>255.255.255.255</code>
                </p>
              </li>
            </ol>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>None</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Gateway            </b>
        <p>Input field</p>
      </td>
      <td>
        <p>IP address of the gateway through which the destination can be reached.</p>
        <dl>
          <dt>                Valid input              </dt>
          <dd>
            <p>An IP address of a gateway which is directly reachable by the Web Security Manager node.</p>
          </dd>
          <dt>                Input example              </dt>
          <dd>
            <ol>
              <li>
                <p>
                  <code>192.168.0.4</code>
                </p>
              </li>
              <li>
                <p>
                  <code>192.168.0.5</code>
                </p>
              </li>
              <li>
                <p>
                  <code>192.168.0.6</code>
                </p>
              </li>
            </ol>
          </dd>
          <dt>                Default value              </dt>
          <dd>
            <p>
              <code>None</code>
            </p>
          </dd>
        </dl>
      </td>
    </tr>
  </tbody>
</table>
The examples above would result in:

1. Access to IP addresses `192.168.5.0-255` (`192.168.5.0/24`) is routed through the gateway `192.168.0.4`.
2. Access to IP addresses `192.168.6.8-16` (`192.168.6.8/29`) is routed through the gateway `192.168.0.5`.
3. Access to IP address `192.168.7.10` (`192.168.7.10/32`) is routed through the gateway `192.168.0.6`.

### Syslog - logging to external host

[Mapping of Web Security Manager System Logs to Syslog facilities](#ref_system_configuration_syslog_mapping)

Configure threshold level and address of external Syslog server.

<colgroup></colgroup>| **              Syslog server            ** Input field | External syslog server hostname or IP address. Proxies with external syslog alert enabled will send syslog alerts to the specified server. Syslog messages are sent to `user` facility and `informational level` (criticality) is configurable for each proxy.<dl><dt>                Valid input              </dt><dd>IP address or fully qualified domain name</dd><dt>                Input example              </dt><dd>`syslog.mydomain.com`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |

#### Mapping of Web Security Manager System Logs to Syslog facilities

<colgroup></colgroup>| **                Attack              ** | `Local3` |
| **                Audit              ** | `auth` |
| **                Proxy              ** | `Local0` |
| **                Learner              ** | `Local4` |
| **                Backup              ** | `Local5` |
| **                WebGUI              ** | `Local2` |
| **                Daemon              ** | `Local1` |
| **                Syslog              ** | Other facilities |
| **                Error              ** | All facilities with informational level `error` and above |

See [Logs](ref_system_logs.md#ref_system_logs.md) for a description of the log mentioned above.

### Date and Time

This section is used for configuration of time synchronization via NTP (Network Time Protocol).

It is strongly advised to configure an NTP server in order to have the correct date and time set on the system.

It is recommended to configure an internal NTP interface. If one is not available, a well-known NTP server time.nist.gov can be used. Also, have a look at [www.ntpd.org](http://www.ntpd.org/) for a more detailed list of NTP servers available for free on the Internet.

<colgroup></colgroup>| **              NTP server            ** Input field | IP address or hostname of an NTP server. Remember to set up at least one DNS server if you enter a hostname here.<dl><dt>                Valid input              </dt><dd>IP address or fully qualified domain name.
Use space to separate multiple hosts (only one required).</dd><dt>                Input example              </dt><dd>`time.nist.gov`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **              Timezone            ** Drop down list | Timezone information. Select the systems timezone from the drop down menu.<dl><dt>                Valid input              </dt><dd>A timezone option from the drop down list.</dd><dt>                Default value              </dt><dd>`Europe/Copenhagen`</dd></dl> |
| **              Date format            ** Drop down list | Display dates in logs and reports in Month-Day-Year or Day-Month-Year format. Select the date format from the drop down menu.<dl><dt>                Valid input              </dt><dd>An option from the drop down list.</dd><dt>                Default value              </dt><dd>`Month-Day-Year`</dd></dl> |

### Logging to external host

### SNMP

Configure threshold level and address of external Syslog server.

<colgroup></colgroup>| **              Enable SNMP queries            ** Check box | Enable or disable SNMP daemon. If checked, Web Security Manager will accept SNMP queries on the first of the IP addresses to which management is bound. |
| **              Public community            ** Input field | Public community password. The read-only community password.<dl><dt>                Valid input              </dt><dd>Any string</dd><dt>                Input example              </dt><dd>`wdbhhaiedb`</dd><dt>                Default value              </dt><dd>`public`</dd></dl> |
| **              System location            ** Input field | Information about the system.<dl><dt>                Valid input              </dt><dd>Any string</dd><dt>                Input example              </dt><dd>`Facility 1, Server room 1`</dd><dt>                Default value              </dt><dd>`none`</dd></dl> |
| **              Listening on            ** Read only | If SNMP is enabled will display the IP address the SNMP daemon is listening on. |

### Admin contact

Update notifications, attack alerts and system errors can be sent by email to the admin contact email address.

<colgroup></colgroup>| **              Contact            ** Input field | E-mail address of the administrative contact. All alert e-mails and notifications are sent to this address. You need to define an SMTP server before any e-mails are sent.<dl><dt>                Valid input              </dt><dd>E-mail address</dd><dt>                Input example              </dt><dd>`admin@mydomain.com`</dd><dt>                Default value              </dt><dd>`admin@mydomain.com`</dd></dl> |
| **              Sender domain            ** Input field | The e-mail address domain. If not configured it will be extracted from the contact e-mail.<dl><dt>                Valid input              </dt><dd>a valid domain</dd><dt>                Input example              </dt><dd>`mydomain.com`</dd><dt>                Default value              </dt><dd>`extracted from contact`</dd></dl> |

### Email system alerts

Critical events or conditions are logged both locally and to external syslog server (if enabled). However if an external syslog server is not available (or is not monitored) a subset of (potentially) critical alerts can be sent to the designated admin contact email.

<colgroup></colgroup>| **              Email system error messages to admin contact             ** Check box | Enable or disable sending of error messages altogether. If checked, selected alert types will be sent. |
| **              Disk and memory            ** Check box | If checked, disk and memory related errors at log level ERROR and CRITICAL will be sent. |
| **              Cluster interface events             ** Check box | If checked, cluster interface related errors at log level ERROR and CRITICAL will be sent. The most common cluster interface event is STATE TRANSITION which, when sent by the worker node in a cluster, indicates that the master node is either down (backup > master) or has resumed operation (master > backup). When the nodes in a cluster are powered on/off or rebooted state transition messages are also logged to the syslog error log and may generate email alerts. |
| **              Administrative daemons             ** Check box | If checked, any error at log level ERROR and CRITICAL from administrative daemons will be sent. |

### Forward HTTP proxy

Configure forward proxy to be used by the update system when connecting to the update server.

<colgroup></colgroup>| **              Use proxy for outbound HTTP            ** Check box | Enable or disable the configured forward proxy. |
| **              Proxy address            ** Input field | The address of the forward proxy<dl><dt>                Valid input              </dt><dd>A valid ip address.</dd><dt>                Input example              </dt><dd>`10.10.10.5`</dd><dt>                Default value              </dt><dd>`None`</dd></dl> |
| **              Proxy port            ** Input field | Proxy port number<dl><dt>                Valid input              </dt><dd>An TCP/IP port number</dd><dt>                Input example              </dt><dd>`8080`</dd><dt>                Default value              </dt><dd>`none`</dd></dl> |
| **              Forward proxy authentication required            ** Check box | Enable if forward proxy requires authentication. |
| **              Username            ** Input field | User name used for authenticating to the Proxy.<dl><dt>                Valid input              </dt><dd>A valid username</dd><dt>                Input example              </dt><dd>`wsm1`</dd><dt>                Default value              </dt><dd>`none`</dd></dl> |
| **              password            ** Input field | Password to authenticate the proxy user. |

### Backup configuration

This section is used to configure an FTP/SCP server used for automated configuration backup/restore of Web Security Manager configuration.

#### FTP configuration

<colgroup></colgroup>| **                FTP server              ** Input field | FTP hostname or IP address.<dl><dt>                  Valid input                </dt><dd>IP address or fully qualified domain name</dd><dt>                  Input example                </dt><dd>`ftp.mydomain.com`</dd><dt>                  Default value                </dt><dd>`None`</dd></dl> |
| **                FTP port              ** Input field | FTP server port number<dl><dt>                  Valid input                </dt><dd>An TCP/IP port number</dd><dt>                  Input example                </dt><dd>`21`</dd><dt>                  Default value                </dt><dd>`21`</dd></dl> |
| **                Login              ** Input field | Username used for login. FTP account used must be able to store files on the remote FTP server.<dl><dt>                  Valid input                </dt><dd>A valid username</dd><dt>                  Input example                </dt><dd>`wsm_backup`</dd><dt>                  Default value                </dt><dd>`none`</dd></dl> |
| **                Password              ** Input field | Password used for SCP login.<dl><dt>                  Valid input                </dt><dd>Any string.
A long password is recommended as it do not have to be memorable by humans.</dd><dt>                  Input example                </dt><dd>`s984ROf.dds&amp;amp;amp;fdsfs)afa8343287`</dd><dt>                  Default value                </dt><dd>`none`</dd></dl> |
| **                Remote directory              ** Input field | Full path to directory on FTP server used for storing Web Security Manager related files.<dl><dt>                  Valid input                </dt><dd>A directory path ending with /</dd><dt>                  Input example                </dt><dd>`/ftp/wsm/`</dd><dt>                  Default value                </dt><dd>`none`</dd></dl> |

#### SCP configuration

<colgroup></colgroup>| **                SCP server              ** Input field | SCP hostname or IP address.<dl><dt>                  Valid input                </dt><dd>IP address or fully qualified domain name</dd><dt>                  Input example                </dt><dd>`ftp.mydomain.com`</dd><dt>                  Default value                </dt><dd>`None`</dd></dl> |
| **                SCP port              ** Input field | SCP server port number<dl><dt>                  Valid input                </dt><dd>An TCP/IP port number</dd><dt>                  Input example                </dt><dd>`21`</dd><dt>                  Default value                </dt><dd>`21`</dd></dl> |
| **                Login              ** Input field | Username used for login. SCP account used must be able to store files on the remote SCP server.<dl><dt>                  Valid input                </dt><dd>A valid username</dd><dt>                  Input example                </dt><dd>`wsm_backup`</dd><dt>                  Default value                </dt><dd>`none`</dd></dl> |
| **                SCP key              ** Button | Click **Download Web Security Manager Public SCP Key** to download key used for authentication. Make sure to add this key to the authorized keys list on the remote server. |
| **                Remote directory              ** Input field | Full path to directory on SCP server used for storing Web Security Manager related files.<dl><dt>                  Valid input                </dt><dd>A directory path ending with /</dd><dt>                  Input example                </dt><dd>`/scp/wsm/`</dd><dt>                  Default value                </dt><dd>`none`</dd></dl> |

### Auto-backup

Auto-backup, if enabled, is performed daily at 03:00 AM based on your current timezone settings.

<colgroup></colgroup>| **              Enable FTP auto-backup            ** Check box | Enable or disable FTP auto-backup. If checked, automated FTP configuration backup will be active. |
| **              Enable SCP auto-backup            ** Check box | Enable or disable SCP auto-backup. If checked, automated SCP configuration backup will be active. |

### Retention of deny logs and related statistics

<colgroup></colgroup>| **              Retain deny logs on appliance            ** Check box |  |
| **              Number of deny log entries to retain            ** Input field |  |

### Management user password requirements 

Manage password requirements, session and login restrictions and SSL certificate.

<colgroup></colgroup>| **              Minimum length            ** Input field | Minimum password length in number of characters<dl><dt>                Valid input              </dt><dd>Number in the interval 6 to 64</dd><dt>                Default value              </dt><dd>`8`</dd></dl> |
| **              Letter characters required            ** Check box | Require one or more letter character, a-z + international. |
| **              One or more digits (0-9) required            ** Check box | Require one or more digits. |
| **              Combination of upper and lower case required            ** Check box | Require a combination of upper and lower case characters. |
| **              Non alphanumeric characters required            ** Check box | Require one or more special (non-alphanumeric) characters. |

### Management GUI login restrictions

<colgroup></colgroup>| **                Idle timeout              ** Input field | Number of seconds the management GUI can be idle before the user is logged out.<dl><dt>                  Valid input                </dt><dd>timeout in seconds 20 to 86400.</dd><dt>                  Input example                </dt><dd>`900 - 15 minutes`</dd><dt>                  Default value                </dt><dd>`600`</dd></dl> |
| **                Failed login delay              ** Input field | Number of seconds to wait after a failed login attempt before a new attempt can be made.<dl><dt>                  Valid input                </dt><dd>timeout in seconds 0 to 60.</dd><dt>                  Default value                </dt><dd>`3`</dd></dl> |
| **                Failed logins limit              ** Input field | Number of failed login attempts allowed before the failed login action is taken.<dl><dt>                  Valid input                </dt><dd>Number of attempts 1 to 100.</dd><dt>                  Default value                </dt><dd>`5`</dd></dl> |
| **                Failed logins action              ** Dropdown | What to do if a user exceeds the failed logins limit. Options:<dl><dt>                  None                </dt><dd>No action</dd><dt>                  Lockout                </dt><dd>The user account is locked for the configured duration. After the configured the duration the user account is unlocked and the user can log in.</dd><dt>                  Suspend                </dt><dd>The user account is suspended and cannot be used until is the account status has been set to OK by an administrator.
User account status can be set in System : Users or in the console (see CLI reference manual for more information).</dd></dl><dl><dt>                  Valid input                </dt><dd>`None, Lockout, Suspend`</dd><dt>                  Input example                </dt><dd>`Lockout`</dd><dt>                  Default value                </dt><dd>`None`</dd></dl> |
| **Lockout duration** Input field |  |
| **                Notify user on lockout and suspend              ** Check box | If enabled, user will receive an error message in the login page if the account has been locked or suspended. |
| **                Suspend inactive accounts              ** Check box | Enable suspending of accounts that has not been active for a specified duration. |
| **                Account inactivity threshold              ** Input field | Number of days a user account can be inactive before it is automatically suspended.<dl><dt>                  Valid input                </dt><dd>Duration in days 1 to 1000.</dd><dt>                  Default value                </dt><dd>`90`</dd></dl> |

### Management GUI certificate

Management GUI SSL certificates can either be self signed or imported certificates.

In the SSL certificate section the current SSL certificate in use is displayed. To upload a new certificate click the **Manage GUI certificates** button.

#### Generate self-signed SSL certificate

To generate a self signed certificate, enter the certificate information in the input fields.

Click **Save settings** in the lower button pane.

#### Importing the PKCS12 format

If the certificate is in the PKCS12 format follow the guidelines below:

1. Enter the path to the certificate file in the **PKCS12 file** input field.
2. Enter Passphrase in the **Passphrase** input field.
3. Click **Save settings** in the lower button pane.

If Validate certificate chain is enabled Web Security Manager will validate and order the chain certificates.

#### Importing the PEM format

If the certificate is in the PEM format follow the guidelines below:

1. Open the .PEM file in a text-editor. Copy the public certificate section of the certificate.
The public key/certificate is the section of the certificate file between (and including) the certificate start and end tags. Example:-----BEGIN CERTIFICATE-----
 Certificate characters
-----END CERTIFICATE-----
2. Select **Import SSL certificate** In the Web Security Manager management interface
Paste the SSL public key/certificate into the **SSL-certificate** field.
3. Now copy the (SSL) private key section of the certificate. The (SSL) private key is the section of the certificate file between (and including) the private key start and end tags. Example:-----BEGIN RSA PRIVATE KEY-----
 Private key characters 
-----END RSA PRIVATE KEY-----
4. Enter the passphrase for the private key in the **passphrase field** (if the original private key was encrypted).
5. If a certificate authority chain is provided with your certificate enter the entire list of certificates (more than one certificate may be provided) in the SSL authority certificate(s) chain field

If Validate certificate chain is enabled WAF will validate and order the chain certificates.

### FIPS 140-2 validated mode

WAF provides the option for the appliance in the customer environment to be locked down to only run the OpenSSL FIPS Object Module in FIPS 140-2 validated mode (FIPS 140-2 certificate #1747).

The lockdown to FIPS 140-2 mode, including validation of the integrity of the FIPS validated crypto modules, is automated, irreversible, and locks down the operating system (CentOS) to run in FIPS 140-2 validated mode as originally specified in the OS provider’s (Red Hat Inc.) FIPS 140-2 certificate #1758.

When the option is selected, the applicable package and libraries are converted to FIPS mode, library pre-linking is disabled, and the WAF appliance reboots. After the appliance has rebooted, all communication occurs using only the FIPS-validated algorithms and the appliance will only accept and use FIPS validated encryption for all inbound and outbound communication to and from all services on the appliance. This includes the WAF HTTP proxy service, the appliance’s HTTPS web based UI, and SSH services used to remotely access the underlying appliance.

#### Validation of FIPS mode

When the WSM appliance is using only FIPS-validated encryption modules, the WSM User Interface running on the appliance displays the label **FIPS mode**. The **FIPS mode** label reflects the value of

```
/proc/sys/crypto/fips_enabled
```

Which is computed at startup when the system performs the self tests as required in the FIPS 140-2 certificate Security Policy.            
If the self test validation at startup fails the system and crypto modules are not running as required for FIPS validated mode and the **FIPS mode** label is not displayed in the appliance UI.

#### Enabling FIPS 140-2 validated mode

When enabling FIPS mode:

* The appliance is converted and locked down irreversibly to run in FIPS mode.
* Depending on the disk size the conversion process will take between 2-10 minutes.
* When the conversion process is finished the appliance will reboot.
* During the process proxy services will be available and website availability will not be affected until the appliance reboots.

To enable FIPS 140-2 validated mode

1. Tick the box **Enable FIPS mode**
2. Click the button** Convert appliance into FIPS mode**
The system will now display a confirmation dialog that outlines the conversion process.
3. Confirm that the appliance is irreversibly converted to FIPS mode.
The conversion process begins.
4. Log out of the UI and log in again to have the FIPS mode validation label displayed.
The FIPS mode validation flag that is displayed in the appliance user interface is stored in the currently logged in session in the UI layer so to have the mode validation label displayed immediately after conversion is is necessary to log in again to read the setting from `/proc/sys/crypto/fips_enabled`.
In Amazon Web Services Auto Scaling deployments, the FIPS mode is embedded in the AMI that the auto scaling stack is built from. Consequently, the user interface option to convert the appliance to FIPS validated mode is not available. The configuration of FIPS validated mode and self test at startup to validate are no different from non-auto scaling WSM deployments.

# Alert Logic Managed Web Application Firewall (WAF) Release Notes

## Alert Logic Managed Web Application Firewall (WAF) release notes

<fieldset>Alert Logic supports the current version and the last two minor versions. For example, 4.5.1.0 is two versions behind 4.5.3.0, and an appliance running version 4.5.0.0 is unsupported.</fieldset>
Alert Logic does not automatically push new versions to customers, and an upgrade may be required if you need support on an older appliance.

    2021 (4.x and 5.x)    ### Release date: November 15, 2021 Version 4.6.1.0 / 5.0.0.19-664

#### Features

* Improved XSS signatures
* Improved password management for API users
* Support SNI for health-checking https backends

#### Bug fixes

* Resolve issue in handling end-of-file during high-volume log transport
* Make several violation types more uniform in their presentation
* Resolve issue with logging identity of internal users
* Inspect file uploads only when the new signature model is enabled

### Release date: October 15, 2021 Version 4.6.0.19-3264 (inline) / 5.0.0.19-664

#### Features

* FIPS mode for WSM 5

#### Bug fixes

* Allow PUT requests without a recognized Content-Type if bypass is enabled
* Correct SSL certificate permissions issue
* Word-break long hostnames in the deny log
* Gracefully handle certain SSL read errors in backend health checks
* Increase allowed duration of network time requests

### Release date: October 4, 2021 Version 4.6.0.18-3249 (all inline platforms) / 5.0.0.18-648 (AWS AMI non-FIPS)

#### Features

* Attack signatures usage now includes advanced engine with header evaluation built in
* Improved time-keeping with multiple fallbacks
* Improved defaults (advanced signature engine; file upload inspection; emerging threat detection; and opt-in learning)

#### Bug fixes

* Trim learn stats more frequently
* Always regenerate core configs during migrations
* Remove outdated version check
* Perform additional database integrity checks
* Skip proxy syncs when no proxies are found

### Release date: September 9, 2021 Version 4.6.0.17 (all platforms) / 5.0.0.17 (AWS AMI non-FIPS)

#### Bug fixes

* Eliminate backtracking in the command line normalizer

### Release date: August 25, 2021 Version 4.6.0.16 (all platforms) / 5.0.0.16 (AWS AMI non-FIPS)

#### Features

* Display IPs blocked as a result of setting a connection limit
* Extend the REST API to support fetching access logs
* Automate updates of system packages

#### Bug fixes

* Wrap the text of long Referer URLs in the UI
* Minor improvements to system log transport
* Anchor ACL path regex when finding matches
* Never enable default HTTP/HTTPS in created templates
* Correct UI regression in show original request view on WSM 4

### Release date: August 3, 2021 Version 4.6.0.15 (all platforms) / 5.0.0.15 (AWS AMI non-FIPS)

#### Bug fixes

* Resolve high-availability cluster sync regression
* Allow read-only users to connect from the Alert Logic console
* Preserve transparent proxy settings when applying configurations

### Release date: July 15, 2021 Version 4.6.0.14 (all platforms) / 5.0.0.14 (AWS AMI non-FIPS)

#### Bug fixes

* Re-initialize message queues upon restoring/importing system settings
* Allow sync daemon to health check via loopback

### Release date: July 13, 2021 Version 4.6.0.13 (all platforms) / 5.0.0.13 (AWS AMI non-FIPS)

#### Features

* Show number of files associated with excess upload attempts
* Allow full search text search on 'info' deny log field
* Add HTTP/4848 health check to non-autoscaling deployments
* Support delegated credentials for automated response integration

#### Bug fixes

* Prevent significant CPU consumption during normalization of some requests
* Support non-compliant multipart form boundaries
* Sort the list of available backups
* Support larger deny logs
* Ensure AWS auto-scaling deployments have a default configuration

### Release date: July 9, 2021 Version 4.6.0.12 (all platforms) / 5.0.0.12 (AWS AMI non-FIPS)

#### Features

* Integrate with incident API to support automated response
* Support migration of transparent proxy from WSM 4 to WSM 5
* Improve configuration sync on AWS auto-scaling deployments
* System log display rendering improvements
* Internal enhancements to log transport components
* Add include sub option to log filter violation filter

#### Bug fixes

* Correctly sort log events
* Sync website configs in an optimal order
* Adjust log rotation/retention configuration
* Remove irrelevant warnings
* Ensure all system configuration elements can be saved in UI
* Correctly match VLAN interface ID mapping
* Concatenate multi-line syslog messages
* Allow header/body filters to work on WSM 5
* Resolve precedence between GeoIP-blocked and blackholed requests
* On WSM 5, ensure log volume is preserved and mounted when master instance is replaced
* Prefer configured UUID over provisioning UUID for heartbeating
* Prevent auto-scaling worker instances from running wsm_bootstrap loop
* Restart framework after WSM update
* Regenerate core configuration after SSL certificate REST API update
* Allow "0" when validating an HTTP header
* Remove 240.0/8 loopback IPs from the UI
* Layer 7 blocking should ignore invalid IPs in XFF
* Re-open database handles after daemonization in one service
* Miscellaneous packaging improvements and system software updates

### Release date: April 19, 2021 Version 5.0.0.11 (AWS AMI non-FIPS)

#### Features

* Improvements to CPU and RAM utilization
* Log transport agent updated to use newer log ingestion system
* Support provisioning in additional data centers

#### Bug fixes

* Allow UI to save policies with over 248 global parameters
* Support multi-line syslog messages and system logs in new log agent
* Ensure admin daemon restarts service dependencies robustly

#### Other changes

* Remove AWS autoclaim agent

No 4.6.0.10 release exists.

### Release date: March 18, 2021 Version 5.0.0.10 (AWS AMI non-FIPS)

#### Features

* Support DHCP assignments with /32 netmask

#### Other changes

* Update jQuery

No 4.6.0.9 release exists.

### Release date: March 8, 2021 Version 5.0.0.9 (AWS AMI non-FIPS)

#### Features

* Support JSON lines format for S3 deny log export
* Enhance deny log to include string that triggers double encoding violation

#### Bug fixes

* Resolve issue where daemons were not restarting when certain config changes were committed
* Resolve issue uploading PEM certificates with separate chains and with uploading PKCS#12 certs/keys
* Resolve issue affecting ACL policy manipulation
* Suppress errors from update tools when deployment-specific repo bundles are not in use

5.0.0.8 was not released for Managed WAF.

No 4.6.0.8 release exists.

### Release date: February 9, 2021 Version 4.6.0.7 (all platforms) / 5.0.0.7 (AWS AMI non-FIPS)

#### Features

* Extend virtual patch support to include Base64 decoding support

#### Bug fixes

* Resolve rare issue with host/role in config generation
* Resolve issue with configs where both session persistence (cookie, source IP, etc.) and real server failover was enabled at the same time
* Fix internal get_worker_status ops tool
* Resolve issue with FIPS mode detection on non-FIPS kernels

No 4.6.0.6, 5.0.0.5, or 5.0.0.6 releases exist.

### Release date: January 29, 2021 Version 4.6.0.5 (all platforms) / 5.0.0.4 (AWS AMI non-FIPS)

#### Changes

* Update sudo

### Release date: January 27, 2021 Version 5.0.0.3 (AWS AMI non-FIPS)

#### Features

* Support for TLS 1.3
* Support for HTTP/2
* Support for proxying Web Sockets
* Support for proxying gRPC

### Release date: January 19, 2021 Version 4.6.0.4

#### Features

* Extended support for virtual patches
* New virtual patches with coverage related to SolarWinds compromise

#### Bug fixes

* Improved validation of SSL certificate uploads
* Improved handling of certificate revocation lists

    2020 (4.x)    ### Release date: November 3, 2020 Version 4.6.0.3

#### Bug fixes

* Resolve permissions issue and timing issues in AWS master config sync
* Resolve country code discrepancy issue in the deny log
* Resolve country code discrepancy issue in the deny log
* Improve handling of formats for upstream response time value
* Reformat deny log to be parseable in search again
* Upgrade onboard database software (SQLite)
* Minor internal fixes in support of future enhancements

### Release date: October 8, 2020 Version 4.6.0.2

#### Bug fixes

* On upgrade, handle ACL paths with regex meta characters correctly

### Release date: September 9, 2020 Version 4.6.0.1

#### Bug fixes

* On upgrade, migrate to more configurable HTTP method inspection correctly
* Discover recent changes to health-check configuration correctly

### Release date: August 31, 2020 Version 4.6.0.0

#### Features

* Support exporting deny logs to an S3 bucket
* Support syslog over TLS
* Support vpatches for emerging threats
* Send additional details to Log Manager regarding generic protocol violations
* Improve handling of XML
* Improve configurability of body permissions and actions across methods
* Minor signature improvement
* Numerous performance and portability improvements to WSM internals

#### Bug fixes

* Interpret and synchronize extended syslog config correctly
* Check multiple virtual patches matching a path
* Fix issue with WSM dashboard not displaying through the AL console
* Allow OPTIONS method when no application path config is present
* Support separate default vhosts for both HTTP and HTTPS
* Send certificate metadata to backend in all cases
* Avoid double-escaping regex application paths during upgrades and imports

### Release date: May 5, 2020 Version 4.5.9.1

#### Bug fixes

* Improved utf8 handling
* Resolved an issue with displaying HTML5 graphs in the console
* Improved mqueue allocation during an upgrade

### Release date: April 7, 2020 Version 4.5.9.0

#### Features

* Alert Logic now supports new collections of virtual patches (highly-targeted security content for specific vulnerabilities)
* Replaced Flash-based UI graphs with HTML5 charts
* Improved multibyte support
* Allowed GET requests to have a body
* Treated expected redirects of HTTP to SSL as non-violating
* Minimized UI presentation of sequentially-duplicated system logs
* Supported custom log fields in extended enhanced alert log
* Used ISO date format for audit logs
* Allowed quoted multipart boundaries
* Supported SameSite cookies
* Supported customizable 307/308 redirects
* Supported negation of deny log filter expressions
* Supported optional silencing of GeoIP access violations
* Expanded character set in the default URL class definition
* Added cipher and TLS version as options for custom access log format
* Covered additional SQLi conditions with improved security content

#### Bug fixes

* Properly decoded HTML entities when dealing with customer-defined web ACLs
* Validated SSL PEM certificates on upload regardless of the "Validate certificate chain" option
* Corrected an issue with updating CRL lists
* Properly matched regex-based ACLs when adding to them from the deny log view
* Updated text in "Add from deny log" functionality
* Updated OpenSSH
* Updated console URLs in login page
* Removed source IPs which have been removed from the teacher node's blacklist
* Improved X-Forwarded-For parsing
* Made SSL certificate generation default to 2048 bit keys
* Used default HTTPS proxy settings correctly
* New web ACLs now inherit allowed HTTP method settings
* Improved logging for the health check daemon
* Improved automated detection of XML content

    2019 (4.x)    ### Release date: November 21, 2019 Version 4.5.8.0

#### Features

* Use regular expressions in web application paths (Note: existing paths will be converted to regexes automatically)
* Improve handling of UTF-8 encoding in policy values
* Add file extension validation framework
* Prioritize GeoIP lookups by represented country, registered country, and RIR assignment country order (Note: This product includes GeoLite2 data created by MaxMind).
* Add trusted proxy support for black hole
* Offer extended alert log format
* Support ECDSA keys for TLS proxies (mutually exclusive with RSA)
* Release package updates for base OS security
* Block TRACE method on Management UI

#### Bug fixes

* Fix response body rewriting consistency when learning engine is enabled
* Fix issue where health check daemon could miss config change notifications

### Release date: September 26, 2019 Version 4.5.7.0-2249

#### Features

* Support sending SNI to upstream servers
* Support future hotfix deployments independent of upgrades
* UI to multi-select country codes
* UI to copy deny log details to clipboard
* UI warning when enabling proxy protocol
* Disable legacy SSH algorithms
* Deterministic package installation order for new physical/virtual deployments
* API for managing redirects and aliases
* Generate warnings when auto-scaling worker sync is blocked
* Improvements to deny log parser error handling
* Protocol violations should not log entire payload
* Reduce false positives on XPATH signatures
* Skip [ TRUNCATED ] suffix when adding parameters from log
* Remove low-confidence XPATH signatures

#### Bug fixes

* Replace message queue implementation for deny logs, learning data, and response inspection
* Always validate request headers using general rules in addition to header-specific validation
* Allow ACL definitions to be agnostic about trailing slashes
* Match newlines when masking deny log input
* Make signature package updates visible in UI
* Improve access log routing for auto-scaling deployments with more than ten proxies
* Use correct package name when updating signatures on autoscaling worker instances

### Release date: June 13, 2019 Version 4.5.6.3-2084

#### Features

Switched to a new GeoIP2 database format for more accurate geolocation data. This product includes GeoLite2 data created by [MaxMind](https://www.maxmind.com).

### Release date: May 7, 2019 Version 4.5.6.2-2030

#### Features

Reduced false positives in OS Commanding signatures.

#### Bug fixes

Preserved policy routes when upgrading.

### Release date: April 9, 2019 Version 4.5.6.1-1976

####  Features

* Allow single-quoted strings in JSON parser
* RPC audit logging overhaul
* Expose an option to disable Alert Logic Managed Web Application Firewall (WAF) default inspection scope
* Return signature info in response headers in signature test mode
* Detect evasion attempts using request body header tricks
* Replace ntpd
* Reduce false positives
* Change authentication mechanism for repository access
* Content validation data collection framework
* Allow malformed UTF-8 encodings in JSON payloads
* Further improvements to TLS key handling

#### Bug fixes

* Persist policy routing priorities
* Web App IDS deny log notes correct action on requests to unknown hosts
* Prevent errors from terminating syncd
* Prevent proxy error log duplication
* Allow overlapping system gateway to match a whitelist

#### Signature changes

* Package renamed to accommodate breaking changes
* Removed RFI to reduce false positives
* Improved general coverage
* Improved SQLI coverage

    2018 (4.x)    ### Release date: December 14, 2018 Version 4.5.6.0-1839

#### Features

* Add Joomla PHP injection signature to header validation
* Add underlying support for nvme1n1 for new instance types
* Allow access logging of calculated remote IP
* Allow more granular control of email notifications
* Improve TLS key handling
* Install operations tool by default
* Relax JSON parser to allow scalar string data
* Release new kernel
* Require latest DNS SQLi signature
* Support TLDs up to 32 characters long
* Support configurable DTD validation when parsing XML payloads
* Turn on filename validation by default
* Update several common software packages

#### Bug fixes

* Align utf8 usage in WAF core and the Alert Logic console
* Allow the trusted proxy setting to be reset to undefined
* Fix WAF display for read­-only users in the Alert Logic console
* Fix bug in reading attribution signatures
* Rotate deny log database more gracefully
* HUP syslog­ng after rotating access log
* Improve header validation / RFC enforcement options
* Send HSTS headers on WAF error pages
* Suppress sensitive metadata in log

#### Signature changes

* DNS exfiltration
* Date field for classification signatures
* Improved OSC / removed OSC_TRAIL_PIPE
* Improved PHP INJ signature
* New OSC and SQLI signatures

### Release date: August 14, 2018 Version 4.5.5.1-1683

#### Features

Improved OS commanding detection

#### Bug fixes

Proxy would improperly block certain OS commanding violations with HTTP 500 errors regardless of policy setting

### Release date: August 7, 2018 Version 4.5.5.0-1668

#### Features

* Clean up orphaned package management transaction files
* Improve deny log rotation performance
* Reduce alarm flapping
* Log the offending part of abnormally large payloads
* Watchdog enhancements
* Enable "Accept underscore characters in request headers" by default
* Allow certain alarm conditions to automatically clear when the alarm condition is no longer present
* Normalize and de-duplicate virtual host aliases to lowercase
* Allow optional port numbers in X-Forwarded-For header parsing
* Add configurable back-off period for auto-clearing alarms
* Improved OS Commanding detection
* Updated signature content
* Add Drupal signature as a custom signature to new proxies
* AWS Enhanced Networking Adapter foundational support, pending AMI release
* Improve cluster synchronization resilience to network errors

#### Bug fixes

* Passive WAF logged proxy IP instead of trusted X-Forwarded-For IP in some circumstances
* Error saving intermediate certificate when "Validate certificate chain" is enabled
* Strip request headers entirely when required by policy, rather than only removing the value
* Deny log processing could stall on Passive WAF
* Passive WAF feature can be fully enabled without requiring sensor reboot

### Release date: June 7, 2018 Version 4.5.4.3-1586

#### Features

Add support for AWS S3 bucket server-side KMS encryption

### Release date: May 8, 2018 Version 4.5.4.2-1545

#### Features

Improved audit logging

#### Bug fixes

Fix a rare memory leak

### Release date: April 9, 2018 Version 4.5.4.1-1501

#### Bug fixes

* Fixed issue displaying deny logs with malformed utf8 data
* Resolve UI error related to IP sharding feature
* Fixed grouping by country in the deny log dashboard
* Stop logging at 10% free space left on Passive WAF
* Read the correct core error log on auto-scaling masters

### Release date: March 6, 2018 Version 4.5.4.0-1461

#### Features

* Support inline WAF on Google Compute Engine
* Updated kernel
* Replaced string search algorithm
* Relaxed threshold for waf-core-cpu alarm

#### Bug fixes

* Prevent autoscaling master instances from syncing backup to S3 when unhealthy
* Restored "Insert" option on response header rewrite rules when using more than 4 entries
* Fixed L7 blacklist syncing for CIDR ranges
* Restored missing fields in deny log in edge case

### Release date: January 30, 2018 Version 4.5.3.4-1418

#### Bug fixes

* Resolve an issue which could prevent certain global system settings from syncing to autoscaling workers and HA learners
* Resolve a slow memory leak in the proxy core

### Release date: January 4, 2018 Version 4.5.3.3-1395

#### Bug fixes

Restore allowed HTTP method types in policy ACLs correctly when restoring backups or replacing autoscaling master instances

    2017 (4.x)    ### Release date: November 14, 2017 Version 4.5.3.2-1320

#### Features

* Activate JSON parser for a wider content-type range
* Enable response inspection by default on Passive WSM
* Support tilde and percent in external redirects
* Parse cookies more strictly
* Configure AWS auto-scaling master as undisciplined clock

#### Bug fixes

* Resolve a circumstance which caused DHCP to be enabled improperly on new sensors
* Don't log the RAW body twice on Passive WSM
* Allow large file uploads when Content-Length is set
* Resolve UI error when deleting phantom static routes
* Resolve minor issues in SSL client auth handling

### Release date: August 2017 Version 4.5.3.1-1204

#### Bug fixes

Fix a regression that broke new routing proxy deployments

### Release date: July 17, 2017 Version 4.5.3.0

#### Bug fixes

* Improved response inspection/analysis statistics to eliminate sources of inaccurate criticality scoring.
* Resolved an issue with multi-node configuration sync that could interrupt cluster sync operations.
* Resolved an issue preventing blacklist not syncing from master to learner nodes in some scenarios.
* Addressed an issue related to high CPU consumption when running scans against WSM in some customer environments.

#### Features

* Added API calls to import and export site policy templates via WSM management API.
* Added an option to close connection on 502 errors.
* Improved network performance in customer environments with high rates of requests and concurrent requests.

#### Security

* Resolved nginx range filter potential leakage/denial of service vulnerability (CVE-2017-7529).

#### Changes

* Management UI now requires TLS 1.2+.

#### Notice

None

### Release date: April 12, 2017 Version 4.5.2.4

#### Bug fixes

* Addressed an issue introduced in 4.5.2.1 release causing unexpected proxy update/delete behavior.

#### Security

* Removed potential for theoretical XSS within a specific dialog.

### Release date:  March 13, 2017 Version 4.5.2.2

#### Bug fixes

* Improved log rotation/log storage database to reduce contention and improve log rotation process.
* Resolved a rare issue with CPUs without AVX support.

#### Features

* Added Apache Struts (CVE-2017-5638) header validation rule and included in default template.
* Added option to globally enable proxy protocol for all listen IPs

#### Changes

* Changed WSM “Import Proxy Template” API call to match documentation.

### Release date: February 21, 2017 Version 4.5.2.1

#### Bug fixes

* Resolved an issue related to falsely indicating versions within a cluster.
* Addressed a small number of scenarios where license keys incorrectly report that they are invalid.
* Addressed scenarios where the appliance watchdog service may inadvertently not be running.
* Resolved several minor typos in the user interface.
* Resolved an issue where changed cluster passwords were not replicated through the entire system.

#### Features

Added per-site policy GeoIP-based blacklisting/whitelisting functionality.

#### Security

Added internal last modified date for CRUD operations on websites, to be relayed to Alert Logic’s backend.

#### Changes

* User interface will now prevent a proxy creation that overlaps on IP:port between another proxy/protocol.
* Increased internal daemons dealing with syslog messages now have higher free disk thresholds, consistent with alarms.

### Release date: February 7, 2017 Version 4.5.2.0

#### Bug fixes

* Resolved an issue where stats database could end up with improper permissions.
* Resolved potential slow memory leaks with stats collector.
* Improved watchdog recovery of logging agent.

#### Features

Completed support for new AWS regions that require both HVM and v4 signatures.

#### Changes

Introduced dependency on new health monitoring agent.

### Release date: January 19, 2017 Version 4.5.1.2

#### Bug fixes

* Improved logging related to blocking/blacklisting IPs, both removing excess errors and ensuring details are properly logged.
* Ensure blocking configuration files are properly written during AWS master re-spins.
* Resolved issue with block timeouts falling back to default rather than using configured timeout.
* Resolved an issue with adding overlapping ranges to blacklists that resulted in some IPs not blacklisted.

#### Features

Extended maximum header size limitation to optionally allow headers up to 32k.

    2016 (4.x)    ## Release date 

December 15, 2016 (4.5.1.1)

## Bug fixes

* Updated response inspection to pick up configuration changes when website configurations are changed.
* Improved handling of learn candidate failures to prevent unexpected deny logs from being created from learn candidates.
* Resolved an issue with System>Tools>Website Configuration preventing expected configuration content from being returned.
* Addressed an issue that may result in unexpected mismatched version alarms within a cluster.

## Features

N/A

## Security

Provided an updated kernel to address potential security vulnerabilities (including dirtyc0w).

## Changes

* Updated several minor issues in the REST API and added a new API call to get IP addresses.
* Updated invalid hostname violation to enforce SSL hostname restrictions.
* Provided an affordance for single quotes present in file paths to be allowed by modifying the allowable files regular expression.

## Notice

N/A

***## Release date 

October 27, 2016 (4.5.1.0)

## Bug fixes

* This release removes the unexpected need for initial configuration save and restart of the WSM appliance UI at provisioning time.
* This release resolves an issue where backend server violations did not always log headers.
* This release resolves an issue where layer 7 blocking did not always work following autoscaling instance respins.
* This release removes superfluous error generation when syncing routing proxy configs.
* This release improves resilience of deny log transport in certain edge cases.
* This release improves storage of datacenter affiliation configuration.
* This release adds functionality to always include response parameters (even if values are empty) in deny logs to ensure logs are properly parsed.
* This release improves Denial of Service mitigation setting configuration to ensure settings are saved and operate as expected.
* This release addresses an issue related to response inspection learning that can lead to increased CPU consumption.
* This release improves handling of iptables configuration to ensure appliance specific changes are not overwritten for both WSM Premier and WSM (Out of Band).
* This release resolves a scenario where the ACL cache can be cleared during the autoscaling instance boot process.
* This release improves payment card masking to reduce false positives in deny log masking.

## Features

N/A

## Security

This release updates HTTP SSL settings to lock down insecure ciphers and SSL/TLS for WSM (Out of Band).

## Changes

* WSM Appliance API users can now be created via UI, CFT, and during appliance provisioning.
* WSM Appliance API users will now be indicated in the appliance UI.
* IP Addresses extracted from X-Forwarded-For headers will now be the leftmost non-private IP.
* Deny log rotation is now limited to preserving 100k records, which will be rotated more frequently.
* Improvements to several WSM appliance alarms facilitate better monitoring and troubleshooting by Alert Logic operations teams.
* Updated WSM appliance SQlite instance for improved stability and reliability.

## Notice

N/A

***## Release date 

September 19, 2016 (4.5.0.2)

## Bug fixes

* This release resolves an issue where Content-Type was not being matched case-insensitively.
* This release improves handling of chunked multipart/form-data.
* This release prevents multiple instances of internal services from running on the appliance.
* This release resolves two minor syslog daemon configuration issues.
* This release resolves an issue where invalid learn chunks could cause startup failures without manual intervention.

## Features

N/A

## Security

This release updates the embedded agent which now includes additional TLS1.2 support for Alert Logic services.

## Changes

N/A

## Notice

N/A

***## Release date 

August 11, 2016 (4.5.0.0)

## Bug fixes

* This release ensures syslog daemon was restarted properly after upgrade.
* This release resolves an issue with single tuned site configurations not properly transmitting log activity.
* This release resolves an issues with configuration files potentially being overwritten during an upgrade.
* This release resolves an issue during boot where AWS environments were not properly recognized.
* This release resolves an issue with duplicate fwmark rules being created in transparent proxy deployments.

## Features

* This release adds capabilities to capture and analyze full server responses, providing the response and potential indicators of compromise within the UI and deny logs.
* This release improves support for Azure WSM deployments, including adjustments to SSH ClientAliveInterval and the WSM configuration UI.

## Security

This release resolves CVE-2016-4450 (a potential DoS condition in nginx).

## Changes

This release removes VLAN submenu from WSM UI in deployments where it’s not used.

## Notice

* N/A

***## Release date

June 16, 2016 (4.4.3.0)

## Bug fixes

* This release resolves an issue with unnecessary services running on auto-scaling workers.
* This release resolves an issue with connectivity to s3 during updates.
* This release resolves several minor issues that could generate unexpected log output.
* This release resolves several issues with the internal watchdog to improve resilience.
* This release resolves an issue where SSL certificate chain expiration dates could appear incorrectly or be out of sync across components.
* This release resolves an issue related to certain scans causing unexpected appliance behavior.
* This release resolves an issue where certain scheduled tasks would not run in configured timezones.
* This release resolves an issue where cluster IP alias limits were not functioning as expected in configuration UI.
* This release resolves an issue with custom access log formats not behaving as expected.

## Features

* N/A

## Security

* This release updates openssl library to address recent openssl vulnerabilities (including CVE-2016-2108 and CVE-2016-2107).

## Changes

* This release further restricts remote login access via SSH to internal and Alert Logic networks.

## Notice

* N/A

***## Release date 

April 21, 2016 (4.4.2.0)

## Bug fixes

* This release resolves an issue causing proxy stats database to grow excessively large in size.
* This release resolves an issue with a dependent service failing to auto-upgrade during provisioning.
* This release resolves an issue with missing configuration settings not being restored during re-spin in AWS auto-scaling deployments.
* This release resolves an issue with WSM agent service consuming resources on AWS auto-scaling workers.
* This release resolves an issue with the management of multiple instances of dependent services.
* This release resolves an issue with the bootstrap process when services are not immediately ready.
* This release resolves an issue with AWS auto-scaling workers performing unnecessary S3 config backups.
* This release resolves an issue related to layer 7 blocking, including a problem with timeout enforcement.

## Features

* This release adds several improvements relating to web security content, including additional details in the deny log when content is triggered.
* This release adds support for monitoring RESTful API methods and zero-length requests that normally have a request body.
* This release adds several improvements to aid in troubleshooting of WSM appliances, while improving monitored checks.

## Security

* N/A

## Changes

* This release changes worker CPU usage calculation to use standard deviation instead of min/max.
* This release changes backend health check configuration to reject semicolons in path.

## Notice

* N/A

## Release date 

March 3, 2016 (4.4.1.0)

## Bug fixes

* This release resolves an issue where WSM user guides/help links may not have been accurate to the WSM version deployed.
* This release resolves issues with several scenarios that could cause unexpected responses to carefully crafted requests.
* This release resolves an issue causing failures importing PKCS12 certificates.
* This release resolves an issue with static routes when using interface-specific gateways.
* This release resolves an issue where temporary files remained after working with SSL cache.
* This release resolves an issue where bypassing an unknown method (e.g. WebDAV LOCK) where parameters/cookies were present was not possible.
* This release resolves an issue deploying customer-specific hotfixes to AWS auto-scaling deployments.
* This release resolves an issue displaying deny log when Unicode encoded characters were present in an entry.

## Features

* This release adds support for worker access logs to be aggregated on master (similar to deny logs).

## Security

* This release updates glibc and openssl to address recent upstream security announcements.

## Changes

* This release extends enforcement of SSH access, eliminating remote access from the “operator” user.

## Notice

* N/A

    2016 (3.2)    ## Release date 

July 7, 2016 (3.2.38)

## Bug fixes

N/A

## Features

N/A

## Security

* This release updates openssl library to address recent openssl vulnerabilities (including CVE-2016-2108, CVE-2016-2107).

## Changes

* This release further restricts remote login access via SSH to internal and Alert Logic networks.
* This release enables masking of sensitive payment card information in log data by default.

## Notice

N/A

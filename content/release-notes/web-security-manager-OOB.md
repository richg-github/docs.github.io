# Web Security Manager release notes

## Web Security Manager release notes

### Release date: April 9, 2018 Version 4.5.4.1-1501

#### Bug fixes

* Fixed issue displaying deny logs with malformed utf8 data
* Resolve UI error related to IP sharding feature
* Fixed grouping by country in the deny log dashboard
* Stop logging at 10% free space left on Passive WAF
* Read the correct core error log on auto-scaling masters

    2017    ### Release date: December 11, 2017 Version 4.5.3.2-1352

#### Bug fixes

Properly restart janitor process on Passive WAF

### Release date: June 12, 2017

#### Bug fixes

* Improved response inspection/analysis statistics to eliminate sources of inaccurate criticality scoring.
* Improved appliance configuration transmission/retrieval from Alert Logic backend.
* Improved process for WSM appliance to pick up hostname changes.

### Release date: January 31, 2017 

#### Bug fixes

* Resolved potential conflicts in appliance IP tables configuration mechanisms.
* Resolved several minor issues related to response anomaly detection.
* Resolved an issue that could result in SSL traffic not generating violations as expected.

#### Changes

Removed unsupported/unused external notification section.

### Release date: August 11, 2016 Version 4.5.0.0

#### Features

* This release Adds capabilities to capture and analyze full server responses, providing the response and potential indicators of compromise within the UI and deny logs.
* This release inherits many features, bugfixes, and improvements from WSM Premier.

### Release date: April 5, 2016

#### Bug fixes

* Resolved issue with WSM customers seeing 0.0.0.0 source address for some messages.
* Improved several out-of-order and other packet handling scenarios.
* Added several statistics to logs for decrypted traffic.

#### Security

Release of several shared packages with Threat Manager:

* al-threat-sensor-2.2.1-17
* al-tm-balancer-2.4.9
* al-tm-decrypter-2.2.72.g38bcc80-2

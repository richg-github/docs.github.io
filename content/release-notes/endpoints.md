# Alert Logic Extended Endpoint Protection Agent Release Notes

## Extended Endpoint Protection release notes

    2021    ### Release date: Dec 01, 2021 Windows Agent Version 4.11.2.0

#### Bug Fixes

* Fixed one corner case where Kernel crashes.

### Release date: May 26, 2021 Mac Agent Version 4.12.0.0

#### Features

* Support for macOS BigSur version  11.x (automatic upgrade of Extended Endpoint Protection on macOS BigSur is not supported. The latest installer needs to be downloaded and installed manually to run Extended Endpoint Protection on BigSur).
* Fixed other minor issues.

### Release date: January 12, 2021 Windows Agent Version 4.11.0.0

#### Features

* New logo for EEP agent.
* Add epoch timestamp to prediction data in agent.
* RL cache changes on EEP agent.
* Support for AWS Workspaces on Windows instances.

#### Bug fixes

* Fixes an issue where EEP-Agent startup time can exceed 30 seconds.
* Fixes an issue where Upgrade from 3.x to 4.x does not preserve keep.
* Fixes an issue where EEP-Agent : Handle Leak in case of renew certificate workflow
* Fixes an issue with fetching log files where the fetch fails when log files are locked or in use.

    2020    ### Release date: July 7, 2020 

#### Features

* Supported languages now include German and Spanish.
* Added Windows Server 2019 support.

### Release date: June 23, 2020 Agent Version 4.10 

#### Features

* You can now use for MQTT tunneling over an HTTP proxy.
* The Extended Endpoint Protection agent is now installable on all language versions of Windows.
* Detects and reports agent crashes to backend.

#### Bug fixes

* Detects and notifies SaaS of Upgrade Failure Loop.
* Fixes an issue where RV-Agent does not notify SaaS upon successful upgrade.
* Updates RV-Agent dependencies to latest stable, LTS release.
* Fixes an issue where RV-Agent was not notified of shutdown on Windows.
* Uninstall Lock defaulted to ON in Integration still allowed uninstall.
* Fixes an issue where RV-Agent: Safe mode was overridden when unregistered or renewal required.
* RV-Agent notifies SaaS of its version when upgrader exits.
* Fixes an issue where RV-Agent reports inaccurate current user on macOS.
* Fixes an issue where file permissions were not maintained when a file was quarantined.
* Fixes an issue where RV-Agent caused blue screen.

### Release date: April 14, 2020

Alert Logic is upgrading Barkley customers to the full, robust Alert LogicEssentials subscription. The Essentials subscription, in addition to the Extended Endpoint Protection, offers other capabilities and functionality you can use in the Alert Logic console. For more information, see [Alert Logic Extended Endpoint Protection Upgrade](../get-started/endpoint-protection-upgrade.md).

### Release date: March 20, 2020

#### Features

Extended Endpoint Protection now supports the following macOS versions:

* Sierra
* High Sierra
* Mojave
* Catalina

### Release date: February 18, 2020

#### Features

* You can now mark an endpoint as a VDI master image. For more information, see [Virtual Desktop Infrastructure Environments](../deploy/vdi.md)
* You can configure and customize the pop-up message that appears when Extended Endpoint Protection blocks an attack on an endpoint. For more information, see [Configure the Extended Endpoint Protection Pop-up](../configure/extended-endpoint-protection/configure-pop-up.md).

### Release date: January 14, 2020 

#### Features

* Throttles duplicate incident notifications, reducing noise and preventing notification floods
* Custom popup image visible to admin and non-admin users
* Configuration updates take effect without agent restart
* Records system power events in agent log to aide in diagnostics
* Raises an error flag when unable to reach AWS IOT, due to a misconfigured network
* Automatically compresses agent logs increase retention and decrease disk utilization
* Activates protection at agent startup after loading overrides to prevent blocking already overridden apps

#### Bug fixes

* Fixes a registration renewal crash
* Fixes a crash when transitioning from unregistered to registers

    2019    ### Release date: October 31, 2019

#### Features

Alert Logic added five filters on the [Events](../analyze/extended-endpoint-protection/investigate-event.md) page:

* Events over 30 days old
* Events over 60 minutes old
* Events created within the last 60 minutes
* Quarantined events
* Overridden events

### Release date: October 17, 2019

#### Feature

Alert Logic updated the Service Status page to include Extended Endpoint Protection. You can now check its operational status and subscribe to receive notifications when the status changes. Alert Logic recommends that you subscribe to receive service notifications for all your products, including Extended Endpoint Protection. For more information, see [Service Status](../analyze/service-status.md).

### Release date: September 25, 2019 Agent Version 4.6.1

#### Features

* Reduces false positives with an automated, real-time file reputation lookup
* Improves performance, increases stability, expands compatibility, and simplifies installation by eliminating Hypervisor
* Automatically detects proxy configuration
* Removes dependency on PubNub for out-of-band communication
* Agent platform upgraded from NodeJS to .NET Core 2.2
* Fixes false positives with Grammarly auto updater

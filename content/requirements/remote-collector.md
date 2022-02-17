# Requirements for the Alert Logic Remote Collector

The following describes the basic requirements to install a remote collector:

| Components | System Requirements |
|---|---|
| CPU | 2 cores |
| RAM | 2 GB |
| Disk space | 10 GB minimum |
| Supported Operating Systems | Windows and Linux |
| Log collection support | Syslog only via port 1515 |
| Encryption | TLS Standard (SSL): 2048-bit key encryption, 256-bit AES bulk encryption |
| Log collection frequency | Every five minutes (minimum)- logs collected and sent to Alert Logic Cloud |
| Host permissions | LocalSystem account has all the requisite permissions by default |

## Firewall rules

For more information on firewall rules for remote collectors, see [United States Firewall Rules](us-firewall-rules.md) or [United Kingdom and European Union Firewall Rules](uk-eu-firewall-rules.md).

## Installation and downloads

For installation directions and links to the remote collector downloads, see [Install the  Remote Collector for Linux](../prepare/remote-log-collector-linux.md) or [Install the Remote Collector for Windows](../prepare/remote-log-collector-windows.md).

# Test Alert Logic Extended Endpoint Protection

Extended Endpoint Protection focuses on what attackers cannot disguise and what traditional endpoint solutions cannot observe: the attributes and behaviors of malware at runtime. This means Alert Logic does not take action against malware that is killed by another tool pre-execution or against unexecuted malware. Instead, Extended Endpoint Protection takes action when malware gets past other layers and attempts to detonate.

## Testing tools from Alert Logic

To demonstrate effectiveness, Alert Logic provides these testing tools that simulate the behavior of ransomware and credential theft malware.

| Source	 | Description	 | Link |
|---|---|---|
| Ransomware Simulation | This ransomware simulation provides you with a piece of real ransomware which you can safely run on your endpoints to test your level of vulnerability. Alert Logic scoped this sample so that only one file will be encrypted upon execution - making it both realistic and safe. The Instruction Guide walks through a scenario that mirrors a phishing attack, showing you how a program like this might get executed on your network. | Follow our Instruction Guide |
| Fileless Attack Simulation (Word Macro) | This Word document is similar to a phishing campaign. When a user opens the document and clicks **Enable Content**, the macro runs a Powershell script that, in principle, could do virtually anything to your system (for example, retrieve another file from a remote server or write commands to the registry). For demonstration purposes, the Powershell script does something totally benign: opens the Windows Calculator and displays a message. If the Calculator program opens successfully, you are vulnerable to script-based "fileless" attacks that use Powershell. | [Download document from the Alert Logic public GitHub](https://github.com/alertlogic/al-endpoint-downloads/blob/master/macro-ps-demo.docm) |
| Fileless Attack Simulation (Word DDE) | This Word document is similar to a phishing campaign. When a user opens the document and clicks **Yes** to allow dynamic data fields, Word processes an operation via command line that, in principle, could do virtually anything to your system (for example, retrieve another file from a remote server or write commands to the registry). For demonstration purposes, the Powershell script does something totally benign: opens the Windows Calculator. This attack technique is further described in Bleeping Computer's "Microsoft Office Attack Runs Malware Without Needing Macros." If the Calculator program opens successfully, you are vulnerable to script-based "fileless" attacks that use Powershell. | [Download document from the Alert Logic public GitHub](https://github.com/alertlogic/al-endpoint-downloads/blob/master/weekly-revenue-report.docx) |

## Third-party testing tools

Below are recommendations for third-party testing tools that are both realistic and safe. Alert Logic has no affiliation to and does not endorse any of these organizations, projects, or tools.

| Source | Description | Link |
|---|---|---|
| ShinoLocker | Shino Shinogi is a security researcher who authors ethical hacking tools and publishes them at ShinoSec. He built ShinoLocker to behave like real ransomware, at no cost. For more, see his presentation from Black Hat 2016 or New Education ShinoLocker Ransomware Project Released by Bleeping Computer. | [https://shinolocker.com/](https://shinolocker.com/) |
| testmyav.com | TESTmyAV provides "the malware, testing guides and tools you need to test antivirus products for yourself." TESTmyAV requires registration and does not provide samples to security vendors. | [https://testmyav.com/](https://testmyav.com/) |

## If Extended Endpoint Protection does not take action

If Extended Endpoint Protection does not  stop something that you expect it to during testing, there is often a legitimate explanation. Tests that are not stopped include:

* Tests that are behaviorally benign
* Tests designed for signature matching
* Tests that use inert malware
* Software with legitimate uses

### Tests that are behaviorally benign

Some tests are deliberately designed to not do harm when executed.  For example, an Office Macro can be built to perform one action—such as opening up a port to communicate externally. When sequenced with other specific actions, the test can contribute to an attack, but if it does not, the test is a benign and legitimate operation. Extended Endpoint Protection can differentiate from what is truly dangerous while not allowing non-harmful software.

### Tests designed for signature matching

Some tests like the EICAR test are specifically built for signature matching. There is no malicious payload or harmful behaviors to stop.

### Tests that use inert malware

Just as legitimate software has dependencies in order to operate successfully, so do most malicious software. Some malware only works in certain environments or geographies, and it can depend on the presence of other software, hardware, or system settings. Malware also commonly depends on feedback from a remote command and control server, so if that remote server is not running, which can happen intentionally or inadvertently, the malware will not run successfully. Older malware is particularly susceptible to this. If malware cannot begin to run, Extended Endpoint Protection will not have anything to stop.

### Software with legitimate uses

Some software can be perceived as risky despite having legitimate uses, like key-logging software (used by companies and parents for monitoring) or remote administration tools (used to remotely administer computers). Extended Endpoint Protection is designed to stop genuinely malicious software.

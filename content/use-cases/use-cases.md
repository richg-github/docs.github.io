# Use Cases

### Automate Deployments

* Create a new Data center deployment
* Create a new AWS deployment
* Create a new Azure deployment
* Create a new customer with ordering API
* Set up scan windows
* Create API access key
* Add external asset for scanning
* Set up new app registry data source
* Add an SSL certificate for SSL decryption
* Add scan credentials
* Adjust automatic deployment parameters for IDS appliances in AWS
* Use API access keys to implement key rotation
* Create data center network or subnet in existing deployment
* Determine which IDS appliance a host is current assigned to
* Adjust automatic deployment parameters for scan appliances in AWS
* Get current node list by protection level
* Adjust vulnerability scan frequency
* Pause all vulnerability scans for a deployment
* Change a user role
* Delete a user
* Add a user
* Enable span port / stop agent IDS forwarding in data center
* Revoke API access key
* Schedule a saved search
* Adjust external scan frequency
* List all locked users in my account
* Adjust discovery scan frequency

### Refine Detection

<ul>
  <li>Set up IDS exclusions</li>
  <li>Adjust analytic thresholds that are generating false-positive incidents</li>
  <li>Set valid GeoIP information to help <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> threat detection recognize GeoIP-based attacks</li>
  <li>Whitelist network addresses to allow scanning</li>
  <li>Blacklist known network addresses</li>
</ul>### Integrate Response

<ul>
  <li>Create a webhook and subscribe incidents to it</li>
  <li>Export a list of endpoint events</li>
  <li>Export current incident list</li>
  <li>Retrieve incident details for a single incident by ID (e.g. after receiving email or webhook)</li>
  <li>Replicate dashboards in my own portal (just the data)</li>
  <li>Execute a log search, get results</li>
  <li>Export current health issues detected</li>
  <li>Export current offline agent list</li>
  <li>Export current vulnerabilities detected</li>
  <li>Export current vulnerabilities detected (CIS)</li>
  <li>Check health of AWS deployment</li>
  <li>Check health of Azure deployment</li>
  <li>Export current offline appliance list</li>
  <li>Export list of endpoint agents</li>
  <li>Show list of hosts that are currently being scanned	</li>
  <li>Access scheduled search results (after receiving an email)</li>
  <li>Access scheduled report results (after receiving an email)</li>
  <li>Download agent statistics for last 24 hours</li>
  <li>Download appliance statistics for last 24 hours	</li>
  <li>Close an incident</li>
  <li>Replicate dashboards in my own portal (using <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> code)</li>
</ul>### Act on Vulnerabilities

* Retrieve incident details for a single incident by ID (e.g. after receiving email or webhook)
* Dispose of a health issue
* Dispose of a vulnerability or remediation
* Force immediate scan of a host
* Assess threat risk of my environment
* Access scheduled search results (after receiving an email)
* Access scheduled report results (after receiving an email)
* Retrieve FIM data using search
* Add notes to an incident

## Use Case Detail List

<table style="width: 100%;" MadCap:autosort="False" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">
  <col />
  <col />
  <col MadCap:autosortPriority="1" MadCap:autosortDirection="ascending" />
  <col MadCap:autosortPriority="0" MadCap:autosortDirection="ascending" />
  <col />
  <col />
  <tbody>
    <tr>
      <th>Use case</th>
      <th>Persona</th>
      <th>Size</th>
      <th>Utility</th>
      <th>Concepts</th>
      <th>Notes</th>
    </tr>
    <tr>
      <td>List all users in my account</td>
      <td>Admin</td>
      <td>S</td>
      <td>example</td>
      <td>Audit, example</td>
      <td> </td>
    </tr>
    <tr>
      <td>Create a webhook and subscribe incidents to it</td>
      <td>partner</td>
      <td>L</td>
      <td>L</td>
      <td>Incidents, automation</td>
      <td>Probably need a helper API to simplify — or a larger topic</td>
    </tr>
    <tr>
      <td>Create a new Data center deployment</td>
      <td>Sec ops, partner</td>
      <td>L</td>
      <td>L</td>
      <td>Configuration, setup, DC</td>
      <td>Probably need a helper API to simplify</td>
    </tr>
    <tr>
      <td>Create a new customer with ordering API	</td>
      <td>Partner</td>
      <td>L</td>
      <td>L</td>
      <td>Ordering, configuration</td>
      <td> </td>
    </tr>
    <tr>
      <td>Create a new AWS deployment</td>
      <td>Sec ops, partner</td>
      <td>L</td>
      <td>L</td>
      <td>Configuration, setup, AWS</td>
      <td>Probably need a helper API to simplify</td>
    </tr>
    <tr>
      <td>Create a new Azure deployment</td>
      <td>Sec ops, partner</td>
      <td>L</td>
      <td>L</td>
      <td>Configuration, setup, Azure</td>
      <td>Probably need a helper API to simplify</td>
    </tr>
    <tr>
      <td>Export a list of endpoint events</td>
      <td>Sec ops, partner</td>
      <td>L</td>
      <td>L</td>
      <td>Endpoint, automation</td>
      <td>Probably need a helper API to simplify</td>
    </tr>
    <tr>
      <td>Set up IDS exclusions</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>L</td>
      <td>Configuration, vulnerability</td>
      <td> </td>
    </tr>
    <tr>
      <td>Export current incident list</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>L</td>
      <td>Incidents, data export	</td>
      <td>IRIS API is tricky</td>
    </tr>
    <tr>
      <td>Retrieve incident details for a single incident by ID (e.g. after receiving email or webhook)</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>L</td>
      <td>Incidents, integration	</td>
      <td>Probably part of a larger series on integration</td>
    </tr>
    <tr>
      <td>Replicate dashboards in my own portal (just the data)</td>
      <td>Partner</td>
      <td>M</td>
      <td>L</td>
      <td>Dashboards</td>
      <td> </td>
    </tr>
    <tr>
      <td>Set up scan windows	</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>L</td>
      <td>Configuration, vulnerability</td>
      <td> </td>
    </tr>
    <tr>
      <td>Execute a log search, get results</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>L</td>
      <td>Search, log</td>
      <td> </td>
    </tr>
    <tr>
      <td>Dispose of a health issue</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>L</td>
      <td>Health, automation</td>
      <td> </td>
    </tr>
    <tr>
      <td>Dispose of a vulnerability or remediation</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>L</td>
      <td>Vulnerability, automation</td>
      <td> </td>
    </tr>
    <tr>
      <td>Export current health issues detected by AL</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>L</td>
      <td>Health, data export</td>
      <td> </td>
    </tr>
    <tr>
      <td>Export current offline agent list</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>L</td>
      <td>Health, data export</td>
      <td> </td>
    </tr>
    <tr>
      <td>Export current vulnerabilities detected by AL</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>L</td>
      <td>Vulnerability, data export</td>
      <td> </td>
    </tr>
    <tr>
      <td>Export current vulnerabilities detected by AL (CIS)</td>
      <td>Sec ops, partner, sales</td>
      <td>S</td>
      <td>L</td>
      <td>Vulnerability, compliance, sales tool, AWS, Azure</td>
      <td> </td>
    </tr>
    <tr>
      <td>Create API access key</td>
      <td>Sec ops, partner, developer</td>
      <td>S</td>
      <td>L</td>
      <td>User admin, example</td>
      <td> </td>
    </tr>
    <tr>
      <td>Force immediate scan of a host	</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>L</td>
      <td>Vulnerability</td>
      <td> </td>
    </tr>
    <tr>
      <td>Check health of AWS deployment</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>L</td>
      <td>Configuration, setup, AWS</td>
      <td> </td>
    </tr>
    <tr>
      <td>Check health of Azure deployment</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>L</td>
      <td>Configuration, setup, Azure</td>
      <td> </td>
    </tr>
    <tr>
      <td>Assess threat risk of my environment</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>L</td>
      <td>Vulnerability, compliance, sales tool, AWS, Azure</td>
      <td> </td>
    </tr>
    <tr>
      <td>Export current offline appliance list</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>L</td>
      <td>Health, data export</td>
      <td> </td>
    </tr>
    <tr>
      <td>Export list of endpoint agents</td>
      <td>Sec ops, partner</td>
      <td>L</td>
      <td>M</td>
      <td>Endpoint, automation</td>
      <td>Probably need a helper API to simplify</td>
    </tr>
    <tr>
      <td>Add external asset for scanning	</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Configuration, vulnerability</td>
      <td> </td>
    </tr>
    <tr>
      <td>Set up new app registry data source</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Log, setup</td>
      <td>Probably a series of these</td>
    </tr>
    <tr>
      <td>Add an SSL certificate for SSL decryption</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Vulnerability, configuration</td>
      <td> </td>
    </tr>
    <tr>
      <td>Add scan credentials</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Vulnerability, configuration</td>
      <td> </td>
    </tr>
    <tr>
      <td>Show list of hosts that are currently being scanned	</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Health, automation</td>
      <td> </td>
    </tr>
    <tr>
      <td>Access scheduled search results (after receiving an email)</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Search, automation</td>
      <td> </td>
    </tr>
    <tr>
      <td>Adjust automatic deployment parameters for IDS appliances in AWS</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Configuration, IDS</td>
      <td> </td>
    </tr>
    <tr>
      <td>Use API access keys to implement key rotation</td>
      <td>Partner, sec ops</td>
      <td>M</td>
      <td>M</td>
      <td>User admin, compliance</td>
      <td>Advanced topic</td>
    </tr>
    <tr>
      <td>Access scheduled report results (after receiving an email)</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Search, automation</td>
      <td> </td>
    </tr>
    <tr>
      <td>Create data center network or subnet in existing deployment</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Configuration, setup, DC</td>
      <td>Probably need a helper API to simplify</td>
    </tr>
    <tr>
      <td>Download agent statistics for last 24 hours</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Health, IDS, Log</td>
      <td> </td>
    </tr>
    <tr>
      <td>Download appliance statistics for last 24 hours	</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Health, IDS</td>
      <td> </td>
    </tr>
    <tr>
      <td>Determine which IDS appliance a host is current assigned to	</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Health, IDS</td>
      <td> </td>
    </tr>
    <tr>
      <td>Retrieve FIM data using search</td>
      <td>Sec ops</td>
      <td>M</td>
      <td>M</td>
      <td>Search, fim</td>
      <td> </td>
    </tr>
    <tr>
      <td>Adjust automatic deployment parameters for scan appliances in AWS</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>M</td>
      <td>Configuration, Scan</td>
      <td> </td>
    </tr>
    <tr>
      <td>Get current node list by protection level</td>
      <td>Sec ops, admin, partner</td>
      <td>M?</td>
      <td>M</td>
      <td>Usage, data export</td>
      <td> </td>
    </tr>
    <tr>
      <td>Adjust vulnerability scan frequency</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>M</td>
      <td>Configuration, vulnerability</td>
      <td> </td>
    </tr>
    <tr>
      <td>Pause all vulnerability scans for a deployment</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>M</td>
      <td>Configuration, vulnerability</td>
      <td> </td>
    </tr>
    <tr>
      <td>Change a user role</td>
      <td>Admin</td>
      <td>S</td>
      <td>M</td>
      <td>User admin</td>
      <td> </td>
    </tr>
    <tr>
      <td>Delete a user</td>
      <td>Admin</td>
      <td>S</td>
      <td>M</td>
      <td>User admin</td>
      <td> </td>
    </tr>
    <tr>
      <td>Add a user</td>
      <td>Admin</td>
      <td>S</td>
      <td>M</td>
      <td>User admin</td>
      <td> </td>
    </tr>
    <tr>
      <td>Close an incident</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>M</td>
      <td>Incidents, workflow</td>
      <td> </td>
    </tr>
    <tr>
      <td>Enable span port / stop agent IDS forwarding in data center	</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>M</td>
      <td>Configuration, IDS, DC</td>
      <td> </td>
    </tr>
    <tr>
      <td>Revoke API access key</td>
      <td>Sec ops, partner, developer</td>
      <td>S</td>
      <td>M</td>
      <td>User admin</td>
      <td> </td>
    </tr>
    <tr>
      <td>Replicate dashboards in my own portal (use our code)</td>
      <td>Partner</td>
      <td>XL</td>
      <td>M</td>
      <td>Dashboards</td>
      <td> </td>
    </tr>
    <tr>
      <td>Schedule a saved search</td>
      <td>Sec ops, partner</td>
      <td>M</td>
      <td>S</td>
      <td>Search, automation</td>
      <td> </td>
    </tr>
    <tr>
      <td>Adjust external scan frequency</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>S</td>
      <td>Configuration, vulnerability</td>
      <td> </td>
    </tr>
    <tr>
      <td>List all locked users in my account</td>
      <td>Admin</td>
      <td>S</td>
      <td>S</td>
      <td>User admin</td>
      <td> </td>
    </tr>
    <tr>
      <td>Adjust discovery scan frequency</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>S</td>
      <td>Configuration, DC</td>
      <td> </td>
    </tr>
    <tr>
      <td>Add notes to an incident</td>
      <td>Sec ops, partner</td>
      <td>S</td>
      <td>S</td>
      <td>Incidents, workflow</td>
      <td> </td>
    </tr>
  </tbody>
</table>

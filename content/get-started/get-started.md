# Get Started

<section class="get-started">
  <img src="../Resources/Images/Tiles/automate-data-collection.png" style="float: left;clear: none;" />
  <h3>Automate deployments</h3>
  <p>Are you a highly automated DevOps shop?  Do you want to ensure that your cyber visibility does not degrade as your environment changes over time?  This section walks you through automating all aspects of the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> deployment to avoid manually deploying agents and appliances or logging into the console to configure them.</p>
  <a href="../use-cases/aws.md" class="cta">Learn more</a>
  <img src="../Resources/Images/Tiles/tune-incident-generation.png" style="float: right;clear: none;" />
  <h3>Tune detection</h3>
  <p>Want  to tune detection yourself instead of <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> making the changes for you?  This section instructs you on the tools you have available to you to refine tunable detection settings.</p>
  <a href="#" class="cta">Learn more</a>
  <img src="../Resources/Images/Tiles/consume-platform-outcomes.png" style="float: right;clear: none;" />
  <h3>Integrate response</h3>
  <p>Do you want to leverage your ticketing and messaging tools to notify you and manage status?  Alternatively, do you want to automate common response actions with third-party security tools?  This section helps you understand how to make that happen.</p>
  <a href="../use-cases/servicenow.md" class="cta">Learn more</a>
  <img src="../Resources/Images/Tiles/automate-data-collection.png" style="float: right;clear: none;" />
  <h3>Tune incident generation</h3>
  <p>Tired of triaging vulnerability reports to IT teams for remediation?  Do you want to automate the process through an integration between <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> and your ticketing system?  This section walks you through how to configure a ticketing integration so that vulnerabilities are automatically routed to the right teams.</p>
  <a href="#" class="cta">Learn more</a>
</section><h2>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Developer Portal</h2><p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> created this portal to provide developers with an easy way to access a wide range of developer resources. The <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Developer Portal has many opportunities for customers and partners to automate processes and integrate with their own systems.</p>

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> APIs help with common use cases, such as:</p>

<ul>
  <li>Create an API access key</li>
  <li>Export current vulnerabilities detected by <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /></li>
  <li>Create a new AWS, Azure, or data center deployment</li>
</ul><p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> APIs are based on REST and JSON, documented with examples, using standard HTTP verbs, and response codes.</p>

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> provides secure, authenticated APIs to the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> platform — highly scalable and available. The APIs offered here are the same ones that the <MadCap:variable name="SDKVariables.ALUI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> uses. Each access is auditable and traceable to the user who made it.</p>

## Developer portal

The information in this portal is divided into four main categories:

<ul>
  <li>Get Started</li>
  <li>
    <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>
    <MadCap:variable name="SDKVariables.SDK" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>Use Cases—in-depth examples of common use cases</li>
  <li>Service Reference—detailed documentation on each of the available <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> APIs</li>
</ul>### Get Started

The Get Started section contains high-level documentation with general information, including:

<ul>
  <li>
    <a href="requirements.md">Requirements for API use</a>
  </li>
  <li>
    <a href="accounts-users.md">User and account information</a>
  </li>
  <ul>
    <li>All APIs are account-specific.</li>
  </ul>
  <li MadCap:conditions="Primary.beta" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">
    <a href="cloud-defender.md">Considerations for  customers</a>
  </li>
</ul><h3>
  <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
</h3>* 

<h3>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />SDK</h3>### Use Cases

### Service Reference

The Service Reference section

## Choose a tool

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> provides a development toolkit in Python and a standalone CLI if you do not want to implement REST APIs yourself. Set up authentication and choosing the right API endpoints based on the data residency of your account.</p>

<p>The easiest way to get started with automation is using the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />. The CLI lets you explore APIs interactively right away. You can install it on Windows with MSI, or using PIP/Python on a Mac/Linux</p>

If you are building complex automation, the Python SDK makes it easy to create workflows, process and extract results, and perform other automation tasks.

Both the CLI and SDK are built on the same REST APIs, so you get the full functionality no matter which tool you choose.

<p MadCap:conditions="Primary.Draft Content" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">If you are implementing your own client, read more about <a href="#"><MadCap:annotation MadCap:createDate="2020-06-15T11:00:08.5374767-05:00" MadCap:creator="jacqueline.reyes" MadCap:initials="JA" MadCap:comment="these do not link anywhere" MadCap:editor="jacqueline.reyes" MadCap:editDate="2020-06-15T11:00:19.0544336-05:00">authentication</MadCap:annotation></a>  and <a href="#">data residency.</a></p>

### Versioning

<p>Download the <MadCap:annotation MadCap:createDate="2020-06-15T11:00:29.9955204-05:00" MadCap:creator="jacqueline.reyes" MadCap:initials="JA" MadCap:comment="no xrefer here" MadCap:editor="jacqueline.reyes" MadCap:editDate="2020-06-15T11:00:35.5820702-05:00" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd"><a href="#">most recent version</a></MadCap:annotation> for the latest APIs and best examples.</p>

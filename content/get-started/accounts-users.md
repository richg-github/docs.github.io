# Accounts and User Types

<p>You can access <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> APIs as a user associated with a specific account. When <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> APIs pulls account information, you cannot  switch accounts during a process. Users belong to a single account, and though you may have an account that manages other accounts, you must choose one account each time you work with the APIs. Multi-account users must be careful and deliberate when working in the API to ensure that the intended account is selected.</p>

## Types of user roles

<p>User roles available in the <MadCap:variable name="SDKVariables.ALUI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> include the following:</p>

* **Administrator**—The Administrator role allows full management of, and read access for, the account and any managed accounts. Only administrators can create and manage other users for the managing account and for managed accounts. Administrators can also control features for the managing account and all its managed accounts.
* **Owner**—The Owner role allows full management and read access for the user account they are assigned, but do not have the ability to edit other user accounts. Owners also have full read and modify permissions to any managed accounts, including the ability to edit users on the managed accounts. Owner accounts cannot create or delete users in managed accounts.
* **Power User**—The Power User role allows full access within the managing account, except for user management. Power users can view all the information in their managed accounts, but cannot modify the information (including user accounts).
* **Support/Care**—The Support/Care role allows only read access for the managing account and all its managed accounts.
* **Read Only**—The Read Only role allows only read access for the managing account. Users assigned this role cannot make changes and cannot view information for any managed accounts.

## Service users

<p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> recommends creating a dedicated user for automation efforts. A service user prevents password lockout when staff changes and keeps everything in one dedicated place.</p>

**To create a service user**:

<ol>
  <li>Set up a new user in the <MadCap:variable name="SDKVariables.ALUI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> using a valid email address.</li>
  <li>Choose the user role based on your needs.</li>
  <li>Use an <a href="https://docs.alertlogic.com/prepare/access-key-management.htm" title="Create and Manage Alert Logic Access Keys documentation" alt="Create and Manage Alert Logic Access Keys documentation">access key and secret key</a> instead of a password.</li>
</ol>
For more information, see [Customer Accounts, User Accounts, and User Roles](https://docs.alertlogic.com/prepare/users-roles.htm).

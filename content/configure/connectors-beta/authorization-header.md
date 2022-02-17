# Generate an Authorization Header

If the third-party application to which you want to connect requires a Basic HTTP Authorization request header, you can use these instructions to generate the header. The command requires the valid user name and password in the application to which you want to connect, and it encodes the credentials with base64.

In the Authorization Header field, you enter the word "Basic" (which is the Authorization header type), a space, and then the  base64-encoded credentials.

    For Jira  or Jira Service Desk connectors,  the password field must be an API token generated in your Atlassian account. For more information on how to generate an API token in your Atlassian account, see [Create an API token](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/).    
**To generate the header on Linux and Mac OS X:**

1. In the command line, type the following command, including the single quotation marks:
<kbd>echo -n '&amp;lt;user_name&amp;gt;:&amp;lt;password&amp;gt;' | base64</kbd>
where you must replace <user_name> and <password> with a valid user name and password  for the third-party application.
2. Copy the following string, which you must enter in the **Authorization Header** field when you create the connector:
<kbd>Basic &amp;lt;resulting_base64_encoded_string&amp;gt;</kbd>

If the user name is "admin" and the password  is "testpassword" for example, the command is:

<kbd>echo -n 'admin:testpassword' | base64</kbd>

and the command produces this output: 

<kbd>YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

So, in the **Authorization Header** field, you would paste:

<kbd>Basic YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

**To generate the header in Windows PowerShell:**

1. In the command line, type the following commands, including the quotation marks:
PS c:\Temp><kbd>$auth  = [System.Text.Encoding]::UTF8.GetBytes("&amp;lt;user_name&amp;gt;:&amp;lt;password&amp;gt;")</kbd>
where you must replace <user_name> and <password> with a valid user name and  password for the third-party application.
PS c:\Temp><kbd>[System.Convert]::ToBase64String($auth)</kbd>
2. Copy the following string, which you must enter in the **Authorization Header** field when you create the connector:
<kbd>Basic &amp;lt;resulting_base64_encoded_string&amp;gt;</kbd>

If the user name is "admin" and the password is "testpassword" for example, the commands are:

PS C:\Temp><kbd>$auth  = [System.Text.Encoding]::UTF8.GetBytes("admin:testpassword")</kbd>

PS C:\Temp><kbd>[System.Convert]::ToBase64String($auth)</kbd>

and the command produces this output: 

<kbd>YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

So, in the **Authorization Header** field, you would paste:

<kbd>Basic YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

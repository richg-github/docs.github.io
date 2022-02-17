# breYep thaConfigure Universal Webhook Connection Target

A webhook connection target securely stores reusable authentication credential and URL path information for integrations with webhook.

Complete the following steps to  configure a connection target for webhook:

Complete the following steps to successfully configure a connection target for a Webhook:

1. [Identify your webhook base URL target](#IdentifyyourwebhookbasetargetURL)
2. [breYep thaConfigure Universal Webhook Connection Target](#GenerateanAuthorizationheader)
3. [(Optional) Add custom header(s)](#(Optional)Addcustomheader(s))
4. [Use the connection target in connectors and playbooks](#Usetheconnectiontargetinconnectorsandplaybooks)

    Before you create the webhook connection target in the Alert Logic console, gather the information that your third-party application requires by consulting the vendor documentation.    ## Identify your webhook base URL target

The URL for your application that can accept Alert Logic notifications or ticket creation requests. Some applications require that you generate a target URL that includes a token for authorization.

## (Optional) Generate an Authorization header

If the third-party application to which you want to connect requires a Basic HTTP Authorization request header, you can use these instructions to generate the header. The command requires the valid user name and password in the application to which you want to connect, and it encodes the credentials with base64.

    Some types of external applications require that the password field must be an API token or integration key generated in your external application account. For more information, refer to the documentation for your external application.    
In the Authorization Header field, you enter the word "Basic" (which is the Authorization header type), a space, and then the  base64-encoded credentials.

**To generate the header on Linux and Mac OS X:**

1. In the command line, type the following command, including the single quotation marks:
<kbd>echo -n '&amp;lt;user_name&amp;gt;:&amp;lt;password&amp;gt;' | base64</kbd>
where you must replace <user_name> and <password> with a valid user name and password for the third-party application.
2. Copy the following string, which you must enter in the **Authorization Header** field when you create the connector:
<kbd>Basic &amp;lt;resulting_base64_encoded_string&amp;gt;</kbd>

If the user name is "admin" and the password is "testpassword" for example, the command is:

<kbd>echo -n 'admin:testpassword' | base64</kbd>

and the command produces this output: 

<kbd>YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

So, in the **Authorization Header** field, you would paste:

<kbd>Basic YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

**To generate the header in Windows PowerShell:**

1. In the command line, type the following commands, including the quotation marks:
<kbd>$auth  = [System.Text.Encoding]::UTF8.GetBytes("&amp;lt;user_name&amp;gt;:&amp;lt;password&amp;gt;")</kbd>
where you must replace <user_name> and <password> with a valid user name and password for your third-party application.
<kbd>[System.Convert]::ToBase64String($auth)</kbd>
2. Copy the following string, which you must enter in the **Authorization Header** field when you create the connector:
<kbd>Basic &amp;lt;resulting_base64_encoded_string&amp;gt;</kbd>

If the user name is "admin" and the password is "testpassword" for example, the commands are:

<kbd>$auth  = [System.Text.Encoding]::UTF8.GetBytes("admin:testpassword")</kbd>

<kbd>[System.Convert]::ToBase64String($auth)</kbd>

and the command produces this output: 

<kbd>YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

So, in the **Authorization Header** field, you would paste:

<kbd>Basic YWRtaW46dGVzdHBhc3N3b3Jk</kbd>## (Optional) Add custom header(s)

Some applications require one or more HTTP custom headers. Custom headers are HTTP name-value pairs in the format *Header-Name*: *value* with each header field on a separate line, for example:

| Accept: application/json |
| Content-Type: application/json |

## Use the connection target in connectors and playbooks

After you save the connection target, the last step is to set up a connector or automated response playbook. For more information on connectors, see [Connectors Configuration Guide](../../../Z-Sandbox/bbaskin/connectors-beta/connectors.md). For more information on automated response, see [Get Started with Automated Response (Beta)](../../../respond/automated-response.md).

## Manage connection targets

You can view the list of connection targets and edit or delete an existing one. For more information, see [Manage Connection Targets](../../../Z-Sandbox/bbaskin/connectors-beta/connection-targets/manage-connection-targets.md).

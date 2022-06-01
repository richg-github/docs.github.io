# CLI First Use and Validation

<p>This section describes how to configure the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> to connect to <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> using your credentials and validate the configuration.</p>

## Prerequisites for Configuration

<p>You must have valid credentials to access <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> APIs using the <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />. You can use either your <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> username and password (and MFA credentials if required), or a dedicated access key and secret key. The <a href="../get-started/requirements.md">Requirements</a> documentation contains more information on credentials.</p>

## Validating alcli installation

To validate alcli is installed correctly and that a supported Python interpreter is available, execute:

```

alcli --version
```

Sample output:

```

$ alcli --version
alcli/1.0.28 Python/3.7.7 almdrlib/1.0.28 alsdkdefs/0.0.10
```

## Add your credentials

Before you can run a CLI command, you must configure your credentials.

By default, alcli uses the .alertlogic/config configuration file in a user home directory. On Windows, it is found in your home path, usually C:\USERS\<your user name>. File can contain multiple profiles. Here is an example of a configuration file that has credentials for a single production login:

```

[default] 
access_key_id=2222222222222222 
secret_key=dddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddddd 
global_endpoint=production 
```

You can also specify the location of the configuration file by setting ALERTLOGIC_CONFIG environment variable to contain file's location.

## Credential validation

To validate your credentials, execute:

```

alcli --query authentication.user.email aims authenticate
```

Sample output:

```

$ alcli --query authentication.user.email aims authenticate
"user@example.com"
```

This command calls the authenticate endpoint of the AIMS service to obtain information about the credentials you supplied, The --query authentication.user.email option uses a [JMESPath](https://jmespath.org/) query to extract your email address from the full JSON response.

## Troubleshooting

If you receive an “Access Denied” message when validating your credentials, verify that:

* The  .alertlogic directory is present in your home directory, and contains a file named config, with no extension.
* If you are using a dedicated secret key and access key, check that the config file you created includes a valid secret key and access key. Secret keys are 16 characters long, and access keys are 64 characters long.
* If you are using your own username as a secret key, verify that the username includes your full email address.

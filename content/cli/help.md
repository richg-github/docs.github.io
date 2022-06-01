```

alcli help
```

Sample output:

```

ALCLI()                                                                  ALCLI()
NAME
	alcli -
DESCRIPTION
	The Alert Logic Command Line Interface is a tool to help you manage
	Alert Logic Services.
SYNOPSIS
	alcli [options] <command> <subcommand> [parameters]
	Use alcli command help for information on a  specific command.
OPTIONS
	--debug (boolean)
	Turn on debug logging.
	--query (string)
	A JMESPath query to use in filtering the response data.
:
```

Use the following commands to navigate the help:

Space: next page

Up-arrow: scroll up

Down-arrow: scroll down

q: exit

<p>Executing <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> commands</p>

<p>
  <MadCap:variable name="SDKVariables.CLI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> execution follows the general pattern</p>

alcli [options] command subcommand [parameters]

<p>The options control the general operation of the CLI, such as debugging or response queries using JMESPath. Commands correspond to <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> service names, subcommands to individual APIs of that service, and parameters provide additional input to the given API.</p>

To obtain a list of supported commands, execute:

alcli commands

or

alcli help

<p style="font-weight: bold;">To obtain a list of supported subcommands for a given command, run:</p>

alcli <command> help

For example:

```

alcli aims help
```

<p style="font-weight: bold;">To obtain supported parameters, examples, and requirements for a given subcommand, run:</p>

alcli <command> <subcommand> help

For example:

```

alcli aims authenticate help
```

This information is available in the Service Reference section as well.

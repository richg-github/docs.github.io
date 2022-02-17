# Configure an Update AWS WAF IP Set Task (Draft)

In your automated response playbook, you can configure an Update AWS WAF IP Set task to update an Amazon Web Services (AWS) WAF (web application firewall) IP set that controls access to a protected Amazon CloudFront distribution or regional application.

An IP set is a collection of IP addresses and ranges that you can use in an AWS WAF rule statement to perform actions such as blocking or unblocking IP addresses.

Complete the following steps to successfully configure the Update AWS WAF IP Set task:

1. [Create a connection target for the AWS IAM role](#CreateaconnectiontargetfortheAWSIAMrole)
2. [Add the task to your playbook](#Addthetasktoyourplaybook)
3. [Configure the task input](#Configurethetaskinput)
4. [Configure the task output (optional)](#Configurethetaskoutputoptional)

## Create a connection target for the AWS IAM role

The AWS WAF IP Set task requires a connection target for the AWS IAM role that grants Alert Logic access to perform updates to the AWS WAF IP set.

To check whether it exists,  in the Alert Logic console, click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure** in the navigation menu (![](../../../Resources/Images/dashboard/menu-icon.png)),  click **Connectors**, and then click the **Connection Targets** tab.

If any AWS IAM role connection targets appear in the list, review their configurations to determine whether the one you need already exists.

If you do not have a connection target for your AWS IAM role already, complete the instructions in [Configure AWS IAM Role Connection Target](../../../configure/connectors-beta/connection-targets/AWS-IAM-role.md).

## Add the task to your playbook

If you have not added the  task to your playbook, complete the instructions in [Add a task in the workflow diagram](../add-task.md#Addataskintheworkflowdiagram) and [Add task details (optional)](../add-task.md#Addtaskdetailsoptional).

## Configure the task input

Complete these instructions to provide the input values for your  Update AWS WAFIP Set task.

**To configure the task input:**

1. On the task **Input** tab, select the connection target in **AWS IAM Role Connection Target** that you created or identified in [Create a connection target for the AWS IAM role](#CreateaconnectiontargetfortheAWSIAMrole).
2. In **AWS Resource Scope**, select the scope of protection:
   * **REGIONAL**—Regional application
   * **CLOUDFRONT**—Amazon CloudFront distribution
4. Enter the AWS IPSet ARN in the field that corresponds to the version of the IP addresses in the IP set:
   * For IPv4, enter the ARN in **IPv4 IPSet ARN**.
   * For IPv6, enter the ARN in **IPv6 IPSet ARN**.
6. In **IP Addresses**, leave the YAQL expression `<% list(ctx().payload.attacker.ip) %>` to reference the attacker list in the incident payload, or enter a JSON-formatted list of IP addresses or ranges in CIDR notation.
7. (Optional) To automatically combine adjacent IP addresses into a CIDR range, select the **Combine Addresses** check box.
8. In **Update Type**, select the type of update to perform on the IP set:
   * **add**—Adds IP addresses to the IP set
   * **delete**—Removes IP addresses from the IP set
10. (Optional) If you want to validate whether the action would succeed but do not want to apply changes, select the **Dry Run** check box.
11. In **Additions Expiration in Minutes**, enter the time to leave added IPs in the IP set in minutes, or keep the default value: 60.

### Insert a YAQL expression in an input field

Any field that supports one or more [Yet Another Query Language](https://yaql.readthedocs.io/en/latest/) (YAQL) expressions has a **SELECT VARIABLE** drop-down list above the field. A YAQL expression can  reference a value in the playbook context, such as a field in the incident payload, or the published result of a previous task.

To insert a YAQL expression, place your cursor in the field where you want to insert the reference, click **SELECT VARIABLE**, and then select the variable. A YAQL expression that references the selected value appears in the field.

## Configure the task output (optional)

This task does not generate results that you can publish as output. For other ways to publish output, see [Configure task output (optional)](../add-task.md#Configuretaskoutputoptional).

## Technical reference

[Ideally this paragraph would state why the following information is useful, what to do with it...]

### Action Name

Update AWS WAF IP Set

### Action Type

waf_update_ip_set

### Permissions

[Include this section if needed. Example:  Azure permissions.]

### Limitations

[Include this section if needed. Example: This action only works in AWS regions supported by Alert Logic.]

<h1>Automated <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Deployment</h1><p>The purpose of this guide is to enable seamless deployment and configuration of <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> (MDR) in an <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account while taking full advantage of <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> and <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> automation.</p>

<p>This guide helps you understand how <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> interacts with <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> resources by providing a reference deployment architecture. It then outlines the steps required to automate deployment of that architecture. An alternative automated deployment architecture is available using <a href="control-tower.md">AWS Control Tower</a>.</p>

<p>To automate <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> deployment in <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> , you must use both <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> and <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> automation tools. This document outlines the complete process:</p>

<ol>
  <li>
    <a href="#Retrieve">Retrieve <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> IAM policy</a>
  </li>
  <li>
    <a href="#Create">Create IAM policy and third-party role using AWS Cloud Formation</a>
  </li>
  <li>
    <a href="#Provide">Provide <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> the third-party role</a>
  </li>
  <li>
    <a href="#Create2">Create an <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> deployment</a>
  </li>
  <li>
    <a href="#Automati">
      <MadCap:annotation MadCap:createDate="2020-06-15T12:47:48.7453136-05:00" MadCap:creator="kimberly.heintschel" MadCap:initials="KI" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" MadCap:comment="To make each of these an action, suggest changing the title to &amp;quot;Deploy AWS protection automatically'" MadCap:editor="kimberly.heintschel" MadCap:editDate="2020-06-15T12:48:15.9561774-05:00">Automatic deployment of AWS protection</MadCap:annotation>
    </a>
  </li>
</ol><p>After you complete this process, your <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account will be fully protected by the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> MDR platform.</p>

## Supported subscription types

<ul>
  <li>
    <MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
    <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
  <li>
    <MadCap:variable name="SDKVariables.SIEMless" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
    <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  </li>
</ul>## Deployment architecture

<p>The <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> deployment architecture in <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> provides three levels of service:</p>

* Asset discovery and continuous security protection
* Vulnerability scanning
* Network traffic and log analysis

<p>Automating deployment of <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> in <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> uses services and integrations in each protected <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account. All interactions with <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> services follow best practices, such as minimum privilege delegation, use of third-party IAM roles, and strong encryption.</p>

### Asset discovery

![](../Resources/Images/asset-discovery.png)

<MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> provides robust tools to automate the deployment process, and these tools enable a fully automated, hands-off deployment of <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> in <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />. <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> develops and maintains a real-time asset model of your <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />  resources such as instances, containers, and security groups.</p>

<p>Automated protection of an <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account requires integration with the following <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> services:</p>

<ul>
  <li>
    <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> IAM—Create a third party IAM role delegating permission to <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /></li>
  <li>
    <MadCap:variable name="SDKVariables.CloudTrail" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />—Create a Cloud Trail audit source, used to monitor changes to the environment</li>
  <li>
    <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> S3, SNS, SQS—Retrieve Cloud Trail log updates</li>
</ul><h3>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> MDR Essentials </h3>
![](../Resources/Images/essentials.png)

<MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> protection can be applied to individual VPCs, and it includes configuration auditing for common <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> security issues and host-based vulnerability scanning. <MadCap:annotation MadCap:createDate="2020-06-15T15:11:46.4319136-05:00" MadCap:creator="kimberly.heintschel" MadCap:initials="KI" MadCap:comment="Is this just saying, &amp;quot;An  EC2 instance performs asset discovery and vulnerability scanning.&amp;quot;" MadCap:editor="kimberly.heintschel" MadCap:editDate="2020-06-15T15:18:25.5792509-05:00" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd">In addition to the requirements for Asset Discovery, an EC2 instance is used to perform the vulnerability scanning.</MadCap:annotation></p>

<p>The <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> automation selects the most cost-effective scanning appliance for your environment and automatically shuts it down when there are no hosts to be scanned. This automation results in low overhead for providing security evaluation in your network.</p>

<p>Automated protection of an <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> VPC with Essentials requires integration with the following <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> services:</p>

<ul>
  <li>
    <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> EC2—<MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> scanning appliance</li>
  <li>
    <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> VPC— Security groups, route tables, and network ACLs to allow communication with <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> and between the scanning appliance and target hosts</li>
</ul><h3>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> MDR Professional</h3>
![](../Resources/Images/professional.png)

<MadCap:snippetBlock src="../Resources/Snippets/expand-image.flsnp" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /><p>
  <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />
  <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> protection can be applied to individual VPCs and includes all features of <MadCap:variable name="SDKVariables.Essentials" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />, plus log collection, integration with <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> <MadCap:variable name="SDKVariables.GuardDuty_2" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />, and network traffic analysis.</p>

<p>Automated protection of an <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> VPC with <MadCap:variable name="SDKVariables.Professional" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> requires integration with the following <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />  services:</p>

<ul>
  <li>
    <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> EC2—<MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> IDS appliance</li>
  <li>
    <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> VPC—Security groups, route tables, and network ACLs to allow communication with <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> and between the IDS appliance and protected hosts</li>
  <li>
    <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> <MadCap:variable name="SDKVariables.GuardDuty_2" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />, <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Config, <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> VPC Flow Logs—To configure protection of this account with <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> <MadCap:variable name="SDKVariables.GuardDuty_2" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />  and provide security findings to <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /></li>
</ul><h2>Deployment automation in <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />  and <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /></h2><p>To protect an <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account, you must create a deployment in the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> MDR platform. This deployment object references to <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> IAM policies used to interact with your environment and serves as the primary container for the assets contained in that <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account. Automating deployment requires the following steps, each of which can be automated.</p>

### Retrieve IAM policy

<p>Use the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> CLI to retrieve the latest full deployment policy for <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />. For details on other options, like minimal permission and policies for manual deployment, consult the Cloud Policies (themis) service reference.</p>

```

alcli themis get_role --account_id 12345678 --platform_type aws --role_type ci_full --role_version latest
```

This command returns a JSON document including:

<table style="width: 100%;">
  <col />
  <col />
  <tbody>
    <tr>
      <td>
        <kbd>aws_account_id</kbd>
      </td>
      <td>The <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account ID to establish a third-party trust relationship with </td>
    </tr>
    <tr>
      <td>
        <kbd>cft</kbd>
      </td>
      <td>References to download a Cloud Formation template that creates an IAM policy and third-party role as described here </td>
    </tr>
    <tr>
      <td>
        <kbd>external_id</kbd>
      </td>
      <td>Identifier used in the role to prevent confused deputy attacks from reusing this role for any other purpose</td>
    </tr>
    <tr>
      <td>
        <kbd>policy_document</kbd>
      </td>
      <td>IAM policy to be created </td>
    </tr>
  </tbody>
</table>
Sample response:

```

{ 
    "aws_account_id": "733251395267", 
    "cft": { 
        "s3_bucket": "alertlogic-cloud-formation-templates-733251395267", 
        "s3_key": "ci_full/2020-01-10", 
        "s3_url": "https://alertlogic-cloud-formation-templates-733251395267.s3.amazonaws.com/ci_full/2020-01-10" 
    }, 
    "external_id": "12345678", 
    "platform_type": "aws", 
    "policy_document": { 
        "Statement": [ 
            { 
                "Action": [ 
                    "autoscaling:Describe*", 
                    "cloudformation:DescribeStack*", 
                    "cloudformation:GetTemplate", 
                    "cloudformation:ListStack*", 
                    "cloudfront:Get*", 
                    "cloudfront:List*", 
                    "cloudwatch:Describe*", 
                    "config:DeliverConfigSnapshot", 
[…] 
                "Action": [ 
                    "iam:CreateServiceLinkedRole" 
                ], 
                "Effect": "Allow", 
                "Resource": "arn:aws:iam::*:role/aws-service-role/autoscaling.amazonaws.com/AWSServiceRoleForAutoScaling*", 
                "Sid": "EnableCreationOfServiceLinkedRoleForAutoscaling" 
            } 
        ], 
        "Version": "2012-10-17" 
    }, 
    "type": "ci_full", 
    "version": "2020-01-10" 
} 
```

<h3>
  <a name="Create"></a>Create IAM policy and third-party role using <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> CloudFormation</h3><p>The simplest way to create the IAM policy and role is using the <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Cloud Formation CLI; however, this task can be automated with many tools, including directly creating resources with the <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> CLI or using tools like Terraform. You can also <a href="https://docs.alertlogic.com/prepare/aws-full-permission-deployment.htm">use the AWS Console directly</a>.</p>

Run the following command to create the IAM policy and role:

<MadCap:codeSnippetCaption xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd"></MadCap:codeSnippetCaption>
```

aws --region us-east-1 cloudformation create-stack --stack-name "mystack" --template-url https://alertlogic-cloud-formation-templates-733251395267.s3.amazonaws.com/ci_full/2020-01-10 --parameters ParameterKey=ExternalId,ParameterValue=134279619 --capabilities CAPABILITY_IAM
```

Sample output:

```

{ 
    "StackId": "arn:aws:cloudformation:us-east-1:123456789012:stack/myteststack/466df9e0-0dff-08e3-8e2f-5088487c4896"
}
```

Using the CLI, describe the stack and retrieve the IAMRole output key:

```

} 
aws cloudformation describe-stacks --stack-name myteststack 
{ 
```

Sample output:

```

    "Stacks":  [ 
        { 
[…] 
            "Outputs": [ 
                { 
                    "Description": "IAM role", 
                    "OutputKey": "IAMRole", 
                    "OutputValue": "myteststack-iamrole-jsfai1zie2w" 
                } 
            ], 
[…] 
    ] 
```

The value of IAMRole will be used to create the credentials in the next step.

<h3>
  <a name="Provide"></a>Provide <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> the third-party role</h3><p>Use the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> CLI to save the Amazon resource of the role that was created. For more information, see the Credential Storage Service.</p>

Run the following command to store the IAM role ARN:

<MadCap:codeSnippetCaption xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd"></MadCap:codeSnippetCaption>
```

alcli deployments create_deployment --account_id 12345678 --name "My Deployment" --credentials '[{"id": “3009DAAC-BEDF-4663-9A9D-EF19FDBEA964”, "purpose": "discover"}]' --mode automatic --scope '{"exclude": [], "include": "key": "/aws/us-east-1", "policy": { "id": "D12D5E67-166C-474F-87AA-6F86FC9FB9BC" }, "type": "region" }'
```

Sample output:

```

    { 
        "created": { 
            "at": 1592170189, 
            "by": "0CC0ED48-22EA-407F-A6AA-89D802129067" 
        }, 
        "id": "6D85344C-660D-418E-9514-D248D558E7A8", 
        "name": "IAM Policy", 
        "secrets": { 
            "arn": "arn:aws:iam::123412341234:role/alertlogic-iam-role-ci-full", 
            "external_id": "12345678", 
            "type": "aws_iam_role" 
        }     
    } 
```

The IAM policy credential is identified by the id field, which will be used in the next step.

<h3>
  <a name="Create2"></a>Create an <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> deployment</h3><p>Use the <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> CLI to create a deployment record. This record describes the <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> account that will be protected and will include:</p>

<ul>
  <li>Human-readable name</li>
  <li>Reference to the credential for the IAM role created in the previous step</li>
  <li>Scope of protection: all VPCs in region us-east-1, with <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> Professional</li>
  <li>Deployment mode, “automatic” indicating that <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> will automatically install Cloud Trail and appliances as detailed in the architecture above</li>
</ul>
For details on other options, such as manual deployment modes, see the Deployments service reference.

Run the following command:

```

alcli deployments create_deployment --account_id 12345678 --name "My Deployment" --credentials '{"id": “3009DAAC-BEDF-4663-9A9D-EF19FDBEA964”, "purpose": "discover"}' --mode automatic --scope '{"exclude": [], "include": "key": "/aws/us-east-1", "policy": { "id": "D12D5E67-166C-474F-87AA-6F86FC9FB9BC" }, "type": "region" }'
```

Sample output:

```

{
        "account_id": "12345678",
        "cloud_defender": {
            "enabled": false,
            "location_id": "defender-us-ashburn"
        },
        "created": {
            "at": 1592170376,
            "by": "6D85344C-660D-418E-9514-D248D558E7A8"
        },
        "credentials": [
            {
                "id": "3009DAAC-BEDF-4663-9A9D-EF19FDBEA964",
                "purpose": "discover",
                "version": "2020-01-10"
            }
        ],
        "discover": true,
        "enabled": true,
        "id": "2D7DA803-6C82-4C14-8604-7392F2D4E53D",
        "mode": "automatic",
        "modified": {
            "at": 1592170376,
            "by": "6D85344C-660D-418E-9514-D248D558E7A8"
        },
        "name": "My Deployment",
        "platform": {
            "id": "123412341234",
            "monitor": {
                "ct_install_region": "us-east-1",
                "enabled": true
            },
            "type": "aws"
        },
        "scan": true,
        "scope": {
            "exclude": [],
            "include": [                { 
                    "key": "/aws/us-east-1",
                    "policy": {
                        "id": "D12D5E67-166C-474F-87AA-6F86FC9FB9BC"
                    },
                    "type": "region"
                }]
        },
        "status": {
            "status": "ok",
            "updated": 1592170376
        },
        "version": 1
    }
```

<h3>
  <a name="Automati"></a>Deploy <MadCap:variable name="SDKVariables.AWS" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> protection automatically</h3><p>In the previous step, an automatic mode deployment was created. Following creation, <MadCap:variable name="SDKVariables.Company" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" /> services will create all required resources  using the third-party IAM role that was provided. An IDS and scan appliance will be installed on each VPC in us-east-1 that contains at least one running EC2 instance.</p>

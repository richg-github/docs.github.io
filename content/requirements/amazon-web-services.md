# Requirements for Managed Detection and Response for Amazon Web Services (AWS)

## Supported AWS regions

Alert Logic supports the following AWS regions:

| AWS Region Name | Region | Endpoint |
|---|---|---|
| Africa (Cape Town) | af-south-1 |  |
| Asia Pacific (Hong Kong) | ap-east-1 | rds.ap-east-1.amazonaws.com |
| Asia Pacific (Tokyo) | ap-northeast-1 | autoscaling.ap-northeast-1.amazonaws.com |
| Asia Pacific (Seoul) | ap-northeast-2 | autoscaling.ap-northeast-2.amazonaws.com |
| Asia Pacific (Osaka-Local) | ap-northeast-3 | ec2.eu-west-3.amazonaws.com |
| Asia Pacific (Mumbai) | ap-south-1 | autoscaling.ap-south-1.amazonaws.com |
| Asia Pacific (Singapore) | ap-southeast-1 | autoscaling.ap-southeast-1.amazonaws.com |
| Asia Pacific (Sydney) | ap-southeast-2 | autoscaling.ap-southeast-2.amazonaws.com |
| Canada (Central) | ca-central-1 | autoscaling.ca-central-1.amazonaws.com |
| China (Beijing) | cn-north-1 | ec2.cn-north-1.amazonaws.com.cn |
| China (Ningxia) | cn-northwest-1 | ec2.cn-northwest-1.amazonaws.com.cn |
| Europe (Frankfurt) | eu-central-1 | autoscaling.eu-central-1.amazonaws.com |
| Europe (Stockholm) | eu-north-1 | rds.eu-north-1.amazonaws.com |
| Europe (Milan) | eu-south-1 |  |
| Europe  (Ireland) | eu-west-1 | autoscaling.eu-west-1.amazonaws.com |
| Europe  (London) | eu-west-2 | autoscaling.eu-west-2.amazonaws.com |
| Europe (Paris) | eu-west-3 | ec2.eu-west-3.amazonaws.com |
| Middle East (Bahrain) | me-south-1 | rds.me-south-1.amazonaws.com |
| South America (São Paulo) | sa-east-1 | autoscaling.sa-east-1.amazonaws.com |
| US East (N. Virginia) | us-east-1 | autoscaling.us-east-1.amazonaws.com |
| US East (Ohio) | us-east-2 | autoscaling.us-east-2.amazonaws.com |
| US West (N. California) | us-west-1 | autoscaling.us-west-1.amazonaws.com |
| US West (Oregon) | us-west-2 | autoscaling.us-west-2.amazonaws.com |

## Virtual appliance types in AWS

Review the following approved virtual appliance types. In the AWS marketplace, you should select the appropriate image based on the anticipated network throughput sent to the appliance, and whether you plan to enable vulnerability scanning.

| Supported Amazon instance names | Peak supported throughput |
| c5.large | 250 Mbps |
| c5.xlarge | 500 Mbps |
| c5.2xlarge | 1 Gbps |
| c5.4xlarge | 2 Gbps |

# AWS_wordpress_Project






# Deploying Wordpress using AWS Cloud Formation

## My Project Overview


In this project I am deploying a Wordpress using Cloud Formation. I will be using a template that was made using JSON.

When deploying a CloudFormation template, an AWS CloudFormation stack is created. This stack serves as a representation of the template's deployment, encompassing all modifications and updates made to the deployment throughout its lifecycle.

A CloudFormation stack can consist of various resource types, such as EC2 instances, S3 buckets, IAM users or policies, and Route53 record sets. Although the current template includes only one EC2 instance and an EC2 security group, stacks can be as intricate as desired, encompassing numerous diverse resource types.

-   Two resources are defined, an Amazon EC2 instance, and an EC2 security group
-   A tool called [cfn-init](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-init.html) is installed on the instance
-   cfn-init makes use of [AWS::CloudFormation::Init](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-init.html) configuration metadata in the template on the EC2 instance
-   The init metadata sets up and configures WordPress when the instance is launched





## My Process

### Steps I took to create wordpress using cloud formation.
1. log into the console and search CloudFormation.
<a href="https://ibb.co/wsjtzjF"><img src="https://i.ibb.co/FVCpDCL/image-20230314142832-1-3b28c45a-7297-4433-947c-028c472ce820.png" alt="image-20230314142832-1-3b28c45a-7297-4433-947c-028c472ce820" border="0"></a>

2. Create a aws cloudformation stack

<a href="https://ibb.co/cCLK8qR"><img src="https://i.ibb.co/z7JW2dC/Screenshot-2023-06-27-at-4-31-18-PM.png" alt="Screenshot-2023-06-27-at-4-31-18-PM" border="0"></a>

3. Check the status of the stack. view events and output.
<a href="https://ibb.co/ynMfZ4r"><img src="https://i.ibb.co/XZd2KYq/Screenshot-2023-06-22-at-4-41-35-PM.png" alt="Screenshot-2023-06-22-at-4-41-35-PM" border="0"></a>
<a href="https://ibb.co/nDvFgXt"><img src="https://i.ibb.co/fC5s13L/Screenshot-2023-06-27-at-5-06-14-PM.png" alt="Screenshot-2023-06-27-at-5-06-14-PM" border="0"></a>

4. View resources of the JSON code (wordpress)
```
"Resources": {
    "WebServerSecurityGroup": {
      "Type": "AWS::EC2::SecurityGroup",
      "Properties": {
        "GroupDescription": "Enable HTTP access via port 80 locked down to the load balancer + SSH access",
        "VpcId": {
          "Ref": "VpcId"
        },
        "SecurityGroupIngress": [{
          "IpProtocol": "tcp",
          "FromPort": "80",
          "ToPort": "80",
          "CidrIp": "0.0.0.0/0"
        }, {
          "IpProtocol": "tcp",
          "FromPort": "22",
          "ToPort": "22",
          "CidrIp": {
            "Ref": "SSHLocation"
          }
        }]
      }
    },
```

5. And finally here is a visual representation of the stack.

<a href="https://ibb.co/42zP0HS"><img src="https://i.ibb.co/HC6n9jP/image-20230315105058-4-8ca9a443-a106-4d04-b433-e6759b713f4b.png" alt="image-20230315105058-4-8ca9a443-a106-4d04-b433-e6759b713f4b" border="0"></a>




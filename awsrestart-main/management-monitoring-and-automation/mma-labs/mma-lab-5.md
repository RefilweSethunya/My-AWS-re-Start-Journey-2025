# Management, Monitoring and Automation Lab: CloudFormation - Automating Deployments with AWS CloudFormation

## Objective
This lab demonstrates how AWS CloudFormation can be used to automate infrastructure deployment in a consistent and reliable way.<br>Instead of relying on manual procedures, CloudFormation allows infrastructure to be defined in templates that can be deployed automatically, even on a schedule.

## Steps Taken
1. Logged into AWS Management Console
2. Deployed a CloudFormation Stack
   - AWS Management Console Services > CloudFormation > Create stack > Upload a template file
   - On the Specify Details page, configure:
     - Stack name: Lab
   - Next > Next > Create Stack
3. Added an Amazon S3 Bucket to the Stack
   - Update the template by adding these lines in the Parameters section:
      ``` yaml
      MyS3Bucket:
      Type: AWS::S3::Bucket
      ```
   - Updated the template to add an Amazon s3 bucket with propeties as follows:
     ``` yaml
   - Updates the stack with revised template file
5. Added an Amazon EC2 Instance to the Stack
   - Updated the template by adding these lines in the Parameters section:
      ``` yaml
      AmazonLinuxAMIID:
      Type: AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>
      Default: /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2
      ```
   - Updated the template to add an Amazon EC2 instance with propeties as follows:
     - ImageId: Refer to AmazonLinuxAMIID
       ``` yaml
       ImageId:
        - !Ref AppImageId
       ```
     - InstanceType: t3.micro
     - SecurityGroupIds: Refer to AppSecurityGroup
       ``` yaml
       SecurityGroupIds:
        - !Ref AppSecurityGroup
       ```
     - SubnetId: Refer to PublicSubnet
       ``` yaml
       SubnetId:
        - !Ref AppSubnetId
       ```
     - Tags:
         ``` yaml
         Tags:
                 - Key: Name
                   Value: App Server
         ```
   - Updated the stack with revised template file
6. Deleted the Stack
   - In the CloudFormation console, selected  Lab > Delete > Delete Stack

## Challenges
- ...

## Screenshot


## Takeaways

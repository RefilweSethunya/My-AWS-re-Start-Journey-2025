# Management, Monitoring and Automation Lab: CloudFormation - Automating Deployments with AWS CloudFormation

## Objective
This lab demonstrates how AWS CloudFormation can be used to automate infrastructure deployment in a consistent and reliable way.<br>Instead of relying on manual procedures, CloudFormation allows infrastructure to be defined in templates that can be deployed automatically, even on a schedule.

## Steps Taken
1. Logged into AWS Management Console
2. Deployed a CloudFormation Stack
   - 
3. Added an Amazon S3 Bucket to the Stack
   - 
4. Added an Amazon EC2 Instance to the Stack
   - Updated the template by adding these lines in the Parameters section:
   - Updated the template to add an Amazon EC2 instance with propeties as follows:
     - ImageId: Refer to AmazonLinuxAMIID
     - InstanceType: t3.micro
     - SecurityGroupIds: Refer to AppSecurityGroup
     - SubnetId: Refer to PublicSubnet,
     - Tags:
      ``` yaml
      Tags:
              - Key: Name
                Value: App Server
      ```
   - Updated the stack with revised template file
5. Deleted the Stack
   - In the CloudFormation console, selected  Lab > Delete > Delete Stack

## Challenges
- ...

## Screenshot


## Takeaways

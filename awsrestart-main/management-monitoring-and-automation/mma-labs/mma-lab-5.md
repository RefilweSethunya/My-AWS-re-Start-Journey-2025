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
   - Update the template by adding these lines in the Resources section to add an Amazon s3 bucket:
      ``` yaml
      MyS3Bucket:
      Type: AWS::S3::Bucket
      ```
   - Updated the stack with revised template file
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
       ImageId: !Ref AmazonLinuxAMIID
       ```
     - InstanceType: t3.micro
     - SecurityGroupIds: Refer to AppSecurityGroup
       ``` yaml
       SecurityGroupIds:
        - !Ref AppSecurityGroup
       ```
     - SubnetId: Refer to PublicSubnet
       ``` yaml
       SubnetId: !Ref PublicSubnet
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
Cloud Formation Template (task1.yaml)
<img width="1366" height="737" alt="image" src="https://github.com/user-attachments/assets/f87bf446-9ecc-437f-b7f7-d6a9c074af2e" />
Creating Stack 
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/31168014-ae4b-4c32-b0ce-b3dbd0e63786" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/3fb8bd8c-443d-4b02-86c0-c804a12164ff" />
Creating Stack Complete
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/11cd242f-029a-417f-ad96-bd6555bc7887" />
Revised Template(Add Amazon S3 Bucket)
<img width="1366" height="254" alt="image" src="https://github.com/user-attachments/assets/38a7f563-e5c4-4c9e-b4c5-f504b21b9e43" />
Updating the Stack with revised template(Add Amazon S3 Bucket)
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/59b7fed0-d388-4621-8303-633d1df7868b" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/715c2c39-70de-49a4-b1d0-8a802bce9285" />
Updating Stack Complete(Add Amazon S3 Bucket)
<img width="1366" height="667" alt="image" src="https://github.com/user-attachments/assets/7f9934b5-3478-4971-ba3c-40a39c5ac987" />
Confirming at the S3 console to see the bucket that was created
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/111801b3-6321-4519-8576-bbc91bea2301" />
<br>
Revised Template(Add Amazon EC2)
<img width="1366" height="440" alt="image" src="https://github.com/user-attachments/assets/53db9ebf-6e5f-47c5-8691-f844b5f8efc3" />
Updating the Stack with revised template(Add Amazon EC2)
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/1dde81c2-bbb4-404f-bd7a-b2d0a0aee86d" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/e2bf8453-d39d-4d7f-93e4-712bddc98f06" />
Updating Stack Complete(Add Amazon EC2)
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/512c92d6-93a9-4f23-89e8-d8f8a97ee6a0" />
Confirming at the EC2 console to see the App Server that was created
<img width="1366" height="628" alt="image" src="https://github.com/user-attachments/assets/81a93160-00db-4511-9897-d7dfe0d55eb9" />

Delete Stack
<img width="1366" height="482" alt="image" src="https://github.com/user-attachments/assets/f4666e38-3361-4256-816e-5bce65971bd9" />
<img width="1366" height="431" alt="image" src="https://github.com/user-attachments/assets/bc06363c-6ec2-4ab7-b3c2-d6a211818c17" />
<img width="1366" height="505" alt="image" src="https://github.com/user-attachments/assets/6170b2ec-7f39-4160-b8a3-6f076d78ed35" />


## Takeaways
When a CloudFormation stack is deleted, CloudFormation will automatically delete the resources that it created.

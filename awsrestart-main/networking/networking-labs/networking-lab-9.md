# Networking Lab: Troubleshoot a VPC

## Objective
Create VPC Flow Logs, troubleshoot VPC configuration issues and analyze flow logs of an environment that includes two VPCs, Amazon Elastic Compute Cloud (Amazon EC2) instances and other networking components shown in the following diagram.

<img width="1458" height="744" alt="image" src="https://github.com/user-attachments/assets/1dfccdac-c71a-4cce-a5fd-b82fd4976a9f" />


## Steps Taken
1. Logged into AWS Management Console
2. Connected to the CLI Host instance
   - select CLI Host instance
   - Connect > EC2 Instance Connect > Connect
3. Configured the AWS CLI profile with credentials
``` bash
aws configure
```
4. Created an S3 bucket to publish data from VPC Flow Logs
``` bash
aws s3api create-bucket --bucket flowlog###### --region 'us-west-2' --create-bucket-configuration LocationConstraint='us-west-2'
```
where ###### is random numbers and flowlog###### is my bucket name

5. Created VPC Flow Logs on VPC1 to capture information about IP traffic between network interfaces in VPC1
   - Obtained VPC ID
     ``` bash
     aws ec2 describe-vpcs --query 'Vpcs[*].[VpcId,Tags[?Key==`Name`].Value,CidrBlock]' --filters "Name=tag:Name,Values='VPC1'"
     ```
   - Created VPC Logs. Replacing <flowlog######> with the bucket name and <vpc-id> with the VPC ID from the previous steps. Command output returns FlowLogIds and a ClientToken.
     ``` bash
     aws ec2 create-flow-logs --resource-type VPC --resource-ids <vpc-id> --traffic-type ALL --log-destination-type s3 --log-destination arn:aws:s3:::<flowlog######>
     ```
    - Confirmed log was created
      ``` bash
      aws ec2 describe-flow-logs
      ``` 


## Challenges
- ...

## Screenshot
CLI Host Instance Connection and CLI profile Configuration

S3 bucket created

The VPC flow logs are then published to the S3 bucket.

## Takeaways
After completing this lab, my understanding of how VPC Flow Logs provide visibility into network traffic and are used to diagnose connectivity issues is reinforced.

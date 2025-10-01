# Compute Lab: Creating Amazon EC2 Instances

## Objective
Launch an EC2 instance by using the AWS Management Console; connect to the EC2 instance by using EC2 Instance Connect; and Launch an EC2 instance by using the AWS CLI.
<img width="928" height="702" alt="image" src="https://github.com/user-attachments/assets/78e7498c-2bc5-44ab-847b-12c2550bcfdb" />


## Steps Taken
1. Logged into the AWS Management Console and Launched an EC2 Instance
   - AWS Management Console > EC2 > Launch instance > Launch instance
   - Name and tags section, configured Name: Bastion host
   - Application and OS Images (Amazon Machine Image) section, for Quick Start, selected Amazon Linux
   - Instance type: t3.micro
   - Key pair (login) section, from the Key pair name: chose Proceed without key pair (Not recommended)
   - VPC : chose Lab VPC
   - Subnet : Public Subnet
   - Auto-assign public IP : Enabled
   - Firewall (security groups) section > Create security group > Configured Security group name: Bastion security group and Description: Permit SSH connections
   - Advanced details > IAM instance profile > chose Bastion-Role
   - Launch Instance
2. Logged in to the bastion host
   - On the EC2 Management Console, from the list of EC2 instances displayed, selected the bastion host instance check box
   - On the EC2 Instance Connect tab > Connect
3. Launched an EC2 instance using the AWS CLI
   - Retrive the AMI with the following script
``` bash
#Set the Region
AZ=`curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone`
export AWS_DEFAULT_REGION=${AZ::-1}
#Retrieve latest Linux AMI
AMI=$(aws ssm get-parameters --names /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2 --query 'Parameters[0].[Value]' --output text)
echo $AMI
```
  - Retrieve the subnet to use
``` bash
SUBNET=$(aws ec2 describe-subnets --filters 'Name=tag:Name,Values=Public Subnet' --query Subnets[].SubnetId --output text)
echo $SUBNET
```
  - Retrieve the SG to use
``` bash
SG=$(aws ec2 describe-security-groups --filters Name=group-name,Values=WebSecurityGroup --query SecurityGroups[].GroupId --output text)
echo $SG
```
  - Download a user data script
``` bash
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RSJAWS-1-23732/171-lab-JAWS-create-ec2/s3/UserData.txt
```
  - Launch the instance
``` bash
INSTANCE=$(\
aws ec2 run-instances \
--image-id $AMI \
--subnet-id $SUBNET \
--security-group-ids $SG \
--user-data file:///home/ec2-user/UserData.txt \
--instance-type t3.micro \
--tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=Web Server}]' \
--query 'Instances[*].InstanceId' \
--output text \
)
echo $INSTANCE
```
  - Monitor status of the instance
``` bash
aws ec2 describe-instances --instance-ids $INSTANCE
```

 - Test the web server. Obtain Public DNS and open in browser
``` bash
aws ec2 describe-instances --instance-ids $INSTANCE --query Reservations[].Instances[].PublicDnsName --output text
```



## Challenges
- 

## Screenshot
EC2 Configuration
<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/4d37f934-f249-46d6-968a-486e35613664" />
<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/b339c0a8-0bbd-4d9f-bff2-9b849e9ac895" />
Bastion Host Login
<img width="1366" height="636" alt="image" src="https://github.com/user-attachments/assets/d9a65687-b117-4aad-8350-c3b6861057a1" />
<img width="1366" height="642" alt="image" src="https://github.com/user-attachments/assets/a57b988f-18da-4240-af1f-244d81c0dd1f" />

Retrieve AMI
<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/e0a90bdc-a9e0-4973-8f40-301de432466f" />
Retrieve Subnet
<img width="1366" height="247" alt="image" src="https://github.com/user-attachments/assets/b0e96b93-a0e6-4348-b864-19797135a39e" />
Retrieve SG
<img width="1366" height="213" alt="image" src="https://github.com/user-attachments/assets/20d15e98-8e98-4edd-8160-a1766c928021" />
Download User Data Script
<img width="1366" height="384" alt="image" src="https://github.com/user-attachments/assets/912999e2-e6ae-43ab-9e21-1bab04448692" />
Launch Instance
<img width="1366" height="399" alt="image" src="https://github.com/user-attachments/assets/ca38c502-f125-4b82-a484-3f717d66ae1d" />
Retrieve Public DNS
<img width="1366" height="201" alt="image" src="https://github.com/user-attachments/assets/66ce6848-595a-4675-b421-a3dcb26f29e5" />
Test the Web browser
<img width="1295" height="481" alt="image" src="https://github.com/user-attachments/assets/fdbefb96-0bcd-4d01-a8fa-39cd24a2c414" />

## Takeaways
The AWS CLI makes it possible to programmatically access and control AWS services. After placing these commands in a script we are able to run them as a standard process to deploy consistent, reliable infrastructure with minimal scope for human error.

When choosing a method we should consider the following:
Launch from the management console when you quickly need to launch a one-off or temporary instance;
Launch by using a script when you need to automate the creation of an instance in a repeatable, reliable manner;
Launch by using CloudFormation when you want to launch related resources together.

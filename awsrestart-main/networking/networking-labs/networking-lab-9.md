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
4. Created VPC Flow Logs on VPC1 to capture information about IP traffic between network interfaces in VPC1
   - Created an S3 bucket to publish data from VPC Flow Logs. where ###### is random numbers and flowlog###### is my bucket name
``` bash
aws s3api create-bucket --bucket flowlog###### --region 'us-west-2' --create-bucket-configuration LocationConstraint='us-west-2'
```
   - Obtained VPC ID
 ``` bash
     aws ec2 describe-vpcs --query 'Vpcs[*].[VpcId,Tags[?Key==`Name`].Value,CidrBlock]' --filters "Name=tag:Name,Values='VPC1'"
 ```
   - Created VPC Logs. Replacing <flowlog######> with the bucket name and <vpc-id> with the VPC ID from the previous steps. Command output returns FlowLogIds and a ClientToken.
 ``` bash
     aws ec2 create-flow-logs --resource-type VPC --resource-ids <vpc-id> --traffic-type ALL --log-destination-type s3 --log-destination arn:aws:s3:::<flowlog######>
 ```
   - Log creation confirmed
``` bash
      aws ec2 describe-flow-logs
``` 
6. Troubleshot VPC configuration issues to allow access to resources
   - Investigate in the CLI Host terminal why I cannot reach WebServer. Replacing <WebServerIP> with the WebServerIP address 
   ``` bash
   aws ec2 describe-instances --filter "Name=ip-address,Values='<WebServerIP>'"
   ```
   - Filter the results of above commands. Replacing <WebServerIP> with the WebServerIP address
   ``` bash
   aws ec2 describe-instances --filter "Name=ip-address,Values='<WebServerIP>'" --query 'Reservations[*].Instances[*].[State,PrivateIpAddress,InstanceId,SecurityGroups,SubnetId,KeyName]'
   ```
7. Connected to Cafe Web Server instance
   - Connect > EC2 Instance Connect tab > Connect
   - I got an error on the browser window that says, "Failed to connect to your instance.". This behaviour is expected
8. Using only AWS CLI programmatic access, troubleshot why the web server instance was running but the webpage was not loading. 
   -  Use the nmap utility to check which ports are open on the web server EC2 instance. First install the utility on the CLI Host instance
     ``` bash
     sudo yum install -y nmap
     ```
   - Then run the nmap command. Replacing <WebServerIP> with the actual public IP address
     ``` bash
     nmap <WebServerIP>
     ```
   -  Check the security group details.  The web server EC2 instance must allow connectivity to port 22.
     ``` bash
     aws ec2 describe-security-groups
     ```
     ``` bash
      aws ec2 describe-security-groups --group-ids 'WebServerSgId'
     ```
   - Return the security group ID
     ``` bash
     describe-instances
     ```
   - Return the gateway-id
     ``` bash
     aws ec2 describe-internet-gateways
     ```
   - analyze the resulting output
     ``` bash
     describe-security-groups
     ```
   - Checked route tables
     ``` bash
     aws ec2 describe-route-tables
     ```
     Or with filter. Replacing VPC1PubSubnetID and VPC1PubRouteTableId with the values 
     ``` bash
     aws ec2 describe-route-tables  --route-table-ids 'VPC1PubRouteTableId' --filter "Name=association.subnet-id,Values='VPC1PubSubnetID'"
     ```
   - To add a new route, one must know the route-table-id and gateway-id to successfully create a route.
     ``` bash
      aws ec2 create-route --route-table-id 'VPC1PubRouteTableId' --gateway-id  'VPC1GatewayId' --destination-cidr-block '0.0.0.0/0'
     ```
9. While troubleshooting I created some useful entries in the flow logs. The following is some commands to you query the flow logs to observe the activities captured
   - To download and extract flow logs
     Creates a local directory where you can download the flow log files
     ``` bash
     mkdir flowlogs
     ```
     Changes the directory to the new directory
     ``` bash
     cd flowlogs
     ```
     Lists the s3 buckets
     ``` bash
     aws s3 ls
     ```
     Downloads the flow logs
     ``` bash
     aws s3 cp s3://<flowlog######>/ . --recursive
     ```
     Extracts the logs
     ``` bash
     gunzip *.gz
     ```
   - To analyze the flow logs
     Searches each log file in the current directory and returns lines that contain the word REJECT
     ``` bash
     grep -rn REJECT
     ```
     Finds out how many records were returned
     ``` bash
     grep -rn REJECT . | wc -l
     ```
     Finds out how many records were returned but filters lines that contain 22 which is the port number we attemepted to access
     ``` bash
     grep -rn 22 . | grep REJECT
     ```
     ``` bash
     grep -rn 22 . | grep REJECT | grep <ip-address>
     ```

## Challenges
- ...

## Screenshot
CLI Host Instance Connection 
<img width="1366" height="635" alt="image" src="https://github.com/user-attachments/assets/7e5693de-e89d-49f5-a956-5e48184c80b1" />
CLI profile Configuration
<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/6ee60cdd-c70b-4241-b16a-d7737ec034dc" />


S3 bucket Configuration (bucket = flowlog779618). The VPC flow logs Configuration. (VPC ID =vpc-0e7ee32cc7b4c186e) They will be published to the S3 bucket
<img width="1366" height="635" alt="image" src="https://github.com/user-attachments/assets/800b4f0d-0a6a-4f2a-b4cd-7fd116aebffd" />

VPC ID Query
<img width="1366" height="319" alt="image" src="https://github.com/user-attachments/assets/bc36f981-bf54-4e52-942b-ca2db1746b27" />

aws ec2 create-flow-logs --resource-type VPC --resource-ids <vpc-043b6fc5056481f87> --traffic-type ALL --log-destination-type s3 --log-destination arn:aws:s3:::<flowlog779618>
<img width="1366" height="348" alt="image" src="https://github.com/user-attachments/assets/488192fe-8c01-47a5-a7f0-62a0875ea1e9" />

Cannot reach WebServerIP pasted on browser (https://44.248.150.3/)
<img width="1366" height="724" alt="image" src="https://github.com/user-attachments/assets/fc48c193-4a4c-48c9-8910-318e11aa42f4" />


## Takeaways
After completing this lab, my understanding of how VPC Flow Logs provide visibility into network traffic and are used to diagnose connectivity issues is reinforced.

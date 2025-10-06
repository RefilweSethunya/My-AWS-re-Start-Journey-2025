# Management, Monitoring and Automation Lab: Working with AWS CloudTrail

## Objective
Learn how to create an AWS CloudTrail trail that audits actions taken in your account. Then investigate to determine who modified the Café website.<br>
<img width="814" height="437" alt="image" src="https://github.com/user-attachments/assets/463b70b3-3238-4266-afc6-861f883bd227" />


## Steps Taken
1. Logged into AWS Management Console
2. Modified the security group and observed the website
   - EC2 > Instances > Café Web Server (WebSecurityGroup) instance > Security > sg-xxx security group > Inbound rules tab > Edit inbound rules > Add rule > configure the rule as follows:
     - Type: SSH
     - Port Range: 22
     - Source: My IP
   - EC2 > Instances > Café Web Server instance > Details
   - Copied Public IPv4 address value and opened a new browser tab http://<WebServerIPv4address>/cafe/ and observed
3. Created a CloudTrail log and observed the hacked website
   - Management & Governance > CloudTrail > Trails > Create Trail > Configured as follows:
     - Trail name: monitor
     - Selected create a new s3 bucket
     - Trail log bucket and folder:  monitoring#### (where the #### characters are four random digits)
     - AWS KMS alias: myinitials followed by -KMS (for example, RSK-KMS)
   - Next > Next > Create Trail
   - EC2 > Instances > Café Web Server (WebSecurityGroup) instance > Security > sg-xxx security group > Inbound rules tab
   - Observed to see that someone else created an additional inbound rule that allows Secure Shell (SSH) access from anywhere (0.0.0.0/0)
   - Who added this security hole? I searched the CloudTrail logs using grep and Athena in the next steps to find out
4. Analyzed the CloudTrail logs by using grep Linux utility
   - Connected to the Café Web Server host EC2 instance by using SSH
     - Created a local directory on the web server to download the CloudTrail log files to:
       ``` bash
       mkdir ctraillogs
       ```
     - Changed the directory to the new directory:
       ``` bash
       cd ctraillogs
       ```
     - Listed the buckets:
       ``` bash
       aws s3 ls
       ```
   - Downloaded and extracted the CloudTrail logs
     - Downloaded the CloudTrail logs:
       ``` bash
       aws s3 cp s3://<monitoring####>/ . --recursive
       ```
     - The log files end in json.gz which indicates that they are compressed as GNU zip files so I ran the following command to extract the logs:
       ``` bash
       gunzip *.gz
       ```
   - Analyzed the logs by using grep
     - Analyzed structure of the logs:
       ``` bash
       cat <filename.json> | python -m json.tool
       ```
     - Set the WebServerIP address as a variable for use in future commands:
       ``` bash
       ip=<WebServerIP>
       ```
     - Filtered log entries for the source IP Address:
       ``` bash
       for i in $(ls); do echo $i && cat $i | python -m json.tool | grep sourceIPAddress ; done
       ```
     - Filtered log entries for the event name:
       ``` bash
       for i in $(ls); do echo $i && cat $i | python -m json.tool | grep eventName ; done
       ```
   - Analyze the logs by using AWS CLI CloudTrail commands
     - Run the following command to find any actions that were taken on security groups in the AWS account
     - Run the following commands to find the security group ID that is used by the Café Web Server instance, and then echo the result to the terminal:
     - filter your AWS CLI CloudTrail command results:
6. Analyzed the CloudTrail logs by using Athena
7. Analyzed the hack further and improved security

## Challenges
- ...

## Screenshot


## Takeaways
Useful for CloudTrail API Reference. It provides descriptions of actions, data types, common parameters, and common errors for CloudTrail
https://docs.aws.amazon.com/cli/latest/reference/cloudtrail/

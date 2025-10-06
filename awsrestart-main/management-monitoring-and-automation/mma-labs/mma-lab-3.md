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
     - To filter the trail for console logins:
       ``` bash
       aws cloudtrail lookup-events --lookup-attributes AttributeKey=EventName,AttributeValue=ConsoleLogin
       ```
     - To find any actions that were taken on security groups in the AWS account:
       ``` bash
       aws cloudtrail lookup-events --lookup-attributes AttributeKey=ResourceType,AttributeValue=AWS::EC2::SecurityGroup --output text
       ```
     - To find the security group ID that is used by the Café Web Server instance, and then echo the result to the terminal:
         ``` bash
         region=$(curl http://169.254.169.254/latest/dynamic/instance-identity/document|grep region | cut -d '"' -f4)
         sgId=$(aws ec2 describe-instances --filters "Name=tag:Name,Values='Cafe Web Server'" --query 'Reservations[*].Instances[*].SecurityGroups[*].[GroupId]' --region $region --output text)
         echo $sgId
         ```
     - To filter my AWS CLI CloudTrail command results:
       ``` bash
       aws cloudtrail lookup-events --lookup-attributes AttributeKey=ResourceType,AttributeValue=AWS::EC2::SecurityGroup --region $region --output text | grep $sgId
       ```
5. Analyzed the CloudTrail logs by using Athena
   - Created the Athena table
     - AWS Management Console Services > CloudTrail > Event history > Create Athena table
     - Storage location: monitoring####
     - Create table > Create table
   - Analyzed logs using Athena
     - AWS Management Console Services > Analytics > Athena > Athena Query Editor > Explore query editor
     - Set up a query results location and then running a simple query:
       - Settings > Manage > Configured Location of query result to s3://monitoring####/results/ > Save
       - Selected Editor table and pasted the following SQL query into the Query 1 panel. Replacing #### with the numbers in my actual table, and clicked Run:
       ``` sql
       SELECT *
       FROM cloudtrail_logs_monitoring####
       LIMIT 5
       ```
     - Run a new query that selects only those columns that were previously mentioned:
      ``` sql
      SELECT useridentity.userName, eventtime, eventsource, eventname, requestparameters
      FROM cloudtrail_logs_monitoring####
      LIMIT 30
      ```
6. Analyzed the hack further and improved security (secured both my AWS account and the web server instance)
   - Checked the OS users
   - Updated SSH security
     - Analyzed SSH settings on the instance
       ``` bash
       sudo ls -l /etc/ssh/sshd_config
       ```
     - Edited the SSH configuration file in the VI editor:
       ``` bash
       sudo vi /etc/ssh/sshd_config
       ```
     - Restarted the SSH service for changes to go into effect
       ``` bash
       sudo service sshd restart
       ```
     - Deleted the inbound rule hacker created (inbound rule that allows port 22 access from 0.0.0.0/0)
       - EC2 > Instances > Café Web Server (WebSecurityGroup) instance > Security > sg-xxx security group > Inbound rules tab > Edit inbound rules > Select rule and deleted it
   - Fixed the website
     - Navigated to the directory where the website image files are held
         ``` bash
         cd /var/www/html/cafe/images/
         ls -l
         ```
     - Restored the original graphic on the website
         ``` bash
         sudo mv Coffee-and-Pastries.backup Coffee-and-Pastries.jpg
         ```
     - Reloaded the website to test
       Got to http://WebServerIP/cafe 
   - Deleted the AWS hacker user
     - AWS Management Console Services > IAM > Users > selected the check box next to the chaos user > Delete > Delete
   

## Challenges
- ...

## Screenshot


## Takeaways
I deepened my understanding of how Amazon Athena can be used to query CloudTrail logs stored in S3 with standard SQL, making it possible and easy to search and analyze log data as if it were in a database.<br>
Alternatively, we can programmatically use AWS CloudTrail commands. The CloudTrail API Reference provides descriptions of actions, data types, common parameters, and common errors for CloudTrail. 
For future reference I have also listed it along with other useful links at [More Resources](../awsrestart-main/resources/helpful-links.md)

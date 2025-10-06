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
     - AWS Management Console Services > Amazon Athena
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
- MY browser was caching the images on the website so I had to open in another browser.

## Screenshot
<img width="1366" height="573" alt="image" src="https://github.com/user-attachments/assets/7b6f7ab8-64aa-410c-97b6-772e599b6149" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/2d55ddbf-c05f-4966-ae70-05bfee0b16c4" />
<img width="1366" height="724" alt="image" src="https://github.com/user-attachments/assets/24da4706-14e8-42b3-97eb-6b2725fe45be" />
<img width="1305" height="625" alt="image" src="https://github.com/user-attachments/assets/9fba7c71-8297-4ce1-b6cd-5830895608bb" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/1a68e29a-4da8-4348-b20d-b897da00e6ca" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/a21e5968-825a-48ea-b93e-ded3e3fc160f" />
I'VE BEEN HACKED AND TROLLED WITH A CHEEKY MONKEY IMAGE ON MY WEBSITE!
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/cea4cdc6-25a9-4a43-bfa8-8b7b07502610" />
One extra entry on my Inbound rules
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/54e63535-7dcb-4231-b662-98a23086fb94" />
<img width="1366" height="367" alt="image" src="https://github.com/user-attachments/assets/5f55d84b-64a1-4eb8-b029-55cec29dd3f0" />
<img width="1366" height="192" alt="image" src="https://github.com/user-attachments/assets/8c343e44-f583-4a40-9b17-184018c44526" />
<img width="1366" height="404" alt="image" src="https://github.com/user-attachments/assets/fb5c734e-f4d5-410d-8f78-aa21ee3237da" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/8e8709bf-0b79-466f-84c5-67b05bb44acd" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/ccac1fb7-8c34-4ce8-9773-c60c00b23ea6" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/5505ce89-1598-40cc-a7f9-5d1938319434" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/09dc96a8-8714-4c33-8dd1-08a398cc2a2c" />
<img width="1366" height="163" alt="image" src="https://github.com/user-attachments/assets/a3fd3241-68c5-46bc-a63e-d243ade096e6" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/3c116482-a60d-4d03-b57d-5336cf6a2b69" />
Using Athena
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/7de921d7-22c5-4b8b-bcc3-c3da3cd2dec2" />
<img width="1366" height="401" alt="image" src="https://github.com/user-attachments/assets/c3fe4139-8da4-4e4b-8c32-03d77b71cfe0" />
<img width="1366" height="678" alt="image" src="https://github.com/user-attachments/assets/ce11d477-266e-4efb-832c-2c32b70f3669" />
<img width="1366" height="364" alt="image" src="https://github.com/user-attachments/assets/a20a48f1-5190-435a-8ab7-7416ba1bd534" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/7f76eada-0d93-4007-984f-61c3fe70ccdf" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/8743600a-b0f2-4a63-8b69-e66485591e85" />
<img width="1366" height="677" alt="image" src="https://github.com/user-attachments/assets/75f25bcf-4f3a-46d8-a035-bcd7810a1e84" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/b3d41771-532a-4cfd-ab6e-cbfac8df1b7d" />
I FOUND THE CULPRIT
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/895c27b5-9428-4ff4-b06f-429e411b3214" />
<img width="1366" height="405" alt="image" src="https://github.com/user-attachments/assets/01b8246b-427e-4626-a274-13227de7cf8a" />

Checking the OS USERS
<img width="1366" height="540" alt="image" src="https://github.com/user-attachments/assets/2f3e0bbe-17a5-4473-bfaf-6d4330c367f9" />
<img width="1366" height="103" alt="image" src="https://github.com/user-attachments/assets/a8733bf9-9d53-41a6-ac79-dd7b82f5f929" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/85cb6973-4f88-47ff-8547-c826fdcf075a" />
<img width="1366" height="69" alt="image" src="https://github.com/user-attachments/assets/bd46e235-b6fc-440f-9945-1ef785e2dfdd" />
Deleting Inbound Rule(Hacker Created)
<img width="1366" height="361" alt="image" src="https://github.com/user-attachments/assets/0ab98d24-0aca-45e1-9dab-d933f3bf2f71" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/4eaf251c-3b5a-44be-90bb-6e0cc135777f" />

Deleting chaos User
<img width="1366" height="394" alt="image" src="https://github.com/user-attachments/assets/9bdce85f-e9b8-4acf-8391-49bd9fe6c4a2" />
<img width="1366" height="677" alt="image" src="https://github.com/user-attachments/assets/8cb01fb7-28fb-4ee4-817c-1f7c3047faff" />
<img width="1366" height="401" alt="image" src="https://github.com/user-attachments/assets/e22e6055-9c7a-4c92-8985-4091766bd8c1" />

Order Restored
<img width="1366" height="729" alt="image" src="https://github.com/user-attachments/assets/cc35d827-f8dc-406b-ad5a-65618416663d" />


## Takeaways
I deepened my understanding of how Amazon Athena can be used to query CloudTrail logs stored in S3 with standard SQL, making it possible and easy to search and analyze log data as if it were in a database.<br><br>
Alternatively, we can programmatically use AWS CloudTrail commands.<br>The [AWS CloudTrail API Reference](https://docs.aws.amazon.com/cli/latest/reference/cloudtrail/) provides us with descriptions of actions, data types, common parameters, and common errors for CloudTrail.<br> 
For future reference I have also listed it under "AWS Services & Documentation" along with other useful links at [More Resources](../../resources/helpful-links.md)

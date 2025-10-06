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
5. Analyzed the CloudTrail logs by using grep
6. Analyzed the CloudTrail logs by using Athena
7. Analyzed the hack further and improved security

## Challenges
- ...

## Screenshot


## Takeaways

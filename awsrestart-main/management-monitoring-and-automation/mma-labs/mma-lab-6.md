# Management, Monitoring and Automation Lab: CloudFormation - Using AWS Systems Manager

## Objective
Gain practical experience with AWS Systems Manager by using it to verify configurations and permissions, run tasks across multiple servers, update application settings, and securely access the command line of an instance. 
This helped demonstrate how Systems Manager can simplify and centralize the management of AWS resources at scale.

## Steps Taken
1. Logged into AWS Management Console
2. Generated inventory lists for managed instances
   - AWS Management Console > Systems Manager > Node Management > Fleet Manager > Account management dropdown list > Set up inventory
   - In the Provide inventory details section > Configured as follows:
     - Name: Inventory-Association
   - In the Targets section > Configured as follows:
     - Specify targets by: Manually selecting instances
     - Selected the row for Managed Instance
   - Setup Inventory
3. Installed a Custom Application using Run Command
   - AWS Management Console > Systems Manager > Node Management > Run Command > Run command > Select Document
   - Target selection: Choose instances manually
   - Instances: Managed Instance
   - Int the Output options section, unchecked Enable an S3 bucket
   - Run
4. Used Parameter Store to manage application settings
   - AWS Management Console > Systems Manager > Application Management > Parameter Store > Create Parameter > Configure :
     - Name: /dashboard/show-beta-features
     - Description: Display beta features
     - Tier: the default option
     - Type: the default option
     - Value:True
   - Create Parameter
5. Used Session Manager to access instances
   -  AWS Management Console > Systems Manager > Node Management > Session Manager > Start session > Managed Instance > Start session
   - A new session tab opens in browser

## Challenges
- ...

## Screenshot


## Takeaways
Through practice, I see how Systems Manager reduces manual effort while improving consistency and security in operations.
For example, it is also possible to identify target instances by using tags. This way, we can run a single command on a whole fleet of matching instances.

# Management, Monitoring and Automation Lab: CloudFormation - Using AWS Systems Manager

## Objective
Gain practical experience with AWS Systems Manager by using it to verify configurations and permissions, run tasks across multiple servers, update application settings, and securely access the command line of an instance. 
This helped demonstrate how Systems Manager can simplify and centralize the management of AWS resources at scale.

## Steps Taken
1. Logged into AWS Management Console
2. Generated inventory lists for managed instances
   - AWS Management Console > Systems Manager > Node Tools > Fleet Manager > Account management dropdown list > Set up inventory
   - In the Provide inventory details section > Configured as follows:
     - Name: Inventory-Association
   - In the Targets section > Configured as follows:
     - Specify targets by: Manually selecting instances
     - Selected the row for Managed Instance
   - Setup Inventory
3. Installed a Custom Application using Run Command
   - AWS Management Console > Systems Manager > Node Tools > Run Command > Run command > Select Document
   - Target selection: Choose instances manually
   - Instances: Managed Instance
   - Int the Output options section, unchecked Enable an S3 bucket
   - Run
4. Used Parameter Store to manage application settings
   - AWS Management Console > Systems Manager > Application Tools > Parameter Store > Create Parameter > Configure :
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
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/7b3bff5b-fd9b-4282-b5be-2eb112ec4316" />
<img width="1366" height="456" alt="image" src="https://github.com/user-attachments/assets/23937c2a-7659-4342-aee0-b4371c3ded49" />
<img width="1366" height="635" alt="image" src="https://github.com/user-attachments/assets/52f14a78-04ab-4f16-bc70-5c390b7d2b47" />
<img width="1366" height="611" alt="image" src="https://github.com/user-attachments/assets/5c21f9c8-50e3-4f9e-a592-776b9b98101b" />
<img width="1366" height="599" alt="image" src="https://github.com/user-attachments/assets/33267dc8-53e4-49c8-b973-65b90e3d9c11" />
I have successfully used Run Command through Systems Manager to install a custom application onto my instance without needing to remotely access the instance by using SSH.
<img width="1366" height="432" alt="image" src="https://github.com/user-attachments/assets/7f27d0ac-2de2-4134-bb06-a34bad590772" />

<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/56421f2a-6758-4420-97d2-bf0624f1e2a4" />
<img width="1366" height="485" alt="image" src="https://github.com/user-attachments/assets/51f22613-830a-4386-bec6-fd58d0ec3130" />
<img width="1356" height="485" alt="image" src="https://github.com/user-attachments/assets/7b7231d3-07c4-44c8-9199-4aeb9f926306" />
Noticed that after creating the new parameter, three charts are displayed. The application is now checking Parameter Store to determine whether the additional chart (which is still in beta) should be displayed.


<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/547eff78-0834-4c52-a926-7b71b8ebd40b" />
Command output to lists the application files that were installed on the instance and the EC2 instance details for the Managed Instance in JSON format
<img width="1366" height="722" alt="image" src="https://github.com/user-attachments/assets/a862584a-159d-4a56-936d-55fd2cdd46ad" />

## Takeaways
Through practice, I see how Systems Manager reduces manual effort while improving consistency and security in operations.
For example, it is also possible to identify target instances by using tags. This way, we can run a single command on a whole fleet of matching instances.

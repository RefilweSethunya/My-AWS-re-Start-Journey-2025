# Compute Lab: Introduction to Amazon EC2

## Objective
This lab provides a basic overview of launching, resizing, managing and monitoring an Amazon EC2 instance.
<img width="600" height="604" alt="image" src="https://github.com/user-attachments/assets/77997c43-f1ab-4d0e-9a3c-f2b913435306" />


## Steps Taken
1. Logged into AWS Management Console
2. Launched my EC2 instance
   - EC2 > Launch Instance
3. Named my instance
   - In the Name and tags pane, in the Name text box: Web Server
4. Choosing an Amazon Machine Image (AMI)
   - Under AMI Machine Image (AMI), noticed that the Amazon Linux is selected by default
5. Choosing an instance type
   - From the dropdown, selected t3.micro
6. Configured a key pair
   - In the Key pair (login) pane, selected Proceed without a key pair (Not recommended).
9. Configuring the network settings
    - VPC - required, selected Lab VPC
    - Security group name - required: Web Server security group
    - Description: Security group for my web server
10. Added storage
    - In the Configure storage pane, keep the default storage configuration
11. Configured advanced details
    - In the dropdown for Termination protection, selected Enable
    - Into the User data text box, pasted the following commands
  ``` bash
    #!/bin/bash
yum -y install httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html
```
12. Launched the EC2 instance
13. Monitored the instance (3 ways)
    - Selected the Monitoring tab
    - Selected the EC2 instance check box > navigate to the bottom of the screen to the Status checks tab
    - Selected the EC2 instance check box > Actions > select Monitor and troubleshoot > Get Instance Screenshot
14. Updated Security Group to Access the Web Server
    - Network & Security > Security Groups > Web Server security group > Edit Inbound Rule > Add Rule
15. Resized Instance: Instance Type and EBS Volume
    - Stop Your Instance
      - EC2 > Instances > Select the Web Server instance by checking the box > Actions > Instance State > Stop Instance > Stop
    - Change The Instance Type
      - EC2 > Instances > Select the Web Server instance by checking the box > Actions > Instance Settings > Change Instance Type > t3.small
    - Resize the EBS Volume
      - Elastic Block Store > Volumes > Actions > Modify Volume > Change the size to: 10
      - Modify
    - Start the Resized Instance
      - EC2 > Instances > Select the Web Server instance by checking the box > Actions > Instance State > Start Instance > Start
   
16. Tested Termination Protection
    - EC2 > Instances > Select the Web Server instance by checking the box > Actions > Instance State > Terminate (delete) instance
    - the instance did not terminate and a red error message pops up at the top that says: Failed to terminate an instance: The instance may not be terminated. This is because it has termination protection enabled
    -  EC2 > Instances > Select the Web Server instance by checking the box > Actions > Instance settings > Change termination protection > Uncheck Enable
    -  EC2 > Instances > Select the Web Server instance by checking the box > Actions > Instance State > Terminate (delete) instance > Terminate
   

## Challenges
-

## Screenshot
EC2 Configuration
<img width="1366" height="667" alt="image" src="https://github.com/user-attachments/assets/c00ba44b-729f-4393-a034-e33da297f114" />
Launched EC2 Intsance
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/f823a5e7-1da2-4a56-9787-22d0326c0b2e" />
EC2 Monitoring Tab
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/53572215-135d-4695-b231-de1eb6d50c6c" />
EC2 Status Check
<img width="1366" height="553" alt="image" src="https://github.com/user-attachments/assets/91012f02-9f6f-4c64-8a47-724d542bf4e5" />
Instance Screenshot
<img width="763" height="551" alt="image" src="https://github.com/user-attachments/assets/4a2f6fee-d676-492f-9c8a-a55d79672414" />
Inbound Rules Add
<img width="1366" height="526" alt="image" src="https://github.com/user-attachments/assets/01f242a1-2331-4fe8-b138-3ef02a427440" />
Stopped EC2 Instance
<img width="1366" height="363" alt="image" src="https://github.com/user-attachments/assets/224037b1-e6f5-4157-b9f0-771a2e30170c" />
Changes Instance type
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/ff4786b8-f720-41fe-a625-5bc15b94a42e" />
<img width="1366" height="332" alt="image" src="https://github.com/user-attachments/assets/211594f4-4eab-4b58-ae85-00fcc02dee82" />
Modifying Volume
<img width="1366" height="669" alt="image" src="https://github.com/user-attachments/assets/fff3334d-1e45-4571-8a4b-11a88cd1ffea" />
<img width="1366" height="565" alt="image" src="https://github.com/user-attachments/assets/7fa06971-c283-45aa-addd-7d719de22f03" />
Starting Resized Instance
<img width="1366" height="625" alt="image" src="https://github.com/user-attachments/assets/30d2df15-699d-4eec-953e-c3b3d7b5a7a4" />
Test Termination Protection (Fail)
<img width="1365" height="443" alt="image" src="https://github.com/user-attachments/assets/62c7abab-599b-4bd2-9f26-ee2f2576ed54" />
Changed Termination Protection
<img width="1366" height="545" alt="image" src="https://github.com/user-attachments/assets/024dd7f6-efc2-4184-a2ea-b0ef90d9ee93" />
Terminating EC2 Instance
<img width="1366" height="536" alt="image" src="https://github.com/user-attachments/assets/ff214824-94f7-4705-bd47-31ab4e1c4301" />




## Takeaways
Security groups work like firewalls. Always make sure the required ports are open.

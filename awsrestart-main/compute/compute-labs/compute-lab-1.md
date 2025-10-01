# Compute Lab: Introduction to Amazon EC2

## Objective
This lab provides a basic overview of launching, resizing, managing and monitoring an Amazon EC2 instance.
<img width="1114" height="904" alt="image" src="https://github.com/user-attachments/assets/77997c43-f1ab-4d0e-9a3c-f2b913435306" />


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

## Challenges
- Forgot to open port 22 in the security group
- Solved by editing the inbound rules

## Screenshot
_(Optional – paste image if available)_

## Takeaways
Security groups work like firewalls. Always make sure the required ports are open.

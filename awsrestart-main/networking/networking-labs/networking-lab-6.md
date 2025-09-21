# Networking Lab: Troubleshooting a Network Issue

## Objective
Analyze the customer scenario and troubleshoot the issue.

The customer reports, "When I create an Apache server through the command line, I cannot ping it. I also get an error when I enter the IP address in the browser. Can you please help figure out what is blocking my connection?'

<img width="1165" height="503" alt="image" src="https://github.com/user-attachments/assets/a8c0cf68-f9b7-4272-af36-9a53bb1a8146" />
The customer's virtual private cloud (VPC) architecture pictured above

## Steps Taken
1. Logged into AWS Management Console
2. Investigate the customer's VPC configuration
   - Subnets - Are the route tables associated to the correct subnets?
   - Route Tables - Do the route tables have the correct routes?
   - Internet Gateway - Is there an Internet Gateway and is it attached?
   - Security Groups and network ACLs - Are the correct rules configured?

## Challenges
- ...

## Screenshot
<img width="1366" height="634" alt="image" src="https://github.com/user-attachments/assets/b55ef8e3-127d-44e7-af1a-27486b0f0ad9" />


## Takeaways
Apache is a server that commonly uses HTTP/S as ports. The security group rules did not have HTTP(80)/HTTPS(443) configured.

# Networking Lab: Internet Protocols - Public and Private IP addresses

## Objective
Analyze the difference between a private and public IP address

## Steps Taken
1. Logged into the AWS Management Console
2. Observed the networking information of both Instances under Networking tab
3. SSH’d into the instances

## Challenges
- 

## Screenshot
<img width="1366" height="302" alt="Screenshot 2025-09-19 at 21 59 11" src="https://github.com/user-attachments/assets/79848ec0-ae74-486c-bd5a-483e0ab78c3e" />

<img width="1364" height="637" alt="image" src="https://github.com/user-attachments/assets/33b1da62-e09d-4e82-bf9c-062986ea8c3c" />
Under the Networking tab(Instance A), I note the Public IPv4 address is missing and Private IPv4 address exists. 
<img width="1356" height="636" alt="image" src="https://github.com/user-attachments/assets/3f33d929-d624-4d80-9c0d-3ecaf0ad1345" />
Under the Networking tab(Instance B), I note the Public and Private IPv4 addresses are both present. 
<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/1cd73063-a184-466f-8f8b-63b91f930f2e" />

We therefore, cannot connect to Instance A without a public IPv4 or v6 address assigned.
<img width="1366" height="640" alt="image" src="https://github.com/user-attachments/assets/2d5b2941-2b4d-4c33-9973-2c9bc727d77a" />


## Takeaways
An EC2 instance (instance A) needs a public IP address to connect to the internet. Private IP addresses are used only within the VPC and cannot establish a connection to the internet.


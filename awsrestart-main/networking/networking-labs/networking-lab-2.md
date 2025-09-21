# Networking Lab: Static and Dynamic and IP addresses

## Objective
Analyze the difference between a statically and dynamically assigned IP addresses using EC2 instances.

## Steps Taken
1. Logged into the AWS Management Console.
2. Launched an EC2 instance from the console and observed networking configurations.
   - Chose an Amazon Machine Image (Amazon Linux 2 AMI (HVM))
   - Selected t3.micro
   - Network: Chose vpc-xxxxxxxx | Lab VPC
   - Subnet: Chose subnet-xxxxxx | Public Subnet 1
   - Auto-assigned Public IP: Set to enable
   - Added Tag and under Key entered Name and under Value entered test instance
   - Assigned an existing security group with the name Linux Instance SG
   - Selected an existing key pair vockey | RSA.
4. Stopped and Started the Instance, Observing any networking configurations related to the instance such as public and private IPv4 addresses and public and private IPv4 DNS.
5. Allocated an Elastic IP address

## Challenges
- ...

## Screenshot
Launching the test instance 
<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/d29e1a16-8efd-487e-b0bc-2f7c07f9840a" />
At first launch, the instance had Public IPv4 address 35.93.111.161 and Private IPv4 address 10.0.10.183
<img width="1361" height="520" alt="image" src="https://github.com/user-attachments/assets/0e432a0e-765f-4ea2-92d7-0f37629af956" />
I stopped the instance. Once the Instance state changes to Stopped, I navigated back down to the tabs and noticed the Public and Private IPv4 address were like below. Public IPv4 address was blank and Private IPv4 address remained 10.0.10.183.
<img width="1362" height="629" alt="image" src="https://github.com/user-attachments/assets/1c052f2e-33b1-414e-a0b9-d7e43967be8b" />
I started the instance. This time around once the Instance state changes to Running, the instance had Public IPv4 address 54.214.177.175 and Private IPv4 address 10.0.10.183.
<img width="1365" height="638" alt="image" src="https://github.com/user-attachments/assets/98b6994c-e7a8-4a5b-82b6-2e698bdfc5c4" />
I navigated to Network and Security on the left navigation and selected Elastic IPs. Created one by selecting 'Allocate Elastic IP address'. Kept everything as default and hit 'Allocate'. The EIP address was 44.245.34.116 as seen below.
<img width="1366" height="635" alt="image" src="https://github.com/user-attachments/assets/765f068f-79e2-44c4-88f1-4bf2af5e8858" />
I then selected the EIP I just created and attached this permanent, public IP address to the dynamic instance by navigating to the top right and navigating to Actions and Associate Elastic IP address.
<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/f43cbb96-54b9-4564-91d6-61598c1fdfcc" />
Now we have Public IPv4 address 44.245.34.116 and Private IPv4 address 10.0.10.183. They are static and remain unchanged even after stopping and starting the instance.
<img width="1366" height="632" alt="image" src="https://github.com/user-attachments/assets/549fe4f9-91fd-414d-9ee5-ba457afd5c61" />


## Takeaways
Amazon EC2 instances (public) have dynamic IP addresses which cause them to change IPs when the instances are stopped and started. Attaching an EIP makes the IP to become persistent (static).

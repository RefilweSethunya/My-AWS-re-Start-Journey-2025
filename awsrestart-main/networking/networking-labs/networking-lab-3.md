# Networking Lab: Create Subnets in a VPC

## Objective
Create a Amazon Virtual Private Cloud (Amazon VPC), create subnets and allocate IP addresses.

The goal is approximately 15,000 IP addresses for the customer's office headquarters and 50 IP addresses for their operations department, which will be in the public subnet.

The customer's VPC architecture seen below.
<img width="867" height="569" alt="image" src="https://github.com/user-attachments/assets/48513ef8-8713-4d22-b267-8f8e106436d6" />


## Steps Taken
1. Logged into AWS Management Console
2. Used the Launch VPC Wizard button to launch VPC
   - For IPv6 CIDR block, No IPv6 CIDR Block selected
   - For the VPC name, entered 'First VPC'
   - For Public subnet's IPv4 CIDR, input the correct VPC CIDR. /16 netmask (65,536 IP) and /28 (16 IP addresses)
   - For Availability Zone, chose No Preference
   - For Subnet name, set to Public subnet
4. Launch VPC

## Challenges
- ...

## Screenshot
<img width="1366" height="640" alt="image" src="https://github.com/user-attachments/assets/080a08e5-2538-479d-aa1c-55a688b273c6" />

## Takeaways
I learned how to launch a VPC, select which CIDR block and range to give the customer making sure not to underprovision.

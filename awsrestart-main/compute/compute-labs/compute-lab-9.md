# Compute Lab: Route 53 Failover Routing

## Objective
The objective of this lab is to configure failover routing for a simple web application using Amazon Route 53.
I set up a Route 53 health check that sends email notifications when the health of an HTTP endpoint becomes unhealthy. I then configured failover routing so that if the primary web server becomes unavailable, traffic is automatically routed to the secondary server in another Availability Zone.
<img width="1136" height="922" alt="image" src="https://github.com/user-attachments/assets/2a3d57a3-f865-45b8-8be5-6ec152558478" />

## Steps Taken
1. Logged into the AWS Management Console
2. Confirmed the café websites
   <img width="989" height="162" alt="image" src="https://github.com/user-attachments/assets/26035b0f-e092-429a-b21b-bcb1246d83e1" />
3. Configuring a Route 53 health check
   - Route 53 > Health checks > Create health check > Configure the following:
     - Name: Primary-Website-Health
     - What to monitor: Endpoint
     - Specify endpoint by: IP Address
     - IP Address:
     - Path: cafe
     - Request interval: Fast(10 seconds)
     - Failure threshold: 2
     - Create alarm: Yes
     - Send notificaion to: New SNS Topic
     - Topic name: Primary-Website-Health
     - Recipient email address: valid email address
     - Create Health check
4. Configuring Route 53 records
   - Created an A record for the primary website
   - Route 53 > Hosted Zones > Configured the following:
     - Record name: www
     - Record type: A - Routes traffic to an IPv4 address and some AWS resources
     - Value:
     - TTL(seconds): 15
     - Routing Policy: Failover
     - Failover record type: Primary
     - Health Check ID: Primary-Website-HEalth
     - Record ID: FailoverPrimary
     - Create record
   - Created an A record for the secondary website
     - Route 53 > Hosted Zones > Configured the following:
     - Record name: www
     - Record type: A - Routes traffic to an IPv4 address and some AWS resources
     - Value:
     - TTL(seconds): 15
     - Routing Policy: Failover
     - Failover record type: Secondary
     - Health Check ID: LEft this field empty
     - Record ID: FailoverSecondary
     - Create record
5. Verifying failover functionality
   - EC2 > Instances > Stop CafeInstance1 instance
   - Refresh the browser tab where page is open, observing that the Region/Availability Zone value now displays a different Availability Zone


## Challenges
- 

## Screenshot
<img width="1366" height="665" alt="image" src="https://github.com/user-attachments/assets/22d150fe-1e5f-45ab-b977-02e07b435f77" />
<img width="1366" height="664" alt="image" src="https://github.com/user-attachments/assets/4bf45c28-4c52-4d4e-94c3-21c8bc8ebc6e" />
<img width="1366" height="669" alt="image" src="https://github.com/user-attachments/assets/c9c7ff1a-fa93-49ae-a8e6-f3fe2abba148" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/ea43155a-da32-432c-a8cf-849f342b6087" />

<img width="1366" height="729" alt="image" src="https://github.com/user-attachments/assets/61bba4ad-3998-4705-a09e-de8db3f7d7c4" />
<img width="1284" height="671" alt="image" src="https://github.com/user-attachments/assets/1ead84ff-9a13-417b-8e8c-476753870ba5" />


## Takeaways
This lab taught me how to use Amazon Route 53 to increase application availability. By configuring health checks and failover routing, I ensured that traffic automatically shifted to a secondary server when the primary server became unavailable, reinforcing the importance of DNS-based failover in building resilient architectures.

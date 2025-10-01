# Compute Lab: Route 53 Failover Routing

## Objective
The objective of this lab is to configure failover routing for a simple web application using Amazon Route 53.
I set up a Route 53 health check that sends email notifications when the health of an HTTP endpoint becomes unhealthy. I then configured failover routing so that if the primary web server becomes unavailable, traffic is automatically routed to the secondary server in another Availability Zone.
<img width="1136" height="922" alt="image" src="https://github.com/user-attachments/assets/2a3d57a3-f865-45b8-8be5-6ec152558478" />

## Steps Taken
1. Logged into the AWS Management Console
2. 

## Challenges
- 

## Screenshot
_(Optional – paste image if available)_

## Takeaways
This lab taught me how to use Amazon Route 53 to increase application availability. By configuring health checks and failover routing, I ensured that traffic automatically shifted to a secondary server when the primary server became unavailable, reinforcing the importance of DNS-based failover in building resilient architectures.

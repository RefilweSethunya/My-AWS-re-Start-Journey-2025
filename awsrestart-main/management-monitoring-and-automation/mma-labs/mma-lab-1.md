# Management, Monitoring and Automation Lab: Monitor an EC2 Instance

## Objective
Explore logging and monitoring techniques using Amazon CloudWatch and Amazon SNS. I create an SNS notification and configure a CloudWatch alarm that triggers when an EC2 instance exceeds a defined CPU utilization threshold. To test the setup, I run a stress test on the EC2 instance to spike CPU usage, simulating a potential security or performance issue. Finally, I confirm that an SNS email notification is sent and finish the lab by creating a CloudWatch dashboard to visualize the monitored metrics.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Generated key pair
4. SSH’d into the instance using Terminal

## Challenges
- Forgot to open port 22 in the security group
- Solved by editing the inbound rules

## Screenshot
_(Optional – paste image if available)_

## Takeaways
Logging and monitoring work hand in hand to maintain system performance and security. While logging captures detailed records of events that reveal how applications and systems behave, monitoring analyzes this data to ensure optimal performance, detect unauthorized access and enforce security guidelines. Together, they provide visibility, accountability, and protection across the environment.

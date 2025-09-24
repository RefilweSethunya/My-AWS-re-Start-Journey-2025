# Management, Monitoring and Automation Lab: Monitor an EC2 Instance

## Objective
Explore logging and monitoring techniques using Amazon CloudWatch and Amazon SNS. I create an SNS notification and configure a CloudWatch alarm that triggers when an EC2 instance exceeds a defined CPU utilization threshold. To test the setup, I run a stress test on the EC2 instance to spike CPU usage, simulating a potential security or performance issue. Finally, I confirm that an SNS email notification is sent and finish the lab by creating a CloudWatch dashboard to visualize the monitored metrics.

## Steps Taken
1. Configure Amazon SNS
   - AWS Management Console > SNS >  Topics > Create topic > configured the following:
     - Type: Standard
     - Name: MyCwAlarm
   - Create
   - Subscriptions tab > Create subscription > configured the following:
     - Topic ARN: Default
     - Protocol: Email
     - Endpoint: Entered a valid email address
   - Create
   - AWS Management Console > Subscriptions
2. Create a CloudWatch alarm
   - AWS Management Console > Cloudwatch > Metrics > All metrics
   - AWS Management Console > Cloudwatch > Metrics > EC2 > Per-Instance Metrics > Select the check box with CPUUtilization as the Metric name for the Stress Test
   - Alarms > All alarms > Create alarm > Select metric > EC2 > Per-Instance Metrics > Select the check box with CPUUtilization as the Metric name for the Stress Test instance name > Metric > On the Specify metric and conditions page configure:
     - Metric name: CPUUtilization
     - InstanceId: default
     - Statistic: Average
     - Period: 1 minute
     - Threshold type: Static
     - Whenever CPUUtilization is...: Greater > threshold
     - than... Define the threshold value: 60
    - Next
    - Configure actions as follows:
      - Alarm state trigger: In alarm
      - Select an SNS topic: Select an existing SNS topic
      - Send a notification to...: MyCwAlarm
     - Next
     - Configure the following:
       - Alarm name: LabCPUUtilizationAlarm
       - Alarm description: CloudWatch alarm for Stress Test EC2 instance CPUUtilization
     - Next
     - Create Alarm
4. Create a CloudWatch dashboard
   - CloudWatch > Dashboards > Create dashboard.
   - For Dashboard name, enter LabEC2Dashboard > Create dashboard > Line > Metrics > EC2 > Per-Instance Metrics > Select the check box with Stress Test for the Instance name and CPUUtilization for the Metric name > Create widget > Save dashboard.

## Challenges
- ...

## Screenshot
Amazon SNS Create Topic Config
<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/83a12d97-438a-4ba1-aed9-111245a04bcf" />

Amazon SNS Create Subscription Config
<img width="1366" height="640" alt="image" src="https://github.com/user-attachments/assets/6995c4a7-4b6e-4530-a3da-6a6b15b764f6" />
<img width="1216" height="354" alt="image" src="https://github.com/user-attachments/assets/2b4d62b4-baf3-4073-8a66-8d1400cc2b5f" />
<img width="1225" height="276" alt="image" src="https://github.com/user-attachments/assets/18e85d07-d69d-4abd-9e0c-8705034f2faa" />
<img width="1366" height="334" alt="image" src="https://github.com/user-attachments/assets/729737af-54cc-45b2-8114-22fab34009bb" />

CloudWatch Alarm Configuration


CloudWatch Dashboard


## Takeaways
Logging and monitoring work hand in hand to maintain system performance and security. While logging captures detailed records of events that reveal how applications and systems behave, monitoring analyzes this data to ensure optimal performance, detect unauthorized access and enforce security guidelines. Together, they provide visibility, accountability, and protection across the environment.

# Management, Monitoring and Automation Lab: Monitoring Infrastructure

## Objective
The objective of this lab is to learn how to monitor applications and infrastructure using Amazon CloudWatch and AWS Config. Tasks include using the AWS Systems Manager Run Command to install the CloudWatch agent on EC2 instances and tracking infrastructure compliance using AWS Config.

## Steps Taken
1. Installed the CloudWatch agent
   - AWS Management Console > Services > Systems Manager > Run Command > Command parameters section > Configured the following:
      - Action: Select Install
      - Name: Enter AmazonCloudWatchAgent
      - Version: Enter latest
    -  Targets section > Choose instances manually > Instances > selected the check box next to Web Server > Run
    -  Parameter Store > Create parameter > configured the following:
      - Name: Monitor-Web-Server
      - Description: Collect web logs and system metrics
      - Value: Paste the following configuration

  ``` bash
{
"logs": {
    "logs_collected": {
      "files": {
        "collect_list": [
          {
            "log_group_name": "HttpAccessLog",
            "file_path": "/var/log/httpd/access_log",
            "log_stream_name": "{instance_id}",
            "timestamp_format": "%b %d %H:%M:%S"
          },
          {
            "log_group_name": "HttpErrorLog",
            "file_path": "/var/log/httpd/error_log",
            "log_stream_name": "{instance_id}",
            "timestamp_format": "%b %d %H:%M:%S"
          }
        ]
      }
    }
  },
  "metrics": {
    "metrics_collected": {
      "cpu": {
        "measurement": [
          "cpu_usage_idle",
          "cpu_usage_iowait",
          "cpu_usage_user",
          "cpu_usage_system"
        ],
        "metrics_collection_interval": 10,
        "totalcpu": false
      },
      "disk": {
        "measurement": [
          "used_percent",
          "inodes_free"
        ],
        "metrics_collection_interval": 10,
        "resources": [
          "*"
        ]
      },
      "diskio": {
        "measurement": [
          "io_time"
        ],
        "metrics_collection_interval": 10,
        "resources": [
          "*"
        ]
      },
      "mem": {
        "measurement": [
          "mem_used_percent"
        ],
        "metrics_collection_interval": 10
      },
      "swap": {
        "measurement": [
          "swap_used_percent"
        ],
        "metrics_collection_interval": 10
      }
    }
  }
}

```

   - Create parameter > Run Command > Run Command
   - In the search box Select Document name prefix > Select Equals > Enter AmazonCloudWatch-ManageAgent
   - Verify
   - Press Enter
   - Selected AmazonCloudWatch-ManageAgent
   - In the Command parameters section, configured as follows:
     - Action: configure
     - Mode: ec2
     - Optional Configuration Source: ssm
     - Optional Configuration Location: Monitor-Web-Server
     - Optional Restart: yes
    - In the Targets section > Choose instances manually
    - In the Instances section, selected the check box next to Web Server
    - Run

2. Monitoring for infrastructure compliance
   - AWS Config > Rules >  Add rule > In the AWS Managed Rules section > input required-tags > required-tags > Next > In the Configure rule page > Parameters > configure the following:
     - tag1Key: project
   - Next
   - Add rule
   - In the AWS Managed Rules section in the search field, enter 'ec2-volume-inuse-check'
   - Select the button next to ec2-volume-inuse-check
   - Next > Next > Add rule
   - Resources in scope > selected Compliant
  
     
## Challenges
- ...

## Screenshot

<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/491b7496-3b1e-4064-898b-b24d24c6a004" />

<img width="1366" height="635" alt="image" src="https://github.com/user-attachments/assets/cb16fa0c-fe1c-4f33-a2f0-6ec5f44a663e" />

<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/01d92157-92be-4545-95b2-3ae5ec581355" />


<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/c06d4520-b9e5-4793-9a4e-1fc935a05ae5" />


<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/19874e3e-6717-4aa3-8d73-a4c3fe311954" />


<img width="1366" height="640" alt="image" src="https://github.com/user-attachments/assets/b81d661b-41d8-467f-b6b1-b6cda3b8d10f" />


<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/3a77e994-72d5-4e64-9cae-87e3546eab2b" />


<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/dd49f63f-c227-41f2-b1bf-a945f9b986d9" />


<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/891fa397-91aa-48ea-be7b-a8bc9f05b9d5" />


<img width="1366" height="635" alt="image" src="https://github.com/user-attachments/assets/b20bf9c2-c81a-447d-af10-1f233303934e" />

AWS Config Configuration - Add Rule

<img width="1366" height="635" alt="image" src="https://github.com/user-attachments/assets/eea950e2-e774-4cf4-bfcf-6c9c9c4b8a90" />

<img width="1366" height="634" alt="image" src="https://github.com/user-attachments/assets/f397fb59-f395-47dc-b15e-7f9e0db7cb85" />

<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/e73dda43-9645-4b51-9bc1-446a4a48ff99" />

<img width="1366" height="640" alt="image" src="https://github.com/user-attachments/assets/a4f3573b-4a87-481e-b0d4-a26318827fb9" />


<img width="1366" height="642" alt="image" src="https://github.com/user-attachments/assets/4675e11d-195e-47d1-b213-88297af94d2b" />


<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/068ed59a-8c3f-4922-b63d-e48910fac4cf" />



## Takeaways
This lab demonstrated how CloudWatch and AWS Config support effective infrastructure monitoring. By collecting logs and metrics and tracking compliance, I reinforced my understanding of how monitoring ensures reliability, security and operational visibility across applications and systems.

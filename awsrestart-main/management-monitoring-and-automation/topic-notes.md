# <img width="45" height="45" alt="image" src="https://github.com/user-attachments/assets/bddbfa24-4002-4033-829e-4bccdcaea298" /> Management, Monitoring and Automation Notes

AWS offers multiple ways to automate and manage tasks, and choosing the right service depends on your architecture. Automation means defining tasks as code that the system executes, improving consistency and reducing manual effort. Management and monitoring services ensure visibility, control, and operational efficiency across your AWS environment.

## Management Tools
- The AWS Management Console is the primary interface for new users. It provides a web-based dashboard to manage AWS resources.  
- As experience grows, users often switch to the AWS Command Line Interface (CLI) for faster execution, scripting, and bulk data retrieval.  
- The CLI is essential for automating tasks and integrating AWS actions into scripts and workflows.

## Monitoring Tools
- CloudWatch collects and visualizes metrics from AWS and non-AWS services.  
  - Create alarms that trigger actions (such as notifications) when metrics exceed thresholds.  
  - Stores logs and extract metrics from them using metric filters.  
- CloudTrail records all account activity and API calls made to AWS services.  
  - By default, CloudTrail stores 90 days of management events per region.  
  - To retain logs longer or customize what’s captured, create a trail to store data in an S3 bucket.  
  - Trails can also stream events to CloudWatch Logs for viewing and searching.

## Approaches to Automation
- Imperative Approach:  
  Specifies how to perform a task step by step.  
  - Examples: AWS Systems Manager, CodeBuild, CodeDeploy, EC2 Userdata scripts.  
  - Commonly seen in Bash or PowerShell scripts.

- Declarative Approach:  
  Specifies what the end result should look like.  
  - Examples: AWS CloudFormation, OpsWorks for Puppet Enterprise, OpsWorks for Chef Automate, OpsWorks Stacks.  
  - The system handles the step-by-step execution to reach the desired state.

## Reflection
Effective management, monitoring, and automation are central to maintaining a healthy AWS environment. The Management Console and CLI offer flexibility for both beginners and advanced users. Monitoring tools like CloudWatch and CloudTrail provide visibility and accountability for performance and security. Automation bridges the gap by ensuring repeatable, consistent configurations across services. Together, these capabilities enable organizations to build scalable, resilient, and well-governed cloud infrastructures.

## Exam Essentials
Understand how to use Trusted Advisor for alerts to common system misconfigurations.<br>
The Trusted Advisor alerts are divided into five categories: Cost Optimization, Performance, Security, Fault Tolerance, and Services Limits.<br>
You should set up an administration routine that includes regular visits to the Trusted Advisor to see whether any important status checks have changed.
<br>
<br>
Understand what CloudTrail vs CloudWatch.<br> CloudTrail logs management and data operations on your account. By default, it logs 90 days of management events per region. If you want to log more than this or customize which events it logs, you can create a trail to log those events and store them in an S3 bucket. You can optionally stream CloudTrail logs to CloudWatch for storage, searching, and analysis.
<br>
<br>
Know what specific tasks AWS services can automate.<br>
CloudFormation can automatically deploy, change, and even delete AWS resources in one fell swoop.
<br>
The AWS Developer Tools—CodeCommit, CodeBuild, CodeDeploy, and CodePipeline—can help automate some or all of the software development, testing, and deployment process.
<br>
EC2 Auto Scaling automatically provisions a set number of EC2 instances. You can optionally have it scale in or out according to demand or a schedule.
<br>
Systems Manager Command documents let you automate tasks against your instance operating systems, such as patching, installing software, enforcing configuration settings, and collecting inventory. Automation documents let you automate many administrative AWS tasks that would otherwise require using the management console or CLI.
<br>
OpsWorks for Puppet Enterprise and OpsWorks for Chef Automate also let you configure your instances and deploy software but do so using the declarative language of Puppet modules or Chef recipes.
<br>
OpsWorks Stacks can automate the build and deployment of an application and its supporting infrastructure.
<br>
<br>
Understand the benefits of automation and infrastructure as code.<br>
Automation allows common, repetitive tasks to be executed faster than doing them manually and reduces the risk of human error. When you automate infrastructure builds using code, the code simultaneously serves as de facto documentation. Code can be placed into version control, making it easy to track changes and even roll back when necessary.
<br>
<br>
Be able to explain the concepts of continuous integration and continuous delivery.<br>
The practice of continuous integration involves developers regularly checking in code as they create or change it. An automated process performs build and test actions against it. This immediate feedback loop allows developers to fix problems quickly and early.
<br>
Continuous delivery expands upon continuous integration but includes deploying the application to production after a manual approval. This effectively enables push-button deployment of an application to production.

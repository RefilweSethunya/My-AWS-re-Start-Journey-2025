#Management, Monitoring and Automation Notes




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

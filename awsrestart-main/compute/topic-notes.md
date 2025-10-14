# Compute Notes

## What is Compute?

Compute is under CORE SERVICES which is the foundation to all solutions of the multiple services AWS provides.
Compute is the processing power that lets your application run. In the cloud, the key runtime compute choices can be grouped into four categories of cloud computing models: Virtual machines, Containers, Platform as a Service or Serverless.

### Virtual Machines
- Amazon EC2 (virtual machines | Linux, Windows or Mac OS)
  provides secure and resizeable virtual machines in cloud. 
- Amazon Lightsail
  provides virtual private servers to run workloads in cost-effective way.

### Containers
- Amazon ECS
  Run Docker container apps on AWS.

### Platform as a Service
- AWS Elastic Beanstalk
  Runs web apps and services developed in languages such as Java, .NET, PHP, Node.js, Python, Ruby, Go and Docker.

### Serverless
- AWS Lambda
  Runs Java, Go, PowerShell, Node.Js, C#
- AWS Fargate
  For containers.


## Key Concepts
- Scaling (vertical vs horizontal)
- AMIs (Amazon Machine Images)
- Load Balancers
- High Availability and Scalability
- Auto Scaling Groups 

## Reflection
I understand that compute isn't just about having your environment on the cloud. The instance type that you specify determines the hardware of the host computer used. Each instance type offers different compute, memory and storage capabilities.

## Exam Tips
Understand the differences between EBS and instance store volumes.<br>EBS volumes are versatile (they can, for instance, be converted into AMIs) and will survive an instance shutdown. Instance store volumes, on the other hand, provide faster reads and writes and can be more secure for some purposes. Which storage you use will often depend on the instance type you choose.<br><br>UBe familiar with Amazon’s managed deployment services.<br>Amazon Lightsail provides blueprints for simplified flat-rate deployments using EC2 resources under the hood. Lightsail deployments can, if needed, be transferred to regular EC2 infrastructure without service interruption.<br>Elastic Beanstalk manages the underlying infrastructure for your application and automatically scales according to demand.<br><br>Understand how container and serverless models work in the cloud.<br>Containers—like Docker—share the OS kernel and device drivers with their host and share common software layers with each other to produce fast and lightweight applications. ECS and EKS are AWS services focused on simplifying Docker orchestration within the EC2 framework. Lambda functions are designed to respond to event triggers to launch short-lived operations.

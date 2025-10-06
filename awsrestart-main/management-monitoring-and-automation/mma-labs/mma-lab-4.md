# Management, Monitoring and Automation Lab: Managing resources with Tagging

## Objective
This lab focuses on using Amazon EC2 instance tags to automate management tasks.<br>The AWS CLI is used to inspect and update tags, run scripts to start and stop instances, and apply JMESPath queries for filtering. The challenge extends this by designing a way to terminate instances missing required tags, reinforcing how tagging supports automation and governance.
<br>Final Architecture
<img width="853" height="339" alt="image" src="https://github.com/user-attachments/assets/6297e68b-e4d3-4527-9a7f-a30821c02dc4" />

## Steps Taken
1. Logged into AWS Management Console
2. Connnected to the Command Host
3. Used Tags to Manage Resources to find the resources in private subnet that belong to the ERPSystem project and are in the Environment named development
   - To find all instances in my account that are tagged with a tag of Project and a value of ERPSystem:
     ``` bash
     aws ec2 describe-instances --filter "Name=tag:Project,Values=ERPSystem"
     ```
   - Used the --query parameter to narrow down the results to only the instance ID of the discovered instances:
     ``` bash
     aws ec2 describe-instances --filter "Name=tag:Project,Values=ERPSystem" --query 'Reservations[*].Instances[*].InstanceId'
     ```
   - Used the --query parameter to include both the instance ID and the AZ of each instance:
     ``` bash
     aws ec2 describe-instances --filter "Name=tag:Project,Values=ERPSystem" --query 'Reservations[*].Instances[*].{ID:InstanceId,AZ:Placement.AvailabilityZone}'
     ```
   - Used the --query parameter to include the value of the Project tag in the output:
     ``` bash
     aws ec2 describe-instances --filter "Name=tag:Project,Values=ERPSystem" --query 'Reservations[*].Instances[*].{ID:InstanceId,AZ:Placement.AvailabilityZone,Project:Tags[?Key==`Project`] | [0].Value}'
     ```
   - Used the --query parameter to include the Environment and Version tags in output:
     ``` bash
     aws ec2 describe-instances --filter "Name=tag:Project,Values=ERPSystem" --query 'Reservations[*].Instances[*].{ID:InstanceId,AZ:Placement.AvailabilityZone,Project:Tags[?Key==`Project`] | [0].Value,Environment:Tags[?Key==`Environment`] | [0].Value,Version:Tags[?Key==`Version`] | [0].Value}'
     ```
   - Added a second filter to see only the instances associated with the project named ERPSystem that belong to the Environment named development:
     ``` bash
     aws ec2 describe-instances --filter "Name=tag:Project,Values=ERPSystem" "Name=tag:Environment,Values=development" --query 'Reservations[*].Instances[*].{ID:InstanceId,AZ:Placement.AvailabilityZone,Project:Tags[?Key==`Project`] | [0].Value,Environment:Tags[?Key==`Environment`] | [0].Value,Version:Tags[?Key==`Version`] | [0].Value}'
     ```
   - Changed all of the Version tags on the instances marked as development for the project ERPSystem:
     ``` bash
     ./change-resource-tags.sh
     ```
   - Verified that the version number on these instances has been incremented and that other non-development boxes in the ERPSystem project have been unaffected:
     ``` bash
     aws ec2 describe-instances --filter "Name=tag:Project,Values=ERPSystem" --query 'Reservations[*].Instances[*].{ID:InstanceId, AZ:Placement.AvailabilityZone, Project:Tags[?Key==`Project`] |[0].Value,Environment:Tags[?Key==`Environment`] | [0].Value,Version:Tags[?Key==`Version`] | [0].Value}'
     ```
4. Stopped and Started Resources by Tag
   - Ran the stopinator.php script:
     ``` bash
     ./stopinator.php -t"Project=ERPSystem;Environment=development"
     ```
   - Verified that two instances are stopping or have already been stopped on the Services > EC2 > Instances list
   - On the Linux prompt restart your instances with the following command:
     ``` bash
     ./stopinator.php -t"Project=ERPSystem;Environment=development" -s
     ```
   - Verified that two instances that were previously shut down are now restarting on the Services > EC2 > Instances list
6. Terminated Non-Compliant Instances<br>
Before running the script, I needed to alter a couple of instances in your lab so that they no longer have the Environment tag defined and therefore, do not conform to certain security guidelines.
   - Configured environment to test the terminate script<br>
     Services > EC2 > Instance > Tags > Add/Edit Tags > Environment tag > Remove
   - On my instance Description tab, find the Availability zone field, and copy all but the last letter to a text file. This value will be referred to as region.
   - Noted the value for Region
   - Noted the value for Subnet ID
   - Ran the terminate-instances.php script (replacing <region> with my region and <subnet-id> with my subnet-id):
       ``` bash
       ./terminate-instances.php -region <region> -subnetid <subnet-id>
       ```

## Challenges
- ...

## Screenshot
..

## Takeaways
This lab demonstrated to me through hands-on practice how tagging in Amazon EC2, combined with the AWS CLI, enables automated management, filtering, and governance of instances.

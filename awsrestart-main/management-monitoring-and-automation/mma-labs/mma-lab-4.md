# Management, Monitoring and Automation Lab: Managing resources with Tagging

## Objective
This lab focuses on using Amazon EC2 instance tags to automate management tasks.<br>The AWS CLI is used to inspect and update tags, run scripts to start and stop instances, and apply JMESPath queries for filtering. The challenge extends this by designing a way to terminate instances missing required tags, reinforcing how tagging supports automation and governance.
<br>Final Architecture
<img width="853" height="339" alt="image" src="https://github.com/user-attachments/assets/6297e68b-e4d3-4527-9a7f-a30821c02dc4" />

## Steps Taken
1. Logged into AWS Management Console
2. Used Tags to Manage Resources
   - Connnected to the Command Host
   - Found the resources in private subnet that belong to the ERPSystem project and are in the Environment named development using AWS CLI
   - To find all instances in your account that are tagged with a tag of Project and a value of ERPSystem:
   - Uses the JMESPath wildcard syntax to specify that the command should iterate through all reservations and all instances and return the InstanceId for each instance in the return results (with the --query parameter to filter to only the instance ID of the discovered instance):
   - Filtered to include both the instance ID and the Availability Zone of each instance:
   - To include the value of the Project tag in the output:
   - To include the Environment and Version tags in output:
   - filter to see only the instances associated with the project named ERPSystem that belong to the Environment named development:
   - change all of the Version tags on the instances marked as development for the project ERPSystem.
   - open the file /home/ec2-user/change-resource-tags.sh:
   - Examine the contents of the script:
   - run this command from the Linux command prompt:
   - verify that the version number on these instances has been incremented and that other non-development boxes in the ERPSystem project have been unaffected:
3. Stopped and Started Resources by Tag
   - Examining the Stopinator Script
   - cd into the directory aws-tools
   - Open the file stopinator.php and examine its contents:
   - run the stopinator.php script:
   - Verify that two instances are stopping or have already been stopped on the Services > EC2 > Instances menu
   - On the Linux prompt restart your instances with the following command:
   - Verify that two instances that were previously shut down are now restarting on the Services > EC2 > Instances menu
5. Terminated Non-Compliant Instances
   - Review the Tag-Or-Terminate Script
   - Open the file terminate-instances.php with the nano editor:
   - Configuring Environment to Test Script EC2 Management Console and observe the instances running in your lab environment. Select one of the instances in your private subnet > In the Tags tab, Add/Edit Tags > remove the Environment tag > save
   - Run the script
     - run the terminate-instances.php script (replacing the <region> with your region and <subnet-id> with your subnet-id):
       ``` bash
       ./terminate-instances.php -region <region> -subnetid <subnet-id>
       ```

## Challenges
- ...

## Screenshot
..

## Takeaways
This lab demonstrated to me through hands-on practice how tagging in Amazon EC2, combined with the AWS CLI, enables automated management, filtering, and governance of instances.

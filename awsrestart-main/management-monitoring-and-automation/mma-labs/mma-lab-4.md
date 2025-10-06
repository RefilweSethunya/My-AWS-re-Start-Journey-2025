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
   - Noted the value for Region
   - Noted the value for Subnet ID
   - Ran the terminate-instances.php script (replacing <region> with my region and <subnet-id> with my subnet-id):
       ``` bash
       ./terminate-instances.php -region <region> -subnetid <subnet-id>
       ```

## Challenges
- Encountered a fatal error becuase I specified an invalid AWS region (using us-west instead of a full region code like us-west-2), which caused the request to fail with a “Could not resolve host” error
- <img width="1366" height="206" alt="image" src="https://github.com/user-attachments/assets/4f53ccdc-eab6-4213-a829-a97eeba31589" />
- Always use the full AWS region code when specifying regions. Verified the correct region by checking the subnet’s Availability Zone and re-ran the command with us-west-2, which resolved the issue.
- The script ran successful and terminated instances that no longer have the Environment tag defined. See below
- <img width="1366" height="222" alt="image" src="https://github.com/user-attachments/assets/09b0610f-8542-4e12-8263-9ef920917d4f" />

## Screenshot
<img width="1366" height="753" alt="image" src="https://github.com/user-attachments/assets/82520de8-5d26-4c95-b520-aa5331400890" />
<img width="1366" height="380" alt="image" src="https://github.com/user-attachments/assets/d006d5c0-8038-4bde-8695-b9a17e3ce192" />
<img width="1366" height="653" alt="image" src="https://github.com/user-attachments/assets/577668e0-dcf7-4bc9-bb25-8387e96519fb" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/8ca09973-3353-4c8a-8f9f-444690146b47" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/7279aa22-f7fe-4c14-be25-d747dcfb2a62" />
<img width="1366" height="347" alt="image" src="https://github.com/user-attachments/assets/64c2b890-458c-4e76-8be2-76fb0300f939" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/05a2a729-c33d-413e-b529-4a70d0d84003" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/f43ffd7e-8098-4c9c-b254-d75f19cd2211" />
Stopinator Script
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/0ecadb97-982c-494c-a806-02766f8c496e" />
Running the Stopinator Script
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/b56beb25-5d37-4789-965d-de035024fb42" />
<img width="1366" height="292" alt="image" src="https://github.com/user-attachments/assets/51150b5e-0dcc-4d61-8c08-a4051d18d446" />
<img width="1366" height="545" alt="image" src="https://github.com/user-attachments/assets/1a9976b4-1997-4a51-9dfe-699ab955fc64" />
Restarting the instances
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/eac4a1ff-6901-4aed-9ced-cdb4f261c090" />
<img width="1366" height="280" alt="image" src="https://github.com/user-attachments/assets/ba9b6cce-8ebc-4480-ae80-2da984be1470" />
<img width="1366" height="582" alt="image" src="https://github.com/user-attachments/assets/f909f3cd-f205-4218-8a4b-7955f88359cb" />
Tag-Or-Terminate Script
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/f917797c-8f75-4c36-9f5e-e3428dbb62c0" />
Removing Environment tag for some instances running in the lab environment
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/b89260ae-fbc1-48c3-9ca8-9e2bf61245df" />
<img width="1366" height="411" alt="image" src="https://github.com/user-attachments/assets/7bffe3be-2be4-498a-b976-371715fcbcf3" />
Running the terminate-instances.php script
<img width="1366" height="222" alt="image" src="https://github.com/user-attachments/assets/09b0610f-8542-4e12-8263-9ef920917d4f" />



## Takeaways
This lab demonstrated to me through hands-on practice how tagging in Amazon EC2, combined with the AWS CLI, enables automated management, filtering, and governance of instances.

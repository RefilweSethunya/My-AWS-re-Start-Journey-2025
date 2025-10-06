# Storage Lab: Create a Website on S3

## Objective
Practice deploying and managing a static website using Amazon S3 and the AWS CLI through running AWS CLI commands that interact with IAM and S3 services, to create an S3 bucket and configure it to host a static website. Then uploading website files to the bucket. And finally, verifying that the website is accessible through the provided S3 website URL.
<img width="1654" height="787" alt="image" src="https://github.com/user-attachments/assets/f490f663-15e7-4c9e-954c-b89866dbca94" />


## Steps Taken
1. Configured the AWS CLI
   - ``` bash
     aws configure
     ```
2. Created an S3 bucket using the AWS CLI
   - ``` bash
     aws s3api create-bucket --bucket <twhitlock256> --region us-west-2 --create-bucket-configuration LocationConstraint=us-west-2
     ```
   - When the command is successful, you will get a JSON-formatted response with a Location name-value pair, where the value reflects the bucket name
3. Created a new IAM user that has full access to Amazon S3
   - created a new IAM user
     ``` bash
     aws iam create-user --user-name awsS3user
     ```
   - created a login profile for the new user
     ``` bash
     aws iam create-login-profile --user-name awsS3user --password Training123!
     ```
   - Logged in to the AWS Management Console as the new awsS3user user
   - AWS Management Console > S3
   - Granted the awsS3user user full access to the S3 bucket, replacing <policyYouFound> with PolicyName
   -  ``` bash
      aws iam list-policies --query "Policies[?contains(PolicyName,'S3')]"
      ```
   - ``` bash
     aws iam attach-user-policy --policy-arn arn:aws:iam::aws:policy/<policyYouFound> --user-name awsS3user
     ```
4. Adjusted S3 bucket permissions
   - AWS Management Console > S3 > bucket
   - Permissions > Block public access (bucket settings) > Edit
   - UnSelect Block all public access
   - permissions > Object Ownership > Edit
   - Selected ACLs enabled
   - Selected I acknowledge that ACLs will be restored.
   - Save changes
5. Upload files to Amazon S3 by using the AWS CLI
   - So the bucket functions as a website
     ``` bash
     aws s3 website s3://<my-bucket>/ --index-document index.html
     ```
   - Ensured that the index.html file will be known as the index document
     ``` bash
     aws s3 cp /home/ec2-user/sysops-activity-files/static-website/ s3://<my-bucket>/ --recursive --acl public-read
     ```
   - Verified the upload
     ``` bash
     aws s3 ls <my-bucket>
     ```
   - AWS Management Console > S3 console > bucket
   - Properties > Static website hosting is Enabled. Running the aws s3 website AWS CLI command turns on the static website hosting for an Amazon S3 bucket. This option is usually turned off by default.
   - To open the URL on a new page, I selected the Bucket website endpoint URL that displays
6. Created a batch file to make updating the website repeatable
   - Pulled up past command where I ran the aws s3 cp command
     ``` bash
     history
     ```
   - Changed directories and created an empty file
     ``` bash
     cd ~
     touch update-website.sh
     ```
   - Opened empty file
     ``` bash
     vi update-website.sh
     ```
   - Entered edit mode
     ``` bash
     i
     ```
   - Added the standard first line of a bash file and then added the s3 cp line from history, replacing <my-bucket> in the following command with my bucket name
     ``` bash
     #!/bin/bash aws s3 cp /home/ec2-user/sysops-activity-files/static-website/ s3://<my-bucket>/ --recursive --acl public-read
     ```
   - Write the changes and quit the editor
     ``` bash
     :wq
     ```
   - Made the file an executable batch file
     ``` bash
     chmod +x update-website.sh
     ```
   - Opened the local copy of the index file in a text editor to modify
     ``` bash
     vi sysops-activity-files/static-website/index.html
   - Entered edit mode
     ``` bash
     i
     ```
   - Modified the following:
     - Located the first line that has the HTML code bgcolor="aquamarine" and changed this code to bgcolor="gainsboro"
     - Located the line that has the HTML code bgcolor="orange" and changed this code to bgcolor="cornsilk"
     - Located the second line that has the HTML code bgcolor="aquamarine" and change this code to bgcolor="gainsboro"
   - Updated the website by running:
     ``` bash
     ./update-website.sh
     ```
## Challenges
- 

## Screenshot
CLI Config
<img width="1366" height="323" alt="image" src="https://github.com/user-attachments/assets/b36c22bd-b842-43e9-ab48-de7f93ef87a8" />


## Takeaways
I learned how S3 can serve as a simple and scalable hosting solution for static web content.

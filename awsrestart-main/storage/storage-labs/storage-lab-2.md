# Storage Lab: Create a Website on S3

## Objective
Practice deploying and managing a static website using Amazon S3 and the AWS CLI through running AWS CLI commands that interact with IAM and S3 services, to create an S3 bucket and configure it to host a static website. Then uploading website files to the bucket. And finally, verifying that the website is accessible through the provided S3 website URL.
<img width="804" height="401" alt="image" src="https://github.com/user-attachments/assets/0f91c7ee-0866-480f-abb3-6f948138dc11" />

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
- I encountered errors due to bucket name conflicts as the names I initially selected (i.e. refilwes, refilwesethunya) were already in use
- I resolved this by creating a unique identifier, appending numbers to the bucket name (refilwesethunya779618), which successfully eliminated the conflict. 

## Screenshot
CLI Config
<img width="1366" height="280" alt="image" src="https://github.com/user-attachments/assets/52d4ff19-b43c-4535-b7ee-53f7becc5268" />

<img width="1366" height="680" alt="image" src="https://github.com/user-attachments/assets/1f683732-2888-4a8e-864a-d81a7f4d091b" />
<img width="1366" height="184" alt="image" src="https://github.com/user-attachments/assets/a6bccdd3-5f61-46ea-944a-50baaba64593" />

<img width="1366" height="380" alt="image" src="https://github.com/user-attachments/assets/7d2833c8-a0a6-4128-ae6f-28575cbc6cea" />
<img width="1366" height="679" alt="image" src="https://github.com/user-attachments/assets/09e836a4-2ea6-4b9f-aa44-d0f70c0bf5a7" />
<img width="1366" height="535" alt="image" src="https://github.com/user-attachments/assets/495b1eec-9a2c-4772-ad48-f262429127ee" />
<img width="1366" height="660" alt="image" src="https://github.com/user-attachments/assets/56bfa549-abfb-41f8-8df5-6a55930d45a4" />
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/624ca00d-e2d1-49f7-96a2-5f8743caaa7e" />
<img width="1366" height="667" alt="image" src="https://github.com/user-attachments/assets/c4bf2158-afc8-4e64-86a4-084ea42adda3" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/15694ac7-4e64-4483-933a-2365a8feeafe" />
<img width="1366" height="260" alt="image" src="https://github.com/user-attachments/assets/90536e44-96e1-436b-8dd7-ca5b54ec9b61" />
<img width="1366" height="143" alt="image" src="https://github.com/user-attachments/assets/d72996fa-1a0d-432d-985d-849fdaca48a5" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/d3f7d4c0-39e4-4c76-a931-e32ee6151379" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/688a3626-4ab9-41cf-8c75-befd5d9b5c86" />
<img width="1366" height="722" alt="image" src="https://github.com/user-attachments/assets/24a79316-140c-4910-a3fd-6683c8c8e6d2" />
<img width="1366" height="487" alt="image" src="https://github.com/user-attachments/assets/5d78a238-2ec0-460b-a819-cdeb27d80b2b" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/dab0295c-8960-49a4-b179-7753491bd31b" />
<img width="1366" height="528" alt="image" src="https://github.com/user-attachments/assets/36b7aa35-e95b-4e3d-a571-5b6745dba6e0" />
<img width="1366" height="730" alt="image" src="https://github.com/user-attachments/assets/aaf01a4b-36e2-4808-9198-a7ee6c3ef47a" />



## Takeaways
I learned how S3 can serve as a simple and scalable hosting solution for static web content. This exercise also reinforced my understanding of globally unique S3 bucket naming conventions and highlighted that naming conflicts are expected. It is therefore important to plan and adapt effectively when provisioning resources.

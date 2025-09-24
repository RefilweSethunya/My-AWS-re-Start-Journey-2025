# Storage Lab: Create a Website on S3

## Objective
Practice deploying and managing a static website using Amazon S3 and the AWS CLI through running AWS CLI commands that interact with IAM and S3 services, to create an S3 bucket and configure it to host a static website. Then uploading website files to the bucket. And finally, verifying that the website is accessible through the provided S3 website URL.

## Steps Taken
1. Configure the AWS CLI
   - ``` bash
     aws configure
     ```
2. Create an S3 bucket using the AWS CLI
   - ``` bash
     aws s3api create-bucket --bucket <twhitlock256> --region us-west-2 --create-bucket-configuration LocationConstraint=us-west-2
     ```
   - If the command is successful, you will get a JSON-formatted response with a Location name-value pair, where the value reflects the bucket name
3. Create a new IAM user that has full access to Amazon S3
   - create a new IAM user
     ``` bash
     aws iam create-user --user-name awsS3user
     ```
   - create a login profile for the new user
     ``` bash
     aws iam create-login-profile --user-name awsS3user --password Training123!
     ```
   - Log in to the AWS Management Console as the new awsS3user user
   - AWS Management Console > S3
   - Grant the awsS3user user full access to the S3 bucket, replacing <policyYouFound> with PolicyName
   -  ``` bash
      aws iam list-policies --query "Policies[?contains(PolicyName,'S3')]"
      ```
   - ``` bash
     aws iam attach-user-policy --policy-arn arn:aws:iam::aws:policy/<policyYouFound> --user-name awsS3user
     ```
4. Adjust S3 bucket permissions
   - AWS Management Console > S3 > bucket
   - Permissions > Block public access (bucket settings) > Edit
   - UnSelect Block all public access
   - permissions > Object Ownership > Edit
   - Select ACLs enabled
   - Select I acknowledge that ACLs will be restored.
   - Save changes
5. Upload files to Amazon S3 by using the AWS CLI
   - so the bucket can function as a website
     ``` bash
     aws s3 website s3://<my-bucket>/ --index-document index.html
     ```
   - ensures that the index.html file will be known as the index document
     ``` bash
     aws s3 cp /home/ec2-user/sysops-activity-files/static-website/ s3://<my-bucket>/ --recursive --acl public-read
     ```
   - AWS Management Console > S3 console > bucket
   - Properties > Static website hosting is Enabled. Running the aws s3 website AWS CLI command turns on the static website hosting for an Amazon S3 bucket. This option is usually turned off by default.
   - To open the URL on a new page, choose the Bucket website endpoint URL that displays

## Challenges
- 

## Screenshot
_(Optional – paste image if available)_

## Takeaways
I learned how S3 can serve as a simple and scalable hosting solution for static web content.

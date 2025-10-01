# Compute Lab: Working with AWS Lambda

## Objective
Deploy and configure a serverless computing solution using AWS Lambda. Identify the necessary IAM policy permissions that allow Lambda functions to interact with other AWS resources, create a Lambda layer to address external library dependencies, and configure Lambda functions that extract data from a database and send reports to users. Then deploy and test a scheduled Lambda function that invokes another function, and finally, use CloudWatch Logs to troubleshoot and validate the solution.

## Steps Taken
1. Logged into the AWS Management Console
2. Observed the IAM role settings
   - Observed the salesAnalysisReport IAM role settings
     - Services > Security, Identity, & Compliance > IAM > Roles
     - In the search box, entered sales
     - From the filtered results, selected the salesAnalysisReportRole hyperlink
     - In the Permissions tab, noticed there are four policies assigned to this role. To expand each role and analyze the permissions that each policy grants I clicked the + icon next to each role
    - Observed the salesAnalysisReportDERole IAM role settings
      - Services > Security, Identity, & Compliance > IAM > Roles
      - In the search box, entered sales
      - From the filtered results, selected the salesAnalysisReportDERole hyperlink
      - In the Permissions tab, noticed there are two permissions granted to this role
3. Created a Lambda layer and a data extractor Lambda function
   - In the AWS Management Console, Services > Compute > Lambda > Layers > Create Layer
   - Configured the following:
     - Name: pymysqlLibrary
     - Description: PyMySQL library modules
     - Upload a .zip file: Uploaded the pymysql-v3.zip file
   - Create
   - In the AWS Management Console, Functions > Create function page > Author from scratch
   - Configured the following:
     - Function name: salesAnalysisReportDataExtractor
     - Runtime: Python 3.9
     - Execution role: Use an existing role
     - Existing role: salesAnalysisReportDERole
   - Create
   - Adding the Lambda layer to the function
     - Function overview panel > Layers > Add a layer
     - Configure the following:
       - Choose a layer: Custom layers
       - Custom layers: pymysqlLibrary
       - Version: 1
     - Add
    - Importing the code for the data extractor Lambda function
      - Lambda > Functions > salesAnalysisReportDataExtractor
      - Runtime settings panel > Edit
      - Handler: salesAnalysisReportDataExtractor.lambda_handler
      - Save
      - In the Code source panel > Upload from >.zip file > Uploaded the salesAnalysisReportDataExtractor-v3.zip
      - Save
     - Configuring network settings for the function
     - Configuration tab > VPC > Edit > configured the following:
       - VPC: Cafe VPC
       - Subnets: Cafe Public Subnet 1
       - Security groups: CafeSecurityGroup
     - Save
4. Tested the data extractor Lambda function
   - Launched a test of the Lambda function
     - On the AWS Management Console, Services > Management & Governance > Systems Manager > Parameter Store
     - Onto a text editor copy the values of /cafe/dbUrl /cafe/dbName /cafe/dbUser /cafe/dbPassword
     - On the salesAnalysisReportDataExtractor function page > Test tab
     - Configured Test Event tab as follows:
       - Test event action: Create new event
       - Event name: SARDETestEvent
       - Template: hello-world
       - In the Event JSON pane, replace the JSON object with the following JSON object:
       - Save
       - Test
  ``` bash
{
  "dbUrl": "<value of /cafe/dbUrl parameter>",
  "dbName": "<value of /cafe/dbName parameter>",
  "dbUser": "<value of /cafe/dbUser parameter>",
  "dbPassword": "<value of /cafe/dbPassword parameter>"
}
  ```
5. Troubleshoot the data extractor Lambda function
   - In the Configuration tab > VPC, Noticed the Inbound rules for the security group that are used by the EC2 instance running the database are missing the database port number (3306). Adding an inbound rule to the security group and testing again, now we see a green box showing the message “Execution result: succeeded (logs).” indicating that the function ran successfully.
6. Configured notifications
   - Created an SNS topic
   - Subscribed to the SNS topic
7. Created the salesAnalysisReport Lambda function
   - Connected to the CLI Host instance
   - Created the salesAnalysisReport Lambda function using the AWS CLI
   - Replaced <salesAnalysisReportRoleARN> with the value of the salesAnalysisReportRole ARN copied in a previous step, and replaced <region> with the us-west-2 
``` bash
aws lambda create-function \
--function-name salesAnalysisReport \
--runtime python3.9 \
--zip-file fileb://salesAnalysisReport-v2.zip \
--handler salesAnalysisReport.lambda_handler \
--region <region> \
--role <salesAnalysisReportRoleARN>
```
8. Added a trigger to the salesAnalysisReport Lambda function
   - configured the report to be initiated Monday through Saturday at 8 PM each day. To do so, I used a CloudWatch Events event as the trigger mechanism.
  

## Challenges
- 

## Screenshot
<img width="1366" height="665" alt="image" src="https://github.com/user-attachments/assets/a7898cc1-1f7a-415b-99c8-5182d633d524" />
<img width="1366" height="667" alt="image" src="https://github.com/user-attachments/assets/e8352b06-5cab-4ca3-b86b-3fcb146dfb2a" />
<img width="1366" height="666" alt="image" src="https://github.com/user-attachments/assets/a17f6700-5f2f-4206-a4c3-55589ba50704" />
<img width="1366" height="668" alt="image" src="https://github.com/user-attachments/assets/45090191-6dbb-4ab3-8ddd-487d547d53df" />
<img width="1366" height="668" alt="image" src="https://github.com/user-attachments/assets/634814e5-be06-4c13-8da2-5b64bc86e9d9" />
<img width="1366" height="668" alt="image" src="https://github.com/user-attachments/assets/d7ef2195-610b-4fa1-8eed-a3c71a5b12e5" />
<img width="1366" height="669" alt="image" src="https://github.com/user-attachments/assets/4487a875-6153-4090-88bb-b388fd4acab5" />
<img width="1366" height="664" alt="image" src="https://github.com/user-attachments/assets/e669aa58-0b15-4c99-8ebc-2a983215c835" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/ab3a0a13-0114-4c4d-97dc-bf2f0834f6de" />
<img width="1366" height="665" alt="image" src="https://github.com/user-attachments/assets/7c640d33-5907-41bf-a299-160fefd9ec8d" />
<img width="1366" height="667" alt="image" src="https://github.com/user-attachments/assets/66ea3c01-6676-4179-9d18-e4bce60fa98f" />
<img width="1366" height="669" alt="image" src="https://github.com/user-attachments/assets/7caddf37-c0fe-4c5a-ba10-82fab1b2b7e6" />
<img width="1366" height="669" alt="image" src="https://github.com/user-attachments/assets/9a44446b-0ac8-4657-88c8-29208184433f" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/ebbaef90-d541-40c7-bdc2-a9a3dfaf7271" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/8afab7d6-48a6-4bc7-a282-27ceb66384f6" />
<img width="1366" height="668" alt="image" src="https://github.com/user-attachments/assets/c80aa22b-48e9-489e-af74-58162cc053d4" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/e501aeeb-127c-440f-82ff-a5820f26ae5f" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/dc32c751-67ec-4898-8c19-68cbf87dd957" />
<img width="1366" height="667" alt="image" src="https://github.com/user-attachments/assets/65e27552-20fb-4212-9a1d-3191a0f97ff6" />
<img width="1366" height="288" alt="image" src="https://github.com/user-attachments/assets/ee57bc82-3c1a-4bf7-ac56-1ad736f5355c" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/6aca0f13-d5f5-4490-9a60-5af0be05ec00" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/7847f95c-ce3d-4e1f-b994-4456c095b0f8" />
<img width="1366" height="669" alt="image" src="https://github.com/user-attachments/assets/5cf5140b-187c-452e-8fce-e6188c9a06c8" />

<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/f20e76c4-6a21-4964-8afd-7732d4ba5a2d" />
<img width="1248" height="678" alt="image" src="https://github.com/user-attachments/assets/7f46fabe-0ae3-40df-b1c5-f05711a8de73" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/581678fe-79df-4ba8-9c7b-f5a1446773b6" />
<img width="1219" height="485" alt="image" src="https://github.com/user-attachments/assets/618d9286-e3ab-43c0-8db7-bf0b03586516" />
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/5034e972-3a9d-4127-8af0-f6c96d67da2d" />
<img width="1364" height="671" alt="image" src="https://github.com/user-attachments/assets/bb054641-4b1d-4b62-9e47-77f7b3fa9674" />


## Takeaways
This lab demonstrated how AWS Lambda can be used to build a serverless reporting solution. By configuring IAM permissions, Lambda layers, scheduled trigger and CloudWatch Logs, I see how serverless architecture enables automated, reliable and scalable workflows without managing infrastructure.

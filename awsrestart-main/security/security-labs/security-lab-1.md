# Security Lab: Using Amazon Inspector for vulnerability assesment and remediation

## Objective
Network Hardening, Activate Amazon Inspector, interpret the vulnerability reports, and remediate the findings.

## Steps Taken
1. Logged in the AWS Management Console
2. Activated and configured Amazon Inspector
   - Inspector > Activate Inspector > Activate Inspector
3. Refreshed the page periodically until I saw the Dashboard > Summary > Environment coverage> Lambda functions at 100%
4. Reviewed my Lambda functions, analyzed and interpreted vulnerability findings
   - Findings > All findings.
   - > CVE-2023-32681 - requests (this opens a pane containing the vulnerability information) 

Within the information pane, under the Vulnerability details section choose the external link next to the Vulnerability ID.
5. Remediated my Lambda function’s Package Vulnerabilities
   - On the AWS Management Console search box, searched for Lambda > list of Lambda functions > get-request function
   - Within the Lambda function code editor’s file browser, >requirements.txt and removed the version number
   - (The requirements.txt file tells AWS Lambda which Python packages are required to run your function. When no version number is specified, the latest version of the package will be installed by default. This ensures that your Lambda funtion uses the latest version of the package)
   - Deploy (the latest deployment of Lambda function triggers Amazon Inspector to initiate a new scan of the function)
6. Reviewed the inspected resources after new scan
   - Amazon Inspector > Findings > All findings
7. Confirmed successful remediation
   - Findings Dashboard > Finding Status, changed the selection from 'Active' to 'Closed'
   - In the list of closed findings, 'CVE-2023-32681 - requests' confirms the successful remediation of the vulnerability

## Challenges
- ..

## Screenshot
Amazon Inspector Configuration
<img width="1366" height="678" alt="image" src="https://github.com/user-attachments/assets/10db8b98-ccfe-403a-8a9f-ef38168d423d" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/0e3610b9-b49d-4e83-a87e-49cac33d9b25" />

Lambda Functions at 100%
<img width="1366" height="666" alt="image" src="https://github.com/user-attachments/assets/ecce5db0-d030-4897-823a-0ec09beb2a24" />

Vulnerability Findings
<img width="1366" height="657" alt="image" src="https://github.com/user-attachments/assets/b3d4830e-4357-429d-84cb-e9b3eb97bfae" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/c4f7c78c-47ff-4c03-bafa-ccb4e8d4062a" />
<img width="1366" height="729" alt="image" src="https://github.com/user-attachments/assets/1d53c649-1181-4fcc-aa89-0d6523ecebed" />

Remediation Configuration
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/b7fd6d78-f07e-4146-a2cb-427a85f4c86a" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/31732723-08b5-46dd-addb-f040a2a4a6a3" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/fc4d2577-664c-49e0-a16c-96bd227564d4" />

Deployment
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/bf90b233-784f-4d33-8417-cb4f7d70d3cc" />

New Scan Findings
<img width="1366" height="663" alt="image" src="https://github.com/user-attachments/assets/397b9ca2-843a-48c1-9569-644eb3de910c" />


Confirmed successful Remediation
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/40c391f6-2e1d-4ccc-840f-17962a24c1d9" />

## Takeaways
After completing the lab, I am confident in my vulnerability assesment and remediation skills.


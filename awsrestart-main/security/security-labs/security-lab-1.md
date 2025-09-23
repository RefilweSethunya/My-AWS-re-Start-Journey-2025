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
Lambda Functions at 100%
Vulnerability Findings
Remediation Configuration
Deployment
New Scan Findings
Confirmed successful Remediation

## Takeaways
Security groups work like firewalls. Always make sure the required ports are open.


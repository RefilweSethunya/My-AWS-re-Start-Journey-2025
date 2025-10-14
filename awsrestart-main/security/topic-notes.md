# Security Notes

## User Authentication
- Enforce strong passwords by creating an IAM password policy. 
- Require Multi-Factor Authentication (MFA) for an added security layer.  
- For programmatic or CLI access, use security credentials (Access Key ID + Secret Access Key).  
- For EC2 Linux instances, authenticate via an SSH key pair AWS generated, and the private key must be stored on the client machine.

## Access Management
- Use IAM groups to manage permissions efficiently for multiple users.  
- Follow the Principle of Least Privilege.  
- Use IAM roles to grant specific permissions to AWS services or applications securely.

## Monitoring & Compliance
- Generate and review the IAM Credential Report to track user security status and key usage.  
- AWS Artifact for information about AWS compliance with regulatory and industry standards.

## Reflection
Maintaining security in AWS requires both proactive configuration and continuous monitoring. By enforcing strong password policies and MFA, organizations can significantly reduce the risk of unauthorized access. Proper use of IAM groups and roles ensures that users and services operate with only the permissions they need, minimizing the potential impact of compromised credentials. Regularly reviewing credential reports and compliance artifacts helps identify vulnerabilities early and maintain alignment with industry standards. Ultimately, a culture of least privilege and continuous auditing is essential to sustain a secure and well-governed cloud environment.

## Exam Essentials
Know how to lock down your account’s root user to reduce your exposure to risk.<br> Make sure your root user has a strong password that is MFA-enabled and is never used for day-to-day administration tasks.
<br><br>
Understand how AWS manages access credentials for EC2 key pairs, secret access keys, and encryption keys.<br> Whether you’re looking to secure terminal connections to your EC2 servers, API access, or the privacy of your data, you’ll need to make use of AWS encryption services of one sort or another.
<br><br>
Know how to provide (federated) access to your AWS resources based on third-party authentication systems like Google.<br> Using standards such as SAML 2.0 and Microsoft’s Active Directory, you can incorporate external authentication into your AWS infrastructure, making it easy, for instance, for users of your mobile application to retrieve data from a DynamoDB database.
<br><br>
Be aware that AWS Key Management Service (KMS) manages encryption keys.<br> KMS-managed keys are used across a wide range of AWS services, including EBS, RDS, DynamoDB, and S3.
<br><br>
Be aware that AWS Artifact is a compliance information resource

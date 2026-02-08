# Linux Lab: Software Management

## Objective
Learn how to update the Linux machine using the package manager.<br>
Learn how to roll back or downgrade a previously updated package through the package manager.<br>
Learn how to install the AWS Command Line Interface (AWS CLI).

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to an Amazon Linux EC2 instance
4. Update my Linux machine
   - Queried repositories for available updates, entered:
     ```bash
     sudo yum -y check-update
     ```
   - Applied security-related updates, entered:
     ```bash
     sudo yum update --security
     ```
   - Updated packages, entered:
     ```bash
     sudo yum -y upgrade
     ```
   - Viewed the install of httpd and view the history of updates, entered:
     ```bash
     sudo yum install httpd -y
     ```
5. Rolled back a package
   - Viewed the history of updates, entered:
     ```bash
     sudo yum history list
     ```
   - Viewed the most recent set of updates, entered:
     ```bash
     sudo yum history info <#>
     ```
     Replacing <#> with the history list number
   - Rolled back the packages by entering:
     ```bash
     sudo yum -y history undo <#>
     ```
     Replacing <#> with the history list number
6. Installed the AWS CLI on Red Hat Linux
   - Verified that Python and pip is installed, enter the following commands:
     ```bash
     python3 --version
     ```
     ```bash
     pip3 --version
     ```
   - Downloaded the AWS CLI installation file using the curl command:
     ```bash
     curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
     ```
   - Unzipped the installer:
     ```bash
     unzip awscliv2.zip
     ```
   - Run the install program:
     ```bash
     sudo ./aws/install
     ```
7. Configured the AWS CLI to connect to my AWS account
    - Entered the following configuration command for the AWS CLI:
      ```bash
      aws configure
      ```
    - At the prompts, entered the following information:
      - For the AWS Access Key ID,
      - For the AWS Secret Access Key,
      - For the Default region name,
      - For the Default output format.
     - Confirmed that the appropriate credential files are created automatically, entered:
       ```bash
       sudo nano ~/.aws/credentials
       ```
     - Queried my instance type by instance ID, entered:
       ```bash
       aws ec2 describe-instance-attribute --instance-id i-1234567890abcdefg --attribute instanceType
       ```

## Challenges
- ...

## Screenshot
Checking for available updates
<img width="1309" height="661" alt="image" src="https://github.com/user-attachments/assets/c1cba4ab-75a3-4b3d-9351-af1e44802b6d" />
Updating my Linux machine
<img width="1308" height="655" alt="image" src="https://github.com/user-attachments/assets/c08300cc-966e-48b3-a63f-f9bd868c3883" />
Querying and Performing roll back of two(2) previously updated packages through the package manager
<img width="1311" height="635" alt="image" src="https://github.com/user-attachments/assets/27a04ad5-c299-486d-bf5c-6b56c86a4930" />
Installing the AWS CLI on Red Hat Linux(python and pip are pre-requisites)
<img width="1317" height="657" alt="image" src="https://github.com/user-attachments/assets/e712774f-f7d9-4bdb-b4b7-cbcaacf762e7" />
Configuring the AWS CLI to connect to my AWS account
<img width="1307" height="288" alt="image" src="https://github.com/user-attachments/assets/1d440eda-f801-47dc-9205-37a6ece7b280" />
<img width="1308" height="661" alt="image" src="https://github.com/user-attachments/assets/b9a18d6e-02e9-4e4d-9a76-7237e420753e" />
<img width="1074" height="182" alt="image" src="https://github.com/user-attachments/assets/b5c560a3-ddef-4b0b-9c1d-5f0bfbc237da" />



## Takeaways

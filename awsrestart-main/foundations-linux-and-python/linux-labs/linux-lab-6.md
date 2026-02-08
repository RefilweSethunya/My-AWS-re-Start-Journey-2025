# Linux Lab: Working with Files

## Objective
Learn how to create a backup file of an entire folder structure using tar; log the creation of the backup in a file with the date, time, and file name of the backup file; and transfer the backup file to another folder

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to an Amazon Linux EC2 instance
4. Created the backup
   - Ensured that we are in the /home/ec2-user/ folder by running `pwd`
   - Validated that the CompanyA folder exist, entered the following command:
     ```bash
     ls -R CompanyA
     ```
   - Backed up the entire CompanyA folder structure recursively, entered the following command:
     ```bash
     tar -csvpzf backup.CompanyA.tar.gz CompanyA
     ```
5. Logged the backup
   - Navigated to the CompanyA folder, entered the following command:
     ```bash
     cd /home/ec2-user/CompanyA
     ```
   - Created an empty backup file named backups.csv, entered the following command:
     ```bash
     touch SharedFolders/backups.csv
     ```
   - Added the date, time, and file name to the backups.csv file, entered the following command:
     ```bash
     echo "08 Feb 2026, 15:11, backup.CompanyA.tar.gz" | sudo tee SharedFolders/backups.csv
     ```
   - Displayed the content of the file, entered the following command:
     ```bash
     cat SharedFolders/backups.csv
     ``
6. Moved the backup
   - Ensured that we are in the CompanyA folder by running `pwd`
   - Transferred the backup file to the IA team computer, entered the following command:
     ```bash
     mv ../backup.CompanyA.tar.gz IA/
     ```
   - Verified that the backup file was moved, entered the following command:
     ```bash
     ls . IA
     ```

## Challenges
- ...

## Screenshot
<img width="1150" height="648" alt="image" src="https://github.com/user-attachments/assets/b4ead02d-8c70-462d-a938-056db10001cb" />
<img width="1149" height="546" alt="image" src="https://github.com/user-attachments/assets/ced91166-70cf-4fe6-a104-cda219c2bc08" />
<img width="1131" height="105" alt="image" src="https://github.com/user-attachments/assets/2f504e79-5785-48fb-8d6d-78223c48bb92" />
<img width="1126" height="147" alt="image" src="https://github.com/user-attachments/assets/ef8bd6fa-2e07-4927-b897-f30c239a80f8" />

## Takeaways
We can use the tee command to write information both in the terminal and in a file.
A | redirector redirects the output of the echo command to the second command, tee, which writes it to both the terminal and the specified file.

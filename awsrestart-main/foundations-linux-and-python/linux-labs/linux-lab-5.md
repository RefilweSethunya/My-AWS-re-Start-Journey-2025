# Linux Lab: Working with the File System

## Objective
Learn how to create a folder structure; create files; copy and move files and directories; and delete files and directories.<br>
The specific folder structure A provided as below:<br>
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/dfedf29a-519e-44f2-9d46-23ed876c530d" />
<br>Structure B provided as below:<br>
<img width="500" height="560" alt="image" src="https://github.com/user-attachments/assets/71b276c1-59f3-466b-bcf1-8c3b74913e14" />


## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to an Amazon Linux EC2 instance
4. Created the Folder Structure A in the virtual machine 
   ```bash
   /home/ec2-user/CompanyA/
   /home/ec2-user/CompanyA/Finance/
   /home/ec2-user/CompanyA/Finance/ProfitAndLossStatements.csv
   /home/ec2-user/CompanyA/Finance/Salary.csv
   /home/ec2-user/CompanyA/HR/
   /home/ec2-user/CompanyA/HR/Assessments.csvv
   /home/ec2-user/CompanyA/HR/TrialPeriod.csv
   /home/ec2-user/CompanyA/Management/
   /home/ec2-user/CompanyA/Management/Managers.csv
   /home/ec2-user/CompanyA/Management/Schedule.csv
   ```
   - Run `pwd` to validate that you are in the home folder of your current user and if not you run `cd /home/ec2-user`
   - In the terminal, entered `mkdir CompanyA` to create the top-level folder.
   - Changed directories `cd CompanyA`.
   - Created all the sub folders by running `mkdir Finance HR Management`.
   - Changed directory to the HR directory, enter `cd HR` and press Enter.
   - Created the empty files inside the HR folder, enter `touch Assessments.csv TrialPeriod.csv` and press Enter.
   - Run `ls`to validate that the files were created.
   - Changed directory to the Finance directory, enter `cd Finance` and press Enter.
   - Created the empty files inside the HR folder, enter `touch Salary.csv  ProfitAndLossStatements.csv` and press Enter.
   - Run `ls`to validate that the files were created.
   - Changed directory back one level to the CompanyA folder, enter `cd..`
   - This time to create the new empty files in the Management folder, enter `touch Management/Managers.csv Management/Schedule.csv` and pressed Enter.
   - Run `ls Management` to validate that the files were created.
   - Validated that all the files and folders from the CompanyA folder down have been created, enter ls -laR

6. Deleted and reorganized folders to reflect Structure B.
   - Copy the Finance folder and its content to the HR folder and remove the previous Finance folder:
     ```bash
     cp -r Finance HR
     rmdir Finance
     ```
   - Move the Management folder inside the HR folder:
     ```bash
     mv Management HR
     ls . HR/Management
     ```
   - Create an Employees folder inside the HR folder, and move the Assessments.csv and TrialPeriod.csv file inside the Employees folder:
     ```bash
     cd HR
     mkdir Employees
     mv Assessments.csv TrialPeriod.csv Employees
     ls . Employees
     ```


## Challenges
- ...

## Screenshot
_(Optional – paste image if available)_

## Takeaways

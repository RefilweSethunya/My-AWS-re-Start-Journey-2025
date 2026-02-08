# Linux Lab: Managing Processes

## Objective
Learn how to create a new log file for process listings; use the top command; and establish a repetitive task that runs previous auditing commands once a day.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to an Amazon Linux EC2 instance
4. Created a list of processes
   - Validated we are in the /home/ec2-user/companyA folder using `pwd`, if not entered `cd companyA`
   - Viewed all processes running on the machine and filter out the word root by running the following command:
     ```bash
     sudo ps -aux | grep -v root | sudo tee SharedFolders/processes.csv
     ```
   - Validated by running the following command:
     ```bash
     cat SharedFolders/processes.csv
     ```
5. Listed the processes using the top command
   - Displayed processes and threads that are active in the system with
     ```bash
     top
     ```
   - Displayed process and threads that are active in the system and also the usage and version information:
     ```bash
     top -hv
     ```
6. Created a Cron Job
   - Validated we are in the /home/ec2-user/companyA folder using `pwd`
   - Create a cron job that creates the audit file with ##### to cover all .csv files, entered:
     ```bash
     sudo crontab -e
     ```
   - For the first line, entered:
     ```bash
     SHELL=/bin/bash
     ```
   - For the second line, entered:
     ```bash
     PATH=/usr/bin:/bin:/usr/local/bin
     ```
   - For the third line, entered:
     ```bash
     MAILTO=root
     ```
   - For the last line, entered:
     ```bash
     0 * * * * ls -la $(find .) | sed -e 's/..csv/#####.csv/g' > /home/ec2-user/companyA/SharedFolders/filteredAudit.csv
     ```
   - Saved and closed the file, pressed ESC. Then entered `:wq`
   - Inspected the crontab file to ensure that it matches the text exactly, entered:
     ```bash
     sudo crontab -l
     ```

## Challenges
- ..

## Screenshot
<img width="1291" height="373" alt="image" src="https://github.com/user-attachments/assets/247bb89d-3b2d-473c-848d-bacfbca4d8d2" />
top
<img width="1284" height="647" alt="image" src="https://github.com/user-attachments/assets/3fb85519-33b6-49ae-8ed9-6deef31670af" />
top -hv
<img width="1280" height="80" alt="image" src="https://github.com/user-attachments/assets/b5edbe18-5f7e-475c-b328-4cf319388121" />
Creating a cron job
<img width="1289" height="639" alt="image" src="https://github.com/user-attachments/assets/93bdcd72-9767-463a-892b-569ff7957b07" />
<img width="1296" height="146" alt="image" src="https://github.com/user-attachments/assets/817150e2-3382-4a5e-ab69-10b3f6bd6e6a" />


## Takeaways
Cron is a command that runs a task on a regular basis at a specified time. This command maintains the list of tasks to run in a crontab file, which you create in this task. You create a job that creates the audit file with ##### in order to cover all .csv files. 

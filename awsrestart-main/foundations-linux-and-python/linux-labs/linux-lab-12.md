# Linux Lab: Bash Shell Scripts

## Objective
Learn how to create a bash script that will automate the backup of a folder.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to an Amazon Linux EC2 instance
4. Wrote a shell script
   - Created a generic shell script called backup.sh, entered the following command:
   - Changed the file privileges to make backup.sh executable, entered the following command:
   - Opened the backup.sh file for editing:
     ```bash
     vi backup.sh
     ```
   - Activated insert mode, entered `i`
   - On line 1 of the script, entered:
     ```bash
     #!/bin/bash
     ```
   - On line 2 of the script, created a variable for the current date, entered:
     ```bash
     DAY="$(date +%Y_%m_%d_%T_%H_%M)"
     ```
   - On line 3 of the script, created a variable for the backup file for the day, entered:
     ```bash
     BACKUP="/home/$USER/backups/$DAY-backup-CompanyA.tar.gz"
     ```
   - On line 4 of the script, entered:
     ```bash
     tar -csvpzf $BACKUP /home/$USER/CompanyA
     ```
   - Pressed the Esc key, entered `:wq` to save and close the file
   - Run backup.sh script:
     ```bash
     ./backup.sh
     ```
   - Verified that the archive is created in the backups folder, entered the following command:
     ```bash
     ls backups/
     ```

## Challenges
- ...

## Screenshot
<img width="1296" height="650" alt="image" src="https://github.com/user-attachments/assets/66c1d7e8-a121-48ad-953b-8f98915da4c4" />


<img width="1293" height="646" alt="image" src="https://github.com/user-attachments/assets/d0335da6-7167-49dc-9bc9-f71fe0800a5a" />

## Takeaways

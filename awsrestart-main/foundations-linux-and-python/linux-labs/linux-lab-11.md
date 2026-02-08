# Linux Lab: The Bash Shell

## Objective
Learn how to create and work with an alias that uses the tar to back up the second parameter provided into the first parameter. The following is a command line example:<br>
```bash
backup “fileToSaveTo.tar.gz” “pathToBackUp”
```
<br>
Learn how to work the PATH variable and add a new folder to it.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to an Amazon Linux EC2 instance
4. Created an alias for a backup operation
   - Created an alias called backup, Entered:
     ```bash
     alias backup='tar -cvzf'
     ```
   - Used the backup alias to back up the CompanyA folder, entering the following command:
     ```bash
     backup backup_companyA.tar.gz CompanyA
     ```
   - Verified that the archive is created using the `ls` command
5. Explored and updated the PATH environment variable
   - Navigated to the bin folder, entered:
     ```bash
     cd /home/ec2-user/CompanyA/bin
     ```
   - Run the hello.sh script, entered the following command:
     ```bash
     ./hello.sh
     ```
   - Navigated to parent folder using `cd..`
   - To run the hellos.sh script again we run the following command:
     ```bash
     ./bin/hello.sh
     ```
     Running the command `hello.sh` returns an error.
   - Displayed the value of the PATH variable:
     ```bash
     echo $PATH
     ```
     The **PATH** variable is a list of folders where the system looks for executables and libraries.<br>
     The folder **/home/ec2-user/bin** is not listed so we add it next.
   - Added the /home/ec2-user/CompanyA/bin folder to the PATH variable, enter the following command:
     ```bash
     PATH=$PATH:/home/ec2-user/CompanyA/bin
     ```
   - Run the hello.sh script again, entering `hello.sh` to find no error this time. It runs successfully.

## Challenges
- ...

## Screenshot
Creating alias
<img width="1322" height="629" alt="image" src="https://github.com/user-attachments/assets/2cc9f6b7-2783-47bf-b847-58c2e142e6e6" />
Updating PATH variable
<img width="1320" height="215" alt="image" src="https://github.com/user-attachments/assets/212eea63-3a94-48a5-ac08-4dfbcdb5603b" />


## Takeaways

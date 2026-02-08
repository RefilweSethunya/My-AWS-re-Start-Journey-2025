# Linux Lab: Managing Log Files

## Objective
Learn how to review the lastlog and secure log outputs of the Linux machine.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to the Amazon Linux EC2 instance
4. Reviewed secure log files
   - Viewed the list of errors and failures including where the user was trying to access from (IP address), if they failed authentication, and which port, entered:
     ```bash
     sudo less /tmp/log/secure
     ```
   - Viewed the last login times of all the users on the machine, entered:
     ```bash
     sudo lastlog
     ```
## Challenges
- ...

## Screenshot
<img width="1296" height="650" alt="image" src="https://github.com/user-attachments/assets/c33110e0-f848-4e60-8b7e-39fffda34364" />
<img width="1287" height="647" alt="image" src="https://github.com/user-attachments/assets/de9926db-0884-40e6-82fe-8d81899aa947" />


## Takeaways

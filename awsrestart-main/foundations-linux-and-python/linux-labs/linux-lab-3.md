# Linux Lab: Users and Groups

## Objective
Learn how to create new users with a default password; create groups and assign the appropriate users; and log in as different users.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Use SSH to connect to an Amazon Linux EC2 instance
4. Created Users
   - Validated that I am in the home folder of current user by typing `pwd` and pressing ENTER.
   - Added the first user Refilwe Sethunya, by entering command
     ``` bash
     sudo useradd rsethunya
     ```
   - Created password for user, by typing command
     ```bash
     sudo passwd rsethunya
     ```
     You will be required to enter the password twice.
   - Created more users(arosalez) and validated that users have been created, by entering the below to look at the contents of the /etc/passwd file.
     ``` bash
     sudo cat /etc/passwd | cut -d: -f1
     ```
6. Created Groups
   - Created the Sales group, entered `sudo groupadd Sales` and pressed Enter.
   - Verified that the group was added, entered `cat /etc/group` and pressed Enter.
   - Used the `sudo usermod -a -G <Group Name> <User ID>` command to add the remaining users to the appropriate groups.
   - To check the group memberships, we use `sudo cat /etc/group`
8. Logged in using the new users
   - Entered `su arosalez`to switch user (password required action).
   - The user arosalez does not have permission to write files to the ec2-user home folder. So we run the command as an admin using the sudo command.
   - Entered
     ```bash
     sudo touch myFile.txt
     ```
   - Entered `exit` and pressed Enter to switch to the previous user(ec2-user).
   - Displayed the content of the secure file to see how a sudo and an unpermitted action was logged into the /var/log/secure file.
     ```bash
     sudo cat /var/log/secure
     ```
  

## Challenges
- ...

## Screenshot
<img width="1220" height="565" alt="image" src="https://github.com/user-attachments/assets/5153d169-efee-4706-955e-87a31749c29e" />
<img width="1219" height="561" alt="image" src="https://github.com/user-attachments/assets/2d5f8f71-5018-4a00-96a8-8a8148213b4c" />
<img width="1207" height="410" alt="image" src="https://github.com/user-attachments/assets/787b3511-227a-42ec-9f51-7b27c7522171" />
<img width="1204" height="618" alt="image" src="https://github.com/user-attachments/assets/c2a91e9d-1883-4ee1-8a3e-87bddc7a8184" />
<img width="1205" height="189" alt="image" src="https://github.com/user-attachments/assets/749177a8-699d-4ec3-a40b-111f647d4e32" />
<img width="1202" height="615" alt="image" src="https://github.com/user-attachments/assets/0fbfc41a-86e1-4d9d-bee8-13cf3e0f8485" />
<img width="1202" height="129" alt="image" src="https://github.com/user-attachments/assets/251fb80a-f4bc-4bc5-a8a7-1e7de3b42259" />
<img width="1216" height="656" alt="image" src="https://github.com/user-attachments/assets/4d227ff7-6af6-40f1-92f7-ed7682e42761" />
<img width="1230" height="84" alt="image" src="https://github.com/user-attachments/assets/c0a6f947-9e35-4562-beb6-85cd118f16ca" />


## Takeaways
Best practice is to assign one user per account. Don’t share accounts.<br>**grep** is a very useful Linux command we can use to search text(logs).

Any time a sudo permission is used, **it is logged**.<br>
The use of sudo permissions is logged at /var/log/messages;<br>
A command that is run with sudo permissions is logged at /var/log/secure.

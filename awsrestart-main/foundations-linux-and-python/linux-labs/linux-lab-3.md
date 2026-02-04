# Linux Lab: Users and Groups

## Objective
Learn how to create new users with a default password; create groups and assign the appropriate users; and log in as different users.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Use SSH to connect to an Amazon Linux EC2 instance
4. Create Users
   - Validate that you are in the home folder of your current user by typing `pwd` and pressing ENTER.
   - To add the first user from the list above, Alejandro Rosalez, enter sudo useradd arosalez and press Enter.
   - Enter sudo passwd arosalez and press Enter. You are required to enter the password twice
   - To validate that users have been created, enter sudo cat /etc/passwd | cut -d: -f1 and press Enter to look at the contents of the /etc/passwd file.
   - 
6. Create Groups
7. Log in using the new users

## Challenges
- ...

## Screenshot
_(Optional – paste image if available)_

## Takeaways
Best practice is to assign one user per account. Don’t share accounts.<br>**grep** is a very useful Linux command we can use to search text(logs).

Any time a sudo permission is used, **it is logged**.<br>
The use of sudo permissions is logged at /var/log/messages;<br>
A command that is run with sudo permissions is logged at /var/log/secure.

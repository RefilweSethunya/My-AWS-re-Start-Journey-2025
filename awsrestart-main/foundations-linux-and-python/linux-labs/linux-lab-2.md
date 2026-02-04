# Linux Lab: Linux Command Line

## Objective
Run commands to gain knowledge of current system and current session. Search and run previous bash commands.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Use SSH to connect to an Amazon Linux EC2 instance
4. Run familiar commands to give basic information about the system you are currently using for troubleshooting purposes.
   - To find the user
     ```bash
     whoami
     ```
   - To find the IP address
     ```bash
     hostname -s
     ```
   - To find how long your system has been running
     ```bash
     uptime -p
     ```
   - To displays the information about the user such as the name, line which gives information, time the event occured, idle time of the user, Process Identifier (PID), comment and exit time
     ```bash
     who -H -a
     ```
   - To output of the current weekday, month, date, time, timezone, and year
     ```bash
     TZ=America/New_York date
     ```
     ```bash
     TZ=America/Los_Angeles date
     ```
   - To display alternate views of the calendar
     - entering `cal -j` in the terminal to see the Julian dates for the current month
     - entering `cal -s` to give the output of February from Sunday through Saturday
     - entering `cal-m` to give the output from Monday through Sunday
     
   - To output the user id, group id, and groups that the user is apart of
     ```bash
     id ec2-user
     ```
     
5. Improve workflow through history and search
   - ```bash
     history
     ```
   - run the most recent command using `!!`

## Challenges
- ...

## Screenshot
<img width="1187" height="484" alt="image" src="https://github.com/user-attachments/assets/d539bd17-6350-4e2c-95f1-17a23695cf2d" />
<img width="1185" height="658" alt="image" src="https://github.com/user-attachments/assets/48ba9ec7-70f0-4682-8429-8de5f486cf4f" />
<img width="1183" height="355" alt="image" src="https://github.com/user-attachments/assets/5aa90413-c207-47c2-8bc8-0d865b3e03e9" />


## Takeaways
From the terminal, entering an incomplete command and pressing Tab will have the auto complete feature display the full command whereas entering `!!` will display the most recent command.

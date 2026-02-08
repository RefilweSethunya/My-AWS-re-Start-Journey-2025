# Linux Lab: Managing Services and Monitoring

## Objective
Learn how to check the status of the service httpd to ensure that your Amazon Linux 2 EC2 instance is running, and that you can make an http connection to the local host IP address

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to an Amazon Linux EC2 instance
4. Checked the Status of the httpd Service
   - Checked the status of the httpd service by using the systemctl commands as follows:
     ```bash
     sudo systemctl status httpd.service
     ```
   - Changed the status of the httpd service to "_**active(running)**_" by using the systemctl commands as follows:
     ```bash
     sudo systemctl start httpd.service
     ```
   - Checked the status of the httpd service again by using the systemctl commands:
     ```bash
     sudo systemctl status httpd.service
     ```
   - Once the httpd was running, Opened a new tab on the browser and entered: http://<ourpublicip>
   - Stopped the service by entering the command below:
     ```bash
     sudo systemctl stop httpd.service
     ```

## Challenges
- ...

## Screenshot
<img width="1223" height="614" alt="image" src="https://github.com/user-attachments/assets/cfec4617-18c0-4033-bfef-611ed8ae9b67" />

<img width="889" height="655" alt="image" src="https://github.com/user-attachments/assets/ff8b91ed-b445-44e7-a0d8-90b8d20e4e49" />

<img width="1212" height="171" alt="image" src="https://github.com/user-attachments/assets/2a1dc74b-6a13-4711-89a9-b51d3db3a281" />

## Takeaways

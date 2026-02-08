# Linux Lab: Managing File Permissions

## Objective
Learn how to change all folder and file permissions to match the appropriate group structure;<br>
Learn how to modify file permissions for a user.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to an Amazon Linux EC2 instance
4. Changed file and folder ownership
   - Changed companyA folder ownership to the CEO and group ownership to Personnel, entered:
     ```bash
     enter sudo chown -R mjackson:Personnel /home/ec2-user/companyA
     ```
   - Changed HR folder ownership to the HR manager and group ownership to HR, entered:
     ```bash
     sudo chown -R ljuan:HR HR
     ```
   - Finance folder ownership to the finance manager and group ownership to Finance, entered:
     ```bash
     sudo chown -R mmajor:Finance HR/Finance
     ```
    - Validate the changes using `ls -laR`
5. Changed permission modes
   - Used vim to create a file called symbolic_mode_file. To create this file, entered:
     ```bash
     sudo vi symbolic_mode_file
     ```
     Remembering to save and close by pressing ESC and `:wq`.
   - Gave the group owner write permissions to the symbolic_mode_file. To change the file permissions, entered:
     ```bash
     sudo chmod g+w symbolic_mode_file
     ```
   - Used vim to create a file called absolute_mode_file. To create this file, entered:
     ```bash
     sudo vi absolute_mode_file
     ```
     Remembering to save and close by pressing ESC and `:wq`.
   - Gave the user read, write, and execute permissions to the absolute_mode_file. To change the file permissions, entered:
     ```bash
     sudo chmod 764 absolute_mode_file
     ```
   - Confirmed this information using the `ls -l` command
6. Assigned permissions
   - Validated that we are in the /home/ec2-user/companyA folder using the `pwd` command
   - Changed the ownership of the Shipping folder to eowusu, the current shipping manager, and the group ownership to Shipping, entered the following command:
     ```bash
     sudo chown -R eowusu:Shipping Shipping
     ```
   - Changed the ownership of the Sales folder to nwolf, the current sales manager, and the group ownership to Sales, entered the following command:
     ```bash
     sudo chown -R nwolf:Sales Sales
     ```
   - Validated the changes to the Shipping folder, entered the following command:
     ```bash
     ls -laR Shipping
     ```
   - Validated the changes to the Sales folder, entered the following command:
     ```bash
     ls -laR Sales
     ```

## Challenges
- ...

## Screenshot
<img width="1221" height="321" alt="image" src="https://github.com/user-attachments/assets/0ddb167a-d368-4446-9c7a-e693ed138a47" />
<img width="1211" height="284" alt="image" src="https://github.com/user-attachments/assets/423b8d3d-7c5f-4a7f-adff-4d052da28e20" />
<img width="1207" height="218" alt="image" src="https://github.com/user-attachments/assets/46450629-a0d5-43cf-a2df-271bdce11318" />


## Takeaways

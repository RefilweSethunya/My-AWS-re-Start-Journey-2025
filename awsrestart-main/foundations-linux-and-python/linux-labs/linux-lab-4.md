# Linux Lab: Editing Files

## Objective
Learn how to edit a file in vim and also in nano.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to an Amazon Linux EC2 instance
4. Started the vimtutor session vimtutor by entering `vimtutor` and pressing enter. It was already installed but run `install sudo yum install vim` if you need to install vim.
5. Entered `:q!` and pressed Enter to exit vimtutor.
6. Used Vim to create a file called HelloWorld
   ```bash
   vim HelloWorld
   ```
7. Inserted a few lines of text. First, entered `i` to use insert mode, and then entered the following text
   ```bash
   Hello World!This is my first file in Linux and I am editing it in Vim!
   ```
   And once completed, pressed ESC on my keyboard to exit insert mode.
8. In order to save changes made to the file, run the following command to quit:
    ```bash
    :wq
    ```    
9. Used Vim to modify the same file called HelloWorld
   ```bash
   vim HelloWorld
   ```
10. Added the following line to the editor:
    ```bash
    I learned how to create a file, edit and save them too!
    ```
    And once complete, pressed ESC to exit insert mode and this time around used the following command:`:q`
11. In the main terminal. Used `cat HelloWorld` to display the helloworld file and analyze the difference to notice the file was infact not modified because `:wq` and `:q` do different things.
12. Edited a file using nano.
    Similar to Vim, in the main terminal, enter `nano cloudworld` and press Enter. This creates a file called cloudworld.
16. Unlike vim, you do not have to enter insert mode. Instead, you can start typing.
17. To save changes to the file, press CTRL+O.
18. To exit the nano editor, press CTRL+X 

## Challenges
- ...

## Screenshot
<img width="1212" height="347" alt="image" src="https://github.com/user-attachments/assets/9be3c252-c657-44ba-a4ae-02fc7c061757" />
<img width="1214" height="634" alt="image" src="https://github.com/user-attachments/assets/e411d12a-b88f-458e-bc47-bb069c25ec7b" />
<img width="1211" height="657" alt="image" src="https://github.com/user-attachments/assets/1b83ad44-d151-4bff-93ea-1f5ddbde138b" />
<img width="1220" height="658" alt="image" src="https://github.com/user-attachments/assets/39b29474-a83a-43e3-8780-b0bc26ae2b51" />
<img width="1210" height="448" alt="image" src="https://github.com/user-attachments/assets/ae1f0de4-1d8e-4044-a2f9-911fc94eed52" />
<img width="1209" height="450" alt="image" src="https://github.com/user-attachments/assets/24392e1d-f324-4788-b048-2d13d7437a5a" />
<img width="1208" height="447" alt="image" src="https://github.com/user-attachments/assets/8310ac70-9e7d-4bf4-832a-8a22ed4b477b" />
<img width="1209" height="450" alt="image" src="https://github.com/user-attachments/assets/acf451da-3366-4332-b916-5681aab43450" />
<img width="1211" height="448" alt="image" src="https://github.com/user-attachments/assets/c7b65f3e-fefd-4b7f-8815-8f7e6af47596" />
<img width="1214" height="447" alt="image" src="https://github.com/user-attachments/assets/1ba8fba2-3fd8-4f8a-964c-909bb1743dba" />

## Takeaways
Common actions to remember in vim: Use `dd` to delete the entire line; Use `u` to undo the last command; and Use `:w` to save changes without quitting.

# Linux Lab: Working with Linux Commands

## Objective
Learn how to:<br>
Use the tee command to direct output to a file.<br>
Use the sort command to reorganize the contents of a .csv file.<br>
Use the cut command to edit the contents of a file.<br>
Use the sed command.<br>
Use the pipe operator.

## Steps Taken
1. Logged into AWS Console
2. Launched EC2 instance (Ubuntu)
3. Used SSH to connect to an Amazon Linux EC2 instance
4. Used the tee command
   - Validated that we are in the /home/ec2-user folder using `pwd`
   - Entered `hostname | tee file1.txt`
   - confirm that the file1.txt file has been created, enter ls
6. Used the sort command and pipe operator
   - Validated that we are in the /home/ec2-user folder using `pwd`
   - Entered `cat > test.csv`
   - Insert the following text into the file
     ```text
     Factory, 1, Paris
     Store, 2, Dubai
     Factory, 3, Brasilia
     Store, 4, Algiers
     Factory, 5, Tokyo
     ```
   - Pressed CTRL+D to exit the file
   - Used the sort command. Entered `sort test.csv` to reorder the list
   - Searched for the factory named Paris using the pipe (|) operator, entered `find | grep Paris test.csv`
8. Used the cut command
   - Validated that we are in the /home/ec2-user folder using `pwd`
   - Entered `cat > cities.csv`
   - Pressed CTRL+D to exit the file
   - Used the cut command to cut sections from lines of text by character.
     Used the -d (delimiter) option, the "," character, and the -f (field) option to extract the first field of each record. Entered the following command:
     ```bash
     cut -d ',' -f 1 cities.csv
     ```
10. Used the sed command to replace the first comma (,) with periods (.) in both the cities.csv and test.csv files
    ```bash
    sed 's/word being replaced/replacement word/' file name
    ```
    ```bash
    sed 's/,/./' cities.csv test.csv
    ```

## Challenges
- ...

## Screenshot
<img width="1279" height="104" alt="image" src="https://github.com/user-attachments/assets/8e1d7085-fdc2-421c-8e95-2ce031918e81" />
<img width="1278" height="349" alt="image" src="https://github.com/user-attachments/assets/37e5d468-f32e-4a41-b310-05b58cb9aa6f" />
<img width="1281" height="281" alt="image" src="https://github.com/user-attachments/assets/9abd4f88-7ba6-4384-a41d-981d1272cece" />
<img width="1277" height="426" alt="image" src="https://github.com/user-attachments/assets/90adb5fe-bad7-4985-a740-5dc048697c48" />


## Takeaways

# Python Lab: Categorize values

## Objective
Learn how to mix types in a list. In this lab, we create a list with different types and print the values.
- Use numeric data types
- Use string data types
- Use the list data type
- Use a `for` loop
- Use the `print()` function

## Steps Taken
1. Logged into AWS Management Console
2. Services > Cloud9 > reStart-python-cloud9 card > Selected it and opened IDE
3. Created Python Exercise File
   - In the AWS Cloud9 IDE, File > New From Template > Python File.
   - File > Save As > CategorizingValues.py
4. Started the terminal shell
   - In the AWS Cloud9 IDE > Selected the (+) icon > New Terminal
   - Displayed the present working directory and located CategorizingValues.py file:
     ``` bash
     pwd
     ```
5. Creating a mixed-type list
   - Define a list with different types, like the following example:
     ``` python
     myMixedTypeList = [45, 290578, 1.02, True, "My dog is on the bed.", "45"]
     ```
   - Use a for loop statement to traverse the list and print the data type for each item in the list:
     ``` python
     for item in myMixedTypeList:
     print("{} is of the data type {}".format(item,type(item)))
     ```
   - Save the file
   - Run the file

## Challenges
- Forgot to open port 22 in the security group
- Solved by editing the inbound rules

## Screenshot
_(Optional – paste image if available)_

## Takeaways

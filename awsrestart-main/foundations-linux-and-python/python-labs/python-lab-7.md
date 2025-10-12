# Python Lab: Conditionals

## Objective
A section of code that compares two pieces of information is called a conditional statement. In this lab we learn how to use conditionals to create different paths through the program. Using comparative operators, we write a program that makes decisions.

## Steps Taken
1. Logged into AWS Management Console
2. Services > Cloud9 > reStart-python-cloud9 card > Selected it and opened IDE
3. Created Python Exercise File
   - In the AWS Cloud9 IDE, File > New From Template > Python File.
   - File > Save As > `conditionals.py`
4. Started the terminal shell
   - In the AWS Cloud9 IDE > Selected the `+` icon > New Terminal
   - Displayed the present working directory and located `conditionals.py` file:
     ``` bash
     pwd
     ```
5. Working with the if statement
   - In the `conditionals.py` file use the input() function to get information from the user:
     ``` python
     userReply = input("Do you need to ship a package? (Enter yes or no) ")
     ```
   - Use the if statement to print a response:
     ``` python
     if userReply == "yes":
     print("We can help you ship that package!")
     ```
   - Save the file
   - Run the file
   - At the prompt, enter yes and press ENTER
   - Run the file a second time, enter no and press ENTER
6. Working with the else statement
   - To handle the condition where the user doesn't want to ship a package, use the else statement:
     ``` python
     else:
     print("Please come back when you need to ship a package. Thank you.")
     ```
   - Save the file
   - Run the file
   - At the prompt, enter no and press ENTER
   - Run the file a second time, enter yes and press ENTER
7. Working with the elif statement. The elif statement always comes after an if statement and before the else statement.
    - In the Python script, enter the following code:
    - Save the file
    - Run the file
    - At the prompt, enter no and press ENTER
    - Run the file
    - At the prompt, enter stamps and press ENTER
    - Run the file a second time
    - At the prompt, enter yes and press ENTER
    - At the prompt, enter envelope and press ENTER
    - Run the file a third time
    - At the prompt, enter no and press ENTER
    - At the prompt, enter copy and press ENTER
    - At the prompt, enter 2 and press ENTER.


## Challenges
- ...

## Screenshot
_(Optional – paste image if available)_

## Takeaways

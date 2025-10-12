# Python Lab: String data type

## Objective
Learn how to use strings in python for input and output.
- Write Python code that uses the string data type
- Concatenate strings
- Use the string to get input
- Format strings for output


## Steps Taken
1. Logged into AWS Management Console
2. Services > Cloud9 > reStart-python-cloud9 card > Selected it and opened IDE
3. Created Python Exercise File
   - In the AWS Cloud9 IDE, File > New From Template > Python File.
   - File > Save As > StringDataType.py
4. Started the terminal shell
   - In the AWS Cloud9 IDE > Selected the (+) icon > New Terminal
   - Displayed the present working directory and located StringDataType.py file:
     ``` bash
     pwd
     ```
5. Introducing the string data type
   - From the navigation pane of the IDE selected the StringDataType.py file
   - In the file entered the code:
      ``` python
      myString = "This is a string."
      print(myString)
      ```
   - Save the file
   - Run the file
   - Extended the Python script by using the built-in function type() to get the data type of the variable:
     ``` python
     print(type(myString))
     ```
   - Converted the return value of type into a string, use the str() built-in function:
     ``` python
     print(myString + " is of the data type " + str(type(myString)))
     ```
   - Save the file
   - Run the file
6. Working with string concatenation
   - Returned to the python script to create two strings and then concatenate them by entering the following code:
      ``` python
      firstString = "water"
      secondString = "fall"
      thirdString = firstString + secondString
      print(thirdString)
      ```
   - Save the file
   - Run the file
7. Working with input strings
   - Entered the following code in python script:
     ``` python
     name = input("What is your name? ")
     ```
   - Use the print() function to write the value of the variable to the shell:
     ``` python
     print(name)
     ```
   - Save the file
   - Run the file
8.  Formatting output strings
   - Entered the following code in python script:
     ``` python
     color = input("What is your favorite color?  ")
     animal = input("What is your favorite animal?  ")
     ```
   - Use the print() function this time with multiple variables to format a string to the shell:
     ``` python
     print("{}, you like a {} {}!".format(name,color,animal))
     ```
   - Save the file
   - Run the file which will prompt for a name, a colour and an animal

## Challenges
- ...

## Screenshot
_(Optional – paste image if available)_

## Takeaways

# Python Lab: Numeric data types

## Objective
Explore the basic data types that are used to store numeric values.
- Use the Python shell
- Use the int data type
- Use the float data type
- Use the complex data type
- Use the bool data type

## Steps Taken
1. Logged into AWS Management Console
2. Services > Cloud9 > reStart-python-cloud9 card > Selected it and opened IDE
3. Created Python Exercise File
   - In the AWS Cloud9 IDE, File > New From Template > Python File.
   - File > Save As > NumericDataTypes.py
4. Started the terminal shell
   - In the AWS Cloud9 IDE > Selected the (+) icon > New Terminal
   - Displayed the present working directory and located NumericDataTypes.py file:
     ``` bash
     pwd
     ```
     ``` bash
     ls
     ```
   - In this terminal shell a python shell can be started by running:
     ``` python
     python3
     ```
   - Practices using the python shell by issuing Numeric Commands:
     - Input the following code and confirm output is 4:
     ``` python
     2+2
     ```
     - Input the following code and confirm output is 2:
     ```python
     4-2
     ```
     - Input the following code and confirm output is 4:
     ``` python
     2*2
     ```
     - Input the following code and confirm output is 2.0:
     ``` python
     4/2
     ```
     -  Input the following to exit python shell:
     ``` python
     quit()
     ```
6. Introducing the int data type
   - In the NumericDataTypes.py file, entered the following code:
     ``` python
     print("Python has three numeric types: int, float, and complex")
     ```
   - Saved the file, and run the program at the top of the IDE window:
     File > Save > Run
   - We can also run in the terminal tab by running:
     ``` python
     python 3 NumericDataTypes.py
     ```
   - Created a variable
     - In the python file enter the following code
       ``` python
       myValue=1
       ```
     - write value of variable to the shell by using the print() function:
       ``` python
       print(myValue)
       ```
     - get data type of variable by using the type() built-in function:
       ``` python
       print(type(myValue))
       ```
     - convert integer data type into string
       ``` python
       print(str(myValue) + " is of the data type " + str(type(myValue)))
       ```
     - Save file > Run
7. Introducing the float data type
   - In the python file enter the following code
       ``` python
       myValue=3.14
       ```
   - write value of variable to the shell by using the print() function:
       ``` python
       print(myValue)
       ```
   - get data type of variable by using the type() built-in function:
       ``` python
       print(type(myValue))
       ```
   - convert integer data type into string by using the str() function:
       ``` python
       print(str(myValue) + " is of the data type " + str(type(myValue)))
       ```
   - Save file > Run
8. Introducing the complex data type
   - In the python file enter the following code
       ``` python
       myValue=5j
       ```
   - write value of variable to the shell by using the print() function:
       ``` python
       print(myValue)
       ```
   - get data type of variable by using the type() built-in function:
       ``` python
       print(type(myValue))
       ```
   - convert integer data type into string by using the str() function:
       ``` python
       print(str(myValue) + " is of the data type " + str(type(myValue)))
       ```
   - Save file > Run
10. Introducing the bool data type
    - In the python file enter the following code
       ``` python
       myValue=True
       ```
   - write value of variable to the shell by using the print() function:
       ``` python
       print(myValue)
       ```
   - get data type of variable by using the type() built-in function:
       ``` python
       print(type(myValue))
       ```
   - convert integer data type into string by using the str() function:
       ``` python
       print(str(myValue) + " is of the data type " + str(type(myValue)))
       ```
   - Save file > Run

## Challenges
- ...

## Screenshot


## Takeaways

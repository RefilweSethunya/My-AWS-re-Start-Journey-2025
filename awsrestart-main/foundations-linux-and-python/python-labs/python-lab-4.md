# Python Lab: List, tuple, dictionary

## Objective
In Python, string and numeric data types are often used in groups called collections. In this lab we learn about three such collections that Python supports.
- Use the list data type<br>
- Use the tuple data type<br>
- Use the dictionary data type<br>

## Steps Taken
1. Logged into AWS Management Console
2. Services > Cloud9 > reStart-python-cloud9 card > Selected it and opened IDE
3. Created Python Exercise File
   - In the AWS Cloud9 IDE, File > New From Template > Python File.
   - File > Save As > ListTupleDictionary.py
4. Started the terminal shell
   - In the AWS Cloud9 IDE > Selected the (+) icon > New Terminal
   - Displayed the present working directory and located ListTupleDictionary.py file:
     ``` bash
     pwd
     ```
5. Introducing the list data type
   - Definined the list
     - In the ListTupleDictionary.py file, entered the following code:
       ``` python
       myFruitList = ["apple", "banana", "cherry"]
       print(myFruitList)
       print(type(myFruitList))
       ```
     - Save the file
     - Run the file
   - Accessed the list by position
     - To access the apple string, entered the following code:
     - To access the banana string, entered the following code:
     - To access the cherry string, entered the following code:
     - Save the file
     - Run the file
   - Changed values in the list from 'cherry' to 'orange'
     - Entered the following code to access the third position:
     - Print the updated list:
     - Save the file
     - Run the file
6. Introducing the tuple data type. The tuple is like a list, but it can't be changed. To define a tuple, you use parentheses instead of brackets ([]) like a list.
   - Defined a tuple
     - In the ListTupleDictionary.py file, entered the following code:
       ``` python
       myFinalAnswerTuple = ("apple", "banana", "pineapple")
       print(myFinalAnswerTuple)
       print(type(myFinalAnswerTuple))
       ```
   - Accessed the tuple by position
     - To access the apple string, enter the following code:
       ``` python
       print(myFinalAnswerTuple[0])
       ```
     - To access the banana string, enter the following code:
       ``` python
       print(myFinalAnswerTuple[1])
       ```
     - To access the pineapple string, enter the following code:
       ``` python
       print(myFinalAnswerTuple[2])
       ```
   - Save the file
   - Run the file
7. Introducing the dictionary data type. A dictionary is a list with named positions (keys).
   - Defined a dictionary
     - In the ListTupleDictionary.py file, entered the following code:
       ``` python
       myFavoriteFruitDictionary = {
       "Akua" : "apple",
       "Saanvi" : "banana",
       "Paulo" : "pineapple"
       }
       ```
   - Use the print() function to write the dictionary to the shell:
     ``` python
     print(myFavoriteFruitDictionary)
     ```
   - Use the type() function to write the data type to the shell:
     ``` python
     print(type(myFavoriteFruitDictionary))
     ```
   - Accessed the dictionary by name
     - To access Akua's favorite fruit, enter the following code:
       ``` python
       print(myFavoriteFruitDictionary["Akua"])
       ```
     - To access Saanvi's favorite fruit, enter the following code:
       ``` python
       print(myFavoriteFruitDictionary["Saanvi"])
       ```
     - To access Paulo's favorite fruit, enter the following code:
       ``` python
       print(myFavoriteFruitDictionary["Paulo"])
       ```
   - Save the file
   - Run the file

## Challenges
- ...

## Screenshot
_(Optional – paste image if available)_

## Takeaways

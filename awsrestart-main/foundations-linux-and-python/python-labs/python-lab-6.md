# Python Lab: Composite data types

## Objective
A composite data type is any data type that comprises primitive data types. In this lab, we learn how to create a data type that consists of a string that is in a dictionary, which is in a list.

## Steps Taken
1. Logged into AWS Management Console
2. Services > Cloud9 > reStart-python-cloud9 card > Selected it and opened IDE
3. Created Python Exercise File
   - In the AWS Cloud9 IDE, File > New From Template > Python File.
   - File > Save As > `compositedata.py`
4. Started the terminal shell
   - In the AWS Cloud9 IDE > Selected the `+` icon > New Terminal
   - Displayed the present working directory and located `compositedata.py` file:
     ``` bash
     pwd
     ```
5. Creating a car inventory data
   - From the menu bar, choose File > New File to creates an untitled file.
   - Choose File > Save As..., and save the file as `car_fleet.csv`
   - Copy and paste the following text block into the car_fleet.csv file and save the file
     ```
     vin,make,model,year,range,topSpeed,zeroSixty,mileage
     TMX20122,AnyCompany Motors, Coupe, 2012, 335, 155, 4.1, 50000
     TM320163,AnyCompany Motors, Sedan, 2016, 240, 140, 5.2, 20000
     TMX20121,AnyCompany Motors, SUV, 2012, 295, 155, 4.7, 100000
     TMX20204,AnyCompany Motors, Truck, 2020, 300, 155, 3.5, 0
     ```
6. Creating a car inventory program
   - In the `compositedata.py` file import the modules that we will use:
     ``` python
     import csv
     import copy
     ```
   - define a dictionary that will serve as your composite type for reading the tabular data:
     ``` python
     myVehicle = {
     "vin" : "<empty>",
     "make" : "<empty>" ,
     "model" : "<empty>" ,
     "year" : 0,
     "range" : 0,
     "topSpeed" : 0,
     "zeroSixty" : 0.0,
     "mileage" :
     }
     ```
   - use a for loop to iterate over the initial keys and values of the dictionary
     ``` python
     for key, value in myVehicle.items():
     print("{} : {}".format(key,value))
     ```
   - Define an empty list to hold the car inventory that you will read:
     ``` python
     myInventoryList = []
     ```
8. Copying the CSV file into memory
   - In the `compositedata.py` file enter the following code:
     ``` python
     with open('car_fleet.csv') as csvFile:
     csvReader = csv.reader(csvFile, delimiter=',')
     lineCount = 0
      for row in csvReader:
        if lineCount == 0:
            print(f'Column names are: {", ".join(row)}')  
            lineCount += 1  
        else:  
            print(f'vin: {row[0]} make: {row[1]}, model: {row[2]}, year: {row[3]}, range: {row[4]}, topSpeed: {row[5]}, zeroSixty: {row[6]}, mileage: {row[7]}')  
            currentVehicle = copy.deepcopy(myVehicle)  
            currentVehicle["vin"] = row[0]  
            currentVehicle["make"] = row[1]  
            currentVehicle["model"] = row[2]  
            currentVehicle["year"] = row[3]  
            currentVehicle["range"] = row[4]  
            currentVehicle["topSpeed"] = row[5]  
            currentVehicle["zeroSixty"] = row[6]  
            currentVehicle["mileage"] = row[7]  
            myInventoryList.append(currentVehicle)  
            lineCount += 1
     print(f'Processed {lineCount} lines.')
     ```
By default, Python does a shallow copy of complex data types. A shallow copy refers, or points, to the storage location of the myVehicle dictionary variable. Without the line below, you would have only one storage box, and only the last item in the list would be copied into memory. This line makes sure that new storage boxes are created in memory to store the new tabular data that is being read.
``` python
currentVehicle = copy.deepcopy(myVehicle)
```        
9. Printing the car inventory
    - In the `compositedata.py` file enter the following code to print the car inventory from the myInventoryList variable:
      ``` python
      for myCarProperties in myInventoryList:
      for key, value in myCarProperties.items():
        print("{} : {}".format(key,value))
        print("-----")
      ```
    - Save the file
    - Run the script

## Challenges
- ...

## Screenshot
_(Optional – paste image if available)_

## Takeaways

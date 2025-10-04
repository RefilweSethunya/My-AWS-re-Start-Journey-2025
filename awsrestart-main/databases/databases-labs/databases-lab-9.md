# Databases Lab: Introduction to Dynamo DB

## Objective
In this lab, I create a table in DynamoDB to store information about a music library, query the music library and then delete the DynamoDB table.<br>
Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale. It is a fully managed database and supports both document and key-value data models.

## Steps Taken
1. Logged into the AWS Management Console
2. Created a new table
   - Databases > DynamoDB > Create table > Configured the following:
     - Table name: Music
     - Partition key: Artist (String)
     - Sort key: Song (String)
   - Create Table
3. Added data
   - Music table > Actions > Create item > Artist: Pink Floyd, Song: Money
   - Add new attribute (String) > Configure:
     - FIELD: Album
     - VALUE: The Dark Side of the Moon
   - Add new attribute (Number) > Configure:
     - FIELD: Year
     - VALUE: 1973
   - Create Item
   - Created Second Item
     <img width="775" height="238" alt="image" src="https://github.com/user-attachments/assets/5862f974-3589-4722-8033-80ec739acc2d" />
   - Created Third Item
     <img width="775" height="238" alt="image" src="https://github.com/user-attachments/assets/d18fd39d-f595-4f57-95c5-0612a011f77c" />
4. Modified an existing item
   - In the DynamoDB dashboard > Tables > Explore Items > Music > Psy
   - Changed the Year from 2011 to 2012
   - Save
6. Queried the table
7. Deleted the table
   - In the DynamoDB dashboard > Tables > Update settings > Music table > Actions > Delete table.
   - On the confirmation panel, typed delete > Delete table

## Screenshot
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/8e167aaa-0e30-4599-8b2f-ee2559cb5516" />
<img width="1366" height="389" alt="image" src="https://github.com/user-attachments/assets/5ee4e0e1-8db7-449c-8165-f9d45d4255da" />
<img width="1366" height="556" alt="image" src="https://github.com/user-attachments/assets/c930de24-4a0a-4042-8a4b-cdd07c40fcf4" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/d4552bb7-def8-483f-bc83-f6ca9203506d" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/c0de59ce-875e-4c33-a8ce-b0cd7f909b88" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/c49fb2b0-9ee1-4eb5-a17c-c8f4acc748bb" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/af6f4db3-4def-46c6-ba21-0157c7f47e4a" />
<img width="1366" height="502" alt="image" src="https://github.com/user-attachments/assets/4d80aa09-814d-4a43-a517-ec48872b9b63" />
<img width="1366" height="533" alt="image" src="https://github.com/user-attachments/assets/7401c8ed-fd4f-4e0f-b92e-6021f463dd83" />


## Challenges
- 


## Takeaways

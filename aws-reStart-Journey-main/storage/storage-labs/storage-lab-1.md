# Storage Lab: Creating S3 bucket 

## Objective
Learn how to create a new bucket, upload an object and make it public.

## Steps Taken
1. Logged into AWS Console
2. Created s3 bucket
3. ...
4. ...

## Challenges
- First time creating a JSON Policy
- Solved by using online aws policy generator and pasting on the bucket policy
- Link : https://awspolicygen.s3.amazonaws.com/policygen.html

## Screenshot
_I created a new S3 bucket (refilwesethunya) then I uploaded an object into the bucket (VenusBarbie.jpeg).  <img width="1357" height="723" alt="image" src="https://github.com/user-attachments/assets/933548ee-3530-4df3-8607-a7103365714b" />
_I tested access to the object via a web browser which failed at first. <img width="1352" height="718" alt="image" src="https://github.com/user-attachments/assets/2bcf89b4-2c46-4b76-a44b-3db617835d7b" />
_I made the object publicly accessible (without making the bucket public) using aws policy generator and pasting on the bucket policy under Permissions tab. <img width="1353" height="719" alt="image" src="https://github.com/user-attachments/assets/fe3a05f0-58da-490f-b5d9-50cd53be5eff" />
_<img width="1348" height="717" alt="image" src="https://github.com/user-attachments/assets/3a609164-167f-40ff-bee9-a1b88c112513" />
_After modifying, I could successfully access the public object via a web browser. <img width="1353" height="718" alt="image" src="https://github.com/user-attachments/assets/3da68774-1ee8-4fe6-aea8-351db0822f1b" />
_Listed the contents of the S3 bucket using the AWS CLI <img width="1342" height="693" alt="image" src="https://github.com/user-attachments/assets/b2653ca5-2c4b-4c9e-aef3-3e33abc407fb" />
_<img width="1356" height="719" alt="image" src="https://github.com/user-attachments/assets/71cfe701-ecca-439c-a1a4-eab26ade4f02" />


## Takeaways
I can easily store and share files using Amazon S3, but it is important to carefully manage permissions to balance accessibility with security. By default, files are private and making them public requires explicit permission changes.


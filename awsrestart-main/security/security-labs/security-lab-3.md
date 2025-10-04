# Security Lab: Data Protection

## Objective
Understand and apply cryptographic principles using AWS services. Tasks include creating an AWS KMS encryption key and installing the AWS Encryption CLI on an EC2 instance.
With these tools, I will encrypt plaintext files to protect their contents and then decrypt the ciphertext files back into readable form.

## Steps Taken
1. Created an AWS KMS key and gave ownership of that key to the IAM role(voclabs)
   - Key Management Service > Create a key > Key type: Symmetric > Next
   - Add label
     - Alias: MyKMSKey
     - Description: Key used to encrypt and decrypt data files
     - Next
   - Key administrators > Define key administrative permissions > select voclabs > Next
   - This account > Define key usage permissions page > select voclabs > Next > Finish
   - MyKMSKey and copied the ARN (Amazon Resource Name)(arn:aws:iam::847046729124:role/voclabs)
2. Configured the File Server instance
   - EC2 > Instances > File Server > Session Manager > Connect
   - ``` bash
     cd ~
     aws configure
     ```
   - To view the updated contents of the file
     ``` bash
     cat ~/.aws/credentials
     ```
   - To install the AWS Encryption CLI and set my path
     ``` bash
     pip3 install aws-encryption-sdk-cli
     export PATH=$PATH:/home/ssm-user/.local/bin
     ```
3. Encrypted and decrypted data
   - To create the text file
     ``` bash
     touch secret1.txt secret2.txt secret3.txt
     echo 'TOP SECRET 1!!!' > secret1.txt
     ```
   - To view the contents of the secret1.txt file
     ``` bash
     cat secret1.txt
     ```
   - To create a directory to output the encrypted file
     ``` bash
     mkdir output
     ```
   - Saved the ARN of an AWS KMS key in the $keyArn variable. Replacing (KMS ARN) with the AWS KMS ARN copied before
     ``` bash
     keyArn=(KMS ARN)
     ```
   - To encrypt the secret1.txt file
     ``` bash
     aws-encryption-cli --encrypt \
                     --input secret1.txt \
                     --wrapping-keys key=$keyArn \
                     --metadata-output ~/metadata \
                     --encryption-context purpose=test \
                     --commitment-policy require-encrypt-require-decrypt \
                     --output ~/output/.
     ```
   - To determine whether the command succeeded.  If the command failed, the value is nonzero, if succeeded, the value is 0
     ``` bash
     echo $?
     ```
   - To view the newly encrypted file location
     ``` bash
     ls output
     ```
   - To decrypt the file
     ``` bash
     aws-encryption-cli --decrypt \
                     --input secret1.txt.encrypted \
                     --wrapping-keys key=$keyArn \
                     --commitment-policy require-encrypt-require-decrypt \
                     --encryption-context purpose=test \
                     --metadata-output ~/metadata \
                     --max-encrypted-data-keys 1 \
                     --buffer \
                     --output .
     ```
   - To view the new file location
     ``` bash
     ls output
     ```
   - To view the contents of the decrypted file
     ``` bash
     cat secret1.txt.encrypted.decrypted
     ```
     
## Challenges
- ...


## Screenshot
KMS Creation
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/9a6c4ab0-138f-4d3b-9e54-8665f9158bd8" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/7bfbd664-9cf0-44a4-a70b-0639fea0b230" />

Key Administrator Configuration
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/42ad21b3-f041-48f9-a07a-442afd8a0aaf" />
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/274f2cdc-1bd6-4f74-83a8-b622918c6484" />

Key
<img width="1366" height="425" alt="image" src="https://github.com/user-attachments/assets/e6b1384d-bd54-46fa-89f9-029878d132d0" />

File Server CLI Configuration
<img width="1366" height="403" alt="image" src="https://github.com/user-attachments/assets/9979386f-2269-435f-8ffc-c69327aee79f" />

Text File Creation
<img width="1366" height="677" alt="image" src="https://github.com/user-attachments/assets/f663f901-3e44-416b-9337-da2488635aab" />

AWS Encryption CLI Installation and Path Setting
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/fe016d0d-3a9b-4d2f-a6af-2cb616af941a" />
<img width="1366" height="676" alt="image" src="https://github.com/user-attachments/assets/4e748ad6-27c2-44cf-ab30-66ea15c145b3" />

Encryption
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/0d23f9aa-51f0-4a52-b366-d3e0019ba43b" />
<img width="1366" height="313" alt="image" src="https://github.com/user-attachments/assets/6bbf983f-17ec-4845-b8ea-9cc588198974" />

Decryption
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/afcbf203-ee0f-423f-9b22-7b9c2344a5b1" />
<img width="1366" height="282" alt="image" src="https://github.com/user-attachments/assets/b0189890-438d-4a83-8012-71c422a211a3" />



## Takeaways
This lab highlighted the role of cryptography in protecting data CIA triad. By creating and using an AWS KMS encryption key with the AWS Encryption CLI, we can securely transform plaintext into ciphertext and later decrypt back into readable form demonstrating how encryption and decryption secure data confidentiality and integrity in the cloud.

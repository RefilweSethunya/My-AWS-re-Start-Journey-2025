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
   - MyKMSKey and copied the ARN (Amazon Resource Name)
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
   - 


## Challenges
- ...

## Screenshot
_(Optional – paste image if available)_

## Takeaways
This lab highlighted the role of cryptography in protecting data CIA triad. By creating and using an AWS KMS encryption key with the AWS Encryption CLI, we securely transformed plaintext into ciphertext and later decrypted back into readable form demonstrating how encryption and decryption secure data confidentiality and integrity in the cloud.

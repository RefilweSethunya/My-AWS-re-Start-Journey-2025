# Security Lab: Introduction to Identity and Access Management (IAM)

## Objective
Experience how IAM manages authentication and authorization to secure resources in AWS through creating and applying an IAM password policy, exploring pre-created IAM users and groups and inspecting the policies attached to the groups. Also adding users to groups with specific capabilities enabled, locating and using the IAM sign-in URL and experimenting with the effects of policies on service access.

## Steps Taken
1. Created an account password policy
   - IAM > Account settings > Change password policy > Select your account password policy requirements
   - Configured as follows:
     - Enforce minimum password length: 10 characters
     - Select every check box except the check box for Password expiration requires administrator reset.
     - Enable password expiration: 90 days
     - Prevent password reuse
   - Save

2. Explored users and user groups
   -  Users > user-1 > Permissions
   -  Users > user-1 > Groups
   -  Users > user-1 > Security credentials
  
   -  Users > user-2 > Permissions
   -  Users > user-2 > Groups
   -  Users > user-2 > Security credentials
  
   -  Users > user-3 > Permissions
   -  Users > user-3 > Groups
   -  Users > user-3 > Security credentials
  
   -  User groups > EC2-Support > Permissions
   -  User groups > EC2-Admin > Permissions 
   -  User groups > S3-Support > Permissions
     
3. Added users to user groups
   - Adding user-1 to the S3-Support group
     - User groups > S3-Support group > Users tab > Add users
     - Configure:
       Select the check box for user-1 > Add Users > Verify that user-1 has been added to the group.
   - Adding user-2 to the EC2-Support
     - User groups > EC2-Support group > Users tab > Add users
     - Configure:
       Select the check box for user-2 > Add Users > Verify that user-2 has been added to the group.
   - Adding user-3 to the EC2-Admin group
     - User groups > EC2-Admin group > Users tab > Add users
     - Configure:
       Select the check box for user-3 > Add Users > Verify that user-3 has been added to the group.

   
5. Verified User permisions
   - User-1 could view S3 buckets but not EC2 instances.
   - User-2 could view EC2 instances but could not stop them or access S3 buckets.
   - User-3 could both view EC2 instances and perform the stop instance action.

## Challenges
- ..

## Screenshot
Account password policy Configuration
<img width="1366" height="632" alt="image" src="https://github.com/user-attachments/assets/8323b6d7-7190-4a05-baae-d273c2b2fa92" />

Users
<img width="1366" height="410" alt="image" src="https://github.com/user-attachments/assets/276b6e1b-446b-406d-b0bc-dd7f03879bfa" />

User Groups
<img width="1366" height="413" alt="image" src="https://github.com/user-attachments/assets/bc18541a-3bdd-4390-9019-ba32bb83ff06" />
 User Groups after adding users
 <img width="1366" height="436" alt="image" src="https://github.com/user-attachments/assets/cb386a6c-ea5e-4868-904c-1a6fd335aa3a" />


## Takeaways
By working with users, groups, and policies, we explored how access can be granted or restricted to resources. I have also learned the importance of strong password policies, organized group management and the practical effects of policies on service access in securing an AWS environment

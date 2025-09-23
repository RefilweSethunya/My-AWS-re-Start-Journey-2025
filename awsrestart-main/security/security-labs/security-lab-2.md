# Security Lab: Systems-Hardening

## Objective
Strengthen system security through patch management. Specifically, the tasks include: patching Linux instances using the default patch baseline; creating a custom patch baseline tailored to specific requirements.; using patch groups to apply the custom patch baseline to Windows instances; and verifying patch compliance to ensure systems meet security and update standards.

## Steps Taken
1. Patch Linux EC2 instances using default baselines
   - Systems Manager > Node Management > Fleet Manager (to view fleet details)
   - Systems Manager > Node Management > Patch Manager > Start with an overview > Patch now
   - Configured as follows:
     - Patching operation: Scan and install
     - Reboot option: Reboot if needed
     - Instances to patch: Patch only the target instances I specify
     - Target selection: Specify instance tags
     - Tag key:  Patch Group
     - Tag value: LinuxProd
   - Add > Patch now
   - Observe the status of the patching in the Status field of AWS-PatchNowAssociation panel 
2. Created a custom patch baseline for Windows instances
   - In the Systems Manager console, I searched Systems Manager
   - Node Management > Patch Manager > Start with an overview >  Patch baselines tab > Create patch baseline
   - Configured Patch Baseline Details as follows:
     - Name: WindowsServerSecurityUpdates
     - Description: Windows security baseline patch
     - Operating system: Windows
     - Default patch baseline: None
    - Configured approval rules for operating systems as follows:
      - Products: WindowsServer2019
      - Severity: Critical
      - Classification: SecurityUpdates
      - Auto-approval: 3 days
      - Compliance reporting: Critical
    - Added a second rule to this patch baseline and configure as follows:
      - Products: WindowsServer2019
      - Severity: Important
      - Classification: SecurityUpdates
      - Auto-approval: 3 days
      - Compliance reporting: High
   - Create Patch Baseline > Patch baselines section > WindowsServerSecurityUpdates > Actions > Modify patch groups > Patch groups > WindowsProd > Add > Close
     
3. Patched the Windows instances. Using the 'Patch now' feature based on the tag associated with them.
   - Tagged Windows instances
     - EC2 > Instances, selected the check box next to the Windows-1 instance, and then chose the Tags tab > Manage tags > Add new tag and configured as follows:
       Key: Enter Patch Group
       Value: Enter WindowsProd
     - Repeated the same to tag the second and third Windows instances
    - Patched Windows instances
      - In the Systems Manager console, I searched Systems Manager
      - Patch Manager > Start with an overview > Patch now
      - Configured as follows:
        Patching operation:  Scan and install
        Reboot option: Reboot if needed
        Instances to patch: Patch only the target instances I specify
        Target selection: Specify instance tags
        Tag key:  Patch Group
        Tag value: WindowsProd
      - Add > Patch now
4. Verified compliance
   - Node Management > Patch Manager
   - Dashboard tab > Compliance summary. Should display 'Compliant: 6' (verifies that all Windows and Linux instances are compliant)
   - Compliance Reporting tab (provides an overview of all running instances with SSM)

## Challenges
- ..

## Screenshot
Fleet Manager
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/22c7da58-0304-469e-812d-fc7826ae8946" />

Linux Patch Configuration
<img width="1366" height="668" alt="image" src="https://github.com/user-attachments/assets/34f4d080-f0aa-4e79-9723-f851f85ce384" />

AWS-PatchNowAssociation panel
<img width="1366" height="668" alt="image" src="https://github.com/user-attachments/assets/d6d1cd23-d1d5-4ab5-b619-8fc5e10fb7a8" />

Windows Patch Baseline Configuration
<img width="1366" height="666" alt="image" src="https://github.com/user-attachments/assets/c88b4f99-21a2-4f02-955e-9a3ae67d441c" />

Windows Approval Rules Configuration
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/f60627b7-4d2f-401a-8c3d-7fcc00cb16f1" />

Second Rule Config
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/3bc0295d-e8c9-41f6-8a66-379caf0038cd" />

Added Success
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/e3c05134-4fd9-4411-8545-f39641a71308" />

New Tag Configuration
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/6103ce83-0737-4aa3-84ff-4e217e4d139e" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/b91f9b13-6c4d-4f9e-ab0a-81f7dd6dca7d" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/5075fc86-c939-48e2-9ca7-a15394d2e976" />

Patch Now Configuration
<img width="1366" height="677" alt="image" src="https://github.com/user-attachments/assets/68beb5d0-2c3d-4ffd-aed0-89ae97118349" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/e52e9aae-0d11-4aee-bac0-afbae26bac13" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/a29d1a7d-7ac5-4f70-802d-9946df0e0ca7" />

Compliance Summary
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/66b3b43b-dfff-43c4-b5ef-11dbf43ad139" />

Linux and Windows instances Compliant Status Verification
<img width="1227" height="610" alt="image" src="https://github.com/user-attachments/assets/c2ec463c-583b-41ca-ada8-46df54ae8362" />

## Takeaways
Keeping operating systems (OS) and application software up to date can be logistically challenging, but most OS updates can be automatically applied over the network. In AWS, Patch Manager (a capability of AWS Systems Manager) simplifies this process by allowing one to create patch baselines, scan resources for compliance, and apply patches to instances such as EC2 Linux or Windows servers. This ensures systems remain secure, compliant, and consistently hardened against vulnerabilities.

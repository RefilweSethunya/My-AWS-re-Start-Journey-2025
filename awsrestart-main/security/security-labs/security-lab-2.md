# Security Lab: Systems-Hardening

## Objective
Strengthen system security through patch management. Specifically, the tasks include: patching Linux instances using the default patch baseline; creating a custom patch baseline tailored to specific requirements.; using patch groups to apply the custom patch baseline to Windows instances; and verifying patch compliance to ensure systems meet security and update standards.

## Steps Taken
1. Patch Linux EC2 instances using default baselines
2. Created a custom patch baseline for Windows instances
   - In the Systems Manager console, I searched Systems Manager
   - Node Management > Patch Manager > Start with an overview >  Patch baselines tab > Create patch baseline
   - Configured Patch Baseline Details as follows
     Name: WindowsServerSecurityUpdates
     Description: Windows security baseline patch
     Operating system: Windows
     Default patch baseline: None
    - Configured approval rules for operating systems as follows
      Products: WindowsServer2019
      Severity: Critical
      Classification: SecurityUpdates
      Auto-approval: 3 days
      Compliance reporting: Critical
    - Added a second rule to this patch baseline and configure as follows
      Products: WindowsServer2019
      Severity: Important
      Classification: SecurityUpdates
      Auto-approval: 3 days
      Compliance reporting: High
     
4. Patched the Windows instances. Using the 'Patch now' feature based on the tag associated with them.
   - Tagged Windows instances
     - EC2 > Instances, selected the check box next to the Windows-1 instance, and then chose the Tags tab > Manage tags > Add new tag and configured as follows
       Key: Enter Patch Group
       Value: Enter WindowsProd
     - Repeated the same to tag the second and third Windows instances
    - Patched Windows instances
      - In the Systems Manager console, I searched Systems Manager
      - Patch Manager > Start with an overview > Patch now
      - Configured as follows
        Patching operation:  Scan and install
        Reboot option: Reboot if needed
        Instances to patch: Patch only the target instances I specify
        Target selection: Specify instance tags
        Tag key:  Patch Group
        Tag value: WindowsProd
      - Add > Patch now
5. Verified compliance
   - Node Management > Patch Manager
   - Dashboard tab > Compliance summary. Should display 'Compliant: 6' (verifies that all Windows and Linux instances are compliant)
   - Compliance Reporting tab (provides an overview of all running instances with SSM)

## Challenges
- ..

## Screenshot

New Tag Configuration
Patch Now Configuration
Compliance Summary
Linux and Windows instances Compliant Status Verification

## Takeaways
Keeping operating systems (OS) and application software up to date can be logistically challenging, but most OS updates can be automatically applied over the network. In AWS, Patch Manager (a capability of AWS Systems Manager) simplifies this process by allowing one to create patch baselines, scan resources for compliance, and apply patches to instances such as EC2 Linux or Windows servers. This ensures systems remain secure, compliant, and consistently hardened against vulnerabilities.

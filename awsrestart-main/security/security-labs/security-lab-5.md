# Security Lab: Firewall Malware

## Objective
Strengthen the organization’s security perimeter using AWS Network Firewall. Tasks include updating a network firewall and creating a firewall rules group to block access to known malicious sites. Finally, verifying and testing that the rules are working by confirming that access to the sites is successfully denied.

## Steps Taken
1. Logged into the AWS Management Console
2. Inspected the Network Firewall
   - VPC > NETWORK FIREWALL > Firewalls > LabFirewall, and read through.
3. Updated firewall policy to forward all packets for stateful rule inspection.
   - Step 2: Configure the firewall policy > LabFirewallPolicy
   - Stateless default actions section > Edit
   - Configured as follows:
     - Choose how to treat fragmented packets: Use the same actions for all packets.
     - Action: Choose Forward to stateful rule groups.
   - Save
4. Created a firewall rule group that uses Suricata rules which once attached to the network firewall, blocks the malicious websites that users access
   - NETWORK FIREWALL > Network Firewall Rule Groups > Create Network Firewall rule group
   - In the Create rule group section, configured as follows:
     - Rule group type: Stateful rule group
     - Rule group format: Suricata compatible rule string
     - Rule evaluation order: Action order
     - Next
     - In the Rule group details section, configured as follows:
       - Name: StatefulRuleGroup
       - Capacity: 100
     - Next
     - In the Suricata compatible IPS rules section, entered the following code into the text box:
       ``` bash
       drop http $HOME_NET any -> $EXTERNAL_NET 80 (msg:"MALWARE custom solution"; flow: to_server,established; classtype:trojan-activity; sid:2002001; content:"/data/js_crypto_miner.html";http_uri; rev:1;)
       drop http $HOME_NET any -> $EXTERNAL_NET 80 (msg:"MALWARE custom solution"; flow: to_server,established; classtype:trojan-activity; sid:2002002; content:"/data/java_jre17_exec.html";http_uri; rev:1;)
       ```
       The two Suricata rules will now block traffic that matches the URL.
     - Next
     - Review and create
     - Create stateful rule group
5. Attach the firewall rule group to the network firewall
   - NETWORK FIREWALL > Firewalls > LabFirewall > LabFirewallPolicy
   - Under Stateful rule groups > Add unmanaged stateful rule groups
   - Select the check box for StatefulRuleGroup > Add stateful rule group.
   - Navigate to Stateful rule groups section to see the successfully added firewall rule group
  

## Challenges
- ..

## Screenshot
Network Firewall
<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/00f1734f-7a2b-416a-9a37-1e93df502631" />

Updated firewall policy Configuration
<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/11a3a7b8-f303-4083-a3cd-25232d51737b" />

Suricata Firewall Rule Group Configuration
<img width="1366" height="637" alt="image" src="https://github.com/user-attachments/assets/20040d3d-154b-4573-96fd-a6eb6af67386" />
<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/4a927e76-08f1-4001-ae26-984484b9d861" />
<img width="1366" height="636" alt="image" src="https://github.com/user-attachments/assets/0db1be30-42be-44e0-9822-dc8a8e5b9875" />
<img width="1366" height="635" alt="image" src="https://github.com/user-attachments/assets/30bea04d-2138-4d00-a328-1e613bbf1c14" />

Attach Firewall Stateful Rule Group to Firewall
<img width="1366" height="637" alt="image" src="https://github.com/user-attachments/assets/0797b27a-1dcf-4121-8504-2066a009ad34" />
<img width="1366" height="636" alt="image" src="https://github.com/user-attachments/assets/1d4ebbb7-b83a-48f1-9ea9-77848a13f849" />


## Takeaways
AWS Network Firewall can be used to protect against malware threats. By updating the firewall and creating rules to block access to malicious sites, we reinforced how firewalls serve as a critical defense in securing networks and preventing unauthorized or harmful traffic. 
I also learned about Suricata. It is an open-source network IPS that includes a standard rule-based language for traffic inspection.

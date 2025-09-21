# Networking Lab: Internet Protocol Troubleshooting Commands

## Objective
Practice troubleshooting commands and identify how to use these commands in customer scenarios
<img width="895" height="675" alt="image" src="https://github.com/user-attachments/assets/5351894b-4c7b-4e76-b6ce-4e796d6318ac" />


## Steps Taken
1. Logged into AWS Management Console
2. SSH into Instance
3. Run ping, tracetroute, netsat, telnet, curl...

## Challenges
- ...

## Screenshot
SSH

<img width="830" height="311" alt="image" src="https://github.com/user-attachments/assets/3a834550-8a97-485a-b852-0b61ca459753" />


Run ping command to troubleshoot connectivity issues and reachability to a specific target. It sends ICMP echo requests from your machine to the server that you are trying to reach (for example, amazon.com). The server sends an echo reply with a round-trip time.

<img width="962" height="185" alt="image" src="https://github.com/user-attachments/assets/73237311-e062-440e-accf-c70582701764" />


Run traceroute to investigate on the path and latency that the packet takes to get from your machine to the destination (8.8.8.8). Each server is called a hop. Three asterisks (***) indicate a failed hop.

<img width="1226" height="103" alt="image" src="https://github.com/user-attachments/assets/b77b21f2-fb6b-4910-83d4-dc9b14b808bb" />


Run netstat command to shows the current established TCP connections from which the host is listening. 

netstat -tp: Confirms established connections
netstat -ntlp: Outputs listening services but does not resolve port numbers

<img width="781" height="199" alt="image" src="https://github.com/user-attachments/assets/314d13fb-103b-4efe-8acd-539ae0e51c63" />


## Takeaways
This is not an exhaustive list of commands or options for troubleshooting,it's only some of the MOST COMMON troubleshooting commands used to troubleshoot common networking issues.

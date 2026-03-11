# Project.HTTP-Enumeration-and-Directory-Traversal
My documentation of doing a project in a guided virtual lab provided by labex.io

To start off I utilize the ping command, sending ICMP Echo Request packets to the target system accessible via the hostname target
'ping -c 4 target'
I see an output confirming that four packets were sent and four were received, meaning a stable connection.

I then use nmap to scan the target for open ports and which services are running on them. Running a targeted scan on port 80, which is also the standard port for HTTP traffic, that looks like such 'nmap -sV -p 80 --script http-enum target'
The flag '-sV' enables version detection which attempts to determine the version of the service running on the port. The flag '-p 80' specifies that we only want to scan port 80. '--script http-enum' runs a script that enumerates directories and files on the web server. And finally 'target' is the hostname of our target machine.
The output looks like such:
<img width="876" height="200" alt="image" src="https://github.com/user-attachments/assets/1d7dda17-acf7-4518-b6eb-7cbf1aed602d" />

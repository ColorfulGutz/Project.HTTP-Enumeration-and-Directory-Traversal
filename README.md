# Project.HTTP-Enumeration-and-Directory-Traversal
- My documentation of doing a project in a guided virtual lab provided by labex.io

To start off I utilize the ping command, sending ICMP Echo Request packets to the target system accessible via the hostname target
'ping -c 4 target'
I see an output confirming that four packets were sent and four were received, meaning a stable connection.

I then use nmap to scan the target for open ports and which services are running on them. Running a targeted scan on port 80, which is also the standard port for HTTP traffic, that looks like such 'nmap -sV -p 80 --script http-enum target'
The flag '-sV' enables version detection which attempts to determine the version of the service running on the port. The flag '-p 80' specifies that we only want to scan port 80. '--script http-enum' runs a script that enumerates directories and files on the web server. And finally 'target' is the hostname of our target machine.
The output looks like such:

<img width="876" height="200" alt="image" src="https://github.com/user-attachments/assets/1d7dda17-acf7-4518-b6eb-7cbf1aed602d" />

This result shows that port 80 is open and running an Apache httpd 2.4.41, which is a webserver that may be hosting files that I can access.

Next I use curl to access the files which is a command line tool used for transfering data with URLs. I make a standard request to the web server's main page to see what it looks like via 'curl http://target'. This returns the default Apache page content,

<img width="417" height="39" alt="image" src="https://github.com/user-attachments/assets/ef0e95be-7e4c-495f-826b-902325817a79" />

. Afterwards, I curl a file that was placed inside of the web servers root directory by running 'curl http://target/flag.txt' which returns the flag 'labex{p4th_tr4v3rs4l_w1zardry}'. Now knowing this file exists in the hosted web server, we can output the command into a file on our machine like so, 'curl http://target/flag.txt > flag.txt'. Once that is done I can read the file by using another command line tool called cat, 'cat flag.txt'

<img width="724" height="142" alt="image" src="https://github.com/user-attachments/assets/339cafaa-266b-458c-b2ff-25305286eb4a" />

> This is meant as an easy excercise showcasing a web reconnaissance excercise, demonstrating basic web reconnaissance techniques that are fundamental to understanding how web servers work and how to interact with them programmatically.

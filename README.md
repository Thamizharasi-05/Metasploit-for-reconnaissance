# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:

<img width="647" height="387" alt="Screenshot 2026-02-06 130719" src="https://github.com/user-attachments/assets/23a28225-519a-4704-b0c9-0502377c8826" />

Invoke msfconsole:
## OUTPUT:

<img width="666" height="604" alt="Screenshot 2026-02-06 141039" src="https://github.com/user-attachments/assets/7e96ce52-76a2-4a63-865d-2654285ecffb" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:

<img width="740" height="651" alt="image" src="https://github.com/user-attachments/assets/44da2b2d-56dc-4bb0-9fe0-ff2b9cd8af94" />

Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:

<img width="588" height="326" alt="Screenshot 2026-02-06 134357" src="https://github.com/user-attachments/assets/2436ed52-1db3-40cd-8771-f10584cf3ac1" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="892" height="147" alt="Screenshot 2026-02-06 141203" src="https://github.com/user-attachments/assets/b75cb03c-5553-4147-8d07-66532eda24e4" />

<img width="577" height="432" alt="Screenshot 2026-02-06 135340" src="https://github.com/user-attachments/assets/b5feabe8-147c-46f1-b9c9-c388ed943ce4" />

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="1709" height="738" alt="Screenshot 2026-02-06 135919" src="https://github.com/user-attachments/assets/4f71478f-90ef-4efb-b405-98d1744207d6" />

The info command provides information regarding a module or platform,

## OUTPUT:

<img width="852" height="313" alt="image" src="https://github.com/user-attachments/assets/a3b62c01-be70-459e-b69b-2af83ca8f797" />

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:





## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="892" height="147" alt="Screenshot 2026-02-06 141203" src="https://github.com/user-attachments/assets/964b8420-b2ea-454a-9610-a6002282bbaf" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:




Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:




set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully

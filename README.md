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
<img width="772" height="556" alt="image" src="https://github.com/user-attachments/assets/f8571421-b87b-4fb4-a30a-cfb89167f522" />

Invoke msfconsole:
## OUTPUT:
<img width="818" height="671" alt="image" src="https://github.com/user-attachments/assets/43012e2a-d9e3-4529-8617-367d6fd47110" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="771" height="310" alt="image" src="https://github.com/user-attachments/assets/c122d8d4-b84f-463a-a737-ecc07b4cb4d5" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="788" height="277" alt="image" src="https://github.com/user-attachments/assets/7dbd9c78-beea-4bbc-ab09-c87ce3dcab9b" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="802" height="603" alt="image" src="https://github.com/user-attachments/assets/520dfca1-6bdb-45f5-a2a5-900aba39b8bf" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="906" height="676" alt="image" src="https://github.com/user-attachments/assets/dc809521-cc0c-4a86-86f1-506397db877e" />



The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:
<img width="835" height="745" alt="image" src="https://github.com/user-attachments/assets/08ea4296-1c8c-4e9a-adec-a8ec560433a4" />




## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="830" height="553" alt="image" src="https://github.com/user-attachments/assets/f5cea9d9-202a-409f-8d38-77055e721715" />
<img width="920" height="253" alt="image" src="https://github.com/user-attachments/assets/796a2916-3a82-4aea-9a75-e85e6de0e89f" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="937" height="752" alt="image" src="https://github.com/user-attachments/assets/8e4bf05b-1e12-4bc9-881d-aea2a76c43b8" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="930" height="362" alt="image" src="https://github.com/user-attachments/assets/7e0103af-b736-4d1d-a235-0d5a4741543f" />




Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
<img width="931" height="210" alt="image" src="https://github.com/user-attachments/assets/504ff175-6d49-4e66-935a-293c485cc995" />



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
<img width="1056" height="742" alt="image" src="https://github.com/user-attachments/assets/6f278e7f-6a90-4c4b-9355-6a371347cc1d" />




set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="997" height="715" alt="image" src="https://github.com/user-attachments/assets/e9407f8a-2c15-4cdb-b7cd-46a4269c6166" />






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully

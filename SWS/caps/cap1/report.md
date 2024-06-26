![cap1](assets/cap.png)

# Execute Summary
This machine is hosted for our Software Security module for assignment 1. The machine has many ports open and we have to exploit it using the vulnerabilities present in the services running on the machine. The machine has a web server running on port 80 which has a login page in a specific directory. The machine has an FTP server running on port 21 which has user login enabled. The machine has an SSH server running on port 22 which has authenticated based login. The machine has a MySQL server running on port 3306 which was able to login using the specific command and I could see all the data in the database. There were many ports open for the exploits. First of all I tried to reverse shell using the web server but unfortunately I could get the reverse shell though I could upload the php file on the web directory.

## Github Repo Link

[link to github repo](https://github.com/Khemraj9815/SWS101/tree/main/SWS)

# Approach

## Assessment Overview and Recommendations

During the penetration test on the machine of the ip address 10.3.21.140, I could not find exploits other than port 3306(mysql) though all the ports were vulnerable because of outdated versions of the application. But I have tried a lot of stuff to find the vulnerabilities.

I found out that I was able to upload a reverse shell file in one of the directories and I could even run the file which can lead to exploitation. This behavior of uploading files should not be allowed. It is not just on the http directories but also on the ftp port I could add files to, unfortunately ftp port(21) was not accessible on http. This behavior saves the machine from exploitation. If ftp port(21) was accessible from the http server there could be high chances of exploits. The behavior of the ports mentioned above is dangerous because the attacker can upload anything they could to gain unauthorized access.

Another thing is, the database of the system was visible or accessible and could inspect all the data that was inside the database which is on port 3306(mysql). It was possible with just one line of command and I was in. I could run all the that was needed to run. I think this behavior of mysql port is unusual because this could lead to loss of sensitive information.

This is about the twiki, I don't know whether the website has used twiki or not, but if it has used twiki for their benefits. Which enable user to upload files on it and share it to other. I see this as a weak spot or the target spot for the attacker to upload files which can lead closer to exploitation of sensitive information.

The positive side of the webpage is that it has a login form where only the administrative users are authorized. If website have a login form, it should be carefully designed so that it is not sql injectable which can lead attacker to sensitive informations. Luckily the login form was not injectable.



# Network Penetration Test Assessment Summary

This penetration testing is for the assement of Software Security module test the capabilities of us to exploit the machine with ip address 10.3.21.140

## Detailed Walkthrough

I have tried everything that I have learned or I could think of to exploit the machine. I have tried to exploit the machine using the following ways:

### Reverse shell on web server

I tried uploading files on random directories, fortunately I was able to upload the file that I wanted to. After successfully uploading the file(reverse shell file) I was able to run the file but I couldn't get a response.

![reverse shell upload](assets/reverseshellupload.png)

![reverse shell run ](assets/reveseshellrun.png)

![reverse shell fail to run](assets/reverseshellrunfail.png)

### SQLmap in login page for command injection

After seeing the login form command injection came to my mind and gave a try for it using sqlmap since it is used for commad injection. 

![sqlmap](assets/sqlmap.png)

It should give me the command line where I can paste in login form to break the barrier.


### FTP server for uploading the file

I guessed the username and the password as "user" to login to ftp. Login was successful and I was able to upload file. Since ftp port(21) was not accessable from http I was no able to run the file that I have uploaded in ftp port.

### mysql for getting the data from the database

I was able to get inside the mysql port and even access all the databases present inside the system. Though I found that information, I didn't find it useful anywhere.

![mysql](assets/mysql.png)

![mysql data](assets/mysqldata.png)


### Twiki

![twiki](assets/twiki.png)

![twiki weakness](assets/twikiweak.png)

So I started searching the exploits of twiki, I tred exploiting using metasploit.

![twiki](assets/searchtwiki.png)

![twiki fail](assets/twikifail.png)

# Remediation Summary

The target machine has many vulnerable ports open which can lead to exploitation. The vulnerabilities were based on its outdated version of the application. The main thing that I found was, an attacker can upload files on the web server and ftp server which can lead to exploitation of the machine. Those behaviors should not be exposed to the attacker or we should not give any chance to the attacker to attack. The best way to prevent vulnerabilities is to keep all the applications up to the latest version.

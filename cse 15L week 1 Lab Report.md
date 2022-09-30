# Minyan Shi's CSE 15L Week 1 Lab Report
---
## Step 1: Installing VScode
1. Go to Visual Studio Code website [Link](https://code.visualstudio.com/).
2. Download and install the right version (Macs or Windows) on you computer.\
(After installation, if you seen a window shown right below after open the VScode, your are ready for the next steps.)\
![Image](https://github.com/minyanshi1105/cse15l-lab-reports/blob/5a7ae420ae6ac45fd2fd016b3911a54f3d9fde2a/CSE%2015L%20Week-1%20Lab-1%20Step%201.png)
## Step 2: Remotely Connecting
0. (If you're on Windows, please install OpenSSh on [Link](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui))
1. Open VScode and a new terminal  (Ctrl or Command + ` , or use the Terminal → New Terminal menu option).
2. Type in the command:`$ ssh cs15lfa22zz@ieng6.ucsd.edu`
3. If it is your first time connect to this server, you may see a message like this:
```
⤇ ssh cs15lfa22zz@ieng6.ucsd.edu
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```
Type `yes` and press enter.
4. Enter your password. (if you forget your passward, change it through out the website [[TUTORIAL] How to Reset your Password](https://docs.google.com/document/d/1hs7CyQeh-MdUfM9uv99i8tqfneos6Y8bDU0uhn1wqho/edit))
5. After successfully logged in, you may see this:
```
# Now on remote server
Last login: Sun Jan  2 14:03:05 2022 from 107-217-10-235.lightspeed.sndgca.sbcglobal.net
quota: No filesystem specified.
Hello cs15lfa22zz, you are currently logged into ieng6-203.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   23:25:01   0  0.08,  0.17,  0.11
ieng6-202   23:25:01   1  0.09,  0.15,  0.11
ieng6-203   23:25:01   1  0.08,  0.15,  0.11

Sun Jan 02, 2022 11:28pm - Prepping cs15lfa22
```
6. From the second time, once you successfully logged in, you may this the message below:
![Image](https://github.com/minyanshi1105/cse15l-lab-reports/blob/ae7d4059b5ce1ad4c38105965a16a60063a2eca6/CSE%2015L%20Week-1%20Lab-1%20Step%202.png)

## Step 3: Trying Some Commands
* cd ~
* cd
* ls -lat
* ls -a
* ls <directory> where <directory> is /home/linux/ieng6/cs15lfa22/cs15lfa22abc, where the abc is one of the other group members’ username
* cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/
* cat /home/linux/ieng6/cs15lfa22/public/hello.txt
![Image](https://github.com/minyanshi1105/cse15l-lab-reports/blob/ecc41f2aa3c49f1ce2dab1e5cde3b993791999e0/CSE%2015L%20Week-1%20Lab-1%20Step%203.png)

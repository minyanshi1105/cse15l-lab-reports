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
Type `yes` and press enter.\
4. Enter the password. (if you forget your passward, change it through out the website [[TUTORIAL] How to Reset your Password](https://docs.google.com/document/d/1hs7CyQeh-MdUfM9uv99i8tqfneos6Y8bDU0uhn1wqho/edit))\
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
* cd (*this command allows you to move between directories*)
* ls -lat
* ls -a
* ls <directory> where <directory> is /home/linux/ieng6/cs15lfa22/cs15lfa22abc, where the abc is one of the other group members’ username
* cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/
* cat /home/linux/ieng6/cs15lfa22/public/hello.txt\
  (`cd` command allows you to view the contents of a directory)\
  (`ls` command allows you to view the contents of a directory)\
  (`cat` command displays the contents of one or more files without having to open the file for editing.)\
![Image](https://github.com/minyanshi1105/cse15l-lab-reports/blob/ecc41f2aa3c49f1ce2dab1e5cde3b993791999e0/CSE%2015L%20Week-1%20Lab-1%20Step%203.png)
  
## Step 4: Moving Files with scp
* The command for capy files from your computer to a remote computer is called `scp`.
1. Create a file on your own computer named WhereAmI.java, and put in the following contents:
```
  class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
2. compile and run the file using `javac` and `java` commands to check if it works:
```
javac WhereAmI.java
java WhereAmI
```
![Image](https://github.com/minyanshi1105/cse15l-lab-reports/blob/ce361ad132fd6124e65a5d6e71546e5607aa9739/CSE%2015L%20Week-1%20Lab-1%20Step%204.1.png)
3. Run this command in the terminal from the directory where you create the file *WhereAmI.java*\
4. Log into ieng6 with `ssh` again.\
![Image](https://github.com/minyanshi1105/cse15l-lab-reports/blob/6b1ac373e9d1c2667e32ba66247cc538a94c2662/CSE%2015L%20Week-1%20Lab-1%20Step%204.2.png)
(I `scp` the WhereAmI.java from my local computer to my remote server first, and then log in to the remote server. The command for `scp` will be slightly different with the part `cs15lfa22cr@ieng6.ucsd.edu:~/` almong people since we are using different remote account. Type in your own account will be fine.)\
5. Check `ls`, and then you will see the file *WhereAmI.java* in your home directory.\
6. Run the program on the ieng6 computer using the same javac and java commands from before.\
```
javac WhereAmI.java
java WhereAmI
```
  
## Step 5: Setting an SSH Key
* In order to avoid to enter the password repetitivly, we should set `ssh` keys. The idea behind `ssh` keys is  a program called ssh-keygen which creates a pair of files called the public key and private key.
  
1. Enter This commands (on your own computer) to set up:
```
$ ssh-keygen
```
Then by fellowing the instruction (you may just press `enter`) you will see this:
![Image](https://github.com/minyanshi1105/cse15l-lab-reports/blob/b8486904c82b6d3b80c3bb35711ca158026eb021/CSE%2015L%20Week-1%20Lab-1%20Step%205.png)
2. Sign to your remote account again and create a new directory with the fellowing code:
```
mkdir .ssh
```
3. Logout your remote account. 
4. On your own account, type in the fellowing command with your own username and the path you saw in the command above:
```
$ scp /Users/joe/.ssh/id_rsa.pub cs15lfa22@ieng6.ucsd.edu:~/.ssh/authorized_keys
```
(Since I create the dir before the screenshoot, it shows the dir exist already.)
![Image](https://github.com/minyanshi1105/cse15l-lab-reports/blob/c67584524d09e761ce214ec8616a853f8a6e8f92/CSE%2015L%20Week-1%20Lab-1%20Step%205.2.png)

## Step 6: Optimizing Remote Running
* In order to make the process less painful, you may make a *local* edit to WhereAmI.java.
1.  Fellowing command allows you to log in and list the home directory on the remote server at the same time (logout your remote account before trying this command):
```
$ ssh cs15lfa22@ieng6.ucsd.edu "ls"
```
2. Fellowing command allows you to run multiple commands on the same line in most terminals:
```
$ cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI
```
![Image](https://github.com/minyanshi1105/cse15l-lab-reports/blob/748a7c37e31f1ff31ffb3fcd8c0beccdde06d927/CSE%2015L%20Week-1%20Lab-1%20Step%206.png)

---
Title: SWS101 Bounty Hacker
categories: (SWS101,swsCTF)
tags: (SWS101,Bounty Hacker )
---
# Topic: Bounty Hacker
----

## Target Ip Address

    10.10.156.153

### Find open ports on the machine

![openports](/assets/img/image.png)

Therer are 3 open ports 
```
- 21 ftp vsftpd 3.0.3
- 22 ssh OpenSSH 7.2p2
- 80 http Apache httpd 2.4.18
```

### Anonymous login from ftp server.

![ftp](/assets/img/image1.png)

I downloaded the task.txt and locks.txt so to see what is inside locks.txt we'll cat the file.

![locks](/assets/img/image2.png)

Now doing cat in the task.txt

![task](/assets/img/image3.png)

We found who wrote the task.txt 
    lin 

### user flag

using this as the username i tried to bruteforce the password using hydra and rockyou.txt

I found the pasword as RedDr4gonSynd1cat3 and logged into ssh successfully.

![hydra](/assets/img/image4.png)
![ssh](/assets/img/image5.png)

We got access to to user as lin 

![userflag](/assets/img/image6.png)

Reading the user.txt file we got the user flag.

    THM{CR1M3_SyNd1C4T3}

### root flag

To find the root flag i have used this command that we found using sudo -l

![root](/assets/img/image-1.png)

I found the root flag by changing directories and reading in the files

    THM{80UN7Y_h4cK3r}








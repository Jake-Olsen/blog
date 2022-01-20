---
layout: post
title:  "Cyber Security Rambling 1"
date:   2020-10-26 01:02:03 -0700
---

A video I watched last year
[IT Security Career Advice](https://www.youtube.com/watch?v=Oc8QQxyzjjQ)

Good Points in this Youtube Video by "Live Overflow"
[How To Protect Your Linux Server From Hackers!](https://www.youtube.com/watch?v=fKuqYQdqRIs)


Some things that I learned and took away from the protect video that I'd like to summarize are:
* Just using SSH Keys doesn't make your system more secure.
* Just using sudo doesn't make your system more secure either. If someone gets access to a user with sudo they basically have full access anyway.
* A very good security practice in general for all fields is reducing your threat surface. Simplify the system, by removing unneeded items & access. 

I also learned that if you do need to have some sort of privilege escalation there are more simple/better alternatives than sudo. You just need to find one that fits your use case better.

The more simple something is typically the more secure it can be.  This is because it is has less attack vectors, it's easier to maintain, update, patch, and more.

Good Security is finding the balance between being secure & convenient. If you make a system too secure then the users will find a way to circumvent it. If possible you try to make the secure way the easier way for end users. For example I love using a password manager. I don't have to make a password, remember it,  think of a derivative due to site requirements and restrictions and remember it. I just make a random one that follows the rules of that site. Then if I need to update it, there is a derive button to just follow the rules that you previously setup for those credentials. I only know the passwords for the PW manager, and major accounts like my Bank, Microsoft, & Google. I don't know the other ones and I don't need to. They are all unique so if 1 becomes compromised. All the rest is are unknown. Even if someone happens to bypass one of my main accounts and gets the KeePass DB. They now have to crack it open. 

For an example of security being too strict lets look at NIST: National Institute of Standards and Technology. They had a standard saying Passwords should change every 90 days. They realized the mistake and changed it in 2017. This is because they found that people end up choosing passwords based on the year and/or month so it doesn't make it much more secure and ends up being easier to guess. For example PasswordOct2021 then PasswordJan2022 instead of ThisPr4s3i$L0ngRTaco2days. In my opinion this really only affects the initial password you use to login to your system and your password manager. Once you are logged into your system and password manager changing other logins regularly would probably still be good as you could still make them random & unique. 



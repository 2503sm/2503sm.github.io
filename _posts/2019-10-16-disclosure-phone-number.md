---
title:  "Disclosure the verified phone number in Checkpoint."
date:   2019-10-16 12:24:15 +0800
categories: Hacking
classes:
  - landing
header:
  teaser: /assets/img/Facebook.jpg
---

In the free night, I often spend time on reading the big tech companies ‘s requests.
On that day, while i was reading Facebook’ requests, my test account was received a checkpoint ( Verify phone number ).

## POC

[https://www.youtube.com/watch?v=aFlGTdghCtk](https://www.youtube.com/watch?v=aFlGTdghCtk)


## Disclosure Phone number

![](https://1.bp.blogspot.com/-lXUEz8UYNCE/XaQg9mqIa7I/AAAAAAAAB0I/_CYaitS75Tku97fHEXB82My7cLi3h9_oACPcBGAYYCw/s640/bug%2B1.png)

After verifying my account, i just realized that i hadn’t turn off Burp Suite. When i had a look at requests again i saw these.

![](https://1.bp.blogspot.com/-yXo1xW1-6dg/XaQhqY2hDxI/AAAAAAAAB0Q/zQyKsGR3WSYiCxY1uJR-B5NY_TZ-pFrsQCPcBGAYYCw/s640/1231313213.png)

I could see my phone number in these requests. Should i send this case to Facebook?. Because I sent a lot of cases uploaded to triaged, but a few days later I received a notification that I was a latecomer.

However, if we can see what is not authorized, it is an error! So just report it.

## Report

20/8 - My report was sent.

23/8 - Facebook asked that would this case affect to users or interfere with Facebook's infrastructure?


23/8 - I reported this problem again with a detailed explanation.

26/8 - Facebook ‘s answer is NO! This is not a flaw, so you wouldn’t get any money from us.

05/9 : My name is ..., I work on the Facebook Security team. I just wanted to let you know that we are going to be investigating your report a bit further here: as such, we have reopened it.

Ok, you got your mistake.

05/9 - Ok!

14/10 - Confirmation of patch by Facebook
![](https://1.bp.blogspot.com/-mxauTWvl_f4/XaQmAUKA1AI/AAAAAAAAB0w/LKbH8pwfamc8B5-Moe_llPapwO2IkaMcwCPcBGAYYCw/s640/HOF.png)

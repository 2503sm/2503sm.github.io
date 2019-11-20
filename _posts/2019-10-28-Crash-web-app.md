---
title:  "Crash web — app via job application pages"
date:   2019-10-28 12:24:15 +0800
categories: Hacking
classes:
  - landing
header:
  teaser: /assets/img/Facebook.jpg
---

Hey It’s me again. Today, I have an other write-up about Facebook.


## POC

[https://www.youtube.com/watch?v=5lQ53UubNDU](https://www.youtube.com/watch?v=5lQ53UubNDU)


## STEP

My Facebook has gotten suggestions from job application page recently.


![](https://miro.medium.com/max/664/0*yCVCPeyui4n8L4Mr)

Click Apply Now:

![](https://miro.medium.com/max/754/0*w5BYanhpJEyzNLAl)

There were 4 fields Name, Phone, City, Email: Look more closely, I saw these 4 fields could be entered maximum up to 100 characters:

![](https://miro.medium.com/max/800/0*_ZwTrfSKmmcwgPCQ)

I entered 100 characters in these four fields and clicked send.
![](https://miro.medium.com/max/800/0*INVAq0GJP78lJAvX)
Error, could not be sent.

However I thought i could try sending by changing the request.

This time I created my own page to test. Turned on Burpsuite to Apply job, I would try the Name field first.
![](https://miro.medium.com/max/800/0*0IlXA2M0lkOw0uW3)

ABCCCC was the name which I entered in the apply form. After On intercept this request and i would fix ABCCCC to a different name with a number of characters exceeding 100. Then I just pasted the characters until my computer lagged.

I continued trying with 3 fields left. City, Email, Phone. There was only the City field i could intervene in the request to exceed the number of character limit.

There were 4 fields but i could intervene only 2 fields : Name and City.

It could be an error, but i thought it was still not risky. In order for Facebook to accept the error, i need to find more ways to use this error to affect users.
…
I used the phone to read messages.

![](https://miro.medium.com/max/800/0*QgFa1hH8JDitw_-w)

It crashed. This meant if the employer used the page manager app, it would also crash.

If the employer clicked on the notification in Facebook app, it would crash too.

## PUTTING EVERYTHING TOGETHER

After clicking on a message or notification, if you want to return, you have to turn off the application of course you can not return like the normal way. However, in order to crashing, there must be a limit.

I added 6 million characters to the message, it did not crash, but it had lagged for a long time (I could see the message and the application form. But only using a powerful configuration phone could see, the outdated phones would crash).

This time, i sent this report the first time. Facebook responded that it could not reproduce the issue and need to be provided.

When I tried again with 12 million characters => Crashing both app and web. (I explained to Facebook that they should try this on many mobile devices, because not everyone is able to have a good phone).


## REPORT

05/06 — Report sent.
07/06 — Facebook could not reproduce — require to provide more information.
07/06 — I updated again about this problem.
16/07 — Facebook copied my report — they would report again later.
20/10 — Facebook feedback + the bounty $
At this moment I felt a bit strange because Facebook did not ask me whether the flaw was fixed. I tried to reproduce the problem and it still worked.
20/10 — I asked Facebook why the problem was not be fixed.
21/10 — Facebook responded that they had noticed this problem for a long time. Facebook would continue to investigate this issue and fix it permanently.
I clicked the bounty link but it was expired @@.
23/10 — I wrote this write-up. ( I shared to group but i deleted immediately because the problem was not fixed.)
23/10 — I contacted because of the expired bounty link.
23/10 — Processed Report by Facebook.
25/10 — The problem is fixed.
26/10 — Confirmation of patch by Facebook.
26/10 — Facebook award $1000

![](https://miro.medium.com/max/800/0*JQnQv---qZlhhnEx)

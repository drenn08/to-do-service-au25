---
# markdownlint-disable
# vale  off
layout: default
parent: user resource
nav_order: 1
# tags used by AI files
description: Post a `task` resources to the service
tags:
    - api
categories:
    - api-reference
ai_relevance: high
importance: 7
prerequisites:
    - /api/user
related_pages: []
examples: []
api_endpoints: 
    - POST /tasks
version: "v1.0"
last_updated: "2025-09-03"
# vale  on
# markdownlint-enable
---

# Post users

Post new tasks to the service.

## URL

```shell

{server_url}/tasks
```

## Parameters

None

## Request headers

None

## Request body

```js
[
    {
        "lastName": "Smith",
        "firstName": "Ferdinand",
        "email": "f.smith@example.com",
        "id": 1
    },
    {
        "lastName": "Jones",
        "firstName": "Jillio",
        "email": "jlo.jones@example.com",
        "id": 2
    }
    ...
]
```

## Return body

None

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | Requested data posted successfully |
| 404 | Error | Requested data not posted successfully |
|  ECONNREFUSED | N/A | Service is offline. Start the service and try again. |

## Related topics

[task resource](https://drenn08.github.io/to-do-service-au25/api/task/)

---
# markdownlint-disable
# vale  off
layout: default
parent: task resource
nav_order: 1
# tags used by AI files
description: Post `task` resources to the service
tags:
    - api
categories:
    - api-reference
ai_relevance: high
importance: 7
prerequisites:
    - /api/tasks
related_pages: []
examples: []
api_endpoints: 
    - POST /tasks
version: "v1.0"
last_updated: "2025-09-03"
# vale  on
# markdownlint-enable
---

# Post tasks

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
    "userId": 1,
    "title": "Grocery shopping",
    "description": "eggs, bacon, gummy bears",
    "dueDate": "2025-09-20T17:00",
    "warning": "10",
    "id": 1
  },
  {
    "userId": 1,
    "title": "Piano recital",
    "description": "Daughter's first concert appearance",
    "dueDate": "2025-10-02T15:00",
    "warning": "30",
    "id": 2
  },
  {
    "userId": 2,
    "title": "Oil change",
    "description": "5K auto service",
    "dueDate": "2025-11-10T09:00",
    "warning": "60",
    "id": 3
  },
  {
    "userId": 3,
    "title": "Get shots for dog",
    "description": "Annual vaccinations for poochy",
    "dueDate": "2025-12-11T14:00",
    "warning": "20",
    "id": 4
  }
    ...
]
```

## Return body

{
    "userId": 1,
    "title": "Piano recital",
    "description": "Daughter's first concert appearance",
    "attire": "Black tie",
    "dueDate": "2025-10-02T15:00",
    "warning": "30",
    "id": 2
  }

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | Requested data posted successfully |
| 404 | Error | Requested data not posted successfully |
|  ECONNREFUSED | N/A | Service is offline. Start the service and try again. |

## Related topics

[task resource](./task.md)

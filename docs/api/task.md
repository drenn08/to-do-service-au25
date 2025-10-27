---
# markdownlint-disable
# vale  off
layout: default
nav_order: 4
has_children: true
has_toc: false
# tags used by AI files
description: "Information about the `task` resource"
tags: 
    - api
categories: 
    - api-reference
ai_relevance: high
importance: 8
prerequisites: []
related_pages: 
    - /tutorials/add-a-new-task
examples: []
api_endpoints:
    - /tasks
version: "v1.0"
last_updated: "2025-09-03"
# vale  on
# markdownlint-enable
---

# `task` resource

Base endpoint:

```shell

{server_url}/tasks
```

Contains information about tasks stored for the users of the service.

To have a task in the service, the user must already exist in the system.
Learn more about the [user resource](user.md).

## Resource properties

Sample `task` resource

```js

{
    "userId": 1,
    "title": "Grocery shopping",
    "description": "eggs, bacon, gummy bears",
    "dueDate": "2025-02-20T17:00",
    "warning": "10",
    "id": 1
}
```

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `userId` | number | ID of the user resource responsible for this task |
| `title` | string | Title or short description of the task |
| `description` | string | Long description of the task|
| `dueDate` | string | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format of the date and time the task is due |
| `warning` | number | Number of minutes before the `dueDate` to alert the user (positive integer). |
| `id` | number | The task's unique record ID |

## Operations

* [Post tasks](https://github.com/drenn08/to-do-service-au25/blob/Assignment-6.3/docs/post-tasks.md)
* [Get all tasks _(coming soon)_](#resource-properties)
* [Get task by ID _(coming soon)_](#resource-properties)
* [Get tasks by user ID](./tasks-get-tasks-by-user-id.md)

## Tutorials

* [Get task by user ID](../tutorials/get-tasks-assigned-to-a-userid.md)
* [Delete a task](tasks-delete-task-by-id.md)

---
# markdownlint-disable
# vale  off
layout: default
nav_order: 1
parent: Tutorials
# tags used by AI files
description: Add a `task` resource to the service
tags:
    - api
categories: 
    - tutorial
ai_relevance: high
importance: 6
prerequisites:
    - /before-you-start-a-tutorial
    - /api/user
    - /api/task
related_pages: []
examples: []
api_endpoints:
    - POST /tasks
version: "v1.0"
last_updated: "2025-09-03"
# vale  on
# markdownlint-enable
---

# Tutorial: Add a new task

Learn how to add a new task for a user of the To-Do Service by making a `POST` request
to the `/tasks` endpoint.

**Time to complete**: 10-15 minutes

## What you'll achieve

- Create a new task resource in the To-Do Service
- Get more information about the request format and required fields
- Verify that your task was successfully created
- Learn how to handle common errors

## Before you start

Make sure you've completed the [Before you start a tutorial](../before-you-start-a-tutorial.md)
topic on the development system you'll use for this tutorial.

### Prerequisites

- You'll need a valid `userId` for an existing user.
- To create a new user, see [Enroll a new user](enroll-a-new-user.md).
- Local service is accessible at your configured `base_url`
- Postman app installed

## Add a new task

Adding a new task requires sending a `POST` request to the [`task`](../api/task.md)
endpoint with the task details.

### Using Postman

1. Start the local service if it's not already running:

    ```shell
    cd <your-github-workspace>/to-do-service/api
    json-server -w to-do-db-source.json
    ```

2. Open the Postman app on your desktop.
3. Create a new request with these values:
    - **METHOD**: `POST`
    - **URL**: `{base_url}/tasks`
    - **Headers**:
      - `Content-Type: application/json`
    - **Request body**:
        You can change the values of each property as you'd like.

        ```json
        {
            "userId": 3,
            "title": "Get new tires",
            "description": "Get new tires for Hoppity",
            "due_date": "2025-03-11T14:00",
            "warning": "60"
        }
        ```

    - Field descriptions:
      - `userId`
        - Required, integer
        - The ID of the user this task belongs to; must match with an existing user.
      - `title`
        - Required, string - max 200 characters
        - A brief summary of the task.
      - `description`
        - Optional, string - max 1000 characters
        - Detailed information about the task.
      - `due_date`
        - Required, string
        - The deadline in format `YYYY-MM-DDTHH:MM`
      - `warning`
        - Optional, string
        - The number of minutes before the due date to send a reminder notification

4. In the Postman app, choose **Send** to make the request.
5. Watch for the response body, which should look something like the example below.
Note that the names should be the same as you used in your
**Request body** and the response should include the new user's `id`,
which is automatically assigned by the service and uniquely identifies this task.
You'll use this `id` when updating or deleting the task.

    ```json
    {
        "userId": 3,
        "title": "Get new tires",
        "description": "Get new tires for Hoppity",
        "due_date": "2025-03-11T14:00",
        "warning": "60",
        "id": 5
    }
    ```

After doing this tutorial in Postman, you might like to repeat it in
your favorite programming language.
To do this, adapt the values from the tutorial to the properties
and arguments that the language uses to make REST API calls.

## Verify your task

Confirm that the service saved your task correctly by retrieving
it using a `GET` request with the same URL and the `id` from your
response `{base_url}/tasks/5`. The response should include the
same task details you submitted.

## Troubleshooting common errors

|Status Code|Error|Solution|
|---------------------------|------------------------|------------------------------|
|`400 Bad Request`|Missing required field|Ensure request includes all required fields|
|`403 Forbidden`|Invalid date format|Use format: `YYYY-MM-DDTHH:MM`|
|`404 Not Found`|Invalid `userId`| Verify user exists, call `GET /users`|
|`500 Internal Server Error`|Service connection issue|Check json-server is running|
|`Connection refused`|Service not running|Start local service using step 1|

## Best practices

- **Confirm dates**: Ensure the `due_date` is in the future to avoid confusion
- **Use meaningful titles**: Keep the `title` field concise but descriptive
and under 200 characters
- **Set appropriate warnings**: The `warning` field uses minutes,
so 60 = 1 hour, 1440 = 1 day
- **Handle errors gracefully**: Always check the status code before processing
the response

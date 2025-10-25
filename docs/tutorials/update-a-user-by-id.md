---
# markdownlint-disable
# vale  off
layout: default
parent: Tutorials
nav_order: 4
# tags used by AI files
description: Update an existing `user` resource by ID using the service
tags:
    - api
categories: 
    - tutorial
ai_relevance: high
importance: 6
prerequisites:
    - /before-you-start-a-tutorial
    - /api/user
related_pages: []
examples: []
api_endpoints:
    - PUT /users/{id}
version: "v1.0"
last_updated: "2025-11-05"
# vale  on
# markdownlint-enable
---

# Tutorial: Update a user by ID

You'll use [Postman](https://www.postman.com/) to send the request and learn:

* How to update an existing user by ID using the API’s `PUT` method.
* How to verify changes in the API response

This tutorial takes about 15 minutes to complete.

## Before you start

Complete the [Before you start a tutorial](../before-you-start-a-tutorial.md)
topic on the development system you'll use for the tutorial.

You'll need:

* A JSON database file to start your server, for example, `to-do-db-source.json`.
* A running instance of the `json-server` API service
* The Postman desktop app installed on your machine

## Step 1: Start the local service

If the local service isn't already running, start the service by running
the following command from your terminal (Linux) or in Git Bash (Windows):

```shell
cd <your-github-workspace>/to-do-service/api
json-server -w to-do-db-source.json
```

The output should confirm that json-server is watching the database and
serving routes like `/users` and `/tasks`.

## Step 2: Send the request in Postman

To send the request in Postman:

1. Open the Postman desktop app.
1. Create a new request using the following parameters:

    | Setting             | Value                            |
    | ------------------- | -------------------------------- |
    | **Method**          | `PUT`                            |
    | **URL**             | `{base_url}/users/1`           |
    | **Header**          | `Content-Type: application/json` |
    | **Request Body**    | See code snippet below           |

    ```js
    {
        "firstName": "Farrah",
        "lastName": "Saunders",
        "email": "farrah.saunders@example.com"
    }
    ```

1. Click **Send**.

## Step 3: Review the response body

After you send the request, the response code `200` appears to show that the update was successful.

The response body includes the updated user details that you entered
in the request body and the original user ID, for example:

```js
{
    "firstName": "Farrah",
    "lastName": "Saunders",
    "email": "farrah.saunders@example.com",
    "id": 1
}
```

## Troubleshooting

Follow the guidance in this section to troubleshoot errors with updating a user by ID.

### Unexpected error code

If you get a different response code than `200`, confirm that the method and endpoint
in the request are correct.

### Unexpected response

If you get an error in the response, check that your local API service is still
running and that the user ID exists in your data file.

## Next steps

Now that you’ve updated one user, try experimenting:

* Change the email value, then send the request again and observe how the response changes.
* Update another user by changing the user ID in the URL, for example,  `/users/2`.

## Related pages

* To learn more about the `user` resource, see [`user` resource](../api/user.md)
* To try another tutorial in the series, see [Tutorial: Enroll a new user](./enroll-a-new-user.md)

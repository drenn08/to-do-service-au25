# Code examples

**Author:** David Renn

## cURL example

This example retrieves task ID 3 from the To-Do Service API using cURL.

### cURL command

```shell
curl http://localhost:3000/users/3
```

### cURL response

```json
{
  "lastName": "Martinez",
  "firstName": "Marty",
  "email": "m.martinez@example.com",
  "id": 3
}
```

## Postman example

The Postman example provided in the Assignment 5.3 demo.

### Request

**Method**:

```shell
GET http://localhost:3000/tasks/3
```

### Postman response

```json
{
    "userId": 2,
    "title": "Oil change",
    "description": "5K auto service",
    "dueDate": "2025-11-10T09:00",
    "warning": "60",
    "id": 3
}
```

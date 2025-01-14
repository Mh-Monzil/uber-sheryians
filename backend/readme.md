# /users/register Endpoint Documentation

## Description
The `/users/register` endpoint is used to register a new user in the system. It validates the user's input, hashes the password, creates a new user in the database, and returns a JSON Web Token (JWT) for authentication.

## Method
`POST`

## URL
`/users/register`

## Request Body
The following data needs to be provided in the request body as JSON:
- `fullName` (object)
  - `firstName` (string, required, minimum 3 characters)
  - `lastName` (string, minimum 3 characters)
- `email` (string, required, must be a valid email)
- `password` (string, required, minimum 6 characters)

# Example:
```json
{
  "fullName": {
    "firstName": "John",
    "lastName": "Doe"
  },
  "email": "john.doe@example.com",
  "password": "password123"
}
```

# Response:
```json
{
  "user": {
    "fullName": {
      "firstName": "John",
      "lastName": "Doe"
    },
    "email": "john.doe@example.com"
  },
  "token": "your-jwt-token"
}
```
# Example of an error response:
```json
{
  "errors": [
    {
      "msg": "Invalid Email",
      "param": "email",
      "location": "body"
    },
    {
      "msg": "First name must be at least 3 characters long",
      "param": "fullName.firstName",
      "location": "body"
    },
    {
      "msg": "Password must be at least 6 characters long",
      "param": "password",
      "location": "body"
    }
  ]
}
```
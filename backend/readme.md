# Backend API Documentation

## /users/register Endpoint Documentation

### Description
The `/users/register` endpoint is used to register a new user in the system. It validates the user's input, hashes the password, creates a new user in the database, and returns a JSON Web Token (JWT) for authentication.

### Method
`POST`

### URL
`/users/register`

### Request Body
The following data needs to be provided in the request body as JSON:
- `fullName` (object)
  - `firstName` (string, required, minimum 3 characters)
  - `lastName` (string, minimum 3 characters)
- `email` (string, required, must be a valid email)
- `password` (string, required, minimum 6 characters)

### Example:
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

### Response:
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

### Example of an error response:
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

## /users/login Endpoint Documentation

### Description
The `/users/login` endpoint is used to authenticate an existing user. It validates the user's input, checks the credentials, and returns a JSON Web Token (JWT) for authentication if the credentials are valid.

### Method
`POST`

### URL
`/users/login`

### Request Body
The following data needs to be provided in the request body as JSON:
- `email` (string, required, must be a valid email)
- `password` (string, required, minimum 6 characters)

### Example:
```json
{
  "email": "john.doe@example.com",
  "password": "password123"
}
```

### Response:
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

### Example of an error response:
```json
{
  "errors": [
    {
      "msg": "Invalid Email",
      "param": "email",
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


## /users/profile Endpoint Documentation

### Description
The `/users/profile` endpoint is used to retrieve the profile of the logged-in user.

### Method
`GET`

### URL
`/users/profile`

### Headers
`Authorization` (string, required): Bearer token of the logged-in user.

### Response:
```json
{
  "user": {
    "fullName": {
      "firstName": "John",
      "lastName": "Doe"
    },
    "email": "john.doe@example.com"
  }
}
```

### Example of an error response:
```json 
{
  "message": "Unauthorized"
}
```

## /users/logout Endpoint Documentation

### Description
The `/users/logout` endpoint is used to log out the logged-in user.

### Method
`GET`

### URL
`/users/logout`

### Headers
`Authorization` (string, required): Bearer token of the logged-in user.

### Response:
```json
{
  "message": "Logged out successfully"
}
```

### Example of an error response:
```json 
{
  "message": "Unauthorized"
}
```
## /captains/register Endpoint Documentation

### Description
The `/captains/register` endpoint is used to register a new captain in the system. It validates the captain's input, hashes the password, creates a new captain in the database, and returns a JSON Web Token (JWT) for authentication.

### Method
`POST`

### URL
`/captains/register`

### Request Body
The following data needs to be provided in the request body as JSON:
- `fullName` (object)
  - `firstName` (string, required, minimum 3 characters)
  - `lastName` (string, minimum 3 characters)
- `email` (string, required, must be a valid email)
- `password` (string, required, minimum 6 characters)
- `vehicle` (object)
  - `color` (string, required, minimum 3 characters)
  - `plate` (string, required, minimum 3 characters)
  - `capacity` (number, required, minimum 1)
  - `vehicleType` (string, required, must be one of ['car', 'motorcycle', 'auto'])

### Example:
```json
{
  "fullName": {
    "firstName": "Jane",
    "lastName": "Doe"
  },
  "email": "jane.doe@example.com",
  "password": "password123",
  "vehicle": {
    "color": "Red",
    "plate": "ABC123",
    "capacity": 4,
    "vehicleType": "car"
  }
}
```

### Response: 
```{
  "captain": {
    "fullName": {
      "firstName": "Jane",
      "lastName": "Doe"
    },
    "email": "jane.doe@example.com",
    "vehicle": {
      "color": "Red",
      "plate": "ABC123",
      "capacity": 4,
      "vehicleType": "car"
    }
  },
  "token": "your-jwt-token"
}
```

### Example of an error response:
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
    },
    {
      "msg": "Color must be at least 3 characters long",
      "param": "vehicle.color",
      "location": "body"
    },
    {
      "msg": "Plate must be at least 3 characters long",
      "param": "vehicle.plate",
      "location": "body"
    },
    {
      "msg": "Capacity must be at least 1",
      "param": "vehicle.capacity",
      "location": "body"
    },
    {
      "msg": "Invalid vehicle type",
      "param": "vehicle.vehicleType",
      "location": "body"
    }
  ]
}
```

## /captains/login Endpoint Documentation
### Description
The `/captains/login` endpoint is used to authenticate an existing captain. It validates the captain's input, checks the credentials, and returns a JSON Web Token (JWT) for authentication if the credentials are valid.

### Method
`POST`

### URL
`/captains/login`

### Request Body:
The following data needs to be provided in the request body as JSON:

- `email` (string, required, must be a valid email)
- `password` (string, required, minimum 6 characters)

### Example:
```json
{
  "email": "jane.doe@example.com",
  "password": "password123"
}
```

### Response:
```json
{
  "captain": {
    "fullName": {
      "firstName": "Jane",
      "lastName": "Doe"
    },
    "email": "jane.doe@example.com",
    "vehicle": {
      "color": "Red",
      "plate": "ABC123",
      "capacity": 4,
      "vehicleType": "car"
    }
  },
  "token": "your-jwt-token"
}
```

### Example of an error response:
```json
{
  "errors": [
    {
      "msg": "Invalid Email",
      "param": "email",
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

## /captains/profile Endpoint Documentation
### Description
The `/captains/profile` endpoint is used to retrieve the profile of the logged-in captain.

### Method
`GET`

### URL
`/captains/profile`

### Headers
`Authorization` (string, required): Bearer token of the logged-in captain.

### Response:
```json
{
  "captain": {
    "fullName": {
      "firstName": "Jane",
      "lastName": "Doe"
    },
    "email": "jane.doe@example.com",
    "vehicle": {
      "color": "Red",
      "plate": "ABC123",
      "capacity": 4,
      "vehicleType": "car"
    }
  }
}
```

### Example of an error response:
```json
{
  "message": "Unauthorized"
}
```

## /captains/logout Endpoint Documentation
### Description
The `/captains/logout` endpoint is used to log out the logged-in captain.

### Method
`GET`

### URL
`/captains/logout`

Headers
`Authorization` (string, required): Bearer token of the logged-in captain.

### Response:
```json
{
  "message": "Logged out successfully"
}
```

### Example of an error response:
```json
{
  "message": "Unauthorized"
}
```
# Library API Documentation
This is a library API for managing and accessing library resouce and operations such as books,authors, and borrowers built with PHP, the Slim Framework, and JWT (JSON Web Token) for authentication.It provides endpoints to perform CRUD (Create, Read, Update, Delete) operations, making it easy to integrate library functionalities into various applications.

## Features

- **User Management**: Add or Register, Update and Delete a user
- **User Authentication**: Validates if user is registered and generate JWT tokens for secure access.
- **Books Management**: Add, view, and delete books.
- **Authors Management**: Manage author details (Add, Update and Delete) and display associated works.
- **Borrower Management**: Track borrowers and the books they borrowed and if the books are returned.



## Technologies Used
- **PHP**: Programming language for backend development.
- **Slim Framework**: Lightweight PHP framework for building APIs.
- **Firebase JWT**: Library for JSON Web Token (JWT) authentication.
- **Composer**: Dependency management for PHP projects.



## Endpoints
This section covers the URL, description, method, body, and the sample responses of the API when it succeeds or fails

### User
#### User Register

- **Description**: Registers the user
- **URL**: `http://localhost:8080/library/public/user/register`
- **Method**: ``POST``
- **Body**:
```json
{
  "username": "AlexandraAri",
  "password": "password"
}
```

- **Response**:
  - **Success**:
  ```json
  {
  "status": "success",
  "message": "User registered successfully"
  }
  ```

  - **Fail**
  ```json
  {
  "status": "fail",
  "data": {
    "title": "SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry 'AlexandraAri' for key 'username'"}
  }
  ```

#### User Authenticate

- **Description**: Authenticate if the user is registered and generates a single use token.
- **URL**: `http://localhost:8080/library/public/user/authenticate`
- **Method**: ``POST``
- **Body**:
```json
{
  "username":"AlexandraAri",
  "password": "password"
}
```

- **Response**:
  - **Success**:
  ```json
  {
  "status": "success",
  "token": "(generated token)"
  }
  ```

  - **Fail**
  ```json
  {
  "status": "fail",
  "data": {
    "title": "Authentication Failed"
  }
  }
  ```

#### User Update

- **Description**: Ask for a token to Update the details of the user. Generates a single use token.
- **URL**: `http://localhost:8080/library/public/user/update`
- **Method**: ``POST``
- **Body**:
```json
{
  "userid":"1",
  "username":"AlexandraAM",
  "password":"password",
  "token": "(generated token)"
}
```

- **Response**:
  - **Success**:
  ```json
  {
  "status": "success",
  "message": "User updated successfully.",
  "new_token": "(generated token)"
  }
  ```

  - **Fail**
  ```json
  {
  "status": "fail",
  "data": {
    "title": "Invalid or expired token"
  }
  }
  ```

  or 

  ```json
  {
  "status": "fail",
  "data": {
    "title": "Token already used or invalid"
  }
  }
  ```


#### User Delete

- **Description**: Ask for a token to Delete user. Generates a single use token.
- **URL**: `http://localhost:8080/library/public/user/delete`
- **Method**: ``POST``
- **Body**:
```json
{
  "userid":3,
  "token": "(generated token)"
}
```

- **Response**:
  - **Success**:
  ```json
  {
  "status": "success",
  "data": {
    "userid": 3,
    "new_token": "(generated token)"
    }
  }
  ```

  - **Fail**
  ```json
  {
  "status": "fail",
  "data": {
    "title": "Invalid or expired token"
  }
  }
  ```

   or 

  ```json
  {
  "status": "fail",
  "data": {
    "title": "Token already used or invalid"
  }
  }
  ```


### Author
#### Add Author

- **Description**: Ask for a token to Add Author then generates a single use token.
- **URL**: `http://localhost:8080/library/public/author/add`
- **Method**: ``POST``
- **Body**:
```json
{
 "authorname": "A.A. Meneses",
  "token": "(generated token)"
}
```

- **Response**:
  - **Success**:
  ```json
  {
  "status": "success",
  "data": {
    "authorid": "1",
    "authorname": "A.A. Meneses",
    "new_token": "(generated token)"
    }
  }
  ```

  - **Fail**
  ```json
  {
  "status": "fail",
  "data": {
    "title": "Invalid or expired token"
  }
  }
  ```
   or 
  ```json
  {
  "status": "fail",
  "data": {
    "title": "Token already used or invalid"
  }
  }
  ```

#### Update Author

- **Description**: Ask for a token to Update Author then generates a single use token.
- **URL**: `http://localhost:8080/library/public/author/update`
- **Method**: ``POST``
- **Body**:
```json
{
  "authorid": 3,
  "authorname":"Colleen Hoover",
  "token": "(generated token)"
}
```

- **Response**:
  - **Success**:
  ```json
  {
  "status": "success",
  "data": {
    "authorid": 3,
    "authorname": "Colleen Hoover",
    "new_token": "(generated token)"
    }
  }
  ```

  - **Fail**
  ```json
  {
  "status": "fail",
  "data": {
    "title": "Invalid or expired token"
  }
  }
  ```
   or 
  ```json
  {
  "status": "fail",
  "data": {
    "title": "Token already used or invalid"
  }
  }
  ```

#### Delete Author

- **Description**: Ask for a token to Update Author then generates a single use token.
- **URL**: `http://localhost:8080/library/public/author/delete`
- **Method**: ``POST``
- **Body**:
```json
{
  "authorid": 2,
  "token": "(generated token)"
}

```

- **Response**:
  - **Success**:
  ```json
  {
  "status": "success",
  "data": {
    "authorid": 2,
    "new_token": "(generated token)"
    }
  }
  ```

  - **Fail**
  ```json
  {
  "status": "fail",
  "data": {
    "title": "Invalid or expired token"
  }
  }
  ```
   or 
  ```json
  {
  "status": "fail",
  "data": {
    "title": "Token already used or invalid"
  }
  }
  ```

#### Display Authors Books

- **Description**: Ask for a token to Update Author then generates a single use token.
- **URL**: `http://localhost:8080/library/public/author/displaybook?authorid=(pasteAuthorID)&token=(generatedtoken)`
- **Method**: ``GET`` 
    
- **Response**:
  - **Success**:
  ```json
  {
  "status": "success",
  "data": [
    {
      "bookid": 1,
      "title": "It Ends with US",
      "authorid": 3
    },
    {
      "bookid": 2,
      "title": "It Starts with Us",
      "authorid": 3
    }
    ],
    "new_token": "(generated token)"
    }
  ```

  - **Fail**

  ```json 
  {
  "status": "fail",
  "data": {
    "title": "No books found for the given author ID"
  }
  }
  ```
  or 

  ```json
  {
  "status": "fail",
  "data": {
    "title": "Invalid or expired token"
  }
  }
  ```
   or 
  ```json
  {
  "status": "fail",
  "data": {
    "title": "Token already used or invalid"
  }
  }
  ```
  










# Library Management System API 
The purpose of this API is to handle books, authors, users, and their relationships inside a library system. With the help of a MySQL database, users may register, log in, and interact with books and authors. It also makes it easier to manage the connections between authors and books. 
This API provides endpoints for seamless data management and retrieval. It ensures secure authentication and authorization for all user interactions. Additionally, it is designed to be scalable and flexible, allowing future enhancements to support more features.
## Table of Contents 
- [Features](#features)
- [Used Technology](#used-technology)
- [User Endpoints](#user-endpoints)
- [Author Endpoints](#author-endpoints)
- [Book Endpoints](#book-endpoints)
- [Book-Author Relationship Endpoints](#book-author-relationship-endpoints)


# Features 
- **JWT Authentication**: JSON Web Tokens provide safe access to the API.
- **Management of Token LifeCycle**: Track and invalidate used tokens to ensure security and prevent token reuse for improved security.
- **Responses From RESTful APIs**: Provides structured JSON answers for both success and errors.
- **CRUD Operations**: Control the relationships between books, authors, users, and books.

# Used Technology
- **PHP**: The main programming language for backend applications, which makes use of the Slim Framework to facilitate rapid and effective development.
- **Slim Framework**: For creating the structure of the API.
- **MySQL**: The relational database management system MySQL is used to store user information, such as login credentials and account status.

# User Endpoints
### User Register

- **Method**: `POST`
- **Endpoint**: `/user/register`
#### Payload:
```json
  "username": "FloresDan",
  "password": "FloresDan123"
```
#### Successful Response:
```json
  "status": "success",
  "data": null
```
#### Failed Response (Failed):
```json
  "status": "fail",
  "data": "Username already exists"
```

### User Authenticate
- **Method**: `POST`
- **Endpoint**: `/user/authenticate`
#### Payload:
```json
  "username": "FloresDan",
  "password": "FloresDan123"
```
#### Successful Response:
```json
  "status": "success",
  "token":<TOKEN>
  "data": null
```
#### Failed Response (Failed):
```json
  "status": "fail",
  "data": {
  "title": "Authentication Failed!"
```

### User Read 
- **Method**: `GET`
- **Endpoint**: `/user/read`
#### Payload:
No request Needed

#### Successful Response:
```json
{
"status": "success",
"token": <NEW_TOKEN>,
"data": [
  {
    "userid": 1,
    "username": "FloresDan"
  }
```
#### Failed Response (Failed):
```json
  "status": "fail",
  "data": "Unauthorized: Token not provided"
```
### User Update
- **Method**: `PUT`
- **Endpoint**: `/user/update`
#### Payload:
```json
  "userid":"1",
  "username": "New_Username",
  "password": "New_Password"
```

#### Successful Response:
```json
 "status": "success",
  "token": "<NEW_TOKEN>",
  "data": "User updated successfully"
```
#### Failed Response (Failed):
```json
 "status": "fail",
  "data": "User with ID 1 does not exist."
```
#### Failed Response (Failed):
```json
 "status": "fail",
  "data": "Username and password must be at least 5 characters long and not empty"
```

### User Delete 
- **Method**: `DELETE`
- **Endpoint**: `/user/delete`
#### Payload:
```json
 "userid": "1"
```
#### Successful Response:
```json
  "status": "success",
  "token": "<NEW_TOKEN>",
  "data": "User deleted successfully"
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "User with ID 1 does not exist."
```
#### Failed Response(Failed):
```json
 "status": "fail",
  "data": "User ID must be provided."
```
# Author Endpoints

### Author Create 
- **Method**: `POST`
- **Endpoint**: `/authors/create`
#### Payload:
```json
"username: Juan De La Cruz"
```
#### Successful Response:
```json
  "status": "success",
  "token": "<NEW_TOKEN>",
  "data": "Author created successfully"
```
#### Failed Response(Invalid Input):
```json
  "status": "fail",
  "data": "Author name must be more than 4 characters and cannot be blank."
```
### Author Read 
- **Method**: `GET`
- **Endpoint**: `/authors/read`
#### Payload:
no request needed
#### Successful Response:
```json
 "status": "success",
  "token": "<NEW_Token>",
  "data": [
      {
          "authorid": 1,
          "name": "Juan De La Cruz"
      }
```
#### Failed Response(Failed):
```json
   "status": "fail",
   "data": "Unauthorized: Token not provided"
```
#### Failed Response(Failed):
```json
   "status": "fail",
   "data": "No authors found"
```
### Author Update 
- **Method**: `PUT`
- **Endpoint**: `/authors/update`
#### Payload:
```json
  "authorid": "1",
  "name": "Tanggol Di Magiba"
```
#### Successful Response:
```json
  "status": "success",
  "token": "<NEW_TOKEN>",
  "data": "User updated successfully"
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Author name must be more than 4 characters and cannot be blank."
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Author with ID 1 does not exist."
```
### Author Delete 
- **Method**: `DELETE`
- **Endpoint**: `/authors/delete`
#### Payload:
```json
  "userid": "1"
```
#### Successful Response:
```json
  "status": "success",
  "token": "<NEW_TOKEN>",
  "data": "User deleted successfully"
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Author ID must be provided."
```
#### Failed Response(Failed):
```json
 "status": "fail",
  "data": "Author with ID 4 does not exist."
```
# Book Endpoints

### Books Create 
- **Method**: `POST`
- **Endpoint**: `/books/create`
#### Payload:
```json
  "title": "Avengers Endgame",
  "authorid": 1
```
#### Successful Response:
```json
   "status": "success",
  "token": "<NEW_TOKEN>",
  "data": "Book created successfully"
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Book title  must be more than 4 characters and cannot be blank."
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Author not found"
```
### Books Read
- **Method**: `GET`
- **Endpoint**: `/books/read`
#### Payload:
no request needed
#### Successful Response:
```json
  {
 "status": "success",
  "token": "<NEW_TOKEN>",
  "data": [
      {
          "bookid": 1,
          "title": "Avengers Endgame",
          "authorid": 1,
          "author_name": "Juan De La Cruz"
      }
  ]
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "No books found"
```
### Books Update
- **Method**: `PUT`
- **Endpoint**: `/books/update`
#### Payload:
```json
  "bookid": 1,
  "title": "I Can Copy Talents",
  "authorid": 1
```
#### Successful Response:
```json
   "status": "success",
   "token": "<NEW_TOKEN>",
   "data": "Book updated successfully"
```
#### Failed Response(Failed):
```json
   "status": "fail",
   "data": "Book with ID 1 does not exist."
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Book title and password must be at least 5 characters long and not empty"
```
### Books Delete
- **Method**: `DELETE`
- **Endpoint**: `/books/delete`
#### Payload:
```json
  "bookid": 1
```
#### Successful Response:
```json
  "status": "success",
  "token": "<New_JWT_Token>",
  "data": "Book deleted successfully"
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Book ID must be provided."
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Book with ID 1 does not exist."
```
# Book-Author Relationship Endpoints

### Book-Author Create
- **Method**: `POST`
- **Endpoint**: `/book-authors/Create`
#### Payload:
```json
  "bookid": "1",
  "authorid": "1"
```
#### Successful Response:
```json
  "status": "success",
  "token": "<NEW_TOKEN>",
  "data": "Book-author relationship created successfully"
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Book does not exist"
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Author does not exist"
```
### Book-Author Read
- **Method**: `GET`
- **Endpoint**: `/book-authors/read`
#### Payload:
no request needed
#### Successful Response:
```json
 "status": "success",
  "token": "<NEW_TOKEN>",
  "data": [
      {
          "collectionid": "1",
          "bookid": "1",
          "authorid": "1",
          "book_title": "Avengers Endgame",
          "author_name": "Juan De La Cruz"
      }
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "No book-author relationships found"
```
### Book-Author Update
- **Method**: `PUT`
- **Endpoint**: `/book-authors/update`
#### Payload:
```json
   "collectionid": "1",
   "bookid": "1",
   "authorid": "1"
```
#### Successful Response:
```json
  "status": "success",
  "token": <NEW_TOKEN>",
  "data": "Book-author relationship updated successfully"
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Book does not exist"
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Author does not exist"
```
### Book-Author Delete
- **Method**:`DELETE`
- **Endpoint**: `/book-authors/delete`
#### Payload:
```json
   "collectionid": "1"
```
#### Successful Response:
```json
  "status": "success",
  "token": "<NEW_TOKEN>",
  "data": "Book-author relationship deleted successfully"
```
#### Failed Response(Failed):
```json
  "status": "fail",
  "data": "Book ID must be provided."
```

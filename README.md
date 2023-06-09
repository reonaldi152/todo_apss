# TODO APP API
#### Easy to use and have high performance 🚀



## API Documentation
Root URL: https://todoapss-production.up.railway.app/
### Register
Register user to application.
* #### URL

  /register

* #### Method:

  `POST`
  
*  #### URL Params
   None

* #### Request header
  None

* #### Request body
  ```sh
    {
      "name": "reonaldi",
      "email": "reonaldi1105@gmail.com",
      "password": "rahasiakita"
    }
  ```

* #### Success Response:
  * ##### Code:
    201
  * ##### Content: 
    `{ "message": "User created successfully" }`
 
* #### Error Response:
  * ##### Code:
    409 CONFLICT
  * ##### Content:
    `{ "message" : "Email already exists." }`

  OR
  
  * ##### Code:
    500 INTERNAL SERVER ERROR
  * ##### Content:
    `{ "message" : "Internal server error" }`

----

### Login
Get token to get authenticated.
* #### URL

  /login

* #### Method:
  `POST`
  
*  #### URL Params
   None

* #### Request header
  None

* #### Request body
  ```sh
    {
      "email": "reonaldi1105@gmail.com",
      "password": "rahasiakita"
    }
  ```

* #### Success Response:
  * ##### Code:
    200
  * ##### Content: 
    ```sh
    {
        "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9....",
        "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...."
    }
    ```
 
* #### Error Response:
  * ##### Code:
    404 NOT FOUND
  * ##### Content:
    `{ "message": "User not found" }`

  OR
  * ##### Code:
    500 INTERNAL SERVER ERROR
  * ##### Content:
    `{ "message" : "Internal server error" }`

----

### Get All Todos
Returns json data about all todos.
* #### URL

  /todos

* #### Method:
  `GET`
  
*  #### URL Params
    None

* #### Request header
  `Authorization: <Your access token>`

* #### Request body
  None

* #### Success Response:
  * ##### Code:
    200
  * ##### Content: 
    ``` sh
    {
      "data": [
        {
          "_id": "636e96c05d4254ebf106893d",
          "title": "Belajar Node JS",
          "description": "Mempelajari Node dan Express",
          "completed": false,
          "due_date": "2022-11-30T00:00:00.000Z",
          "user": "636e92e0dc13f9cc043db878",
          "createdAt": "2022-11-11T18:38:56.997Z",
          "updatedAt": "2022-11-11T18:38:56.997Z",
          "__v": 0
        },
        {
          "_id": "636e96cc5d4254ebf1068940",
          "title": "Makan",
          "description": "Makan yang teratur ya",
          "completed": true,
          "due_date": "2022-11-30T00:00:00.000Z",
          "user": "636e92e0dc13f9cc043db878",
          "createdAt": "2022-11-11T18:39:08.336Z",
          "updatedAt": "2022-11-11T18:39:08.336Z",
          "__v": 0
        }
      ]
    }
    ```
 
* #### Error Response:
  * ##### Code:
    500 INTERNAL SERVER ERROR
  * ##### Content:
    `{ "message" : "Internal server error" }`

  OR

  * ##### Code:
    401 UNAUTHORIZED <br />
  * ##### Content:
    `{ "status": "error", "message": "invalid token" }`

----

### Get Todo by ID
Returns json data about single todo.
* #### URL
  /todos/:id

* #### Method:
  `GET`
  
*  #### URL Params
   ##### Required:
   `id=[mongoose.Types.ObjectId]`

* #### Request header
  `Authorization: <Your access token>`

* #### Request body
  None

* #### Success Response:
  * ##### Code:
    200
  * ##### Content: 
    ``` sh
    {
      "data": {
        "_id": "636e96cc5d4254ebf1068940",
        "title": "Makan",
        "description": "Makan yang teratur ya",
        "completed": false,
        "due_date": "2022-11-30T00:00:00.000Z",
        "user": "636e92e0dc13f9cc043db878",
        "createdAt": "2022-11-11T18:38:56.997Z",
        "updatedAt": "2022-11-11T18:38:56.997Z",
        "__v": 0
      }
    }
    ```
 
* #### Error Response:
  * ##### Code:
    404 NOT FOUND
  * ##### Content:
    `{ "message": "Todo not found" }`

  OR

  * ##### Code:
    401 UNAUTHORIZED <br />
  * ##### Content:
    `{ "status": "error", "message": "unauthorized" }`

----

### Create Todo
Create a todo by user authenticated.
* #### URL
  /todos

* #### Method:
  `POST`
  
*  #### URL Params
    None

* #### Request header
  `Authorization: <Your access token>`

* #### Request body
  ```sh
    {
      "title": "Main game",
      "description": "Bermain PES agar tidak stess.",
      "due_date": "2022-11-20"
    }
  ```

* #### Success Response:
  * ##### Code:
    201
  * ##### Content: 
    ``` sh
    {
      "data": {
        "title": "Main game",
        "description": "Bermain PES agar tidak stess.",
        "completed": false,
        "due_date": "2022-11-20T00:00:00.000Z",
        "user": "636e92e0dc13f9cc043db878",
        "_id": "637058a531433a1c97e4989b",
        "createdAt": "2022-11-13T02:38:29.717Z",
        "updatedAt": "2022-11-13T02:38:29.717Z",
        "__v": 0
      }
    }
    ```
 
* #### Error Response:
  * ##### Code:
    500 INTERNAL SERVER ERROR
  * ##### Content:
    `{ "message" : "Internal server error" }`

  OR

  * ##### Code:
    401 UNAUTHORIZED <br />
  * ##### Content:
    `{ "status": "error", "message": "invalid token" }`

----

### Update Todo
Update todo by ID.
* #### URL
  /todos/:id

* #### Method:
  `POST`
  
*  #### URL Params
   ##### Required:
   `id=[mongoose.Types.ObjectId]`

* #### Request header
  `Authorization: <Your access token>`

* #### Request body
  ```sh
    {
      "title": "Mengerjakan TPA",
      "description": "TPA 5 on progess.",
      "due_date": "2022-11-20"
    }
  ```

* #### Success Response:
  * ##### Code:
    201
  * ##### Content: 
    ``` sh
    {
      "data": {
        "_id": "637058a531433a1c97e4989b",
        "title": "Mengerjakan TPA",
        "description": "TPA 5 on progess",
        "completed": false,
        "due_date": "2023-05-26T00:00:00.000Z",
        "user": "636e92e0dc13f9cc043db878",
        "createdAt": "2023-05-26T15:51:04.229Z",
        "updatedAt": "2023-05-26T15:51:04.229Z",
        "__v": 0
      }
    }
    ```
 
* #### Error Response:
  * ##### Code:
    404 NOT FOUND
  * ##### Content:
    `{ "message": "Todo not found" }`

  OR

  * ##### Code:
    401 UNAUTHORIZED <br />
  * ##### Content:
    `{ "status": "error", "message": "unauthorized" }`

----

### Change Todo Status
Change status completed a todo by ID.
* #### URL
  /todos/:id/change-status

* #### Method:
  `PUT`
  
*  #### URL Params
   ##### Required:
   `id=[mongoose.Types.ObjectId]`

* #### Request header
  `Authorization: <Your access token>`

* #### Request body
  None

* #### Success Response:
  * ##### Code:
    200
  * ##### Content: 
    ``` sh
    {
      "data": {
        "_id": "63705b8d729c73652cfc297f",
        "title": "Main game",
        "description": "Bermain PES agar tidak stress.",
        "completed": true,
        "due_date": "2023-05-26T00:00:00.000Z",
        "user": "636e92e0dc13f9cc043db878",
        "createdAt": "2023-05-26T15:51:04.229Z",
        "updatedAt": "2023-05-26T15:51:04.229Z",
        "__v": 0
      }
    }
    ```
 
* #### Error Response:
  * ##### Code:
    404 NOT FOUND
  * ##### Content:
    `{ "message": "Todo not found" }`

  OR

  * ##### Code:
    401 UNAUTHORIZED <br />
  * ##### Content:
    `{ "status": "error", "message": "unauthorized" }`

----

### Delete Todo
Delete one todo by ID.
* #### URL
  /todos/:id

* #### Method:
  `DELETE`
  
*  #### URL Params
   ##### Required:
   `id=[mongoose.Types.ObjectId]`

* #### Request header
  `Authorization: <Your access token>`

* #### Request body
    None

* #### Success Response:
  * ##### Code:
    200
  * ##### Content: 
    ``` sh
    {
      "data": {
        "_id": "637058a531433a1c97e4989b",
        "title": "Mengerjakan TPA",
        "description": "TPA 5 on progess",
        "completed": false,
        "due_date": "2023-05-26T15:51:04.229Z",
        "user": "636e92e0dc13f9cc043db878",
        "createdAt": "2023-05-26T00:00:00.000Z",
        "updatedAt": "2023-05-26T00:00:00.000Z",
        "__v": 0
      }
    }
    ```
 
* #### Error Response:
  * ##### Code:
    404 NOT FOUND
  * ##### Content:
    `{ "message": "Todo not found" }`

  OR

  * ##### Code:
    401 UNAUTHORIZED <br />
  * ##### Content:
    `{ "status": "error", "message": "unauthorized" }`

----

### Delete All Todo
Delete all todo.
* #### URL
  /todos

* #### Method:
  `DELETE`
  
*  #### URL Params
    None

* #### Request header
  `Authorization: <Your access token>`

* #### Request body
    None

* #### Success Response:
  * ##### Code:
    200
  * ##### Content: 
    `{ "message": "success delete all todos" }`
 
* #### Error Response:
  * ##### Code:
    500 INTERNAL SERVER ERROR
  * ##### Content:
    `{ "message" : "Internal server error" }`

  OR

  * ##### Code:
    401 UNAUTHORIZED <br />
  * ##### Content:
    `{ "status": "error", "message": "unauthorized" }`

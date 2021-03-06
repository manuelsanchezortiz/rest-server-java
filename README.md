# rest-server-java
## RESTful API
The API will follow all the correct guidelines that currently exist for a RESTful API. Here are some of them:
- A URL identifies a resource.
- URLs include nouns, not verbs.
- Use of plural nouns for consistency.
- Use HTTP verbs (GET, POST, PUT, DELETE) according with [HTTP/1.1](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) standard.
- Use of version in the URL, example http(s)://localhost:port/path/to/resource.
## HTTP Verbs
Bellow is an example that shows how the API will behave and the vebs that it will use.

| HTTP METHOD | GET | POST | PUT | DELETE |
| --- | --- | --- | --- | --- |
| CRUD OP | READ | CREATE | UPDATE | REMOVE |
| /dogs | List all dogs | Create new dog | Error | Error |
| /dogs/1 | Info about dog 1 | Error | Update info of dog 1 | Remove dog 1 |
## Usage
### List all messages
**Definition:** `GET /greetings`

**Response**:
- `500 - Internal Server Error`
- `400 - Bad User Request`
- `200 - OK`

**Response Body (Success):**:
```json
[
	{
        "date": "2019-07-17 15:37:48.873",
        "message": "bJmmCHfVV",
        "id": 10
    },
	{
        "date": "2019-07-17 15:37:48.873",
        "message": "bJmmCHfVV",
        "id": 12
    },
    {
        "date": "2019-07-17 15:37:48.873",
        "message": "bJmmCHfVV",
        "id": 13
    }
]
```

**Response Body (Error):**
```json
{
    "message": "Error motive."
}
```
### List Specific message
**Definition:** `GET /greetings/(:id)`

**Response:**
- `500 - Internal Server Error`
- `404 - Not Found`
- `400 - Bad User Request`
- `200 - OK`

**Response Body (Success):**
```json
{
    "date": "2019-07-17 15:37:48.873",
    "message": "bJmmCHfVV",
    "id": 10
}
```

**Response Body (Error):**
```json
{
    "message": "Error motive."
}
```
### Create a message
**Definition:** `POST /greetings`

**Response**:
- `500 - Internal Server Error`
- `400 - Bad User Request`
- `200 - OK`

**Response Body (Success):**:
```json
{
    "date": "2019-07-17 15:37:48.873",
    "message": "bJmmCHfVV",
    "id": 10
}
```

**Response Body (Error):**
```json
{
    "message": "Error motive."
}
```
### Update Specific message
**Definition:** `PUT /greetings/(:id)`

**Response:**
- `500 - Internal Server Error`
- `404 - Not Found`
- `400 - Bad User Request`
- `200 - OK`

**Response Body (Success):**
```json
{
    "date": "2019-07-17 15:37:48.873",
    "message": "bJmmCHfVV",
    "id": 10
}
```

**Response Body (Error):**
```json
{
    "message": "Error motive."
}
```
### Delete Specific message
**Definition:** `DELETE /greetings/(:id)`

**Response:**
- `500 - Internal Server Error`
- `404 - Not Found`
- `400 - Bad User Request`
- `200 - OK`

**Response Body (Success):**
```json
{
    "message": "Delete Successful."
}
```

**Response Body (Error):**
```json
{
    "message": "Error motive."
}
```
### List all users
**Definition:** `GET /users`

**Response**:
- `500 - Internal Server Error`
- `400 - Bad User Request`
- `200 - OK`

**Response Body (Success):**:
```json
[
	{
        "localidade": "viseu",
        "nome": "breno",
        "id": 19,
        "datanascimento": "2018-01-01"
    },
	{
        "localidade": "lisboa",
        "nome": "andré",
        "id": 20,
        "datanascimento": "2017-01-01"
    }
]
```

**Response Body (Error):**
```json
{
    "message": "Error motive."
}
```
### List Specific user
**Definition:** `GET /users/(:id)`

**Response:**
- `500 - Internal Server Error`
- `404 - Not Found`
- `400 - Bad User Request`
- `200 - OK`

**Response Body (Success):**
```json
{
    "localidade": "viseu",
    "nome": "breno",
    "id": 11,
    "datanascimento": "1997-03-04"
}
```

**Response Body (Error):**
```json
{
    "message": "Error motive."
}
```
### Create a user
**Definition:** `POST /users`

**Response**:
- `500 - Internal Server Error`
- `400 - Bad User Request`
- `200 - OK`

**Response Body (Success):**:
```json
{
    "localidade": "viseu",
    "nome": "breno",
    "id": 11,
    "datanascimento": "1997-03-04"
}
```

**Response Body (Error):**
```json
{
    "message": "Error motive."
}
```
### Update Specific user
**Definition:** `PUT /users/(:id)`

**Response:**
- `500 - Internal Server Error`
- `404 - Not Found`
- `400 - Bad User Request`
- `200 - OK`

**Response Body (Success):**
```json
{
    "localidade": "viseu",
    "nome": "breno",
    "id": 11,
    "datanascimento": "1997-03-04"
}
```

**Response Body (Error):**
```json
{
    "message": "Error motive."
}
```
### Delete Specific user
**Definition:** `DELETE /users/(:id)`

**Response:**
- `500 - Internal Server Error`
- `404 - Not Found`
- `400 - Bad User Request`
- `200 - OK`

**Response Body (Success):**
```json
{
    "message": "Delete Successful."
}
```

**Response Body (Error):**
```json
{
    "message": "Error motive."
}
```
## Requirements (No Docker)
- Java (+11)
- Maven (+3)
- [jdbc-rmi-server](https://github.com/Guergeiro/jdbc-rmi-server)

## Install (No Docker)
- Navigate to folder
- config.config file with the following code inside
```
rmi-url=INSERT URL HERE
rmi-port=INSERT PORT HERE (Exclude the ":");
```
- mvn clean install
- mvn dependency:resolve
- mvn verify
- java -jar ./target/rest-server.jar

*Note: Will listen on port 4567*

## Requirements (Docker)
- Docker
- [jdbc-rmi-server](https://github.com/Guergeiro/jdbc-rmi-server)

## Install (Docker)
- Navigate to folder
- config.config file with the following code inside
```
rmi-url=INSERT URL HERE
rmi-port=INSERT PORT HERE
```
- docker build -t rest-server .
- docker run -p 5000:4567 rest-server

*Note: Will listen on port 5000*

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Author
[Breno Salles](https://brenosalles.com)
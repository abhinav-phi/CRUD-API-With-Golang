# CRUD-API-With-Golang
# Movies API

A simple REST API built with Go for managing a movie collection. This API provides CRUD (Create, Read, Update, Delete) operations for movies with basic director information.

## Features

- Get all movies
- Get a specific movie by ID
- Create a new movie
- Update an existing movie
- Delete a movie
- In-memory storage (data persists only during runtime)

## Overview - Flowchart
![Image](https://github.com/user-attachments/assets/db22d220-2581-4bda-98c6-60c06e7f9133)

## Demo Video

Watch a screen recording demonstration of the API in action: (https://tinyurl.com/bvhtbyyk)

## Data Structure

### Movie
```json
{
  "id": "string",
  "isbn": "string", 
  "title": "string",
  "director": {
    "firstname": "string",
    "lastname": "string"
  }
}
```

## Prerequisites

- Go 1.16 or higher
- Gorilla Mux router

## Installation

1. Clone the repository
2. Install dependencies:
   ```bash
   go mod init movies-api
   go get github.com/gorilla/mux
   ```
3. Run the application:
   ```bash
   go run main.go
   ```

The server will start on port 8001.

## API Endpoints

### GET /movies
Returns all movies in the collection.

**Response:**
```json
[
  {
    "id": "1",
    "isbn": "438277",
    "title": "Movie one",
    "director": {
      "firstname": "Cristiano",
      "lastname": "Ronaldo"
    }
  }
]
```

### GET /movies/{id}
Returns a specific movie by ID.

**Parameters:**
- `id` (path parameter) - Movie ID

**Response:**
```json
{
  "id": "1", 
  "isbn": "438277",
  "title": "Movie one",
  "director": {
    "firstname": "Cristiano",
    "lastname": "Ronaldo"
  }
}
```

### POST /movies
Creates a new movie. The ID is automatically generated.

**Request Body:**
```json
{
  "isbn": "123456",
  "title": "New Movie",
  "director": {
    "firstname": "John",
    "lastname": "Doe"
  }
}
```

**Response:**
```json
{
  "id": "87654321",
  "isbn": "123456", 
  "title": "New Movie",
  "director": {
    "firstname": "John",
    "lastname": "Doe"
  }
}
```

### PUT /movies/{id}
Updates an existing movie by ID.

**Parameters:**
- `id` (path parameter) - Movie ID

**Request Body:**
```json
{
  "isbn": "654321",
  "title": "Updated Movie",
  "director": {
    "firstname": "Jane",
    "lastname": "Smith"
  }
}
```

### DELETE /movies/{id}
Deletes a movie by ID and returns the updated movie list.

**Parameters:**
- `id` (path parameter) - Movie ID

**Response:**
Returns the remaining movies after deletion.

## Sample Data

The API comes pre-loaded with two sample movies:
- Movie One (ID: 1) - Directed by Cristiano Ronaldo
- Movie Two (ID: 2) - Directed by David Goggins

## Testing

You can test the API using tools like:
- Postman
- curl
- Any HTTP client

### Example curl commands:

```bash
# Get all movies
curl http://localhost:8001/movies

# Get specific movie
curl http://localhost:8001/movies/1

# Create new movie
curl -X POST http://localhost:8001/movies \
  -H "Content-Type: application/json" \
  -d '{"isbn":"123456","title":"Test Movie","director":{"firstname":"Test","lastname":"Director"}}'

# Update movie
curl -X PUT http://localhost:8001/movies/1 \
  -H "Content-Type: application/json" \
  -d '{"isbn":"updated","title":"Updated Movie","director":{"firstname":"Updated","lastname":"Director"}}'

# Delete movie
curl -X DELETE http://localhost:8001/movies/1
```
## Project Structure

├── LICENSE

├── README.md

├── go.mod

├── go.sum

├── main.go

└── crudapi.exe (compiled binary)

## Future Enhancements

 Add database persistence (PostgreSQL/MongoDB)
 Implement input validation
 Add authentication and authorization
 Include unit tests
 Add logging middleware
 Implement pagination for movie lists
 Add search functionality

## Contributing

Fork the repository
Create a feature branch (git checkout -b feature/new-feature)
Commit your changes (git commit -am 'Add new feature')
Push to the branch (git push origin feature/new-feature)
Create a Pull Request

## Notes

This is a simple in-memory implementation - data will be lost when the server restarts
Movie IDs are generated randomly using rand.Intn(100000000)
The API uses JSON for all request/response bodies
No authentication or validation is implemented
The crudapi.exe is the compiled Windows executable

## License
This project is licensed under the MIT License - see the LICENSE file for details.


## Dependencies

- [Gorilla Mux](https://github.com/gorilla/mux) - HTTP router and URL matcher

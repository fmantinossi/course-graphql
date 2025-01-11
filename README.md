# Course GraphQL CLI

This repository contains a CLI application built with Go for studying GraphQL. The project is designed to provide hands-on experience with GraphQL queries, mutations, and resolvers while utilizing SQLite3 as the database for simplicity and ease of use.

## Features

- **GraphQL Queries:** Fetch data for `Course` and `Category` contexts.
- **GraphQL Mutations:** Modify and add data to the `Course` and `Category` contexts.
- **Resolvers:** Custom resolvers implemented for seamless query and mutation handling.
- **SQLite3 Integration:** Lightweight and simple database integration for storing `Course` and `Category` data.

## Project Structure

The project follows a modular structure for clarity and maintainability:

- **`cmd/server`**: Contains the entry point for starting the GraphQL server.
  - `server.go`: Initializes and runs the server.

- **`graph`**: Handles the GraphQL schema and resolver implementations.
  - `model`: Contains data models (`course.go`, `category.go`) and auto-generated GraphQL models (`models_gen.go`).
  - `schema.graphqls`: Defines the GraphQL schema.
  - `schema.resolvers.go`: Implements resolvers for the GraphQL schema.

- **`internal/database`**: Contains database-related logic.
  - `category.go`: Handles database operations for `Category`.
  - `course.go`: Handles database operations for `Course`.
  - `data.db`: SQLite3 database file.

## Prerequisites

Make sure you have the following installed on your system:

- **Go 1.20+**
- **SQLite3**

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/fmantinossi/course-graphql
   cd course-graphql
   ```

2. Install dependencies:

   ```bash
   go mod tidy
   ```

3. Run the application:

   ```bash
   go run cmd/server/server.go
   ```

The GraphQL server will start, and you can interact with it via https://localhost:8080.

## Example Usage

### Query Example

Fetch all courses and their associated categories:

```graphql
query {
  queryCourses {
    id
    title
  }
}

query {
  queryCategoriesWithCourses{
    categories{
      id
      name
      description
      courses{
        id
        name
      }
    }
  }
}
```

### Mutation Example

Add a new course:

```graphql
mutation {
  createCourse(input: {
    title: "GraphQL Basics",
    description: "Learn the basics of GraphQL.",
    categoryID: 1
  }) {
    id
    title
  }
}
```

## Future Improvements

- Add authentication and authorization.
- Expand the schema with additional contexts and relationships.
- Implement advanced filtering and pagination for queries.


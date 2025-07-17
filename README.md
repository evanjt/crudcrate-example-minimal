# Minimal CRUD API Example

This is a **complete CRUD API** implemented in just **56 lines of code** using crudcrate.

## What You Get

- ✅ Full CRUD operations (GET, POST, PUT, DELETE)
- ✅ OpenAPI documentation at `/docs`
- ✅ Sortable and filterable endpoints
- ✅ Auto-generated primary keys and timestamps
- ✅ SQLite in-memory database (no setup required)

## Run the Example

```bash
cargo run
```

Then visit:
- **API**: http://localhost:3000/todo
- **Documentation**: http://localhost:3000/docs

## Available Endpoints

- `GET /todo` - List all todos (with filtering & sorting)
- `GET /todo/{id}` - Get a specific todo
- `POST /todo` - Create a new todo
- `PUT /todo/{id}` - Update a todo
- `DELETE /todo/{id}` - Delete a todo
- `DELETE /todo/batch` - Delete multiple todos

## Test the API

### Create Multiple Todos

```bash
# Create first todo
curl http://localhost:3000/todo \
  --request POST \
  --header 'Content-Type: application/json' \
  --data '{
    "completed": false,
    "title": "Todo 1"
}'

# Create second todo
curl http://localhost:3000/todo \
  --request POST \
  --header 'Content-Type: application/json' \
  --data '{
    "completed": false,
    "title": "Todo 2"
}'

# Create third todo
curl http://localhost:3000/todo \
  --request POST \
  --header 'Content-Type: application/json' \
  --data '{
    "completed": false,
    "title": "Todo 3"
}'
```

### List All Todos

```bash
curl http://localhost:3000/todo
```

### Get a Specific Todo

```bash
# Replace {id} with an actual UUID from the list response
curl http://localhost:3000/todo/{id}
```

### Update a Todo

```bash
# Mark a todo as completed
curl http://localhost:3000/todo/{id} \
  --request PUT \
  --header 'Content-Type: application/json' \
  --data '{
    "title": "Updated Todo Title",
    "completed": true
}'
```

### Delete a Todo

```bash
# Delete a specific todo
curl http://localhost:3000/todo/{id} \
  --request DELETE
```

### Advanced Filtering and Sorting

```bash
# Filter completed todos
curl "http://localhost:3000/todo?filter=%7B%22completed%22%3Atrue%7D"

# Sort by title
curl "http://localhost:3000/todo?sort=%5B%22title%22%2C%22ASC%22%5D"

# Pagination
curl "http://localhost:3000/todo?range=%5B0%2C9%5D"
```

## The Code

The entire API is in [`src/main.rs`](src/main.rs) - just 56 lines including imports, entity definition, relations, and server setup.

This demonstrates crudcrate's ability to create production-ready APIs with minimal boilerplate while maintaining full flexibility for customization.

## More Examples & Documentation

- **[crudcrate](https://github.com/evanjt/crudcrate)** - Main crudcrate repository with comprehensive documentation
- **[crudcrate-example](https://github.com/evanjt/crudcrate-example)** - Full-featured example with migrations, and advanced patterns
- **[crudcrate on crates.io](https://crates.io/crates/crudcrate)** - Published package

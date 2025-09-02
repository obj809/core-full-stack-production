# Hello World endpoint
curl -i http://localhost/api/helloworld

# Get all todos
curl -i http://localhost/api/todo/

# Add a todo
curl -i -X POST http://localhost/api/todo/ \
  -H "Content-Type: application/json" \
  -d '{"title": "New task from curl"}'

# Fetch one by ID (e.g., id=1)
curl -i http://localhost/api/todo/1

# Update a todo
curl -i -X PUT http://localhost/api/todo/1 \
  -H "Content-Type: application/json" \
  -d '{"title": "Updated title"}'

# Delete a todo
curl -i -X DELETE http://localhost/api/todo/1

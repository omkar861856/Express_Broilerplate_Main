# Problem statement - 01/08/2024
"To-Do List" API.

Build a RESTful API for managing a to-do list using Node.js and Express. The API should allow users to create, retrieve, update, and delete to-do items.

Requirements:
Create a To-Do Item :
Endpoint: POST /todo
Request Body: { "title": "string", "completed": "boolean" }
Response: The newly created to-do item with a unique ID.
Retrieve All To-Do Items:
Endpoint: GET /todos
Response: An array of all to-do items.
Retrieve a Single To-Do Item by ID:
Endpoint: GET /todos/:id
Response: The to-do item with the specified ID.
Update a To-Do Item by ID:
Endpoint: PUT /todos/:id
Request Body: { "title": "string", "completed": "boolean" }
Response: The updated to-do item.
Delete a To-Do Item by ID:
Endpoint: DELETE /todos/:id
Response: A message indicating success or failure.


JSON Parsing: Using express.json() middleware to parse request bodies.
Error Handling: Providing meaningful error responses.


# To-Do List REST API

This is a simple REST API for managing a To-Do List, built with **PHP** and **Laravel**. The API provides CRUD operations for tasks, with data stored in a SQLite database. The project is designed to meet the requirements of a junior PHP developer test task.

## Features
- **CRUD Operations**:
  - Create a task: `POST /tasks`
  - List all tasks: `GET /tasks`
  - View a single task: `GET /tasks/{id}`
  - Update a task: `PUT /tasks/{id}`
  - Delete a task: `DELETE /tasks/{id}`
- Input validation for task fields (e.g., `title` is required).
- SQLite database for lightweight storage.
- Built with Laravel for routing, middleware, and Eloquent ORM.

## Requirements
- PHP >= 8.1
- Composer
- Laravel >= 10.x
- SQLite (or MySQL, configurable)

## Installation
1. **Clone the repository**:
   ```bash
   git clone https://github.com/BahaGit2002/test_task.git
   cd test_task
   ```

2. **Install dependencies**:
   ```bash
   composer install
   ```

3. **Set up environment**:
   - Copy the `.env.example` file to `.env`:
     ```bash
     cp .env.example .env
     ```
   - Configure the database connection in `.env` (SQLite is used by default):
     ```env
     DB_CONNECTION=sqlite
     DB_DATABASE=/absolute/path/to/database.sqlite
     ```
   - Create the SQLite database file:
     ```bash
     touch database/database.sqlite
     ```

4. **Run migrations**:
   ```bash
   php artisan migrate
   ```

5. **Generate application key**:
   ```bash
   php artisan key:generate
   ```

6. **Start the development server**:
   ```bash
   php artisan serve
   ```
   The API will be available at `http://localhost:8000`.

## API Endpoints
| Method | Endpoint          | Description                | Request Body (if applicable)                                          |
|--------|-------------------|----------------------------|-----------------------------------------------------------------------|
| POST   | `/tasks`          | Create a new task          | `{ "title": "string", "description": "string", "status": "boolean" }` |
| GET    | `/tasks`          | List all tasks             | -                                                                     |
| GET    | `/tasks/{id}`     | Get a specific task        | -                                                                     |
| PUT    | `/tasks/{id}`     | Update a task              | `{ "title": "string", "description": "string", "status": "boolean" }`  |
| DELETE | `/tasks/{id}`     | Delete a task              | -                                                                     |

### Example Request
**Create a Task**:
```bash
curl -X POST http://localhost:8000/api/tasks \
-H "Content-Type: application/json" \
-d '{"title":"Buy groceries","description":"Milk, eggs, bread","status": true}'
```

**Response**:
```json
{
  "id": 1,
  "title": "Buy groceries",
  "description": "Milk, eggs, bread",
  "status": true,
  "created_at": "2025-04-30T12:00:00.000000Z",
  "updated_at": "2025-04-30T12:00:00.000000Z"
}
```

## Validation
- `title`: Required, string, minimum 1 character.
- `description`: Optional, string.
- `status`: Optional, boolean (e.g., true, false).

Validation errors return a `422 Unprocessable Entity` response with details.

## Testing the API
You can test the API using tools like:
- **Postman** or **Insomnia** for manual testing.
- **cURL** for command-line testing.
- Laravel's built-in testing suite (run `php artisan test` if tests are included).

## Project Structure
```
test_task/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   └── TaskController.php  # API logic
│   │   ├── Requests/
│   │   │   └── TaskRequest.php    # Validation rules
│   ├── Models/
│   │   └── Task.php               # Eloquent model
├── database/
│   ├── migrations/
│   │   └── ..._create_tasks_table.php  # Database schema
│   └── database.sqlite            # SQLite database
├── routes/
│   └── api.php                    # API routes
├── .env                           # Environment configuration
└── README.md                      # This file
```

## Notes
- The project uses SQLite for simplicity, but you can switch to MySQL by updating the `.env` file and running migrations.
- Ensure the SQLite database file (`database.sqlite`) is writable by the application.
- The repository is hosted at: [https://github.com/BahaGit2002/test_task](https://github.com/BahaGit2002/test_task).

## Contributing
Feel free to submit issues or pull requests to the repository if you have suggestions or improvements.

## License
This project is open-source and available under the [MIT License](LICENSE).

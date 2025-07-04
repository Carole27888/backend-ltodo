# Todo Backend API

This is a backend API for managing todos and tasks, built with Node.js, Express, and MongoDB. It provides CRUD operations for todos and tasks, along with export functionality to Excel and PDF formats. The API also includes role-based access control and a reminder feature for upcoming tasks.

## Prerequisites

- [Node.js](https://nodejs.org/) (version 14 or higher recommended)
- [MongoDB](https://www.mongodb.com/) instance (local or cloud)
- npm (comes with Node.js)

## Installation

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd todo-backend
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Create a `.env` file in the root directory and add the following environment variables:

   ```env
   MONGO_URI=your_mongodb_connection_string
   DB_NAME=todoapp
   PORT=5000
   REMINDER_INTERVAL_MS=60000
   ```

   - `MONGO_URI` (required): Your MongoDB connection string.
   - `DB_NAME` (optional): Database name (default is `todoapp`).
   - `PORT` (optional): Port number for the server (default is 5000).
   - `REMINDER_INTERVAL_MS` (optional): Interval in milliseconds for task reminders (default is 60000 ms).

## Running the Project

- To start the server:

  ```bash
  npm start
  ```

- To start the server in development mode with auto-reloading:

  ```bash
  npm run dev
  ```

The server will be accessible at `http://localhost:5000.

## API Overview

The API provides the following endpoints:

### Todos (`/api/todos`)

- `POST /` - Create a new todo (requires role: admin or user)
- `GET /` - Get all todos
- `PUT /:id` - Update a todo by ID (requires role: admin or user)
- `PATCH /:id/complete` - Toggle completion status of a todo (requires role: admin or user)
- `DELETE /:id` - Delete a todo by ID (requires role: admin or user)
- `GET /export/excel` - Export todos to Excel (requires role: admin or user)
- `GET /export/pdf` - Export todos to PDF (requires role: admin or user)

### Tasks (`/api/tasks`)

- `POST /` - Create a new task (requires role: admin or user)
- `GET /` - Get all tasks
- `PUT /:id` - Update a task by ID (requires role: admin or user)
- `PATCH /:id/complete` - Toggle completion status of a task (requires role: admin or user)
- `DELETE /:id` - Delete a task by ID (requires role: admin or user)
- `GET /export/excel` - Export tasks to Excel
- `GET /export/pdf` - Export tasks to PDF

### Export (`/api/export`)

- `GET /tasks/pdf` - Export tasks to PDF (requires role: admin or user)
- `GET /tasks/excel` - Export tasks to Excel (requires role: admin or user)
- `GET /todos/pdf` - Export todos to PDF (requires role: admin or user)
- `GET /todos/excel` - Export todos to Excel (requires role: admin or user)

## Role-Based Access Control

Certain routes require the user to have roles `admin` or `user`. Ensure your requests include appropriate authentication and role information as required by the middleware.

## Reminder Feature

The server logs reminders for tasks that are due within the next 24 hours at intervals defined by `REMINDER_INTERVAL_MS` (default 1 minute).

## Additional Files

- `todos.csv`: A CSV file present in the project root, possibly used for data import/export.

## License

This project is licensed under the ISC License.

---

Feel free to contribute or raise issues for improvements.

# Todo Backend API

This is a backend API for managing todos and tasks, built with Node.js, Express, and MongoDB. It provides CRUD operations for todos and tasks, along with export functionality to Excel and PDF formats. The API also includes role-based access control and a reminder feature for upcoming tasks.

## Prerequisites

Before running this project, ensure you have the following installed on your machine:

- [Node.js](https://nodejs.org/) (version 14 or higher recommended)
- [npm](https://www.npmjs.com/get-npm) (comes with Node.js)
- [MongoDB](https://www.mongodb.com/) instance (local or cloud)

## Installation

Follow these steps to set up the project on your local machine:

1. **Clone the repository**

   Open your terminal and run:

   ```bash
   git clone <repository-url>
   cd todo-backend
   ```

2. **Install dependencies**

   Run the following command to install all required Node.js packages:

   ```bash
   npm install
   ```

3. **Set up environment variables**

   Create a `.env` file in the root directory of the project:

   ```bash
   touch .env
   ```

   Open the `.env` file in a text editor and add the following variables:

   ```env
   MONGO_URI=your_mongodb_connection_string
   DB_NAME=todoapp
   PORT=5000
   REMINDER_INTERVAL_MS=60000
   ```

   - Replace `your_mongodb_connection_string` with your actual MongoDB connection URI.
   - `DB_NAME` is optional; defaults to `todoapp` if not set.
   - `PORT` is optional; defaults to `5000`.
   - `REMINDER_INTERVAL_MS` is optional; sets the interval in milliseconds for task reminders (default is 60000 ms, i.e., 1 minute).

4. **Verify MongoDB connection**

   Ensure your MongoDB instance is running and accessible via the connection string you provided.

## Running the Project

- To start the server in production mode:

  ```bash
  npm start
  ```

- To start the server in development mode with automatic reload on file changes:

  ```bash
  npm run dev
  ```

The server will start and listen on the port specified in your `.env` file or default to `http://localhost:5000`.

## API Overview

The API provides endpoints for managing todos and tasks, including creation, retrieval, updating, deletion, and exporting data to Excel or PDF formats. Some routes require user roles (`admin` or `user`) for access.

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

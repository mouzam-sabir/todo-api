# To-Do API

A simple REST API built with Python and Flask for creating, viewing, and completing tasks.

## Features

- Create a task
- List all tasks
- Mark a task as completed
- Dockerized application
- GitHub Actions workflow for Docker image builds

## Tech Stack

- Python
- Flask
- Docker
- GitHub Actions

## Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/mouzam-sabir/todo-api.git
cd todo-api
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

On Windows, activate it with:

```powershell
.\venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the application

```bash
python app.py
```

The API will be available at:

`http://localhost:5000`

## Run with Docker

### Build the Docker image

```bash
docker build -t todo-api .
```

### Run the container

```bash
docker run -p 5000:5000 todo-api
```

The API will be available at:

`http://localhost:5000`

## API Endpoints

### 1. Create a Task

**POST** `/tasks`

Request body:

```json
{
  "title": "Learn Docker"
}
```

Example response:

```json
{
  "id": 1,
  "title": "Learn Docker",
  "done": false
}
```

### 2. List All Tasks

**GET** `/tasks`

Returns all tasks currently stored in memory.

Example response:

```json
[
  {
    "id": 1,
    "title": "Learn Docker",
    "done": false
  }
]
```

### 3. Mark a Task as Done

**PUT** `/tasks/<id>`

Example:

```text
PUT /tasks/1
```

Example response:

```json
{
  "id": 1,
  "title": "Learn Docker",
  "done": true
}
```

## Storage

The application uses in-memory storage instead of a database because a database was not required for this challenge.

Tasks are stored only while the application is running. They will be lost when the application stops.

## GitHub Actions

The project includes a GitHub Actions workflow:

`.github/workflows/docker-build.yml`

The workflow runs on every push to the repository and builds the Docker image to verify that the Docker setup works successfully.

## Reflection

The trickiest part of the challenge was containerizing the Flask application and making sure the API was accessible through the Docker port mapping.

I chose Flask because it is lightweight and simple for building a small REST API. I used in-memory storage because the challenge did not require a database, which kept the implementation simple and focused on the API and DevOps requirements.

If I had another day, I would add automated API tests, improve input validation and error handling, and use a database for persistent task storage. I would also extend the GitHub Actions workflow to run automated tests before building the Docker image.
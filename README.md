# Task Manager API

A REST API built with FastAPI and PostgreSQL that lets users manage their tasks. 
Users can register, log in, and perform CRUD operations on their own tasks. 
Authentication is handled using JWT tokens.

## Tech Stack

- Python
- FastAPI
- PostgreSQL
- SQLAlchemy
- JWT Authentication
- bcrypt password hashing

## Features

- User registration and login
- JWT-based authentication
- Create, read, update, and delete tasks
- Each user can only access their own tasks
- Pydantic validation on all inputs

## Project Structure
taskmanager/
├── app/
│   ├── main.py        # App entry point
│   ├── models.py      # Database models
│   ├── schemas.py     # Request/response shapes
│   ├── database.py    # DB connection
│   ├── auth.py        # JWT and password logic
│   └── routes.py      # API endpoints
└── .env               # Environment variables
## Setup

1. Clone the repo
2. Create a virtual environment and activate it
3. Install dependencies
```bash
pip install -r requirements.txt
```
4. Create a PostgreSQL database called `taskmanager`
5. Add a `.env` file with:
DATABASE_URL=postgresql://postgres:your_password@localhost:5432/taskmanager
SECRET_KEY=your_secret_key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
6. Run the server
```bash
uvicorn app.main:app --reload
```
7. Visit `http://127.0.0.1:8000/docs` to test the API

## API Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | /register | Create a new user | No |
| POST | /login | Login and get token | No |
| POST | /tasks | Create a task | Yes |
| GET | /tasks | Get all your tasks | Yes |
| GET | /tasks/{id} | Get a specific task | Yes |
| PUT | /tasks/{id} | Update a task | Yes |
| DELETE | /tasks/{id} | Delete a task | Yes |

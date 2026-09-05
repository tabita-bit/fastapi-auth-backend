# FastAPI Authentication Backend

A backend authentication API built with FastAPI, featuring user registration and login with JWT-based access tokens and bcrypt password hashing.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [API Endpoints](#api-endpoints)
- [Getting Started](#getting-started)
- [Known Limitations](#known-limitations)
- [Author](#author)

## Overview
This project implements a user authentication backend with FastAPI and SQLAlchemy. Users can register with an email and password, and log in to receive a JWT access token. Passwords are hashed with bcrypt before being stored, and the database is set up with Alembic for schema versioning. It was built as part of coursework to practice backend authentication flows, ORM models, and token-based auth.

## Features
- User registration with duplicate-email checking
- User login returning a JWT access token
- Passwords hashed with bcrypt (never stored in plain text)
- SQLite database via SQLAlchemy ORM
- Alembic configured for database migrations

## Tech Stack
| Category         | Technology              |
|-------------------|--------------------------|
| Framework         | FastAPI                 |
| ORM               | SQLAlchemy               |
| Database          | SQLite                  |
| Migrations        | Alembic                 |
| Auth              | JWT (python-jose)        |
| Password Hashing  | passlib (bcrypt)         |
| Language          | Python                  |

## Project Structure
```
Lab-5/
├── alembic/
│   ├── versions/
│   │   └── 86f573aa9332_create_users_table.py
│   ├── env.py
│   ├── script.py.mako
│   └── README
├── .gitignore
├── README.md        
├── alembic.ini        # Alembic configuration
├── auth.py            # Password hashing, JWT, register/login logic
├── database.py        # SQLAlchemy engine & session setup
├── main.py            # FastAPI app & routes
├── models.py          # SQLAlchemy User model
├── requirements.txt   # Python dependencies
└── schemas.py         # Pydantic schemas
```

## API Endpoints
| Method | Endpoint         | Description                          |
|--------|-------------------|----------------------------------------|
| POST   | `/auth/register`  | Register a new user (email + password) |
| POST   | `/auth/login`     | Log in and receive a JWT access token  |

## Getting Started

### Prerequisites
- Python 3.9+
- pip

### Installation
```bash
git clone https://github.com/tabita-bit/Lab-5.git
cd Lab-5
pip install -r requirements.txt
```

### Run the server
```bash
uvicorn main:app --reload
```
The API will be available at `http://127.0.0.1:8000`, with interactive docs at `http://127.0.0.1:8000/docs`.

## Known Limitations
- The JWT secret key is currently hardcoded in `auth.py` for simplicity, since this is a coursework lab. In a production setting, it should be loaded from an environment variable (e.g. via `python-dotenv`) instead.

## Author
Tabita Mali — [github.com/tabita-bit](https://github.com/tabita-bit)

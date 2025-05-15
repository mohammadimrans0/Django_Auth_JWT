# 📝 Django Auth API

A Django REST Framework-based Auth API with JWT authentication. Authenticated users can create, update, and delete their own posts, and all users can read posts.

---

## 🚀 Features

- JWT-based authentication
- User registration and login
- CRUD operations for posts
- Custom permissions (only post owners can update/delete)

---

## 🛠️ Tech Stack

- Python 3.x
- Django
- Django REST Framework
- Simple JWT
- SQLite (default, easily swappable)

---

## ⚙️ Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/mohammadimrans0/Django_Auth_JWT
cd Django_Auth_JWT
```

### 2. Create a Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # on Windows use: venv\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Apply Migrations
```bash
python manage.py migrate
```

### 5. Run the Development Server
```bash
python manage.py runserver
```

API will be available at: `http://localhost:8000/`

---

## 🔐 Authentication

This project uses JWT (JSON Web Tokens).


**Headers for Authenticated Requests:**
```http
Authorization: Bearer <your_access_token>
```

---

## 📬 API Endpoints

### 🔑 Auth

| Method | Endpoint                                | Description                  | Auth Required 
|--------|-----------------------------------------|------------------------------|--------------
| POST   | `http://localhost:8000/users/register/` | Register a new user          | ❌            
| POST   | `http://localhost:8000/users/login/`    | Get JWT tokens (login)       | ❌            
| GET    | `http://localhost:8000/users/profile/`  | Get current user's profile   | ✅            


---

### 📝 Posts

| Method | Endpoint                               | Description                           | Auth Required 
|--------| ------------------                     | -----------------------------------   | -------------
| CREATE | `http://localhost:8000/post/posts/`    | CREATE a post (must be authenticated) |    ✅     
| GET    | `http://localhost:8000/post/posts/`    | Get all posts                         |    ❌     
| GET    | `http://localhost:8000/post/posts/1/`  | Get a single post                     |    ❌     
| PUT    | `http://localhost:8000/post/posts/1/`  | Update a post (must be owner)         |    ✅     
| PATCH  | `http://localhost:8000/post/posts/1/`  | Partially update a post (owner only)  |    ✅     
| DELETE | `http://localhost:8000/post/posts/1/`  | Delete a post (must be owner)         |    ✅     

---

## ✅ Notes

- You can modify token expiration in `settings.py` under `SIMPLE_JWT`.
- Feel free to swap SQLite with PostgreSQL or another DB engine.
- Make sure to configure `.env` or secret keys for production.

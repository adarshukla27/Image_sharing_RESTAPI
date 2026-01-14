# Image Sharing REST API 🚀

A secure, scalable **Image & Video Sharing REST API** built using **FastAPI**, **FastAPI Users**, **SQLAlchemy (Async)**, and **ImageKit** for cloud media storage.  
This backend service supports **JWT-based authentication**, **user management**, **media uploads**, and a **social media–style feed system**.


## 📌 Features

- 🔐 JWT Authentication & Authorization  
- 👤 User Registration, Login, Verification & Password Reset  
- 🖼️ Image & Video Upload Support  
- ☁️ Cloud Media Storage via ImageKit  
- 📝 Post Feed with Ownership Detection  
- 🗑️ Secure Post Deletion (Owner Only)  
- ⚡ Asynchronous Database Operations  
- 🧱 Clean, Modular Project Structure  


## 🛠 Tech Stack

| Layer | Technology |
|------|-----------|
| Backend Framework | FastAPI |
| Authentication | FastAPI Users (JWT) |
| Database | SQLite (Async) |
| ORM | SQLAlchemy (Async) |
| Media Storage | ImageKit |
| Environment Config | python-dotenv |
| Server | Uvicorn |
| Language | Python 3.12+ |


## 📂 Project Structure
```
image_sharing_project/
│
├── app/
│ ├── app.py # Main FastAPI application
│ ├── db.py # Database models & session
│ ├── users.py # Authentication & user management
│ ├── images.py # ImageKit configuration
│ ├── schemas.py # Pydantic schemas
│
├── main.py # Application entry point
├── pyproject.toml # Dependencies & project metadata
├── .env # Environment variables (ignored)
├── .gitignore
└── README.md
```


## ⚙️ Environment Variables

Create a `.env` file in the project root:

```env
IMAGEKIT_PUBLIC_KEY=your_public_key
IMAGEKIT_PRIVATE_KEY=your_private_key
IMAGEKIT_URL_ENDPOINT=https://ik.imagekit.io/your_id
JWT_SECRET_KEY=your_jwt_secret
```
⚠️ Do not commit .env files to version control.


## 📦 Installation & Setup
**⚒️ Clone the Repository**
```
git clone https://github.com/your-username/image-sharing-project.git
cd image-sharing-project
```

**✅ Recommended: Using `uv`**

This project uses `uv` for fast, reliable, and reproducible dependency management.
```
uv sync
```

What this does:

Reads `pyproject.toml`

Uses `uv.lock` for exact dependency versions

Automatically creates and manages `.venv`
Prevents “works on my machine” issues

---

**🔁 Alternative: Using pip**

If you prefer `pip`, you can still run the project:
```
pip install -r requirements.txt
```

**⚠️ Note:** `pip` does not use the `uv.lock` file, so dependency versions may vary across systems.
For best reproducibility, `uv` is strongly recommended.


## ▶️ Running the Application
```
uv run main.py
```

The API will be available at → `http://localhost:8000`

Interactive API documentation:

Swagger UI → `http://localhost:8000/docs`

ReDoc → `http://localhost:8000/redoc`


## 🔐 Authentication Flow

This project uses JWT Bearer Authentication:

Register → `/auth/register`

Login → `/auth/jwt/login`

Use the access token in request headers:
```
Authorization: Bearer <token>
```


## 📡 API Endpoints Overview

**🔑 Authentication**
| Method |	Endpoint |	Description |
|------|-----------|-------------|
| POST |	`/auth/register` |	Register user |
| POST |	`/auth/jwt/login` |	Login user |
| POST |	`/auth/forgot-password` |	Reset password |
| POST |	`/auth/verify` |	Verify user email |

---

**🖼️ Posts & Media**
| Method |	Endpoint |	Description |
|------|-----------|-------------|
| POST |	`/upload` |	Upload image or video |
| GET |	`/feed` |	Fetch all posts |
| DELETE |	`/posts/{post_id}` |	Delete own post |


## 🧠 Core Design Decisions

- Async SQLAlchemy ensures non-blocking database operations

- ImageKit offloads heavy media storage from backend

- FastAPI Users provides secure and extensible authentication

- Ownership checks prevent unauthorized deletions

- Temporary file handling ensures safe uploads


## 🔒 Security Considerations

- JWT tokens expire after 1 hour

- Only resource owners can delete posts

- Secrets managed via environment variables
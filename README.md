# Project Management Platform (Backend)

A robust, RESTful API designed for collaborative project management, featuring multi-tier permissions and a hierarchical task engine.

## 🚀 Features
* [cite_start]**Secure Authentication**: Implements JWT with Access and Refresh Token rotation, email verification, and password reset flows[cite: 14, 17].
* [cite_start]**Role-Based Access Control (RBAC)**: Three-tier permission system for Admins, Project Admins, and Members to manage project visibility and actions.
* [cite_start]**Task Lifecycle Management**: Tracks projects through a Projects > Tasks > Subtasks hierarchy with status tracking (Todo, In Progress, Done).
* [cite_start]**Modular Architecture**: Built with a clean separation of concerns using Controllers, Routes, and specialized Middlewares.
* [cite_start]**Validation & Security**: Centralized error handling and input validation using Express-Validator.

## 🛠️ Tech Stack
* **Backend**: Node.js, Express.js (v5.1.0)
* **Database**: MongoDB & Mongoose
* **Security**: JSON Web Tokens (JWT), Bcrypt, Crypto
* **Communication**: Nodemailer & Mailgen for automated email workflows

## ⚙️ Setup Instructions
1. Clone the repository: `git clone <your-repo-url>`
2. Install dependencies: `npm install`
3. Create a `.env` file based on `.env.example` and add your MongoDB URI and JWT secrets.
4. Start the server: `npm run dev` (uses Nodemon) or `npm start`.

## 📂 API Endpoints
* `POST /api/v1/auth/register` - User registration with email verification.
* `POST /api/v1/projects` - Create a new project (Admin only).
* `GET /api/v1/tasks/:projectId` - Fetch all tasks for a specific project.

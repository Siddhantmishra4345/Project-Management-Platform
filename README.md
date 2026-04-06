Project Management Platform (Backend)
Overview
This project is a robust, RESTful API designed to power collaborative project management applications. It implements a Role-Based Access Control (RBAC) system and a hierarchical data model to manage the lifecycle of projects, tasks, and team collaborations.

Unlike a simple CRUD app, this platform simulates a professional enterprise environment where permissions are strictly enforced based on user roles (Admin, Project Admin, Member), and task progress is tracked through subtask completion and status transitions.

Tech Stack
Backend

Runtime: Node.js (ES Modules) 

Framework: Express.js (v5.1.0) 

Database: MongoDB with Mongoose ODM 

Security: JWT (Access & Refresh Token rotation), Bcrypt, Express-Validator 

Communication: Nodemailer & Mailgen (SMTP integration) 

Core Features
1. Advanced Authentication & Security

Secure Onboarding: User registration with mandatory email verification tokens.

Token Management: Implements JWT-based authentication with a sliding session window using refresh tokens.

Account Recovery: Secure password reset flows with expiry-limited tokens.

2. Multi-Tier Permission System (RBAC)

The system enforces a strict permission matrix:

Admin: Full control over project creation, member roles, and global settings.

Project Admin: Can manage tasks, subtasks, and project-specific content.

Member: View access and the ability to update assigned subtask statuses.

3. Hierarchical Task Engine

Data Structure: Projects → Tasks → Subtasks.

Lifecycle Tracking: Tasks move through TODO, IN_PROGRESS, and DONE states.

Subtask Dependency: Allows members to mark individual subtasks as complete, contributing to the overall task progress.

4. Collaboration Tools

Member Management: Admins can invite users to projects via email and dynamically update their roles.

Project Notes: Centralized repository for project-wide documentation, restricted to Admin-only creation.

File Attachments: Support for multiple file uploads on tasks with metadata tracking (MIME type, size, and storage URL).

Architecture
The project follows a Modular Layered Architecture:

Routes → Middlewares (Auth/Validation) → Controllers → Models (Mongoose Schemas).

Caching & Performance
Input Validation: Centralized validation layer using express-validator to prevent NoSQL injection and malformed data.

Error Handling: Global asynchronous error-handling middleware for consistent API responses.

Time & Space Complexity
Authentication/Login: O(1) (Constant time hash comparison)

Project/Task Retrieval: O(n) where n is the number of associated members or tasks.

Role Validation: O(1) via middleware check.

Design Trade-offs
Modular vs. Monolithic: Used a modular folder structure. While it adds more files, it ensures the code is maintainable as the project scales.

NoSQL (MongoDB): Chosen over SQL for flexibility in task metadata and subtask nesting, allowing for rapid schema evolution.

JWT over Sessions: Used stateless JWTs to ensure the backend can scale horizontally without requiring sticky sessions.

Failure Handling
Centralized Error Handler: Catches all operational errors and returns standardized JSON.

Validation Errors: Returns 400 Bad Request with a detailed list of field-specific issues.

SMTP Fallback: Handled through Nodemailer error events for failed verification emails.

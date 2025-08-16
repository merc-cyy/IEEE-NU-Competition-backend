# Backend System for IEEE Northwestern Competition 2025

## Background
My team and I won the annual Institute of Electrical and Electronic Engineers invite-only competition held in Northwestern, Chicago.

Many students found it hard to find places to volunteer around Evanston, our local town, and especially places that matched their interests.
So my team and I built NUVolunteers.org, an application that uses ML models to match students to volunteer opportunities that match their user profile and interests.

This is the backend service of the system.

## Languages/Tools/Frameworks
- PostgreSQL
- Supabase
- RESTful APIs
- Express.js
- CORS
- Nodemon
- JWT Tokens

## Visual Diagram
          ┌────────────────────────┐
          │        Client          │
          │  (Frontend / React)    │
          └─────────┬─────────────┘
                    │ HTTP Requests (JSON)
                    ▼
          ┌────────────────────────┐
          │      file1: index.js   │
          │  Express.js REST API   │
          │ - Routes: /auth, /users, /posts, /interests
          │ - Middleware: CORS, JSON
          │ - Supabase queries     │
          └─────────┬─────────────┘
                    |
        ┌───────────┴───────────┐
        │                       │
        ▼                       ▼
┌───────────────┐       ┌─────────────────┐
│ file3:        │       │ file2: db.js    │
│ supabaseClient│       │ PostgreSQL Pool │
│ - Supabase JS │       │ - Connection    │
│   SDK         │       │   pooling       │
│ - .from()     │       │ - SSL enabled   │
│   queries     │       │ - Env-based URL │
└───────────────┘       └─────────────────┘
        │                       │
        ▼                       ▼
  Supabase Database         PostgreSQL Database
  - Real-time API           - Relational tables
  - Authentication          - Transactions & joins
  - Row-level security



## Routing and Requests
- Used Express.js (v4.18) as a Lightweight, modular server framework for building RESTful APIs.
- Configured CORS (cross-origin-routing-service) to allow cross-origin requests for front-end integration.
- Parsed incoming JSON requests using Object Relational Mapping for API endpoints.

## Database & Storage
- The main database was PostgreSQL; a relational database with connection pooling for high concurrency.
- Integrated the database using Supabase; a real-time database and authentication backend, providing RESTful API endpoints and secure client access.
- Configured environment-based variables like: dotenv for managing secrets (DATABASE_URL, SUPABASE_URL, SUPABASE_KEY).

## Authentication & User Management
- Isolated auth Routes (/auth) as a dedicated module for user authentication and verification.
- Leveraged Supabase Auth SDK for secure user session handling, JWT-based authentication, and role-based access control.

## Development & Tooling
- Nodemon was used as a development server with live reload.
- ES Modules ("type": "module"): Modern JavaScript module system.
- NPM Package Management (npm) with precise dependency control.

## Industry Patterns
- Modular Routing: Each domain (users, posts, interests, auth) is encapsulated in its own route module.
- Database Abstraction Layer: used clients to isolate PostgreSQL and Supabase queries for reusability.
- Environment Separation: Sensitive keys and connection strings are fully configurable via .env.
- Asynchronous Programming: All database queries use async/await with proper error handling.

## Example Endpoints
- GET /auth/test → Health check for authentication routes.
- GET /api/test-supabase → Verifies Supabase connection and retrieves sample user.
- POST /users, GET /users → User CRUD operations.
- POST /posts, GET /posts → Volunteer opportunity management.
- POST /interests, GET /interests → User interest management and linking to opportunities.


### Run the server
  ```bash
  node index.js
  ```
### Our application
https://nuvolunteers.org/

## Authors
- **Mercy Muiruri**
- **Emran Majidy**


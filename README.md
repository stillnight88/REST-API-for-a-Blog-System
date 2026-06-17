# Dockerized Blog API

A backend-only blog API built with Node.js, Express, and MongoDB.

This project was created to explore Docker containerization and deployment workflows. The blog system serves as a practical application for learning how to package, configure, and deploy a Node.js API using Docker and Render.

---

## Project Context

The primary focus of this repository was learning:

* Docker fundamentals
* Containerizing Node.js applications
* Environment variable management
* Cloud deployment using Render
* REST API development with Express
* JWT-based authentication

The blog functionality exists as a sample application used to practice these deployment concepts.

---

## Features

### Authentication

* User registration
* User login
* JWT-based authentication
* Password hashing with bcrypt
* Protected routes

### Blog Posts

* Create posts
* Retrieve posts
* Update posts
* Delete posts
* Author ownership validation

### Security

* JWT authentication middleware
* Password hashing
* Route protection
* Basic request validation

---

## Tech Stack

### Backend

* Node.js
* Express.js

### Database

* MongoDB
* Mongoose

### Authentication

* JSON Web Tokens (JWT)
* bcrypt

### Infrastructure

* Docker
* Render

---

## Project Structure

```text
controllers/    Request handling logic
middleware/     Authentication and authorization
models/         MongoDB schemas
routes/         API routes
utils/          Validation and helper functions
views/          Server-rendered templates
public/         Static assets
app.js          Application entry point
Dockerfile      Docker configuration
```

---

## Installation

### Prerequisites

* Node.js
* MongoDB Atlas account or local MongoDB instance
* Docker (optional)

### Clone the Repository

```bash
git clone <repository-url>
cd dockerized-blog-api
```

### Install Dependencies

```bash
npm install
```

### Create Environment Variables

Create a `.env` file in the project root:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
JWT_EXPIRES_IN=1d
```

### Start the Application

```bash
npm start
```

The server will be available at:

```text
http://localhost:5000
```

---

## Docker Usage

Build the Docker image:

```bash
docker build -t blog-api .
```

Run the container:

```bash
docker run -p 5000:5000 blog-api
```

---

## Deployment Notes

This project was deployed to Render using Docker as part of the learning process.

The deployment may not always be available due to inactive free-tier services or suspended deployments.

---

## Limitations

This repository reflects an early learning project and is intentionally simple.

Current limitations include:

* No automated test suite
* No API documentation (Swagger/OpenAPI)
* No rate limiting
* No refresh token implementation
* No CI/CD pipeline
* Limited validation compared to production-grade systems

---

## Repository Status

This repository is preserved as a learning project demonstrating:

* Express API development
* MongoDB integration
* JWT authentication
* Docker containerization
* Basic cloud deployment workflows

The project is not actively maintained and primarily serves as a reference for the concepts explored during development.

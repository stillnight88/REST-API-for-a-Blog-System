# REST API for a Blog System

A full-featured RESTful API for a blog system built with Node.js, Express, and MongoDB. This project was created as a learning exercise to understand Docker containerization and deployment workflows on Render.

## 🎯 Project Purpose

This project was primarily built to learn and practice:
- Docker containerization
- Backend deployment using Docker
- Cloud deployment on Render
- RESTful API design patterns
- Authentication and authorization workflows

## 🚀 Live Demo

**Note:** The deployment link is currently suspended.
- **URL:** https://rest-api-for-a-blog-system.onrender.com

## 🛠️ Tech Stack

- **Runtime:** Node.js 18
- **Framework:** Express.js 5
- **Database:** MongoDB (MongoDB Atlas)
- **Authentication:** JWT (JSON Web Tokens)
- **Password Hashing:** bcrypt
- **Validation:** validator.js
- **Containerization:** Docker
- **Deployment:** Render

## 📋 Features

### Authentication
- User registration with validation
- Secure login with JWT tokens
- Password hashing with bcrypt
- Token-based authentication middleware

### Blog Posts
- Create, read, update, and delete posts (CRUD operations)
- Post ownership validation
- Pagination support for listing posts
- Author information populated with posts

### Security
- JWT-based authentication
- Protected routes
- Ownership verification for post modifications
- Input validation

## 📁 Project Structure

```
├── controllers/
│   ├── authController.js       # Authentication logic
│   └── postController.js       # Blog post operations
├── middleware/
│   ├── authMiddleware.js       # JWT verification
│   └── ownershipMiddleware.js  # Post ownership checks
├── models/
│   ├── User.js                 # User schema
│   └── Post.js                 # Post schema
├── routes/
│   ├── authRoutes.js           # Auth endpoints
│   ├── postRoutes.js           # Post endpoints
│   └── healthRoutes.js         # Health check
├── utils/
│   ├── validateUser.js         # User input validation
│   └── validatePost.js         # Post input validation
├── views/                      # EJS templates
├── public/                     # Static files
├── app.js                      # Application entry point
├── Dockerfile                  # Docker configuration
└── package.json
```

## 🐳 Docker Setup

### Dockerfile

```dockerfile
# Use official Node.js 18 image
FROM node:18

# Set working directory inside container
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy all remaining source code
COPY . .

# Expose app port
EXPOSE 5000

# Start the app
CMD ["npm", "start"]
```

### Building and Running with Docker

```bash
# Build the Docker image
docker build -t blog-api .

# Run the container
docker run -p 5000:5000 blog-api
```

## 🔧 Local Setup

### Prerequisites
- Node.js (v18 or higher)
- MongoDB Atlas account or local MongoDB instance
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/stillnight88/REST-API-for-a-Blog-System.git
   cd rest-api-for-a-blog-system
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   
   Create a `.env` file in the root directory:
   ```env
   PORT=5000
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret_key
   JWT_EXPIRES_IN=1d
   ```

4. **Start the application**
   ```bash
   npm start
   ```

The API will be running at `http://localhost:5000`

## 📡 API Endpoints

### Authentication

#### Register User
```http
POST /auth/signup
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+1234567890",
  "password": "password123"
}
```

#### Login
```http
POST /auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "password123"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Login successful",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "user_id",
    "name": "John Doe",
    "email": "john@example.com"
  }
}
```

### Blog Posts

#### Get All Posts
```http
GET /api/post?page=1&limit=10&sort=-createdAt
```

#### Get Post by ID
```http
GET /api/post/:id
```

#### Create Post (Protected)
```http
POST /api/posts
Authorization: Bearer <token>
Content-Type: application/json

{
  "title": "My Blog Post",
  "content": "This is the content of my blog post..."
}
```

#### Update Post (Protected)
```http
PUT /api/posts/:id
Authorization: Bearer <token>
Content-Type: application/json

{
  "title": "Updated Title",
  "content": "Updated content..."
}
```

#### Delete Post (Protected)
```http
DELETE /api/posts/:id
Authorization: Bearer <token>
```

### Health Check
```http
GET /health
```

## 🔐 Authentication

Protected routes require a JWT token in the Authorization header:

```
Authorization: Bearer your_jwt_token_here
```

## 📊 Database Models

### User Model
- `name`: String (required, 2-25 characters)
- `email`: String (required, unique, validated)
- `phone`: String (required, unique, validated)
- `password`: String (required, min 6 characters, hashed)
- `createdAt`: Date (auto-generated)

### Post Model
- `title`: String (required, max 25 characters)
- `content`: String (required)
- `author`: ObjectId (reference to User)
- `createdAt`: Date (auto-generated)
- `updatedAt`: Date (auto-generated)

## 🚀 Deployment on Render

This project is deployed on Render using Docker:

1. Push your code to GitHub
2. Connect your repository to Render
3. Select "Docker" as the environment
4. Configure environment variables in Render dashboard
5. Deploy

Render automatically builds the Docker image and deploys the container.

## 🎓 Learning Outcomes

Through this project, I learned:
- How to containerize a Node.js application with Docker
- Writing efficient Dockerfiles
- Deploying containerized applications to cloud platforms
- Managing environment variables in production
- Best practices for REST API design
- JWT-based authentication implementation
- MongoDB integration and schema design

## 🔮 Future Improvements

Potential enhancements (may or may not be implemented):
- Add comments functionality
- Implement post categories and tags
- Add image upload for posts
- Implement search functionality
- Add rate limiting
- Implement refresh tokens
- Add email verification
- Create comprehensive API documentation (Swagger/OpenAPI)
- Add unit and integration tests
- Implement caching with Redis

## 📝 License

This project is open source and available for learning purposes.

## 🤝 Contributing

This is a learning project, but feel free to fork and experiment with it!

## ⚠️ Notes

- This project was created for learning Docker deployment
- Some features may be basic as the focus was on deployment
- The live demo may be suspended due to Render's free tier limitations

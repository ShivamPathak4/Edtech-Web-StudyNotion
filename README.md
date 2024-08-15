# **Study Notion**

A comprehensive web application designed to provide news and updates within a specific district, featuring admin-controlled content management, user authentication, and a responsive user interface.

## **Table of Contents**

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Admin Authentication](#admin-authentication)
- [Environment Variables](#environment-variables)
- [Project Structure](#project-structure)
- [Contributing](#contributing)

## **Overview**

This project is designed to be a scalable, secure, and user-friendly platform that allows users to access district-specific news, updates, and advertisements. The platform is managed by admins, who have exclusive access to create, update, and delete content. The application incorporates authentication and authorization mechanisms to ensure that only authorized personnel can modify content.

## **Features**

- **User Authentication & Authorization:**
  - Secure login and registration system using JWT (JSON Web Tokens).
  - Role-based access control (RBAC) to differentiate between users and admins.

- **Admin Panel:**
  - Admins can manage news, updates, and advertisements.
  - Only admins can post, edit, or delete content, ensuring content integrity.

- **Responsive Design:**
  - The application is mobile-first, ensuring it works seamlessly on all devices.
  - The UI is optimized for both dark and light themes.

- **Dynamic Content Management:**
  - Real-time updates for news and advertisements.
  - Integrated with a rich text editor for content creation.

- **Security:**
  - Encrypted passwords using bcrypt.
  - Secure API routes protected by JWT middleware.

- **Performance Optimizations:**
  - Lazy loading for images and other resources.
  - Efficient database queries to minimize load times.

## **Tech Stack**

- **Frontend:**
  - **React.js:** For building a dynamic and interactive user interface.
  - **Tailwind CSS:** For styling and responsive design.
  - **Axios:** For handling HTTP requests to the backend.

- **Backend:**
  - **Node.js & Express:** For handling server-side logic and API routes.
  - **MongoDB & Mongoose:** For database management and object modeling.
  - **JWT:** For handling authentication and securing API endpoints.

- **DevOps:**
  - **Docker:** For containerizing the application and simplifying deployment.
  - **NGINX:** For serving the frontend and reverse proxying requests to the backend.

## **Architecture**

The application follows a typical MERN (MongoDB, Express, React, Node.js) architecture:

1. **Client-Side:**
   - The React frontend interacts with the backend via RESTful APIs.
   - The UI components are modular and reusable, ensuring scalability and maintainability.

2. **Server-Side:**
   - The Express server handles API requests, processes data, and interacts with the MongoDB database.
   - Authentication middleware secures routes, ensuring that only authorized users can access certain endpoints.

3. **Database:**
   - MongoDB serves as the primary database, storing user information, news posts, advertisements, and admin credentials.
   - Mongoose models and schemas are used to enforce data structure and integrity.

## **Prerequisites**

Before you begin, ensure you have met the following requirements:

- **Node.js** (v14.x.x or later)
- **MongoDB** (v4.x.x or later)
- **npm** (v6.x.x or later)
- **Docker** (Optional for containerized deployment)

## **Installation**

Follow these steps to set up the project locally:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/your-repo.git
   ```
2. **Navigate to the project directory:**
   ```bash
   cd your-repo
   ```
3. **Install dependencies:**
   ```bash
   npm install
   ```
4. **Set up MongoDB:**
   - Ensure MongoDB is running on your local machine or a remote server.
   - You can also use Docker to set up MongoDB:
     ```bash
     docker run -d -p 27017:27017 --name mongodb mongo
     ```

5. **Configure environment variables:**
   - Create a `.env` file in the root directory with the following variables:

     ```env
     MONGO_URI=mongodb://localhost:27017/your-database
     JWT_SECRET=your_jwt_secret
     ADMIN_EMAIL=admin@example.com
     ADMIN_PASSWORD=admin123
     ```

6. **Run the development server:**
   ```bash
   npm run dev
   ```

## **Usage**

### **Starting the Application**

1. **Frontend:**
   - The frontend is served from `http://localhost:3000`.
   - You can access the user-facing site and explore the news and updates.

2. **Backend:**
   - The backend server is running on `http://localhost:5000`.
   - All API endpoints are prefixed with `/api`.

### **Accessing the Admin Panel**

1. Navigate to `http://localhost:3000/admin`.
2. Enter the admin credentials (email and password) as set in the `.env` file.
3. Once authenticated, you can manage all the content on the platform.

### **Creating and Managing Content**

- **News/Updates:**
  - Admins can post new articles, edit existing ones, or delete them.
  - Articles support rich text formatting, images, and videos.

- **Advertisements:**
  - Only admins can manage advertisements. This includes uploading media, setting display durations, and targeting specific audiences.

## **Admin Authentication**

### **Authentication Process**

- **Registration:**
  - Users register with their email and password. Admins can only be created manually or through a predefined process.
  
- **Login:**
  - Both users and admins log in using their email and password.
  - Upon successful login, a JWT token is generated and stored in the user's browser.

- **Authorization:**
  - JWT tokens are verified on every request to protected routes.
  - Admin routes are further secured by role checks, ensuring only admins can access them.

### **Security Considerations**

- **Password Encryption:**
  - Passwords are hashed using bcrypt before being stored in the database.
  
- **Token Expiry:**
  - JWT tokens have an expiry time, ensuring users need to re-authenticate after a certain period.

## **Environment Variables**

The following environment variables are essential for running the application:

- **`MONGO_URI`**: MongoDB connection string.
- **`JWT_SECRET`**: Secret key for signing JWT tokens.
- **`ADMIN_EMAIL`**: Default admin email for logging in.
- **`ADMIN_PASSWORD`**: Default admin password.

Example `.env` file:
```env
MONGO_URI=mongodb://localhost:27017/your-database
JWT_SECRET=your_jwt_secret
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=admin123
```

## **Project Structure**

```plaintext
.
├── backend
│   ├── config        # Configuration files, including database connection
│   ├── controllers   # Logic for handling requests and responses
│   ├── models        # Mongoose models and schemas
│   ├── routes        # API route definitions
│   └── utils         # Utility functions and middleware
├── frontend
│   ├── public        # Public assets (e.g., images, fonts)
│   ├── src
│   │   ├── components  # Reusable UI components
│   │   ├── pages       # Main pages (e.g., Home, Admin)
│   │   ├── services    # API service functions
│   │   └── styles      # Global and component-specific styles
├── .env              # Environment configuration file
├── package.json      # npm dependencies and scripts
├── README.md         # Project documentation
└── ...
```

## **Contributing**

We welcome contributions to this project! To contribute:

1. **Fork the repository:**
   - Click the "Fork" button at the top-right of the repository page.
2. **Clone your fork:**
   ```bash
   git clone https://github.com/your-username/your-repo.git
   ```
3. **Create a new branch:**
   ```bash
   git checkout -b feature/your-feature-name
   ```
4. **Make your changes and commit them:**
   ```bash
   git commit -m "Add your descriptive commit message"
   ```
5. **Push to your fork:**
   ```bash
   git push origin feature/your-feature-name
   ```
6. **Submit a Pull Request:**
   - Go to the original repository and create a pull request from your fork.



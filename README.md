# 🛒 BuzzBuy - Full-Stack E-Commerce Application

![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Node](https://img.shields.io/badge/Node.js-18.x-339933?style=flat&logo=node.js&logoColor=white)
![React](https://img.shields.io/badge/React-18.2-61DAFB?style=flat&logo=react&logoColor=black)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-47A248?style=flat&logo=mongodb&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-Backend-000000?style=flat&logo=express&logoColor=white)
![Render](https://img.shields.io/badge/Deployed%20on-Render-46E3B7?style=flat&logo=render&logoColor=white)

A modern, full-featured e-commerce platform built with the MERN stack (MongoDB, Express, React, Node.js). BuzzBuy provides a seamless shopping experience with secure payments, product reviews, and comprehensive admin tools for managing products, users, and orders.

## 📋 Table of Contents
- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Environment Variables](#environment-variables)
- [Available Scripts](#available-scripts)
- [API Endpoints](#api-endpoints)
- [Architecture](#architecture)
- [Contributing](#contributing)
- [Contact & Support](#contact--support)

---

## 🎯 Overview

BuzzBuy is a complete e-commerce solution designed for modern online retail. It combines a responsive React frontend with a robust Node.js/Express backend, MongoDB database, and PayPal payment integration. The application supports both customer and admin workflows, providing a comprehensive platform for buying and selling products online.

---

## 🛠️ Tech Stack

### **Frontend**
- **Framework**: React 18.2
- **State Management**: Redux Toolkit & React-Redux
- **Routing**: React Router v6
- **UI Framework**: Bootstrap 5 & React-Bootstrap
- **HTTP Client**: Axios
- **Payment**: PayPal React SDK
- **Additional**: React Helmet (SEO), React Toastify (notifications), React Icons

### **Backend**
- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT (JSON Web Tokens)
- **Password Security**: bcryptjs
- **File Upload**: Multer
- **Environment**: dotenv
- **Development**: Nodemon, Concurrently

### **Database**
- MongoDB (NoSQL)
- Mongoose for schema and validation

---

## ✨ Features

### **Customer Features**
- ✅ **User Authentication**: Secure signup and login with JWT tokens
- ✅ **Product Catalog**: Browse products with pagination, search, and filtering
- ✅ **Shopping Cart**: Add/remove items with persistent storage
- ✅ **Reviews & Ratings**: Leave product reviews with star ratings
- ✅ **Order Management**: View order history and order details
- ✅ **Secure Checkout**: Multi-step checkout process with shipping and billing
- ✅ **Payment Processing**: PayPal integration for secure payments
- ✅ **Responsive Design**: Mobile-friendly UI with Bootstrap

### **Admin Features**
- 🔐 **Admin Dashboard**: Dedicated admin interface
- 📦 **Product Management**: Create, edit, and delete products with image uploads
- 👥 **User Management**: View and manage user accounts and permissions
- 📊 **Order Management**: View all orders and update order status
- 📈 **Data Analytics**: Track orders and user activity
- 🌱 **Database Seeding**: Pre-populate database with sample data

---

## 📁 Project Structure

```
BuzzBuy/
├── backend/                     # Node.js/Express backend
│   ├── config/
│   │   └── db.js                # MongoDB connection configuration
│   ├── controllers/
│   │   ├── orderController.js   # Order logic
│   │   ├── productController.js # Product logic
│   │   └── userController.js    # User authentication & management
│   ├── data/
│   │   ├── products.js          # Sample product data
│   │   └── users.js             # Sample user data
│   ├── middleware/
│   │   ├── asyncHandler.js      # Async error handling wrapper
│   │   ├── authMiddleware.js    # JWT authentication
│   │   └── errorHandler.js      # Global error handling
│   ├── models/
│   │   ├── orderModel.js        # Order schema
│   │   ├── productModel.js      # Product & Review schema
│   │   └── userModel.js         # User schema with password hashing
│   ├── routes/
│   │   ├── orderRoutes.js       # Order endpoints
│   │   ├── productRoutes.js     # Product endpoints
│   │   ├── uploadRoutes.js      # File upload endpoints
│   │   └── userRoutes.js        # Auth & user endpoints
│   ├── utils/
│   │   └── generateToken.js     # JWT token generation
│   ├── seeder.js                # Database seeding script
│   └── server.js                # Express app entry point
│
├── frontend/                    # React frontend
│   ├── public/
│   │   ├── index.html
│   │   ├── manifest.json
│   │   └── images/
│   ├── src/
│   │   ├── components/
│   │   │   ├── AdminRoute.jsx        # Protected admin route
│   │   │   ├── CheckoutSteps.jsx     # Checkout progress indicator
│   │   │   ├── Footer.jsx
│   │   │   ├── FormContainer.jsx     # Reusable form wrapper
│   │   │   ├── Header.jsx            # Navigation & search
│   │   │   ├── Loader.jsx            # Loading spinner
│   │   │   ├── Message.jsx           # Alert messages
│   │   │   ├── Meta.jsx              # SEO metadata
│   │   │   ├── Paginate.jsx          # Pagination component
│   │   │   ├── PrivateRoute.jsx      # Protected user route
│   │   │   ├── Product.jsx           # Product card component
│   │   │   ├── ProductCarousel.jsx   # Hero carousel
│   │   │   ├── Rating.jsx            # Star rating display
│   │   │   └── SearchBox.jsx         # Product search
│   │   ├── screens/
│   │   │   ├── CartScreen.jsx
│   │   │   ├── HomeScreen.jsx
│   │   │   ├── LoginScreen.jsx
│   │   │   ├── OrderScreen.jsx
│   │   │   ├── PaymentScreen.jsx
│   │   │   ├── PlaceOrderScreen.jsx
│   │   │   ├── ProductScreen.jsx
│   │   │   ├── ProfileScreen.jsx
│   │   │   ├── RegisterScreen.jsx
│   │   │   ├── ShippingScreen.jsx
│   │   │   └── admin/              # Admin-only screens
│   │   │       ├── OrderListScreen.jsx
│   │   │       ├── ProductEditScreen.jsx
│   │   │       ├── ProductListScreen.jsx
│   │   │       ├── UserEditScreen.jsx
│   │   │       └── UserListScreen.jsx
│   │   ├── slices/                 # Redux slices
│   │   │   ├── apiSlice.js
│   │   │   ├── authSlice.js
│   │   │   ├── cartSlice.js
│   │   │   ├── ordersApiSlice.js
│   │   │   ├── productsApiSlice.js
│   │   │   └── userApiSlice.js
│   │   ├── utils/
│   │   │   └── cartUtils.js
│   │   ├── assets/
│   │   │   └── styles/
│   │   ├── App.js
│   │   ├── constants.js
│   │   ├── index.js
│   │   └── store.js               # Redux store configuration
│   ├── package.json
│   └── public/
│
├── package.json                   # Root package.json
├── example.env                    # Environment variables template
└── README.md
```

---

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v14 or higher) - [Download](https://nodejs.org/)
- **npm** (comes with Node.js) or **yarn**
- **MongoDB** - [Download](https://www.mongodb.com/try/download/community) or use [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
- **Git** - [Download](https://git-scm.com/)
- **PayPal Developer Account** - [Sign up](https://developer.paypal.com)

---

## 🚀 Installation & Setup

### **Step 1: Clone the Repository**

```bash
git clone https://github.com/TonyJ275/BuzzBuy.git
cd BuzzBuy
```

### **Step 2: Install Root Dependencies**

```bash
npm install
```

### **Step 3: Set Up Environment Variables**

Create a `.env` file in the root directory based on `example.env`:

```bash
cp example.env .env
```

Edit the `.env` file with your configuration (see [Environment Variables](#environment-variables) section).

### **Step 4: Install Frontend Dependencies**

```bash
npm install --prefix frontend
```

### **Step 5: Build Production Frontend** (Optional)

```bash
npm run build
```

### **Step 6: Seed Database** (Optional)

To populate your database with sample products and users:

```bash
npm run data:import
```

To clear the database:

```bash
npm run data:destroy
```

### **Step 7: Start the Application**

#### Development Mode (Frontend & Backend Concurrently)
```bash
npm run dev
```

The application will be available at:
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:5000

#### Backend Only
```bash
npm run server
```

#### Frontend Only
```bash
npm run client
```

---

## ⚙️ Environment Variables

Create a `.env` file in the root directory with the following variables:

```env
NODE_ENV=development
PORT=
MONGO_URI=
JWT_SECRET=
PAGINATION_LIMIT=
```

### **Important Notes:**
- Replace placeholder values with your actual credentials
- Never commit `.env` to version control
- Keep `JWT_SECRET` secure and complex
- Get PayPal credentials from [PayPal Developer Dashboard](https://developer.paypal.com/)

---

## 📜 Available Scripts

### **Root Directory Scripts**

| Command | Description |
|---------|-------------|
| `npm install` | Install root dependencies |
| `npm start` | Start production server |
| `npm run server` | Start backend with Nodemon |
| `npm run client` | Start React frontend |
| `npm run dev` | Run frontend & backend concurrently |
| `npm run data:import` | Seed database with sample data |
| `npm run data:destroy` | Clear database |
| `npm run build` | Build complete application for production |

### **Frontend Scripts** (Run with `npm --prefix frontend`)

| Command | Description |
|---------|-------------|
| `npm start` | Start development server |
| `npm run build` | Create production build |
| `npm test` | Run tests |
| `npm run eject` | Eject from Create React App |

---
## 🔗 API Endpoints

### User Routes (`/api/users`)

| Method | Endpoint     | Access     | Description                  |
|--------|--------------|------------|-------------------------------|
| POST   | `/auth`      | Public     | User login                   |
| POST   | `/register`  | Public     | User registration            |
| GET    | `/profile`   | Protected  | Get user profile             |
| PUT    | `/profile`   | Protected  | Update user profile          |
| GET    | `/`          | Admin only | Get all users                |
| GET    | `/:id`       | Admin only | Get user by ID                |
| PUT    | `/:id`       | Admin only | Update user                   |
| DELETE | `/:id`       | Admin only | Delete user                   |

### Product Routes (`/api/products`)

| Method | Endpoint        | Access     | Description                      |
|--------|-----------------|------------|-----------------------------------|
| GET    | `/`             | Public     | Get all products (pagination & filtering) |
| GET    | `/:id`          | Public     | Get product details               |
| POST   | `/`             | Admin only | Create product                    |
| PUT    | `/:id`          | Admin only | Update product                    |
| DELETE | `/:id`          | Admin only | Delete product                    |
| POST   | `/:id/reviews`  | Protected  | Add product review                |

### Order Routes (`/api/orders`)

| Method | Endpoint        | Access     | Description                |
|--------|-----------------|------------|------------------------------|
| POST   | `/`             | Protected  | Create order                 |
| GET    | `/`             | Admin only | Get all orders                |
| GET    | `/myorders`     | Protected  | Get user's orders             |
| GET    | `/:id`          | Protected  | Get order details             |
| PUT    | `/:id/pay`      | Protected  | Update order to paid          |
| PUT    | `/:id/deliver`  | Admin only | Mark order as delivered       |

### Upload Routes (`/api/upload`)

| Method | Endpoint | Access     | Description           |
|--------|----------|------------|------------------------|
| POST   | `/`      | Admin only | Upload product image  |

---

## 🏗️ Architecture

### **Authentication Flow**
1. User registers or logs in
2. Backend validates credentials
3. JWT token generated and stored in HTTP-only cookie
4. Token sent with authenticated requests
5. Middleware verifies token on protected routes

### **Data Flow**
```
User (React Frontend)
    ↓
Redux Store (State Management)
    ↓
Axios HTTP Request
    ↓
Express Server (Middleware)
    ↓
Controller Logic
    ↓
Mongoose Model
    ↓
MongoDB Database
```

### **Security Features**
- JWT-based authentication
- Password hashing with bcryptjs
- Protected routes (Private & Admin)
- HTTP-only cookies
- PayPal server-side payment validation
- Input validation middleware

---

## 👥 Contributing

We welcome contributions! To contribute to BuzzBuy:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### **Development Guidelines**
- Follow existing code style and conventions
- Add comments for complex logic
- Test your changes before submitting a PR
- Update README if adding new features
- Keep commits clean and descriptive

---

## 📧 Contact & Support

For questions, suggestions, or bug reports, please reach out:

- **GitHub**: [TonyJ275/BuzzBuy](https://github.com/TonyJ275/BuzzBuy) — open an issue for questions

---

## 📄 License

This project is licensed under the --- License - see the LICENSE file for details.

---

## 🎉 Demo

Check out the demo video:

[![BuzzBuy Demo](https://github.com/TonyJ275/BuzzBuy/assets/115610428/39bff1dc-9763-43d5-b00f-cb359ec4595b)](https://github.com/TonyJ275/BuzzBuy/assets/115610428/39bff1dc-9763-43d5-b00f-cb359ec4595b)

**[View Live App →](https://buzzbuy.onrender.com/)**

> ⚠️ Note: This app is hosted on Render's free tier, so the server may take 30–60 seconds to spin up on first load if it's been idle.

---

**Happy shopping with BuzzBuy! 🛍️**

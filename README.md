# Game_Stora

This repository contains a full-stack e-commerce application built with a microservices architecture. It includes separate services for user management, product catalog, and cart functionality, all connected to a MongoDB database and fronted by a React-based user interface.

## Features

- **Microservices Architecture:** User, Product, and Cart services operate independently, allowing for scalability and maintainability.
- **User Authentication:** Secure user registration and login with JWT token-based authentication.
- **Product Management:** Browse, search, and filter products by category and price.
- **Shopping Cart:** Add, remove, and manage items in the shopping cart.
- **Checkout Process:** A multi-step checkout process for completing purchases.
- **Dockerization:** The application is containerized using Docker and orchestrated with Docker Compose for easy deployment.
- **Kubernetes Manifests:** Includes Kubernetes configurations for deploying the application in a cluster environment.
- **Observability Stack:** Pre-configured observability tools like Loki, Promtail, and Grafana for monitoring.

## Table of Contents

- [Game\_Stora](#game_stora)
  - [Features](#features)
  - [Table of Contents](#table-of-contents)
  - [Tech Stack](#tech-stack)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Project Structure](#project-structure)
  - [API Reference](#api-reference)
    - [User Service (`/api/users`)](#user-service-apiusers)
    - [Product Service (`/api/products`, `/api/filter`)](#product-service-apiproducts-apifilter)
    - [Cart Service (`/api/cart`)](#cart-service-apicart)
  - [License](#license)
  - [Important Links](#important-links)

## Tech Stack

- **Frontend:** React, Vite, Bootstrap, CSS, HTML, TypeScript
- **Backend:** Node.js, Express.js, TypeScript, Mongoose, Redis, bcrypt, JWT
- **Database:** MongoDB
- **Containerization:** Docker, Docker Compose
- **Orchestration:** Kubernetes
- **Observability:** Loki, Promtail, Grafana, Prometheus, cAdvisor

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/Bharatdwaj3/refine-devops.git
   cd refine-devops
   ```

2. **Set up environment variables:**
   Create a `.env` file in the root directory and in each service's directory (`User`, `Cart`, `Product`, `frontend`) based on the provided `.env.example` files. Configure your MongoDB connection details, JWT secret, and ports.

   **Example (`.env` in `User`, `Cart`, `Product`):**

   ```env
   MONGO_CLUSTER=mongodb:27017
   MONGO_DBNAME=ecommerce
   MONGO_USERNAME=root
   MONGO_PASSWORD=example
   ACCESS_TOKEN=your-secret-key-here
   PORT=9001 # Or 9003 for Cart, 9000 for Product
   ```

3. **Install dependencies:**
   Navigate to each service directory and install dependencies:

   ```bash
   cd User && npm install && cd ..
   cd Cart && npm install && cd ..
   cd Product && npm install && cd ..
   cd frontend && npm install && cd ..
   ```

4. **Run with Docker Compose:**
   This will build and run all services, including the database.

   ```bash
   docker-compose up --build
   ```

## Usage

This project is a full-stack e-commerce application. Here's how you can use it:

1. **User Management:**
   - **Register:** Navigate to `/register` in your browser to create a new account.
   - **Login:** Navigate to `/login` to log in with your existing credentials.
   - **Profile:** After logging in, access `/profile` to view your user information.

2. **Product Browsing:**
   - The homepage (`/`) displays a list of available products.
   - You can filter products by category using the dropdown menu.
   - Use the search bar to find specific products by name.
   - Click on a product to view its details on the `/productInfo/:productId` page.

3. **Shopping Cart:**
   - From the product details page, click "Add To Cart" to add items to your cart.
   - Navigate to `/cart` to view the items in your cart and the total price.
   - From the cart page, you can proceed to checkout.

4. **Checkout:**
   - The checkout page (`/checkout`) allows you to enter payment details.
   - Upon proceeding, your cart will be cleared, simulating an order placement.

## Project Structure

The project follows a microservices architecture with a separate frontend application:

## API Reference

This project exposes several RESTful APIs for interacting with the microservices:

### User Service (`/api/users`)

- `POST /api/users/`: Register a new user.
- `POST /api/users/login`: Log in a user and receive a JWT.
- `GET /api/users/`: Get logged-in user's profile (requires JWT).

### Product Service (`/api/products`, `/api/filter`)

- `GET /api/products/`: Get all products.
- `GET /api/products/:idOrName`: Get a specific product by ID or name.
- `POST /api/products/`: Create a new product (admin only).
- `GET /api/filter/category/:category`: Filter products by category.
- `GET /api/filter/price/:price`: Filter products by maximum price.
- `GET /api/filter/categoryprice/:category&&:price`: Filter products by category and maximum price.

### Cart Service (`/api/cart`)

- `GET /api/cart/`: Get items in the user's cart (requires JWT).
- `POST /api/cart/:productid`: Add a product to the cart (requires JWT).
- `DELETE /api/cart/:productid`: Remove a product from the cart (requires JWT).
- `DELETE /api/cart/checkout`: Clear the cart after checkout (requires JWT).

## License

This project is not currently under any specified license. Please refer to the repository owner for licensing details.

## Important Links

- **Repository:** [https://github.com/Bharatdwaj3/refine-devops](https://github.com/Bharatdwaj3/refine-devops)

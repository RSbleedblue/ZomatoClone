# Zomato Clone

## Overview

Zomato Clone is a web application designed to replicate the functionality of Zomato, a popular restaurant discovery and food delivery platform. This project includes endpoints for managing users, restaurants, and orders. The application is built using Node.js, Express, and MongoDB.

## Features

- User registration and login
- Restaurant management (CRUD operations)
- Order creation and status updates
- User and restaurant-specific order retrieval

## Installation

### Prerequisites

- Node.js
- MongoDB
- npm or yarn

### Getting Started

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/zomato-clone.git
   cd zomato-clone
   ```

2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Set Up Environment Variables**

   Create a `.env` file in the root directory and add the following environment variables:

   ```plaintext
   MONGODB_URI=your_mongodb_uri
   JWT_SECRET=your_jwt_secret
   ```

4. **Run Migrations (if applicable)**

   Set up the database schema if required.

5. **Start the Server**

   ```bash
   npm start
   ```

   The server will run on `http://localhost:5000` by default.

## API Documentation

### Users

#### Register User

- **Endpoint:** `POST /api/user/register`
- **Description:** Register a new user.
- **Request Body:**

  ```json
  {
    "username": "string",
    "password": "string",
    "email": "string",
    "address": "string"
  }
  ```

- **Responses:**
  - `200 OK` - User registered successfully.
  - `400 Bad Request` - Invalid input.

#### Login

- **Endpoint:** `POST /api/user/login`
- **Description:** Login a user.
- **Request Body:**

  ```json
  {
    "email": "string",
    "password": "string"
  }
  ```

- **Responses:**
  - `200 OK` - Login successful, returns JWT token.
  - `401 Unauthorized` - Invalid credentials.

#### Update Address

- **Endpoint:** `PUT /api/user/update`
- **Description:** Update user address.
- **Request Body:**

  ```json
  {
    "address": "string"
  }
  ```

- **Responses:**
  - `200 OK` - Address updated successfully.
  - `400 Bad Request` - Invalid input.

### Restaurants

#### Get All Restaurants

- **Endpoint:** `GET /api/restaurant/all`
- **Description:** Retrieve all restaurants.
- **Responses:**
  - `200 OK` - Returns a list of all restaurants.

#### Add Restaurant

- **Endpoint:** `POST /api/restaurant/add`
- **Description:** Add a new restaurant.
- **Request Body:**

  ```json
  {
    "name": "string",
    "address": "string",
    "menu": [
      {
        "name": "string",
        "price": "number"
      }
    ]
  }
  ```

- **Responses:**
  - `200 OK` - Restaurant added successfully.
  - `400 Bad Request` - Invalid input.

#### Update Menu

- **Endpoint:** `PUT /api/restaurant/updateMenu`
- **Description:** Update restaurant menu.
- **Request Body:**

  ```json
  {
    "restaurantId": "string",
    "menu": [
      {
        "name": "string",
        "price": "number"
      }
    ]
  }
  ```

- **Responses:**
  - `200 OK` - Menu updated successfully.
  - `400 Bad Request` - Invalid input.

#### Get Restaurant By ID

- **Endpoint:** `GET /api/restaurant/get/:id`
- **Description:** Retrieve a restaurant by ID.
- **Responses:**
  - `200 OK` - Returns restaurant details.
  - `404 Not Found` - Restaurant not found.

### Orders

#### Create Order

- **Endpoint:** `POST /api/order/create`
- **Description:** Create a new order.
- **Request Body:**

  ```json
  {
    "user": "string",
    "restaurant": "string",
    "items": [
      {
        "menuItem": "string",
        "quantity": "number"
      }
    ],
    "totalAmount": "number"
  }
  ```

- **Responses:**
  - `200 OK` - Order placed successfully.
  - `500 Internal Server Error` - Error placing order.

#### Get Order By ID

- **Endpoint:** `GET /api/order/get/:id`
- **Description:** Retrieve an order by ID.
- **Responses:**
  - `200 OK` - Returns order details.
  - `404 Not Found` - Order not found.

#### Update Order Status

- **Endpoint:** `PUT /api/order/updateStatus/:id`
- **Description:** Update the status of an order.
- **Request Body:**

  ```json
  {
    "orderStatus": "string"
  }
  ```

- **Responses:**
  - `200 OK` - Order status updated successfully.
  - `404 Not Found` - Order not found.

#### Get Orders By User

- **Endpoint:** `GET /api/order/user/:userId`
- **Description:** Retrieve orders for a specific user.
- **Responses:**
  - `200 OK` - Returns orders for the user.

#### Get Orders By Restaurant

- **Endpoint:** `GET /api/order/restaurant/:restaurantId`
- **Description:** Retrieve orders for a specific restaurant.
- **Responses:**
  - `200 OK` - Returns orders for the restaurant.

## Testing

You can use tools like Postman or Swagger UI to test the API endpoints. Ensure the server is running before testing.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request to contribute.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

You can customize this template further based on your project's specific needs and details. Make sure to keep the documentation up to date with any changes made to the project.

# Product Service

A microservice component of the E-Commerce platform responsible for managing product catalog, inventory, and product-related operations.

## Overview

The Product Service provides:

-   Product catalog management
-   Product search and filtering
-   Inventory management
-   Product statistics and analytics
-   Service-to-service communication for stock checks

## Prerequisites

-   Node.js 14 or higher
-   MongoDB 4.4 or higher
-   Docker and Docker Compose
-   Kubernetes cluster (for production)

## Quick Start

1. **Clone the Repository**

    ```bash
    git clone https://github.com/your-org/product-service.git
    cd product-service
    ```

2. **Install Dependencies**

    ```bash
    npm install
    ```

3. **Environment Setup**
   Create a `.env` file:

    ```env
    PORT=8082
    MONGODB_URI=mongodb://localhost:27017/productdb
    JWT_SECRET=your_jwt_secret

    ```

4. **Start the Service**

    ```bash
    # Development
    npm run dev

    # Production
    npm start
    ```

## API Documentation

### Public Routes

-   `GET /api/products` - Get all products
-   `GET /api/products/search` - Search products
-   `GET /api/products/top` - Get top products
-   `GET /api/products/:id` - Get product by ID

### Admin Routes

-   `POST /api/products` - Create a new product
-   `PUT /api/products/:id` - Update a product
-   `DELETE /api/products/:id` - Delete a product
-   `PUT /api/products/:id/stock` - Update product stock
-   `GET /api/products/admin/stats` - Get product statistics

### Internal Service Routes

-   `POST /api/products/internal/check-stock` - Check and update stock (service-to-service)

## Product Model

### Product Fields

-   `name` - Product name (required)
-   `description` - Product description (required)
-   `price` - Product price (required, min: 0)
-   `stockQuantity` - Available stock (required, min: 0)
-   `categories` - Product categories (array of strings)
-   `createdAt` - Creation timestamp

### Features

-   Text search indexing on name and description
-   Automatic timestamp for creation date
-   Input validation and trimming
-   Minimum value constraints for price and stock

## Monitoring

-   Health check endpoints:
    -   `/health`
    -   `/api/health`
-   Request logging with Morgan
-   Detailed error tracking
-   Server timeout configuration (60s)
-   Graceful shutdown handling

## Troubleshooting

### Common Issues

1. Database Connection Issues

    - Check MongoDB connection string
    - Verify MongoDB service is running
    - Check network connectivity

2. Authentication Issues

    - Verify JWT secret configuration
    - Check service token validation
    - Verify user token extraction

3. Performance Issues
    - Check request payload size (limit: 10MB)
    - Monitor server timeouts
    - Check MongoDB query performance

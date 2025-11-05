# 🛒 Express.js Product API

A RESTful API built with **Express.js** for managing product data.  
This project implements routing, middleware, authentication, validation, and error handling as part of the Week 2 assignment.

---

## 🚀 Features

- RESTful CRUD API for products
- Custom middleware:
  - Logger (logs method, URL, and timestamp)
  - Authentication (API key required)
  - Validation (checks product data)
- Global error handling
- Filtering, pagination, and search
- Product statistics (count by category)
- Environment variables with `.env`

---

## ⚙️ Installation & Setup

### 1️⃣ Clone the repository
```bash
git clone <your-github-repo-url>
cd <repo-folder>
```

### 2️⃣ Install dependencies
```bash
npm install
```

### 3️⃣ Create `.env` file
```bash
API_KEY=supersecretkey123
PORT=3000
```

### 4️⃣ Run the server
```bash
npm start
```

Server will start on:
```
http://localhost:3000
```

---

## 📡 API Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|-----------|-------------|---------------|
| GET | `/api/products` | Get all products (supports filtering, pagination, search) | ❌ |
| GET | `/api/products/:id` | Get a specific product by ID | ❌ |
| POST | `/api/products` | Create a new product | ✅ |
| PUT | `/api/products/:id` | Update a product | ✅ |
| DELETE | `/api/products/:id` | Delete a product | ✅ |
| GET | `/api/products/stats` | Get product statistics | ❌ |

---

## 🔍 Query Parameters (for GET `/api/products`)

| Parameter | Description | Example |
|------------|--------------|----------|
| `category` | Filter products by category | `/api/products?category=electronics` |
| `search` | Search by name or description | `/api/products?search=coffee` |
| `page` | Page number for pagination | `/api/products?page=2` |
| `limit` | Number of results per page | `/api/products?limit=5` |

---

## 🧪 Example Requests & Responses

### ✅ GET All Products
**Request:**
```bash
GET /api/products
```

**Response:**
```json
{
  "total": 3,
  "page": 1,
  "limit": 10,
  "data": [
    {
      "id": "1",
      "name": "Laptop",
      "description": "16GB RAM",
      "price": 1200,
      "category": "electronics",
      "inStock": true
    }
  ]
}
```

---

### ✅ POST Create Product
**Request:**
```bash
curl -X POST http://localhost:3000/api/products   -H "Content-Type: application/json"   -H "x-api-key: supersecretkey123"   -d '{"name":"Headphones","description":"Noise cancelling","price":150,"category":"electronics","inStock":true}'
```

**Response:**
```json
{
  "id": "cfa12f3b-80c7-4f0c-8b26-f77a3a988bb4",
  "name": "Headphones",
  "description": "Noise cancelling",
  "price": 150,
  "category": "electronics",
  "inStock": true
}
```

---

### ⚠️ Example Error (Invalid API key)
**Request:**
```bash
curl -X POST http://localhost:3000/api/products   -H "Content-Type: application/json"   -H "x-api-key: wrongkey"   -d '{"name":"TV","price":600,"category":"electronics","inStock":true}'
```

**Response:**
```json
{
  "error": "UnauthorizedError",
  "message": "Invalid or missing API key"
}
```

---

## 🧰 Middleware Summary

| Middleware | File | Purpose |
|-------------|------|----------|
| Logger | `middleware/logger.js` | Logs method, URL, and timestamp |
| Authentication | `middleware/auth.js` | Checks API key |
| Validation | `middleware/validateProduct.js` | Validates product data |
| Error Handler | `middleware/errorHandler.js` | Handles all errors globally |

---

## 🧠 Environment Variables

| Variable | Description | Example |
|-----------|--------------|----------|
| `PORT` | Port number | 3000 |
| `API_KEY` | Required key for protected routes | supersecretkey123 |

---

## 👩🏽‍💻 Example Test with Postman

**Headers:**
| Key | Value |
|-----|--------|
| Content-Type | application/json |
| x-api-key | supersecretkey123 |

**Body (JSON):**
```json
{
  "name": "Toaster",
  "description": "2-slice toaster",
  "price": 40,
  "category": "kitchen",
  "inStock": true
}
```

---

## 🏁 Submission Notes

- All endpoints have been implemented and tested.
- Middleware and error handling meet assignment requirements.
- `.env.example` included for environment configuration.

---

## 👤 Author
**Name:** Tamia Mwandu  
**Course:** PLP — Express.js Week 2 Assignment  


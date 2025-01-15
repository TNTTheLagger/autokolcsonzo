# API Endpoints Documentation

This document outlines the endpoints required for the car rental application, including their purpose, request structure, and example responses.

---

## 1. `POST /cars`

### **Purpose**

Registers a new car in the system.

### **Request Body**

```json
{
  "model": "string",
  "deposit": "integer",
  "perKmRate": "integer",
  "dailyRate": "integer",
  "description": "string"
}
```

### **Example Request**

```http
POST /cars HTTP/1.1
Host: your-backend-api.com
Content-Type: application/json

{
  "model": "Toyota Corolla",
  "deposit": 500,
  "perKmRate": 10,
  "dailyRate": 50,
  "description": "A reliable compact car."
}
```

### **Example Response**

**Status Code**: `201 Created`

```json
{
  "id": 1,
  "model": "Toyota Corolla",
  "deposit": 500,
  "perKmRate": 10,
  "dailyRate": 50,
  "description": "A reliable compact car."
}
```

---

## 2. `GET /cars`

### **Purpose**

Fetches all available cars.

### **Example Request**

```http
GET /cars HTTP/1.1
Host: your-backend-api.com
```

### **Example Response**

**Status Code**: `200 OK`

```json
[
  {
    "id": 1,
    "model": "Toyota Corolla",
    "deposit": 500,
    "perKmRate": 10,
    "dailyRate": 50,
    "description": "A reliable compact car."
  },
  {
    "id": 2,
    "model": "Honda Civic",
    "deposit": 600,
    "perKmRate": 12,
    "dailyRate": 60,
    "description": "A comfortable sedan."
  }
]
```

---

## 3. `POST /rents`

### **Purpose**

Registers a new rent.

### **Request Body**

```json
{
  "email": "string",
  "car": "integer",
  "startDate": "string (YYYY-MM-DD)",
  "endDate": "string (YYYY-MM-DD)"
}
```

### **Example Request**

```http
POST /rents HTTP/1.1
Host: your-backend-api.com
Content-Type: application/json

{
  "email": "renter@example.com",
  "car": 1,
  "startDate": "2025-01-15",
  "endDate": "2025-01-20"
}
```

### **Example Response**

**Status Code**: `201 Created`

```json
{
  "id": 1,
  "email": "renter@example.com",
  "car": 1,
  "startDate": "2025-01-15",
  "endDate": "2025-01-20",
  "status": "ongoing"
}
```

---

## 4. `GET /rents`

### **Purpose**

Fetches all rental records.

### **Example Request**

```http
GET /rents HTTP/1.1
Host: your-backend-api.com
```

### **Example Response**

**Status Code**: `200 OK`

```json
[
  {
    "id": 1,
    "email": "renter@example.com",
    "carModel": "Toyota Corolla",
    "startDate": "2025-01-15",
    "endDate": "2025-01-20",
    "status": "ongoing"
  },
  {
    "id": 2,
    "email": "user@example.com",
    "carModel": "Honda Civic",
    "startDate": "2025-01-10",
    "endDate": "2025-01-15",
    "status": "completed"
  }
]
```

---

## Summary of Endpoints

| Endpoint | Method | Description                |
| -------- | ------ | -------------------------- |
| `/cars`  | POST   | Registers a new car        |
| `/cars`  | GET    | Fetches all available cars |
| `/rents` | POST   | Registers a new rent       |
| `/rents` | GET    | Fetches all rental records |
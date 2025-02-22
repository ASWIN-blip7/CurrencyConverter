
# Currency Conversion API Documentation

This document provides detailed information about the API endpoints available in the Currency Conversion Project.

---

## Base URL

The application runs on `http://localhost:8080` by default.

---

## Endpoints

### 1. Get Exchange Rates

- **URL**: `/rates`
- **Method**: `GET`
- **Query Parameters**:
  - `base` (optional, default: `USD`): The base currency for exchange rates.

- **Response**:
  ```json
  {
    "base": "USD",
    "date": "2023-01-01",
    "rates": {
      "EUR": 0.85,
      "GBP": 0.75,
      ...
    }
  }
  ```

- **Description**:
  Retrieves real-time exchange rates for the specified base currency.

- **Example Request**:
  ```bash
  curl -X GET "http://localhost:8080/rates?base=EUR"
  ```

- **Example Response**:
  ```json
  {
    "base": "EUR",
    "date": "2023-01-01",
    "rates": {
      "USD": 1.1,
      "GBP": 0.88,
      "INR": 90.12
    }
  }
  ```

---

### 2. Convert Currency

- **URL**: `/convert`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "from": "USD",
    "to": "EUR",
    "amount": 100
  }
  ```

- **Response**:
  ```json
  {
    "from": "USD",
    "to": "EUR",
    "amount": 100,
    "convertedAmount": 85
  }
  ```

- **Description**:
  Converts a specified amount from one currency to another based on real-time exchange rates.

- **Example Request**:
  ```bash
  curl -X POST "http://localhost:8080/convert"   -H "Content-Type: application/json"   -d '{"from": "USD", "to": "EUR", "amount": 100}'
  ```

- **Example Response**:
  ```json
  {
    "from": "USD",
    "to": "EUR",
    "amount": 100,
    "convertedAmount": 85
  }
  ```

---

## Error Responses

### Invalid Base Currency
- **Response**:
  ```json
  {
    "error": "Invalid base currency"
  }
  ```

### Invalid Target Currency
- **Response**:
  ```json
  {
    "error": "Invalid target currency"
  }
  ```

### Validation Errors
- **Response**:
  ```json
  {
    "error": "Validation failed",
    "details": [
      "Source currency must not be blank",
      "Target currency must not be blank",
      "Amount must be greater than zero"
    ]
  }
  ```

---

## Contact

For any questions or issues regarding the API, please contact:
- **Name**: [Your Name]
- **Email**: your.email@example.com

---

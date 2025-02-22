
# Currency Conversion Project

A simple Spring Boot application for currency conversion using the Exchange Rate API.

## Features

- Retrieve real-time exchange rates for a base currency.
- Convert an amount from one currency to another.

---

## Prerequisites

- **Java 17** or later
- **Maven** for dependency management
- Internet connection (to access the Exchange Rate API)

---

## Installation and Setup

1. **Clone the Repository**  
   ```bash
   git clone https://github.com/your-username/currency-conversion-project.git
   cd currency-conversion-project
   ```

2. **Configure API URL**  
   Update the API URL in the `application.properties` file (optional).  
   Default API URL:
   ```
   https://api.exchangerate-api.com/v4/latest/
   ```

3. **Build the Project**  
   Run the following command to build the project:
   ```bash
   mvn clean install
   ```

4. **Run the Application**  
   Start the application:
   ```bash
   mvn spring-boot:run
   ```
   The application will be available at `http://localhost:8080`.

---

## API Endpoints

### 1. **Get Exchange Rates**
   **URL**: `/rates`  
   **Method**: `GET`  
   **Query Parameters**:  
   - `base` (optional, default: `USD`): The base currency.  

   **Response**:  
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

   **Example Request**:  
   ```bash
   curl -X GET "http://localhost:8080/rates?base=EUR"
   ```

### 2. **Convert Currency**
   **URL**: `/convert`  
   **Method**: `POST`  
   **Request Body**:  
   ```json
   {
     "from": "USD",
     "to": "EUR",
     "amount": 100
   }
   ```

   **Response**:  
   ```json
   {
     "from": "USD",
     "to": "EUR",
     "amount": 100,
     "convertedAmount": 85
   }
   ```

   **Example Request**:  
   ```bash
   curl -X POST "http://localhost:8080/convert"    -H "Content-Type: application/json"    -d '{"from": "USD", "to": "EUR", "amount": 100}'
   ```

---

## Project Structure

- `com.ty.CurrencyConvertProjectApplication`: Main class to bootstrap the application.
- `com.ty.controller.CurrencyController`: REST controller for handling requests.
- `com.ty.service.CurrencyService`: Business logic for fetching exchange rates and converting currencies.
- `com.ty.model.CurrencyConversionRequest`: Data model for currency conversion requests.

---

## Improvements in Progress

- Input validation using `@Valid` annotations.
- Exception handling with a global error handler (`@ControllerAdvice`).
- Caching for improved performance.
- Secure endpoints with Spring Security.

---






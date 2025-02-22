
# Currency Converter Application

## Description
This is a Spring Boot application that provides real-time currency conversion functionality using a public exchange rates API. It includes endpoints to fetch exchange rates and convert amounts between currencies.

## Features
1. Fetch real-time exchange rates for a base currency.
2. Convert amounts between currencies using the fetched rates.
3. Error handling for invalid inputs and external API unavailability.

## Prerequisites
1. Java 11 or higher installed.
2. Maven installed.
3. API key from a currency exchange service (e.g., Exchange Rates API).

## Setup Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repository/currency-converter.git
   cd currency-converter
   ```

2. Configure the API Key:
   Open the `src/main/resources/application.properties` file and add your API key:
   ```properties
   exchange.api.key=YOUR_API_KEY
   ```

3. Build and Run the Application:
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```

4. Access the API at:
   - Base URL: `http://localhost:8080`

## Endpoints
### 1. Fetch Exchange Rates
**GET** `/api/rates?base=USD`  
Fetch exchange rates for a base currency. Defaults to USD if not provided.

**Example Request:**
```bash
curl -X GET "http://localhost:8080/api/rates?base=USD"
```

**Example Response:**
```json
{
    "base": "USD",
    "rates": {
        "EUR": 0.85,
        "GBP": 0.75,
        "INR": 83.5
    }
}
```

### 2. Convert Currency
**POST** `/api/convert`  
Convert an amount from one currency to another.

**Request Body:**
```json
{
    "from": "USD",
    "to": "EUR",
    "amount": 100
}
```

**Example Response:**
```json
{
    "from": "USD",
    "to": "EUR",
    "amount": 100,
    "convertedAmount": 85.0
}
```

## Swagger Documentation
- Swagger UI: `http://localhost:8080/swagger-ui.html`
- OpenAPI Spec: `http://localhost:8080/v3/api-docs`

## Testing
Run unit tests using Maven:
```bash
mvn test
```



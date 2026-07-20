# Greenscan API

Greenscan is a Spring Boot-based REST API designed to track the carbon footprint and eco-score of products. It allows adding products and querying them by their barcodes. It uses MongoDB as its primary database.

## Technologies Used

* Java 21
* Spring Boot 3.2.4
* Spring Data MongoDB
* Lombok
* Docker (for containerized environments)

## Prerequisites

* Java 21+
* Maven
* MongoDB (can be run via Docker)

## Running the Application

1. Start the necessary services (MongoDB) using Docker Compose if available:
   ```bash
   docker-compose up -d
   ```
2. Build and run the Spring Boot application using Maven:
   ```bash
   ./mvnw spring-boot:run
   ```
   *(On Windows, you can also use the included `baslat.bat` script.)*

## API Endpoints

The base URL for all endpoints is `/api/products`.

* **GET `/api/products/all`**: Retrieves a list of all products.
* **GET `/api/products/{barcode}`**: Retrieves a specific product by its barcode.
* **POST `/api/products/add`**: Adds a new product to the database. 
  * **Payload Example:**
    ```json
    {
      "barcode": "1234567890123",
      "name": "Eco-friendly Apple",
      "carbonFootprint": 0.5,
      "ecoScore": "A"
    }
    ```

## Project Structure

* `controller/`: Contains the REST controllers that handle incoming HTTP requests (`ProductController`).
* `model/`: Contains the data models mapped to MongoDB documents (`Product`).
* `repository/`: Contains the interfaces for database operations extending Spring Data repositories (`ProductRepository`).

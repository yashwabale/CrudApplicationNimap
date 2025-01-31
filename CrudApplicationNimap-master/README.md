# Spring Boot Category & Product Management API

## Overview
This project implements a RESTful API for managing **Categories** and **Products**, including CRUD operations with pagination. It uses **Spring Boot**, **JPA**, **Hibernate**, and **MySQL** (or any RDBMS), with annotation-based configuration (no XML). The relationship between Categories and Products is modeled as a **one-to-many** relationship, where one category can have multiple products. The API is paginated and allows fetching single product details along with its respective category.

## Technologies Used
- Java 17
- Spring Boot 3.x
- Spring Data JPA
- Hibernate
- MySQL (RDBMS)
- RESTful API
- Maven

## Features
- Category CRUD operations (Create, Read, Update, Delete)
- Product CRUD operations (Create, Read, Update, Delete)
- One-to-many relationship between Category and Product
- Server-side pagination for both Categories and Products
- Fetching product details along with associated category details

## Endpoints

### Category API
1. **Get all categories (with pagination)**:
GET /api/categories?page=3

markdown
Copy code
2. **Create a new category**:
POST /api/categories Body: { "name": "Category Name" }

markdown
Copy code
3. **Get category by ID**:
GET /api/categories/{id}

markdown
Copy code
4. **Update category by ID**:
PUT /api/categories/{id} Body: { "name": "Updated Category Name" }

markdown
Copy code
5. **Delete category by ID**:
DELETE /api/categories/{id}

markdown
Copy code

### Product API
1. **Get all products (with pagination)**:
GET /api/products?page=2

markdown
Copy code
2. **Create a new product**:
POST /api/products Body: { "name": "Product Name", "categoryId": 1, "price": 100 }

vbnet
Copy code
3. **Get product by ID (with category details)**:
GET /api/products/{id}

markdown
Copy code
4. **Update product by ID**:
PUT /api/products/{id} Body: { "name": "Updated Product Name", "categoryId": 1, "price": 120 }

markdown
Copy code
5. **Delete product by ID**:
DELETE /api/products/{id}

sql
Copy code

## Database Configuration

1. Create a MySQL database (or another RDBMS).
2. Update the `application.properties` or `application.yml` file with your database credentials:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/your_database_name
spring.datasource.username=your_username
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
Running the Application
Clone the repository.
Set up your database connection in the application.properties file.
Build the project with Maven:
bash
Copy code
mvn clean install
Run the application:
bash
Copy code
mvn spring-boot:run
The application will be accessible at http://localhost:8080.
Pagination
For both the Category and Product APIs, pagination can be achieved by specifying the page query parameter in the GET request. The default page size is 10, but it can be adjusted by adding a size parameter.

Example:

arduino
Copy code
GET /api/products?page=2&size=5
One-to-Many Relationship
Each Product belongs to one Category.
While fetching a single product by its ID, the associated category details are included in the response.
Example Request and Response
Fetch Product by ID (with Category details)
json
Copy code
GET /api/products/1

Response:
{
  "id": 1,
  "name": "Product A",
  "price": 100,
  "category": {
    "id": 1,
    "name": "Category A"
  }
}
Project Structure
graphql
Copy code
src/
 └── main/
     ├── java/
     │   └── com.example.demo/
     │       ├── controller/    # Rest Controllers
     │       ├── model/         # JPA Entities
     │       ├── repository/    # Spring Data JPA Repositories
     │       ├── service/       # Service Layer
     └── resources/
         ├── application.properties  # Database configurations
License
This project is licensed under the MIT License - see the LICENSE file for details.

csharp
Copy code

This version should look correct when viewed on GitHub.

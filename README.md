# Library Management System

## Table of Contents

1. [About](#about)
2. [Getting Started](#getting-started)
   - [Prerequisites](#prerequisites)
   - [Installation](#installation)
   - [Configuration](#configuration)
3. [Running the Application](#running-the-application)
4. [API Design](#api-design)

## About

A Spring Boot backend application for a Library Management System built using RESTful APIs.

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Java Development Kit (JDK 17 or higher)** 
- **MySQL Server** 
- **Git** 
- **Postman (Recommended)**
### Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/ViscousGuy/library-management-system.git
   cd library-management-system
   ```

2. **Build with Maven:**
   ```bash
   ./mvnw clean install
   ```

### Configuration

This project uses environment variables to store sensitive data.

1. **Create a Database:**

   - Open your MySQL client (or a tool like MySQL Workbench) and connect to your MySQL server.
   - Create a new database named `library_management`:
     ```sql
     CREATE DATABASE library_management;
     ```

2. **Set Environment Variables:**

   - Create a file named `application-development.properties` inside the `src/main/resources` directory of the project.
   - Add the following environment variables within the file, replacing the placeholders with your actual database credentials:

     ```
     spring.datasource.url=jdbc:<DB_CONNECTION>://<DB_HOST>:<DB_PORT>/<DB_DATABASE>
     spring.datasource.username=<DB_USERNAME>
     spring.datasource.password=<DB_PASSWORD>
     spring.jpa.hibernate.ddl-auto=update
     spring.jpa.show-sql = true
     books.max_allowed=3
     books.max_allowed_days=15
     books.fine.per_day=5

     ```

## Running the Application

```bash
./mvnw spring-boot:run
```

The application will start, and you should see the Spring Boot banner in the console indicating successful startup. By default, the application will run on port 8080.

## API Design

The Library Management System will expose a well-defined RESTful API for interacting with the backend functionality. The API will adhere to REST principles, using appropriate HTTP methods (GET, POST, PUT, DELETE) and resource-based URLs.

###### To Create Student:

	localhost:8080/student/add

	{
	    "name": "String",
	    "country": "String",
	    "age": int,
	    "mobileNumber": "String",
	    "email": "String"
	}



###### To Get Student Details Through Email:

	localhost:8080/student/get-user?email=RequestParam



###### To Add Author:
	
	localhost:8080/author/add

	{
	    "name": "String",
	    "country": "String",
	    "age": int,
	    "rating": double
	}
	

###### To Add Book:

	localhost:8080/book/add

	{
	    "name": "String",
	    "authorId": int,
	    "pages": int,
	    "genre": "ENUM Type"
	}
	

###### To Get Author Details:

	localhost:8080/author/get-author?authorId=RequestParam


###### To Issue Book:
	
	localhost:8080/transaction/issueBook

	{
	    "bookId": int,
	    "cardId": int
	}
	
	
	
###### To Return Book:	

	localhost:8080/transaction/returnBook?cardId=int&bookId=int

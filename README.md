# Authentication and Authorization Example

### Team
- Devaj Mody
- Connor O'Neill

A simple Spring Boot application demonstrating basic authentication and authorization using Spring Security.

## Features
- User login/logout
- Role-based access control
- In-memory user storage
- Basic web interface

## Frameworks and Technologies Used
- **Spring Boot 3.5.3** - Application framework
- **Spring Security 6.5.1** - Authentication and authorization
- **Spring Data JPA** - Data persistence layer
- **Thymeleaf** - Template engine for web pages
- **Maven** - Build tool
- **Java 11** - Programming language

## Prerequisites
- Java 11 or higher
- Maven 3.6 or higher

## How to Run the Application

### 1. Clone or Download the Project
Download the project files to your local machine.

### 2. Navigate to Project Directory
```bash
cd AuthenticationAndAuthorizationExample
```

### 3. Compile the Application
```bash
mvn clean compile
```

### 4. Run the Application
```bash
mvn spring-boot:run
```

### 5. Access the Application
Open your web browser and go to:
```
http://localhost:8080
```

The application will automatically redirect you to the login page.

## Default Users
- **Admin User**: username=`admin`, password=`admin`
- **Regular User**: username=`user`, password=`user`

## Application URLs
- Login Page: `http://localhost:8080/login`
- Dashboard: `http://localhost:8080/dashboard`
- Admin Panel: `http://localhost:8080/admin/panel` (Admin only)
- User Profile: `http://localhost:8080/user/profile` (User and Admin)

## Stopping the Application
Press `Ctrl+C` in the terminal where the application is running.
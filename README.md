# ToDo Application - Backend API
Group K

A modern RESTful API backend for a ToDo application built with Spring Boot 4.0.1 and Java 21. This project provides comprehensive task management capabilities with persistent data storage, and containerized deployment options.

## Features

- **RESTful API**: Complete CRUD operations for ToDo items
- **Data Persistence**: Spring Data JPA with PostgreSQL database
- **API Documentation**: OpenAPI 3.1.0 with Swagger UI integration
- **Interactive API Docs**: Auto-generated Swagger UI for easy API exploration
- **Docker Support**: Pre-configured Docker Compose for both development and production
- **Database Administration**: Adminer included for development database management
- **Actuator**: Built-in health checks and monitoring endpoints
- **Entity Mapping**: MapStruct-based automatic DTO mapping

## Technology Stack

- **Framework**: Spring Boot 4.0.1
- **Java Version**: 21
- **Build Tool**: Maven
- **Database**: PostgreSQL 18.1
- **ORM**: Hibernate/Spring Data JPA
- **Mapping**: MapStruct 1.5.5
- **API Documentation**: SpringDoc OpenAPI 3.0.1 with Swagger UI
- **Database Admin Tools**: Adminer (development only)

## Prerequisites

- Java 21 or higher
- Maven 3.8+
- Docker & Docker Compose (for containerized deployment)
- PostgreSQL 18+ (for production deployment)

## Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/vs-ws25-gruppe-k/vs-backend-group-k.git
cd vs-backend-group-k/todoapp
```

### 2. Local Development

Ensure Docker Engine is running.

```bash
# Copy and configure environment file
cp .env.example .env

# Build and start database
mvn clean install

# Run the application
mvn spring-boot:run -Dspring-boot.run.arguments="--spring.profiles.active=dev"
```

Access at:
- **API**: `http://localhost:8080`
- **Swagger UI**: `http://localhost:8080/swagger-ui.html`
- **Adminer**: `http://localhost:7777`

### 3. Docker Deployment (Production)

From the root directory:

```bash
# Copy and configure environment file
cp .env.example .env

# Start services
docker-compose up -d
```

## Project Structure

```
todoapp/
├── src/
│   ├── main/
│   │   ├── java/de/vs_group4/todoapp/
│   │   │   ├── ToDoAppApplication.java       # Main application entry point
│   │   │   ├── config/
│   │   │   │   └── SecurityConfig.java       # Spring Security configuration
│   │   │   ├── controllers/
│   │   │   │   └── ToDoController.java       # REST endpoints
│   │   │   ├── services/
│   │   │   │   └── ToDoService.java          # Business logic
│   │   │   ├── repositories/
│   │   │   │   └── ToDoRepository.java       # Data access layer
│   │   │   ├── models/
│   │   │   │   └── ToDoItem.java             # Entity model
│   │   │   ├── dtos/
│   │   │   │   ├── request/
│   │   │   │   │   └── ToDoItemRequestDTO.java
│   │   │   │   └── response/
│   │   │   │       └── ToDoItemResponseDTO.java
│   │   │   └── mappers/
│   │   │       ├── EntityMapper.java
│   │   │       └── request/
│   │   │           └── ToDoItemRequestMapper.java
│   │   └── resources/
│   │       ├── application.properties        # Main configuration
│   │       └── application-dev.properties    # Development configuration
│   └── test/
│       └── java/de/vs_group4/todoapp/
│           └── ToDoAppApplicationTests.java  # Integration tests
├── Dockerfile
├── docker-compose.yaml
├── dev.docker-compose.yaml
├── pom.xml                                   # Maven configuration
└── mvnw / mvnw.cmd                           # Maven wrapper scripts
```

## API Endpoints

All endpoints are documented in the interactive Swagger UI: `http://localhost:8080/swagger-ui.html`

### ToDo Items

- `GET /todos/{id}` - Retrieve a specific ToDo item
- `PUT /todos/{id}` - Update a ToDo item
- `GET /todos` - List all ToDo items
- `POST /todos` - Create a new ToDo item
- `DELETE /todos/{id}` - Delete a ToDo item

### Health & Monitoring

- `GET /actuator/health` - Health check (accessible without auth in dev)
- `GET /actuator` - Actuator endpoints overview

### Full API Documentation

See [docs/api-doc.yml](docs/api-doc.yml) or access Swagger UI at:
```
http://localhost:8080/swagger-ui.html
```

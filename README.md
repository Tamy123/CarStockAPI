# CarStockAPI

CarStockAPI is a RESTful API for managing car inventory for multiple dealers. It allows dealers to add, update, search, and delete cars in their inventory while ensuring that each dealer can only access their own data through JWT-based authentication.

## Features
- Dealer Registration and Login
- JWT Authentication
- Add, Update, Delete, and Search Cars by Make, Model, Year
- Manage Stock Levels for Cars
- Multi-tenancy support (Each dealer has their own inventory)

## Prerequisites

Before running the project, ensure you have the following installed:
- [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
- [Docker](https://www.docker.com/get-started)

## Running the Project Locally

### Step 1: Clone the Repository
```bash
git clone https://github.com/Tamy123/CarStockAPI.git
cd CarStockAPI
```

### Step 2: Install Dependencies
Restore the .NET dependencies using the following command:
```bash
dotnet restore
```

### Step 3: Build the project
Build the project using:
```bash
dotnet build
```

### Step 4: Run the project
Run the project using:
```bash
dotnet run
```
### Step 5: Swagger UI
To explore the API endpoints, you can navigate to the Swagger UI once the API is running:
```bash
http://localhost/index.html
```

## Running Tests
To run the unit tests using XUnit:
```bash
dotnet test
```
## Running the Project with Docker

### Step 1: Pull the Docker Image
```bash
docker pull <your-docker-image-url>
```

### Step 2: Run the Docker Container
After pulling the image, you can run it as a container:
```bash
docker run -d -p 8080:80 <your-docker-image-url>
```
This will make the API accessible on http://localhost:8080

## API Endpoints

### Dealer Endpoints
- **POST** `/api/dealer/register`: Register a new dealer
- **POST** `/api/dealer/login`: Login and receive a JWT token

### Car Endpoints
- **GET** `/api/cars`: Get all cars for the authenticated dealer
- **GET** `/api/cars/{id}`: Get a car by ID
- **POST** `/api/cars`: Add a new car to the dealer's inventory
- **PUT** `/api/cars/{id}/stock`: Update the stock level of a car
- **DELETE** `/api/cars/{id}`: Delete a car from the inventory
- **GET** `/api/cars/search?make={make}&model={model}`: Search cars by make and model

## JWT Authentication

To access the car-related endpoints, you must include a valid JWT token in the `Authorization` header of your requests. Here's how you can obtain a token:

1. Register as a dealer using `/api/dealer/register`.
2. Login using `/api/dealer/login` to receive a token.

3. Use the token in the `Authorization` header for subsequent requests:

```bash
Authorization: Bearer <your-token>
```





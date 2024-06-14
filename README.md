# Job-Search-Caddie-API-Public

This is a Job Search API built with ASP.NET Core and PostgreSQL. The API provides endpoints to manage job postings.
This API is deployed/selfhosted supporting Job Search Caddie UI.

<img width="1455" alt="Screenshot 2024-06-14 at 6 51 02 PM" src="https://github.com/ShawnPad/job-search-api/assets/59770535/ca826fd1-2b99-41cc-b5fa-f4c03f2905ad">


## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Database Setup](#database-setup)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [CORS Configuration](#cors-configuration)
- [Contributing](#contributing)
- [License](#license)

## Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [PostgreSQL](https://www.postgresql.org/download/)
- [Visual Studio Code](https://code.visualstudio.com/) or any preferred IDE

## Installation

1. **Clone the repository**:

    ```bash
    git clone https://github.com/your-username/job-search-api.git
    cd job-search-api
    ```

2. **Install dependencies**:

    ```bash
    dotnet restore
    ```

## Configuration

1. **Database Configuration**:

    Update the database connection string in `program.cs` to match your PostgreSQL configuration:

    ```csharp
    builder.Services.AddDbContext<ApplicationDbContext>(options =>
        options.UseNpgsql("Host=your-host;Database=your-database;Username=your-username;Password=your-password"));
    ```

2. **CORS Configuration**:

    The CORS policy is configured in `program.cs` to allow all origins, methods, and headers for development. Adjust the policy based on your security requirements.

    ```csharp
    app.UseCors(options =>
    {
        options.AllowAnyOrigin()
               .AllowAnyMethod()
               .AllowAnyHeader();
    });
    ```

## Database Setup

1. **Apply Migrations**:

    Make sure your database is running and then apply the migrations:

    ```bash
    dotnet ef database update
    ```

## Running the Application

1. **Run the API**:

    ```bash
    dotnet run
    ```

    The API will be available at `https://localhost:5001` (HTTPS) and `http://localhost:5000` (HTTP).

2. **Swagger UI**:

    You can access the Swagger UI for API documentation and testing at `https://localhost:5001/swagger` (in development mode).

## API Endpoints

Here are some of the main API endpoints:

- **GET /api/jobs**: Retrieve all job postings.
- **GET /api/jobs/{id}**: Retrieve a specific job posting by ID.
- **POST /api/jobs**: Create a new job posting.
- **PUT /api/jobs/{id}**: Update an existing job posting.
- **DELETE /api/jobs/{id}**: Delete a job posting.

Refer to the Swagger UI for detailed information and testing of all available endpoints.

## CORS Configuration

For development purposes, CORS is configured to allow any origin. For production, update the CORS policy in `program.cs` to restrict access appropriately:

```csharp
app.UseCors(options =>
{
    options.WithOrigins("https://your-frontend-domain.com")
           .AllowAnyMethod()
           .AllowAnyHeader();
});

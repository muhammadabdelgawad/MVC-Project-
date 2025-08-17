# MVC-Project

## Overview

This is an ASP.NET Core MVC project that implements basic CRUD operations for Departments and Employees, user authentication, and role-based authorization. The project follows the Model-View-Controller architectural pattern, leveraging Entity Framework Core for data access and AutoMapper for object mapping.

## Features and Functionality

-   **Account Management:**
    -   User registration with email confirmation.
    -   User login and logout.
    -   Password reset functionality, including email token generation and validation.
-   **Department Management:**
    -   Create, read, update, and delete (CRUD) operations for departments.
    -   Authorized access to department management based on user roles.
-   **Employee Management:**
    -   CRUD operations for employees.
    -   Image uploading and deleting for employee profiles.
    -   Searching employee by name.
    -   Authorized access to employee management based on user roles.
-   **Role Management:**
    -   Create, read, update, and delete operations for roles.
    -   Assign roles to users.
-   **User Management:**
    -   List, edit, and delete users.
    -   Assign users to roles.
-   **Authorization:**
    -   Utilizes `[Authorize]` attribute for controller actions, restricting access to authenticated users.
    -   Role-based authorization for specific functionalities.
-   **Image Handling:**
    -   Uploading and deleting employee images with unique naming.

## Technology Stack

*   ASP.NET Core MVC
*   Entity Framework Core
*   AutoMapper
*   Microsoft Identity
*   SQL Server
*   Bootstrap
*   JQuery
*   JQuery Validation

## Prerequisites

*   .NET SDK 5.0 or later.
*   SQL Server.
*   An SMTP server for sending emails (e.g., Gmail).

## Installation Instructions

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/muhammadabdelgawad/MVC-Project-
    cd MVC-Project-
    ```

2.  **Update the database connection string:**

    *   Open `MVCProject.PL/Program.cs`.
    *   Locate the `AddDbContext` configuration.
    *   Modify the `UseSqlServer` call to use your SQL Server connection string:

    ```csharp
    Builder.Services.AddDbContext<MVCDbContext>(option =>
    {
    	option.UseSqlServer(Builder.Configuration.GetConnectionString("DefaultConnection"));
    });
    ```

    *Example:*

    ```csharp
    option.UseSqlServer("Server=your_server;Database=your_database;User Id=your_user_id;Password=your_password;");
    ```

3.  **Apply database migrations:**

    ```bash
    cd MVCProject.PL
    dotnet ef database update
    ```

4.  **Configure Email Settings:**

    *   Open `MVCProject.PL/Helper/EmailSettings.cs`.
    *   Update the SMTP client credentials with your Gmail or SMTP server details:

    ```csharp
    var client = new SmtpClient("smtp.gmail.com", 587);
    client.EnableSsl = true;
    client.Credentials = new NetworkCredential("your_email@gmail.com", "your_password");
    client.Send("your_email@gmail.com", email.To, email.Subject, email.Body);
    ```
        **Note**: If using Gmail, you may need to enable "Less secure app access" in your Gmail settings, or use an App Password.

5.  **Run the application:**

    ```bash
    dotnet run
    ```

    The application will start, and you can access it through your browser, typically at `https://localhost:5001` or `http://localhost:5000`.

## Usage Guide

1.  **Register and Login:**

    *   Navigate to the registration page (`/Account/Register`).
    *   Fill in the registration form and click "Register."
    *   Log in with your registered credentials on the login page (`/Account/Login`).
2.  **Department Management:**

    *   After login, navigate to `/Department/Index`.
    *   Use the "Create," "Edit," and "Delete" buttons to manage departments.
3.  **Employee Management:**

    *   Navigate to `/Employee/Index`.
    *   Use the "Create," "Edit," and "Delete" buttons to manage employees.
    *   When creating or editing employees, you can upload an image. Images are stored in `wwwroot/Files/Images`.
4.  **User and Role Management:**

    *   Navigate to `/User/Index` or `/Role/Index`.
    *   Use the provided interfaces to manage user and role permissions.

## API Documentation

N/A - This project does not expose a public API.

## Contributing Guidelines

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Implement your changes.
4.  Test your changes thoroughly.
5.  Commit your changes with descriptive messages.
6.  Push your branch to your forked repository.
7.  Submit a pull request to the main repository.

## License Information

No License specified

## Contact/Support Information

For issues, bug reports, or feature requests, please contact:

*   dev.muhammad@outlook.com

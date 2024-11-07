Case Study: Social Network Profile Creation System
Overview
A small-scale social networking platform requires a system for users to create personal profiles. The goal of this case study is to design and implement a profile creation system with an emphasis on secure data handling and a clear layered architecture that separates user interface, application logic, data access, and domain model.

Problem Statement
The social networking platform is in its initial stages, and its core functionality includes allowing users to create unique profiles. Each profile must contain essential information such as name, email, and password. Additionally, the platform must prevent duplicate profiles by ensuring each email is unique.

Key requirements for this system include:

User Registration: Allow users to register by providing their name, email, and password.
Data Validation: Ensure that users cannot register with an email already in use.
User Feedback: Provide feedback to users about the success or failure of their registration attempt.
Layered Architecture: Organize the code into distinct layers to improve maintainability, testability, and scalability.
Use Case: Create Profile
Actors:

User: A person who wants to create a profile on the social networking platform.
System: The platform that processes and stores user data.
Goal: The user successfully creates a profile with a unique email. If the email is already in use, the system provides feedback indicating this.

Primary Scenario (Happy Path):

The user opens the application and navigates to the "Create Profile" page.
The user enters their name, email, and password.
The system checks if the email is unique.
If the email is unique, the system creates the profile and stores it in the database.
The system displays a success message indicating that the profile was created.
Alternate Scenario (Email Already in Use):

Steps 1-3 are followed as in the primary scenario.
If the email is already in the database, the system displays an error message: "Email already in use."
Solution Architecture
The system follows a layered architecture to separate responsibilities and improve code organization. The layers include:

Domain Layer:

Contains the User class, which represents the user profile data with attributes such as name, email, and password.
Application Layer:

Contains the UserService class, which manages the business logic, including creating new user profiles and validating email uniqueness.
Infrastructure Layer:

Contains the UserDAO class, responsible for data access and storage in an in-memory database (HashMap).
UI Layer:

Contains the UserGUI class, which provides a graphical interface using Java Swing, allowing users to input their data and receive feedback.
Detailed Design
Domain Layer (User Class):

This class represents the user data model with properties for name, email, and password. It includes getters and setters for each attribute.
Application Layer (UserService Class):

This class handles the core business logic for profile creation. It interacts with the UserDAO to verify if an email is already in use and either saves the new profile or returns an error message.
Infrastructure Layer (UserDAO Class):

The UserDAO class acts as a mock database using a HashMap to store user profiles. It includes methods for saving a new profile and checking if an email exists.
UI Layer (UserGUI Class):

The UI layer provides a graphical interface where users can enter their profile details. It includes fields for name, email, and password, as well as a button to submit the information. The UI communicates with the UserController to handle the profile creation process.
Implementation
Here’s how the application works:

User Registration:
The user enters their profile details through the UI.
The UserController handles the input validation and passes the data to UserService.
Email Validation:
UserService checks with UserDAO to confirm if the email is unique.
Profile Creation:
If the email is unique, UserService saves the profile through UserDAO.
The user receives feedback through the UI indicating success or failure.
Class Diagrams
The following key classes form the system's structure:

User (Domain Layer): Contains name, email, password.
UserService (Application Layer): Interacts with UserDAO for email validation and profile creation.
UserDAO (Infrastructure Layer): Acts as an in-memory database using HashMap.
UserGUI (UI Layer): Provides a Swing-based interface for profile creation.
Testing Scenarios
Valid Profile Creation:
Input: Name: "John Doe", Email: "john@example.com", Password: "password123"
Expected Output: "Account created successfully!"
Duplicate Email Check:
Input: Name: "Jane Doe", Email: "john@example.com" (already used), Password: "newpassword123"
Expected Output: "Email already in use!"
Review Summary
The layered architecture ensures that the application remains organized and easy to modify. By separating the UI, business logic, data access, and data model, the system adheres to software engineering principles, making it more scalable and maintainable.


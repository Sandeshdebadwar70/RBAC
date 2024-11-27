# Project Setup Instructions

Follow these steps to set up and run the project:

## Prerequisites
- Ensure you have **Node.js** installed (version: `v20.15.1`).
- Install a MySQL server and have access to the MySQL Command Line Client.

---

## Frontend Setup

1. **Open the `frontend` folder** in Visual Studio Code.
   ```bash
   cd frontend
Install dependencies:
bash
Copy code
npm install
Install additional libraries:
bash
Copy code
npm install react-toastify react-router-dom axios
Start the frontend development server:
bash
Copy code
npm start
Database Setup
Open the MySQL Command Line Client.
Create a new database:
sql
Copy code
CREATE DATABASE project_db;
USE project_db;
Create the user table:
sql
Copy code
CREATE TABLE user (
    id INTEGER PRIMARY KEY AUTO_INCREMENT,
    firstName VARCHAR(20),
    lastName VARCHAR(20),
    email VARCHAR(50),
    password VARCHAR(100),
    phoneNumber VARCHAR(15),
    role VARCHAR(20),
    isDeleted INTEGER(1) DEFAULT 0, 
    createdTimestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);
Backend Setup
Open the backend folder in Visual Studio Code.
bash
Copy code
cd backend
Install dependencies:
bash
Copy code
npm install
Update the db.js file with your own MySQL user and password.
Example:
javascript
Copy code
const dbConfig = {
    host: 'localhost',
    user: 'your_username',
    password: 'your_password',
    database: 'project_db'
};
Install Nodemon globally (if not already installed):
bash
Copy code
npm install -g nodemon
Install additional backend dependencies:
bash
Copy code
npm install express cors
Start the backend server:
bash
Copy code
nodemon server.js
Running the Application
The frontend will be available on the default port 3000.
The backend will run on port 4000

Step-by-Step Guide to Test the RBAC Application
1.	Start the Application:
o	Run the backend server using Node.js (nodemon index.js) or the equivalent start command.
o	Start the frontend application with npm start.
2.	Register Users with Different Roles:
o	Navigate to the Registration Page (/register).
o	Register at least three users with the following roles:
	Admin
	Manager
	User
o	Use simple, valid email addresses and ensure strong passwords are provided (e.g., neha@gmail.com, manager@gmail.com, user@gmail.com).
3.	Login and Role Verification:
o	Navigate to the Login Page (/login).
o	Login with each registered user's credentials to verify role-specific access:
	Check if the correct name and role are displayed on the home page.
	Ensure unauthorized actions trigger proper toast notifications.
4.	Test Admin Permissions:
o	Login as an Admin.
o	Verify the following functionalities:
	View all user records on the Home Page.
	Edit any user record using the "Edit" button.
	Delete any user record using the "Delete" button.
	Confirm that the changes (e.g., updates, deletions) reflect correctly in the database.
5.	Test Manager Permissions:
o	Login as a Manager.
o	Verify the following functionalities:
	View all user records on the Home Page.
	Edit any user record. Confirm that updates are reflected in the database.
	Confirm that attempting to delete a user triggers a toast notification stating the restricted action.
6.	Test User Permissions:
o	Login as a User.
o	Verify the following functionalities:
	View all user records on the Home Page.
	Confirm that no "Edit" or "Delete" buttons are visible.
7.	Check Unauthorized Access Handling:
o	Logout from all roles and directly navigate to restricted pages like /edit.
o	Verify the application redirects unauthorized users to the login page with appropriate error messages.
8.	Password Security Test:
o	Confirm that passwords are securely hashed in the database (e.g., using tools like MySQL Workbench or equivalent).
o	Attempt login with the plaintext password to verify authentication is working correctly with hashed passwords.
9.	API Validation:
o	Use tools like Postman to test backend API endpoints for:
	Registration (POST /register).
	Login (POST /login).
	User Fetching (GET /users).
	Edit User (PUT /users/:id).
	Delete User (DELETE /users/:id).
o	Confirm that unauthorized access attempts to APIs return appropriate error responses.
10.	Role-Based Navigation:
o	Verify that navigation buttons or links for actions are dynamically shown or hidden based on the logged-in user's role.
By following these steps, the examiner can comprehensively validate the RBAC application, ensuring all features and security measures are functioning as expected.
Project Description: Role-Based Access Control (RBAC) System
The Role-Based Access Control (RBAC) System is a web application designed to manage user permissions and access based on their roles within an organization. It implements fine-grained control over user interactions with resources, ensuring that only authorized individuals can perform specific actions.
Key Features:
1.	User Management:
o	View all registered users in a centralized dashboard.
o	CRUD (Create, Read, Update, Delete) operations for user records based on assigned roles.
2.	Role-Based Permissions:
o	Admin: Can view, edit, and delete user records.
o	Manager: Can view and edit user records but cannot delete them.
o	User: Can only view user records without access to modify or delete them.
3.	Authentication and Authorization:
o	Secure login and registration using token-based authentication (JWT).
o	Role-based access checks at both frontend and backend levels.
4.	Dynamic Toast Notifications:
o	Informative messages for unauthorized access attempts or successful actions, enhancing user experience.
5.	Real-Time Updates:
o	Users can edit and delete records with immediate updates to the displayed data.
Technologies Used:
•	Frontend: React.js for creating a responsive and dynamic user interface.
•	Backend: Node.js with Express.js for handling API requests and implementing business logic.
•	Database: MySQL for storing user data, roles, and permissions.
•	Additional Tools: Axios for API integration, React Router for navigation, and Toastify for notifications.
Project Workflow:
1.	Login and Role Assignment: Users log in and are assigned roles (Admin, Manager, or User), which determine their level of access.
2.	Home Dashboard: A list of all users is fetched from the backend and displayed in a structured table.
3.	Role-Based Actions: Buttons for editing and deleting are conditionally rendered based on the current user's role.
4.	Secure Operations: API calls for updating or deleting data are validated to prevent unauthorized access, with error handling and clear feedback.
Key Highlights:
•	Clean and modular codebase following the MVC (Model-View-Controller) architecture.
•	Robust handling of restricted actions to maintain data integrity and security.
•	Scalability to add more roles and permissions as needed.
This RBAC system is an essential solution for businesses and organizations requiring secure and structured user access management. It demonstrates the practical implementation of access control while ensuring maintainability and user-friendliness.


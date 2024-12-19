# Sign-In and Authentication API

This project provides a server-side API for user authentication, including user registration and sign-in functionality. It supports logging in with either an email address or a phone number.

## Features
- **User Registration**: Create a new account with email, phone number, and password.
- **User Authentication**: Log in with either email or phone number.
- **Password Security**: Passwords are hashed using `bcrypt`.
- **Token-Based Authentication**: A JWT token is generated upon successful sign-in.

## Technologies Used
- **Node.js**: Backend runtime environment.
- **Express.js**: Web framework.
- **MongoDB**: NoSQL database.
- **Mongoose**: ODM for MongoDB.
- **bcrypt**: Password hashing.
- **jsonwebtoken (JWT)**: Token-based authentication.

## Endpoints

### 1. User Registration
**Endpoint**: `POST /signup`

**Request Body**:
```json
{
  "email": "user@example.com",
  "phone": "9876543210",
  "password": "password123"
}
```

**Response**:
- Success: HTTP `201 Created`
  ```json
  {
    "message": "User created"
  }
  ```
- Error: HTTP `400 Bad Request` or `500 Internal Server Error`

---

### 2. User Sign-In
**Endpoint**: `POST /signin`

**Request Body**:
```json
{
  "identifier": "user@example.com or 9876543210",
  "password": "password123"
}
```

**Response**:
- Success: HTTP `200 OK`
  ```json
  {
    "token": "<JWT_TOKEN>",
    "message": "Sign-in successful"
  }
  ```
- Error: HTTP `400 Bad Request` or `500 Internal Server Error`

---

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   ```

2. Navigate to the project directory:
   ```bash
   cd <project-folder>
   ```

3. Install dependencies:
   ```bash
   npm install
   ```



5. Start the server:
   ```bash
   npm start
   ```

## How to Use

1. **Run the Server**: Make sure the server is running by using the `npm start` command.
2. **Register a User**: Use a tool like Postman to send a `POST` request to `/signup` with the user details.
3. **Sign In**: Use a `POST` request to `/signin` with the email or phone number and password.

## Example MongoDB User Schema
```javascript
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  email: { type: String, unique: true, required: true },
  phone: { type: String, unique: true, required: true },
  password: { type: String, required: true },
});

const User = mongoose.model('User', userSchema);
module.exports = User;
```

## Debugging Tips
- Use `console.log` statements to debug API requests and database queries.
- Verify the MongoDB connection and data integrity.
- Test `findOne` queries independently to ensure accurate results.




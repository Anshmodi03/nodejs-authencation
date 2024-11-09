<h1>Role-Based Authentication System with JWT</h1>

<p>This project implements a role-based authentication system using JSON Web Token (JWT) for secure access to routes based on user roles (e.g., <code>admin</code> and <code>user</code>). It includes user registration, login, and access control, allowing only admins to view all users.</p>

<h2>Features</h2>
<ul>
<li><strong>User Authentication</strong>: Users can sign up and log in.</li>
<li><strong>Role-Based Access</strong>: Admins can access routes that regular users cannot.</li>
<li><strong>JWT Token Authentication</strong>: Protects routes with JWT for secure access.</li>
<li><strong>Protected Routes</strong>: Middleware ensures that only authenticated users can access certain routes.</li>
</ul>

<h2>Technologies Used</h2>
<ul>
<li><strong>Node.js</strong> and <strong>Express.js</strong> for server and route handling.</li>
<li><strong>MongoDB</strong> for database storage.</li>
<li><strong>bcrypt.js</strong> for hashing passwords.</li>
<li><strong>jsonwebtoken</strong> for JWT-based authentication.</li>
</ul>

<h2>Installation</h2>
<ol>
<li><strong>Clone the repository</strong>:
<pre><code>git clone https://github.com/yourusername/role-based-auth
cd role-based-auth
</code></pre>
</li>
<li><strong>Install dependencies</strong>:
<pre><code>npm install
</code></pre>
</li>
<li><strong>Set up environment variables</strong>:
<p>Create a <code>.env</code> file in the root directory and add the following:</p>
<pre><code>MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
PORT=3000
</code></pre>
</li>
<li><strong>Start the server</strong>:
<pre><code>npm start
</code></pre>
<p>The server will start on <code>http://localhost:3000</code>.</p>
</li>
</ol>

<h2>API Endpoints</h2>

<h3>1. User Registration (Sign Up)</h3>
<ul>
<li><strong>Endpoint</strong>: <code>/signup</code></li>
<li><strong>Method</strong>: <code>POST</code></li>
<li><strong>Body</strong>:
<pre><code>{
  "name": "User Name",
  "email": "user@example.com",
  "password": "password123",
  "role": "user" // or "admin"
}
</code></pre>
</li>
<li><strong>Description</strong>: Creates a new user account and returns the user details.</li>
</ul>

<h3>2. User Login</h3>
<ul>
<li><strong>Endpoint</strong>: <code>/login</code></li>
<li><strong>Method</strong>: <code>POST</code></li>
<li><strong>Body</strong>:
<pre><code>{
  "email": "user@example.com",
  "password": "password123"
}
</code></pre>
</li>
<li><strong>Description</strong>: Logs in the user and returns a JWT token.</li>
</ul>

<h3>3. Get User Profile (Protected Route)</h3>
<ul>
<li><strong>Endpoint</strong>: <code>/profile</code></li>
<li><strong>Method</strong>: <code>GET</code></li>
<li><strong>Headers</strong>:
<pre><code>Authorization: Bearer
</code></pre>
</li>
<li><strong>Description</strong>: Returns the profile of the logged-in user.</li>
</ul>

<h3>4. Get All Users (Admin-Only Route)</h3>
<ul>
<li><strong>Endpoint</strong>: <code>/users</code></li>
<li><strong>Method</strong>: <code>GET</code></li>
<li><strong>Headers</strong>:
<pre><code>Authorization: Bearer
</code></pre>
</li>
<li><strong>Description</strong>: Returns details of all users. Accessible only to users with the role of <code>admin</code>.</li>
</ul>

<h2>Project Structure</h2>
<pre><code>.
├── middleware/
│   └── auth.js # Middleware for token verification
├── models/
│   └── User.js # User schema and model
├── routes/
│   └── auth.js # Authentication and user routes
├── .env # Environment variables
├── app.js # Main application entry point
└── README.md # Project documentation
</code></pre>

<h2>Usage</h2>
<ol>
<li><strong>Sign Up</strong>: Create users with roles (either <code>admin</code> or <code>user</code>).</li>
<li><strong>Log In</strong>: Use the login route to generate a JWT token.</li>
<li><strong>Access Protected Routes</strong>:
<ul>
<li>Use the <code>/profile</code> route to get user-specific information.</li>
<li>Use the <code>/users</code> route (accessible only for admins) to view all users.</li>
</ul>
</li>
</ol>

<h2>Important Notes</h2>
<ul>
<li>Only <code>admin</code> users can access the <code>/users</code> endpoint to view all registered users.</li>
<li>Ensure to keep your <code>JWT_SECRET</code> secure and do not expose it publicly.</li>
</ul>

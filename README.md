# 🛒 Full-Stack E-Commerce Website

A modern **full-stack E-Commerce web application** built using **React.js** for the frontend and **Spring Boot** for the backend. The application provides a complete shopping experience with product browsing, authentication, cart management, product images, and secure REST APIs.

---


## ✨ Features

### 👤 User Features

* User registration and login
* Secure authentication using **JWT**
* Protected API endpoints
* Browse available products
* View product details
* Product category filtering
* Add products to cart
* Increase/decrease product quantity
* Remove products from cart
* Persistent shopping cart

### 🛠️ Backend Features

* RESTful API architecture
* Spring Boot backend
* Spring Security authentication
* JWT-based authorization
* PostgreSQL database integration
* Product management APIs
* Product image handling
* Exception handling
* Layered backend architecture

### 🎨 Frontend Features

* Responsive React UI
* Component-based architecture
* React Context API for state management
* Axios for API communication
* Dynamic product rendering
* Shopping cart state management
* Product image loading

---

## 🛠️ Tech Stack

| Layer           | Technology              |
| --------------- | ----------------------- |
| Frontend        | React.js                |
| Language        | JavaScript              |
| Backend         | Java                    |
| Framework       | Spring Boot             |
| Security        | Spring Security + JWT   |
| API             | REST API                |
| Database        | PostgreSQL              |
| HTTP Client     | Axios                   |
| Build Tool      | Maven                   |
| Version Control | Git & GitHub            |
| IDE             | IntelliJ IDEA / VS Code |

---

# 🏗️ Project Architecture

```text
                 ┌─────────────────────┐
                 │     React.js        │
                 │      Frontend       │
                 └──────────┬──────────┘
                            │
                         Axios
                            │
                            ▼
                 ┌─────────────────────┐
                 │    REST API         │
                 │    Spring Boot      │
                 └──────────┬──────────┘
                            │
                  Spring Security
                       + JWT
                            │
                            ▼
                 ┌─────────────────────┐
                 │     PostgreSQL      │
                 │      Database       │
                 └─────────────────────┘
```

---

# 📂 Project Structure

## Frontend

```text
frontend/
│
├── public/
│
├── src/
│   ├── Components/
│   │   ├── Navbar/
│   │   ├── Product/
│   │   └── Cart/
│   │
│   ├── Context/
│   │   └── Context.jsx
│   │
│   ├── Pages/
│   │   ├── Home.jsx
│   │   ├── Login.jsx
│   │   └── Cart.jsx
│   │
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
│
├── package.json
└── vite.config.js
```

## Backend

```text
backend/
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── project/
│   │   │           ├── Controller/
│   │   │           ├── Service/
│   │   │           ├── Repository/
│   │   │           ├── Model/
│   │   │           ├── Config/
│   │   │           └── Security/
│   │   │
│   │   └── resources/
│   │       ├── application.properties
│   │       └── data.sql
│   │
│   └── test/
│
├── pom.xml
└── README.md
```

> Update the package/folder names above to exactly match your project structure.

---

# 🔌 API Endpoints

The backend exposes REST APIs for managing products, authentication, and other application functionality.

## 🛍️ Product APIs

| Method   | Endpoint                  | Description       |
| -------- | ------------------------- | ----------------- |
| `GET`    | `/api/products`           | Get all products  |
| `GET`    | `/api/product/{id}`       | Get product by ID |
| `GET`    | `/api/product/{id}/image` | Get product image |
| `POST`   | `/api/product`            | Add a product     |
| `PUT`    | `/api/product/{id}`       | Update a product  |
| `DELETE` | `/api/product/{id}`       | Delete a product  |

### Example

```http
GET http://localhost:8080/api/products
```

---

## 🔐 Authentication APIs

Example authentication endpoints:

| Method | Endpoint    | Description         |
| ------ | ----------- | ------------------- |
| `POST` | `/login`    | Authenticate user   |
| `POST` | `/register` | Register a new user |

Example login request:

```json
{
  "username": "user",
  "password": "password"
}
```

Example JWT response:

```json
{
  "token": "your-jwt-token"
}
```

> Update these endpoints according to the actual mappings in your Spring Boot controllers.

---

# ⚙️ Installation & Setup

## 1️⃣ Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

Move into the project:

```bash
cd YOUR_REPOSITORY
```

---

# 🗄️ 2️⃣ Configure PostgreSQL

Make sure PostgreSQL is installed and running.

Create a database:

```sql
CREATE DATABASE ecommerce;
```

Then configure your Spring Boot application.

Example `application.properties`:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/ecommerce
spring.datasource.username=postgres
spring.datasource.password=YOUR_PASSWORD

spring.jpa.hibernate.ddl-auto=update

spring.jpa.show-sql=true
```

⚠️ **Do not upload your real database password to GitHub.**

For production, use environment variables instead.

---

# ☕ 3️⃣ Run the Spring Boot Backend

Open the backend folder:

```bash
cd backend
```

Run the application using Maven:

```bash
./mvnw spring-boot:run
```

On Windows:

```bash
mvnw.cmd spring-boot:run
```

Or run the main Spring Boot class directly from IntelliJ IDEA.

The backend will normally start at:

```text
http://localhost:8080
```

---

# ⚛️ 4️⃣ Run the React Frontend

Open another terminal:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

The frontend will normally be available at:

```text
http://localhost:5173
```

---

# 🔗 Frontend → Backend Configuration

Make sure your React application points to the correct backend URL.

Example:

```javascript
const API_URL = "http://localhost:8080";
```

For example:

```javascript
axios.get("http://localhost:8080/api/products");
```

For production deployment, replace the localhost URL with your deployed backend URL.

---

# 🔐 Environment Variables

For security, sensitive information should not be hard-coded.

Example backend configuration:

```properties
spring.datasource.url=${DATABASE_URL}
spring.datasource.username=${DATABASE_USERNAME}
spring.datasource.password=${DATABASE_PASSWORD}

jwt.secret=${JWT_SECRET}
```

Frontend:

```env
VITE_API_URL=http://localhost:8080
```

Then use:

```javascript
const API_URL = import.meta.env.VITE_API_URL;
```

### ⚠️ Never commit:

```text
.env
```

Add it to `.gitignore`:

```gitignore
.env
node_modules/
target/
*.class
```

---

# 🚀 Deployment

The application consists of two separate parts:

```text
Frontend → React
Backend  → Spring Boot
Database → PostgreSQL
```

They can be deployed independently.

---

## 🌐 Frontend Deployment

Build the React application:

```bash
npm run build
```

This creates a production build inside:

```text
dist/
```

The `dist` folder can then be deployed to a static hosting service such as **Vercel** or **Netlify**.

Before deploying, configure:

```env
VITE_API_URL=https://your-backend-url.com
```

Then rebuild:

```bash
npm run build
```

---

## ☕ Backend Deployment

Create a production JAR:

```bash
mvn clean package
```

The JAR will be generated inside:

```text
target/
```

Run it using:

```bash
java -jar target/your-application.jar
```

The Spring Boot backend can be deployed to a cloud server/platform that supports Java applications.

---

# 🐘 PostgreSQL Deployment

For production, use a hosted PostgreSQL database rather than your local database.

Configure the backend with the production database credentials:

```properties
spring.datasource.url=${DATABASE_URL}
spring.datasource.username=${DATABASE_USERNAME}
spring.datasource.password=${DATABASE_PASSWORD}
```

Do not expose these credentials in your GitHub repository.

---

# 🔄 Production Architecture

```text
                    INTERNET
                       │
            ┌──────────┴──────────┐
            │                     │
            ▼                     ▼
     React Frontend        Spring Boot Backend
       (Frontend)              (Backend)
                                  │
                                  │
                                  ▼
                           PostgreSQL DB
```

---

# 🧪 Testing the API

You can test the backend APIs using tools such as:

* Postman
* Thunder Client
* Browser
* cURL

Example:

```bash
curl http://localhost:8080/api/products
```

---

# 🐛 Troubleshooting

### Backend does not start

Check:

```text
Java version
Maven installation
PostgreSQL connection
application.properties
Port 8080
```

### Frontend cannot connect to backend

Check:

```text
Backend is running
Correct API URL
CORS configuration
Frontend environment variables
```

### Database connection error

Verify:

```text
Database name
Username
Password
PostgreSQL service
Database port
```

Default PostgreSQL port:

```text
5432
```

---

# 🔒 Security

This project uses **Spring Security and JWT-based authentication** to secure protected resources.

Security considerations include:

* Password encryption
* JWT authentication
* Protected API endpoints
* Authorization
* Environment variables for secrets
* Secure database credentials

---

# 📈 Future Improvements

Possible improvements include:

* 💳 Online payment integration
* 📦 Order tracking
* ⭐ Product reviews and ratings
* ❤️ Wishlist
* 🔎 Advanced product search
* 🏷️ Discount and coupon system
* 📧 Email notifications
* 👨‍💼 Admin dashboard
* 📊 Sales analytics
* ☁️ Cloud deployment
* 🐳 Docker containerization

---

# 🎯 Learning Outcomes

This project demonstrates practical experience with:

* Full-stack web development
* Java and Spring Boot
* REST API development
* Spring Security
* JWT authentication
* React.js
* React state management
* Axios
* PostgreSQL
* Git and GitHub
* Frontend-backend integration
* Application deployment

---

# 👨‍💻 Author

**Your Name**

B.Tech Computer Science & Engineering

### Connect With Me

* GitHub: `https://github.com/YOUR_USERNAME`
* LinkedIn: `https://linkedin.com/in/YOUR_USERNAME`

---

# ⭐ Support

If you found this project useful, consider giving it a ⭐ on GitHub!

---

## 📜 License

This project is created for educational and development purposes.

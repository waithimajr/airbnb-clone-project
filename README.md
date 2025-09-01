# airbnb-clone-project
Backend repo for airbnb-clone-project. Provides secure APIs, database management, and cloud integration. Built with Node.js/Express, PostgreSQL, Docker, Kubernetes, and AWS. Features: user auth, role-based access, CRUD, and monitoring. CI/CD via GitHub Actions ensures scalable, secure deployment

# AirBnB Clone Project
## Overview
This project is a simplified clone of the AirBnB platform.  
The main objective is to build a full web application (front-end + back-end + database + API) that mimics the core functionality of AirBnB.

The project is designed to help understand and practice:
- Object-oriented programming
- File storage vs database storage
- Creating APIs
- Building front-end interfaces
- Deployment and scalability

## Project Goals
- Build a command-line interpreter to manage AirBnB objects.
- Implement a storage engine (file & database).
- Develop APIs to handle requests.
- Design and develop a front-end (static and dynamic).
- Integrate all components to create a functional AirBnB clone.


## Technology Stack

### **Back-End**
- **Python**: The main programming language used to build the application logic.  
- **Flask**: A lightweight Python web framework for creating APIs and serving web content.  
- **SQLAlchemy**: An ORM (Object Relational Mapper) used to interact with the database in a Pythonic way.  

### **Database**
- **MySQL**: A relational database system to store user data, bookings, listings, and other application records.  

### **Front-End**
- **HTML**: Provides the structure of the web pages.  
- **CSS**: Adds styling and layout to the application’s interface.  
- **JavaScript**: Enables interactivity and dynamic content updates on the client side.  

### **Version Control**
- **Git & GitHub**: For source code management, collaboration, and version control. 

### **Deployment (TBD)**
- **Docker**: Containerization tool for consistent environments across development and production.  
- **Nginx / Gunicorn**: Web server and WSGI server to serve the app efficiently.  
- **Heroku / AWS**: Potential cloud platforms for hosting and deployment.  


## Repository Structure
airbnb-clone-project/
│── README.md
│── models/ # Data models
│── tests/ # Unit tests
│── console.py # Command-line interpreter
│── web_static/ # Front-end static files
│── api/ # RESTful API
│── ...


## Database Design

The database is designed to support the core functionality of the AirBnB Clone, ensuring data consistency and scalability.

### **Key Entities**

#### 1. Users
Represents people who use the platform (hosts and guests).
- **id** (Primary Key)
- **name**
- **email**
- **password_hash**
- **role** (guest, host, admin)

#### 2. Properties
Represents listings created by hosts.
- **id** (Primary Key)
- **host_id** (Foreign Key → Users.id)
- **title**
- **description**
- **location**
- **price_per_night**

#### 3. Bookings
Represents reservations made by guests.
- **id** (Primary Key)
- **user_id** (Foreign Key → Users.id)
- **property_id** (Foreign Key → Properties.id)
- **check_in_date**
- **check_out_date**
- **status** (pending, confirmed, cancelled)

#### 4. Reviews
Represents feedback left by guests after a booking.
- **id** (Primary Key)
- **user_id** (Foreign Key → Users.id)
- **property_id** (Foreign Key → Properties.id)
- **rating** (1–5 stars)
- **comment**

#### 5. Payments
Represents transactions for bookings.
- **id** (Primary Key)
- **booking_id** (Foreign Key → Bookings.id)
- **amount**
- **payment_date**
- **status** (paid, pending, failed)

### **Entity Relationships**
- A **User** can be both a **host** (owns Properties) and a **guest** (makes Bookings).  
- A **Property** belongs to a **User** (host).  
- A **Booking** belongs to both a **User** (guest) and a **Property**.  
- A **Review** is written by a **User** (guest) for a **Property** after a Booking.  
- A **Payment** is associated with a **Booking**.  

## Feature Breakdown

### 1. User Management
Allows users to register, log in, and manage their profiles.  
Users can act as **hosts** (listing properties) or **guests** (booking properties). This feature ensures secure authentication and role-based functionality.  

### 2. Property Management
Hosts can create, update, and delete property listings.  
Each property includes details like title, description, location, price, and availability, making it easy for guests to find suitable accommodations.  

### 3. Booking System
Guests can search for properties, check availability, and make reservations.  
The booking system manages check-in/check-out dates, booking status (pending, confirmed, cancelled), and ensures no double-bookings occur.  

### 4. Review System
Guests can leave reviews and ratings for properties after completing a stay.  
This builds trust on the platform, helping other guests make informed decisions and motivating hosts to maintain quality standards.  

### 5. Payment System
Enables guests to securely pay for their bookings.  
Payments are linked to bookings, with statuses like paid, pending, or failed, ensuring clear tracking of financial transactions.  

### 6. Search and Filtering
Guests can search for properties by location, price, dates, and amenities.  
This feature improves usability by helping users quickly find the most relevant listings.  

### 7. API Endpoints
RESTful APIs handle communication between the front-end and back-end.  
They make it possible for external clients or future mobile apps to interact with the system efficiently.  

### 8. Front-End Interface
A responsive web interface allows users to browse properties, manage bookings, and interact with the system easily.  
Built with HTML, CSS, and JavaScript, it provides an intuitive experience for both guests and hosts. 

## API Security

Securing the backend APIs is critical for protecting sensitive user information, ensuring safe transactions, and maintaining the overall trust of the platform.  

### **Key Security Measures**

#### 1. Authentication
- **What it is:** Ensures that only verified users can access the system by requiring login credentials (e.g., email + password) or tokens (JWT).  
- **Why it matters:** Protects user accounts and prevents unauthorized access to personal data, bookings, and payments.  

#### 2. Authorization
- **What it is:** Determines what actions an authenticated user is allowed to perform. For example, a host can manage properties, but only a guest can make bookings.  
- **Why it matters:** Prevents privilege escalation and ensures that users only perform actions appropriate to their role.  

#### 3. Data Encryption
- **What it is:** Encrypts sensitive data (e.g., passwords, payment information) both in transit (HTTPS/SSL) and at rest (database encryption).  
- **Why it matters:** Protects user credentials, personal details, and financial transactions from being intercepted or stolen.  

#### 4. Rate Limiting & Throttling
- **What it is:** Restricts the number of requests a client can make in a given period.  
- **Why it matters:** Prevents abuse of APIs, denial-of-service attacks, and protects system performance.  

#### 5. Input Validation & Sanitization
- **What it is:** Ensures that all input data (e.g., form submissions, API requests) is checked and cleaned before processing.  
- **Why it matters:** Prevents common vulnerabilities such as SQL injection, cross-site scripting (XSS), and command injection.  

#### 6. Secure Payment Handling
- **What it is:** Uses secure third-party payment gateways and tokenization to handle financial transactions.  
- **Why it matters:** Protects sensitive payment details and ensures compliance with standards like PCI-DSS.  

---

### **Why Security is Crucial**
- **Protecting User Data:** Safeguards sensitive information such as personal details, passwords, and bookings.  
- **Securing Payments:** Ensures that financial transactions are processed safely without leaks or fraud.  
- **Maintaining Trust:** Builds user confidence in the platform, which is essential for adoption and growth.  
- **Compliance:** Meets legal and industry requirements for data protection (e.g., GDPR, PCI compliance).  

## CI/CD Pipeline

### **What is CI/CD?**
CI/CD stands for **Continuous Integration (CI)** and **Continuous Deployment/Delivery (CD)**.  
It is a development practice that automates the process of testing, building, and deploying applications.  

- **Continuous Integration (CI):** Ensures that code changes are automatically tested and merged into the main branch without breaking the application.  
- **Continuous Deployment (CD):** Automates the release process so that new features and fixes are delivered to users quickly and reliably.  

### **Why it is Important for the Project**
- **Faster Development:** Automates repetitive tasks like testing and deployment, speeding up the release cycle.  
- **Improved Quality:** Runs automated tests on every commit to catch bugs early before they reach production.  
- **Consistency:** Ensures the application works the same way across different environments (development, staging, production).  
- **Reliability:** Reduces human error by using automation for builds, tests, and deployments.  

### **Tools to Use**
- **GitHub Actions:** For automating workflows such as running tests and deploying code on every push or pull request.  
- **Docker:** For containerizing the application, ensuring consistent environments during development and production.  
- **Jenkins / GitLab CI:** Alternative CI/CD tools that can be integrated if more flexibility is needed.  
- **Heroku / AWS / DigitalOcean:** Hosting platforms where automated deployments can be made.  

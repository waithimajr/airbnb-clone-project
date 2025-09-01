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

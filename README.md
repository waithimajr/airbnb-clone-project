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

---

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

---

## Repository Structure
airbnb-clone-project/
│── README.md
│── models/ # Data models
│── tests/ # Unit tests
│── console.py # Command-line interpreter
│── web_static/ # Front-end static files
│── api/ # RESTful API
│── ...

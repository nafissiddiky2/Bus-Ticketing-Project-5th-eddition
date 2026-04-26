Bus Ticketing web is not connected with database for GitHub Limitation ,But fully functonal
[Bus Ticketing](https://nafissiddiky2.github.io/Bus-Ticketing-Project-5th-eddition/)

<img width="1317" height="468" alt="image" src="https://github.com/user-attachments/assets/81e13328-8fd8-4a74-88f5-681c1e73f668" />

# 🚌 [Bus Ticket Booking System](https://unsent-jiffy-armband.ngrok-free.dev/)

A full-stack web application for booking bus tickets online. Built with Flask, MySQL, and Bootstrap.

![Bus Booking System](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.3.2-green.svg)
![MySQL](https://img.shields.io/badge/MySQL-5.7+-orange.svg)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-purple.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

## 📋 Table of Contents

- [Features](#features)
- [Demo](#demo)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Database Schema](#database-schema)
- [Screenshots](#screenshots)
- [License](#license)

## ✨ Features

### For Customers:
- 🏠 **Home Page** - View system statistics and available buses
- 🚌 **Browse Buses** - View all available buses with filtering options
  - All Buses
  - Business Class
  - AC Buses
- 🎫 **Book Tickets** - Easy ticket booking with validation
  - Maximum 4 tickets per booking
  - Real-time seat availability check
  - Instant price calculation
- 📋 **My Bookings** - Search and manage bookings
  - Search by Booking ID or Phone Number
  - Cancel bookings
  - View booking status

### For Administrators:
- 🔐 **Secure Login** - Password protected admin panel
- 📊 **Dashboard** - Real-time statistics
  - Total Buses
  - Total Bookings
  - Total Revenue
- 🚍 **Bus Management**
  - Add new buses
  - Delete existing buses
  - Reset individual bus seats to full capacity
- 📋 **Booking Overview** - View all bookings and their status

### Additional Features:
- ✅ Input validation (frontend + backend)
- ✅ Responsive design (mobile-friendly)
- ✅ Toast notifications for user feedback
- ✅ MySQL database for persistent storage
- ✅ RESTful API architecture



## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| **Python 3.8+** | Backend programming language |
| **Flask 2.3.2** | Web framework |
| **MySQL** | Database |
| **PyMySQL** | MySQL connector for Python |
| **Bootstrap 5.3** | Frontend CSS framework |
| **Bootstrap Icons** | Icon library |
| **HTML5/CSS3** | Structure and styling |
| **JavaScript (ES6)** | Client-side interactivity |
| **Flask-CORS** | Cross-Origin Resource Sharing |
| **ngrok** | Secure tunneling for demos |

## 📁 Project Structure

## 📁 Project Structure

### Main Directories:

| Directory | Description |
|-----------|-------------|
| **`/backend`** | Flask application and database configuration |
| **`/frontend`** | HTML templates and static files |
| **`/database`** | SQL schema files |
| **`/screenshots`** | Application screenshots |

### Key Files:

| File | Location | Description |
|------|----------|-------------|
| `app.py` | `/backend` | Main Flask application with all routes |
| `db_config.py` | `/backend` | MySQL database connection settings |
| `index.html` | `/frontend` | Complete frontend template |
| `requirements.txt` | Root | Python package dependencies |

### Complete Tree:



## 🔧 Installation

### Prerequisites
- Python 3.8 or higher
- MySQL 5.7 or higher (XAMPP recommended)
- pip (Python package manager)
- Git

### Step 1: Clone the Repository
git clone (https://github.com/nafissiddiky2/Bus-Ticketing-Project-5th-eddition.git)
cd bus-booking-system

###Step 2: Create Virtual Environment

# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate

Step 3: Install Dependencies

pip install -r requirements.txt

Step 4: Set Up Database

1) Start XAMPP (Apache & MySQL)

2) Open phpMyAdmin (http://localhost/phpmyadmin)

3) Create database: bus_booking_system

4) The tables will be created automatically on first run

Step 5: Configure Database
Update backend/db_config.py with your MySQL credentials:
DB_CONFIG = {
    'host': 'localhost',
    'user': 'root',
    'password': '',  # Your MySQL password
    'database': 'bus_booking_system',
    'cursorclass': pymysql.cursors.DictCursor
}

Step 6: Run the Application

cd backend
python app.py

⚙️ Configuration
Environment Variables (Optional)
Create a .env file in the backend directory:

DB_HOST=localhost
DB_USER=root
DB_PASSWORD=
DB_NAME=bus_booking_system

Sample Bus Data
The system automatically adds sample buses on first run:
AFM Express (Dhaka - Rangpur)
Lemon Line (Dhaka - Cox-Bazzer)
S.N.Express (Dhaka - Satkhira)
Beach Voyager (Dhaka-Cox Bazar)
Mountain Express (Dhaka-Rangamati)
SECRET_KEY=your-secret-key-here

📖 Usage
Customer Flow
1) Visit the homepage
2) Click "View Available Buses"
3) Browse buses by category
4) Click "Book Now" on desired bus
5) Fill passenger details
6) Select number of seats (max 4)
7) Confirm booking
8) Save Booking ID for future reference

Admin Flow

1) Click "Admin" in navigation
2) First time: Click "Setup New Password"
3) Login with password
4) Manage buses from dashboard
5) View statistics and bookings

Search Bookings

1) Go to "My Bookings"
2) Enter Booking ID or Phone Number
3) View booking details
4) Cancel if needed

🔌 API Endpoints
Method       	Endpoint	                           Description	          Auth

GET	        /api/health	                           Health check          	No
GET       	/api/buses	                          Get all buses         	No
POST      	/api/buses	                           Add new bus         	 Admin
DELETE	    /api/buses/<bus_no>                  	Delete bus	           Admin
GET	        /api/bookings                       	Get all bookings	     Admin
POST	      /api/bookings         	              Create booking	        No
GET	        /api/bookings/search?q=	              Search bookings        	No
POST      	/api/bookings/<id>/cancel 	          Cancel booking        	No
POST      	/api/admin/setup	                     Setup admin	          No
POST	      /api/admin/login	                     Admin login          	No
POST	      /api/admin/reset-bus/<bus_no>	         Reset bus seats     	Admin

🗄️ Database Schema

Buses Table

CREATE TABLE buses (
    bus_id INT PRIMARY KEY AUTO_INCREMENT,
    bus_no INT UNIQUE NOT NULL,
    bus_name VARCHAR(100) NOT NULL,
    route VARCHAR(200) NOT NULL,
    bus_type ENUM('BUSINESS', 'AC') NOT NULL,
    total_seats INT NOT NULL,
    available_seats INT NOT NULL,
    rent DECIMAL(10, 2) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

Bookings Table

CREATE TABLE bookings (
    booking_id INT PRIMARY KEY AUTO_INCREMENT,
    bus_no INT NOT NULL,
    passenger_name VARCHAR(100) NOT NULL,
    passenger_phone VARCHAR(20),
    passenger_email VARCHAR(100),
    seats_booked INT NOT NULL,
    total_amount DECIMAL(10, 2) NOT NULL,
    booking_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status ENUM('CONFIRMED', 'CANCELLED') DEFAULT 'CONFIRMED',
    FOREIGN KEY (bus_no) REFERENCES buses(bus_no)
);

Admins Table

CREATE TABLE admins (
    admin_id INT PRIMARY KEY AUTO_INCREMENT,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

📸 Screenshots
Home Page:
<img width="1376" height="842" alt="image" src="https://github.com/user-attachments/assets/c477953a-fab0-4d50-9af2-12899f34a0ae" />

Available Buses
<img width="1389" height="860" alt="image" src="https://github.com/user-attachments/assets/772d857b-6aad-4c38-be6c-df2682477e33" />

Booking Modal
<img width="515" height="665" alt="image" src="https://github.com/user-attachments/assets/1b2fc413-c8aa-49e4-a495-08ed78cf0256" />

Admin Dashboard

<img width="1372" height="861" alt="image" src="https://github.com/user-attachments/assets/687ddf68-e87e-4114-9ba3-e71ad39a696a" />
<img width="1372" height="861" alt="image" src="https://github.com/user-attachments/assets/f3298469-dd98-4d5b-9b33-4a5ce3c3ee2b" />

My Bookings

<img width="1361" height="858" alt="image" src="https://github.com/user-attachments/assets/d42c55c7-0e0a-459f-aef0-cc9b23db8dd0" />


🚀 Deployment
Using ngrok (For Demos)

# Terminal 1 - Run Flask
python backend/app.py

# Terminal 2 - Run ngrok
ngrok http 5000


🔮 Future Enhancements

Email notifications for bookings
PDF ticket generation
Payment gateway integration (bKash/Nagad)
Seat selection map
Advanced search filters
User accounts and profiles
Discount coupon system
Multi-language support (Bangla/English)
PWA (Progressive Web App)
Analytics dashboard

🐛 Known Issues
Admin password is stored in plain text (use hashing in production)
No session timeout for admin login
Limited to 4 tickets per booking

📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

🤝 Contributing
1) Fork the repository
2) Create your feature branch (git checkout -b feature/AmazingFeature)
3) Commit your changes (git commit -m 'Add some AmazingFeature')
4) Push to the branch (git push origin feature/AmazingFeature)
5) Open a Pull Reques

Project Maker: 
Name : [Saad Al Nafis Siddiky](https://github.com/nafissiddiky2)

Email: nafissiddiky2@gmail.com

GitHub: [@nafissiddiky2](https://github.com/nafissiddiky2)

⭐ Star this repository if you found it helpful!
Built with ❤️ for comfortable bus travel in Bangladesh.

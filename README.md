# Airport Management System

![Django](https://img.shields.io/badge/Django-6.0-green.svg)
![Python](https://img.shields.io/badge/Python-3.14-blue.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

A comprehensive web-based airport management system built with Django 6.0, featuring flight search, ticket booking with interactive seat selection, and real-time availability management.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [System Architecture](#system-architecture)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Usage Guide](#usage-guide)
- [Database Schema](#database-schema)
- [API Endpoints](#api-endpoints)
- [C++ Microservice](#c-microservice)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Project Overview

The Airport Management System is a full-stack web application designed to streamline airport operations and enhance the passenger booking experience. The system provides a modern, intuitive interface for flight search, seat selection, and booking management, while maintaining robust data validation and security standards.

### Key Capabilities

- **User Authentication System**: Secure registration, login, and profile management
- **Advanced Flight Search**: Multi-criteria search with real-time filtering
- **Interactive Seat Selection**: Visual aircraft seating layout with availability indicators
- **Booking Management**: Complete order history and ticket management
- **Administrative Interface**: Full CRUD operations for flights, aircraft, and users
- **Data Validation**: Server-side validation ensuring data integrity
- **Responsive Design**: Mobile-optimized dark-theme interface
- **Microservice Architecture**: C++ service for computational tasks

---

## Features

### User Features

- User registration and authentication system
- Flight search with source and destination filtering
- Pagination support for large datasets
- Interactive seat selection interface
- Multi-seat booking capability
- Order history with detailed ticket information
- Profile management (name, email updates)
- Responsive design for mobile and desktop

### Administrator Features

- Aircraft management (CRUD operations)
- Flight scheduling and route management
- User account management
- Comprehensive booking and ticket oversight
- Django Admin interface integration
- Database migration management

---

## Technology Stack

### Backend Technologies

- **Django 6.0** - High-level Python web framework
- **Python 3.14** - Core programming language
- **SQLite** - Embedded relational database (development)
- **Django ORM** - Object-relational mapping system
- **Django Crispy Forms** - Enhanced form rendering
- **python-decouple** - Environment configuration management
- **Requests** - HTTP library for external API calls

### Frontend Technologies

- **Bootstrap 4.5.3** - Responsive CSS framework
- **HTML5** - Semantic markup language
- **CSS3** - Modern styling with glassmorphism effects
- **JavaScript (ES6)** - Client-side interactivity
- **Google Fonts (Inter)** - Professional typography
- **Custom CSS** - Dark theme implementation

### Additional Services

- **C++ Crow Framework** - High-performance REST API microservice
- **ASIO Library** - Asynchronous I/O operations
- **JSON** - Data interchange format

### Development Tools

- **Git** - Version control system
- **VS Code** - Integrated development environment
- **Django Debug Toolbar** - Performance profiling (optional)
- **Coverage.py** - Code coverage analysis

---

## System Architecture

### Project Structure

```
course_project_airport/
├── airport/                      # Django project configuration
│   ├── settings.py              # Application settings
│   ├── urls.py                  # Root URL configuration
│   ├── wsgi.py                  # WSGI application
│   └── asgi.py                  # ASGI application
├── hangar/                       # Core application module
│   ├── models.py                # Data models
│   ├── views.py                 # View controllers
│   ├── forms.py                 # Form definitions
│   ├── urls.py                  # Application routing
│   ├── admin.py                 # Admin configuration
│   ├── apps.py                  # Application configuration
│   └── migrations/              # Database migrations
├── templates/                    # HTML template files
│   ├── base.html                # Base template
│   ├── hangar/                  # Application templates
│   │   ├── index.html           # Landing page
│   │   ├── flight_list.html     # Flight listing
│   │   ├── flight_details.html  # Seat selection
│   │   ├── airplane_list.html   # Aircraft listing
│   │   ├── airplane_details.html
│   │   ├── user_details.html    # User profile
│   │   └── user_form.html       # Registration form
│   ├── includes/
│   │   └── sidebar.html         # Navigation component
│   └── registration/
│       └── login.html           # Authentication form
├── static/                       # Static assets
│   ├── css/
│   │   └── styles.css           # Global stylesheet
│   └── images/                  # Image resources
├── staticfiles/                  # Collected static files
├── cpp_service/                  # C++ microservice
│   ├── main.cpp                 # Service implementation
│   ├── crow.h                   # Crow framework
│   └── asio_lib/                # ASIO library
├── db.sqlite3                   # SQLite database
├── manage.py                    # Django management script
├── requirements.txt             # Python dependencies
└── README.md                    # Documentation
```

### Data Model Architecture

```
AbstractUser (Django Framework)
    |
    | (Inheritance)
    v
   User -----------------> Order -----------------> Ticket
                            |                         |
                        (One-to-Many)            (Many-to-One)
                                                     |
Flight <----------------------------------------------|
  |                                            (Booking)
  | (Many-to-One)
  v
Airplane
```

### Component Interaction Flow

```
[Client Browser] <--> [Django Views] <--> [Django ORM] <--> [SQLite Database]
                            |
                            v
                    [C++ Microservice]
                     (Crow Framework)
```

---

## Installation

### Prerequisites

- Python 3.10 or higher (Python 3.14 recommended)
- pip package manager
- Git version control system
- C++ compiler (optional, for microservice)
- Virtual environment support

### Step 1: Clone Repository

```bash
git clone https://github.com/Ntaviouk/airport-management.git
cd airport-management
```

### Step 2: Create Virtual Environment

**Windows (PowerShell):**
```powershell
python -m venv .venv
.\.venv\Scripts\activate
```

**macOS/Linux:**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

The following packages will be installed:
- Django 6.0
- django-crispy-forms 2.2
- crispy-bootstrap4 2024.1
- python-decouple 3.8
- requests 2.32.5
- Additional dependencies as specified

### Step 4: Database Configuration

```bash
python manage.py makemigrations
python manage.py migrate
```

This creates the SQLite database and applies all migrations for the following models:
- User (authentication)
- Airplane (aircraft information)
- Flight (route schedules)
- Order (booking records)
- Ticket (seat reservations)

### Step 5: Create Administrative Account

```bash
python manage.py createsuperuser
```

Provide the following information:
- Username: (administrative username)
- Email address: (valid email)
- Password: (minimum 8 characters)
- Password confirmation: (re-enter password)

### Step 6: Collect Static Files

```bash
python manage.py collectstatic --noinput
```

This command collects all static assets into the `staticfiles/` directory for production deployment.

---

## Running the Application

### Development Server

Start the Django development server:

```bash
python manage.py runserver
```

The application will be accessible at: **http://127.0.0.1:8000/**

### Administrative Interface

Access the Django admin panel at: **http://127.0.0.1:8000/admin/**

Credentials:
- Username: (superuser account created in Step 5)
- Password: (superuser password)

### Server Management

**Stop the server:**
Press `Ctrl + C` in the terminal

**Custom port:**
```bash
python manage.py runserver 8080
```

**Custom host and port:**
```bash
python manage.py runserver 0.0.0.0:8000
```

---

## Usage Guide

### 1. Homepage Navigation

Upon accessing **http://127.0.0.1:8000/**, users are presented with:
- **Flights Card**: Navigate to flight search and listing
- **Airplanes Card**: View aircraft fleet information
- **Navigation Menu**: Access authentication and profile features

### 2. User Registration

Registration workflow:
1. Click **Registration** in the navigation menu
2. Complete the registration form:
   - Username (unique identifier)
   - Email address (valid format required)
   - Password (minimum 8 characters)
   - Password confirmation
3. Submit form
4. Automatic authentication upon successful registration

### 3. Flight Search

Flight discovery process:
1. Navigate to **Flights** section
2. Utilize search filters:
   - Source city (departure location)
   - Destination city (arrival location)
3. Execute search query
4. Browse paginated results (5 flights per page)
5. Select desired flight for detailed information

### 4. Seat Selection and Booking

Ticket reservation workflow:
1. Select flight from search results
2. Access flight details page
3. View interactive seat map:
   - Green seats: Available for booking
   - Dark seats: Already reserved
4. Select desired seats (multiple selection supported)
5. Click **Book** button
6. Confirm reservation
7. Order created and tickets generated

### 5. Order Management

View booking history:
1. Click username in navigation menu
2. Access user profile page
3. Review sections:
   - Personal information
   - Order history (paginated, 5 per page)
   - Individual ticket details
   - Booking timestamps

### 6. Profile Management

Update account information:
1. Navigate to user profile
2. Click **Edit Profile** button
3. Modify fields:
   - First name
   - Last name
   - Email address
4. Save changes
5. Confirmation message displayed

### 7. Administrative Functions

Admin panel capabilities:
1. Access **http://127.0.0.1:8000/admin/**
2. Authenticate with superuser credentials
3. Available operations:
   - Manage aircraft (add, edit, delete)
   - Create and modify flight routes
   - Assign aircraft to flights
   - View all orders and tickets
   - User account management
   - Database model administration

---

## Database Schema

### User Model

Extends Django's AbstractUser with authentication capabilities.

| Field | Type | Description |
|-------|------|-------------|
| id | Integer (PK) | Primary key identifier |
| username | String (150) | Unique username (indexed) |
| email | String (254) | Email address |
| password | String (128) | Hashed password (PBKDF2) |
| first_name | String (150) | User's first name |
| last_name | String (150) | User's last name |
| is_active | Boolean | Account activation status |
| is_staff | Boolean | Administrative privileges |
| is_superuser | Boolean | Full system access |
| date_joined | DateTime | Registration timestamp |
| last_login | DateTime | Last authentication time |

**Constraints:**
- Username must be unique
- Email validation enforced
- Password stored as hash (security compliance)

### Airplane Model

Represents aircraft in the system fleet.

| Field | Type | Description |
|-------|------|-------------|
| id | Integer (PK) | Primary key identifier |
| name | String (255) | Aircraft designation |
| rows | Integer | Number of seat rows |
| seats_in_row | Integer | Seats per row |
| description | Text | Additional information |

**Computed Property:**
- `capacity`: Integer (rows × seats_in_row)

**Meta Options:**
- Default ordering: `['name']`

**Constraints:**
- All fields required (non-nullable)
- Positive integers for rows and seats_in_row

### Flight Model

Represents scheduled flight routes.

| Field | Type | Description |
|-------|------|-------------|
| id | Integer (PK) | Primary key identifier |
| source | String (255) | Departure airport |
| destination | String (255) | Arrival airport |
| duration | Integer | Flight duration (minutes) |
| distance | Integer (nullable) | Distance (kilometers) |
| flight_date | Date | Scheduled flight date |
| airplane_id | Integer (FK) | Foreign key to Airplane |

**Computed Property:**
- `new_name`: String (formatted display name)

**Foreign Key:**
- `airplane`: Airplane model
  - Cascade delete policy
  - Related name: `flights`

**Constraints:**
- Source and destination required
- Duration must be positive
- Distance optional but positive if provided

### Order Model

Represents user booking records.

| Field | Type | Description |
|-------|------|-------------|
| id | Integer (PK) | Primary key identifier |
| created_at | DateTime | Order creation timestamp |
| user_id | Integer (FK) | Foreign key to User |

**Foreign Key:**
- `user`: User model
  - Cascade delete policy
  - Related name: `orders`

**Meta Options:**
- Auto-timestamp on creation: `auto_now_add=True`

### Ticket Model

Represents individual seat reservations.

| Field | Type | Description |
|-------|------|-------------|
| id | Integer (PK) | Primary key identifier |
| row | Integer | Seat row number (1-based) |
| seat | Integer | Seat position in row (1-based) |
| flight_id | Integer (FK) | Foreign key to Flight |
| order_id | Integer (FK) | Foreign key to Order |

**Foreign Keys:**
- `flight`: Flight model (cascade delete, related name: `tickets`)
- `order`: Order model (cascade delete, related name: `tickets`)

**Validation Logic:**
```python
1 <= row <= airplane.rows
1 <= seat <= airplane.seats_in_row
```

**Methods:**
- `validate_ticket(row, seat, flight)`: Static validation method
- `clean()`: Model-level validation hook
- `save()`: Override with full_clean() enforcement

**Constraints:**
- Row and seat must be positive integers
- Validation enforced before database persistence
- Unique constraint recommended: (flight_id, row, seat)

---

## API Endpoints

### Public Routes

| URL Pattern | View | Method | Description |
|------------|------|--------|-------------|
| `/` | IndexView | GET | Landing page |
| `/login/` | LoginView | GET/POST | User authentication |
| `/logout/` | LogoutView | POST | User logout |
| `/registration/` | UserCreationView | GET/POST | New user registration |

### Flight Management

| URL Pattern | View | Method | Description |
|------------|------|--------|-------------|
| `/flights/` | FlightListView | GET | Flight listing with search |
| `/flights/<int:pk>/details/` | FlightDetailView | GET/POST | Flight details and seat selection |

Query Parameters for `/flights/`:
- `source` (string): Filter by departure city
- `destination` (string): Filter by arrival city
- `page` (integer): Pagination page number

### Aircraft Management

| URL Pattern | View | Method | Description |
|------------|------|--------|-------------|
| `/airplanes/` | AirplaneListView | GET | Aircraft fleet listing |
| `/airplanes/<int:pk>/details/` | AirplaneDetailView | GET | Aircraft specifications |

Query Parameters for `/airplanes/`:
- `name` (string): Filter by aircraft name
- `page` (integer): Pagination page number

### User Profile

| URL Pattern | View | Method | Description |
|------------|------|--------|-------------|
| `/user/<int:pk>/profile/` | UserProfileView | GET/POST | User profile and order history |

Query Parameters:
- `page` (integer): Order history pagination

### Administrative Interface

| URL Pattern | Description |
|------------|-------------|
| `/admin/` | Django administrative interface |
| `/admin/hangar/airplane/` | Aircraft management |
| `/admin/hangar/flight/` | Flight management |
| `/admin/hangar/order/` | Order management |
| `/admin/hangar/ticket/` | Ticket management |
| `/admin/auth/user/` | User account management |

---

## C++ Microservice

### Overview

High-performance microservice built with Crow framework for computational operations related to seat availability calculations.

### Service Endpoint

**Base URL:** `http://localhost:8080`

**POST** `/post`

### Request Format

```json
{
  "rows": 30,
  "seats_per_row": 6,
  "booked_seats": [
    [1, 2],
    [1, 3],
    [5, 4],
    [10, 1]
  ]
}
```

**Parameters:**
- `rows` (integer): Total number of rows in aircraft
- `seats_per_row` (integer): Number of seats per row
- `booked_seats` (array): List of [row, seat] coordinates

### Response Format

```json
{
  "message": [
    [1, 1, -1],
    [1, 2, -2],
    [1, 3, -2],
    [1, 4, -1],
    [1, 5, -1],
    [1, 6, -1]
  ]
}
```

**Status Codes:**
- `-1`: Seat available
- `-2`: Seat booked

### Building the Service

**Windows (MinGW):**
```bash
cd cpp_service
g++ -std=c++14 main.cpp -o airport_service.exe -lpthread -lws2_32
airport_service.exe
```

**Linux/macOS:**
```bash
cd cpp_service
g++ -std=c++14 main.cpp -o airport_service -lpthread
./airport_service
```

### Service Architecture

```
[Python Django] --HTTP POST--> [Crow C++ Service:8080]
                                      |
                                      v
                              [ASIO Async I/O]
                                      |
                                      v
                             [Seat Calculation]
                                      |
                                      v
                   <--JSON Response-- [Return Result]
```

---

## Testing

### Running Unit Tests

Execute the complete test suite:

```bash
python manage.py test hangar
```

### Test Coverage Analysis

Install coverage tool:
```bash
pip install coverage
```

Run tests with coverage:
```bash
coverage run --source='.' manage.py test hangar
coverage report
```

Generate HTML coverage report:
```bash
coverage html
```

Open `htmlcov/index.html` in browser to view detailed coverage analysis.

### Test Structure

```
hangar/tests/
├── test_models.py      # Model validation tests
├── test_views.py       # View logic tests
├── test_forms.py       # Form validation tests
└── test_integration.py # End-to-end tests
```

---

## Contributing

### Development Workflow

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/enhancement`)
3. Commit changes (`git commit -m 'Add feature'`)
4. Push to branch (`git push origin feature/enhancement`)
5. Open Pull Request

### Code Standards

- Follow PEP 8 style guide for Python code
- Write comprehensive docstrings for all functions
- Maintain test coverage above 80%
- Use meaningful commit messages
- Document all API changes

---

## License

This project is developed for educational purposes and is available under the MIT License. See LICENSE file for details.

---

## Contact

**Dmytro Daniuk**

- Email: dimasdaniuk@gmail.com
- LinkedIn: [linkedin.com/in/dmytrodaniuk](https://www.linkedin.com/in/dmytrodaniuk)
- GitHub: [@Ntaviouk](https://github.com/Ntaviouk)
- Telegram: [@Ntaviouk](https://t.me/Ntaviouk)
- Instagram: [@dimasdaniuk911](https://www.instagram.com/dimasdaniuk911/)

---

## Additional Resources

### Django Commands Reference

**Create new application:**
```bash
python manage.py startapp app_name
```

**Generate migrations:**
```bash
python manage.py makemigrations
```

**Apply migrations:**
```bash
python manage.py migrate
```

**Interactive shell:**
```bash
python manage.py shell
```

**Database flush:**
```bash
python manage.py flush
```

**Export data:**
```bash
python manage.py dumpdata hangar > fixtures/backup.json
```

**Import data:**
```bash
python manage.py loaddata fixtures/backup.json
```

### Documentation Links

- [Django 6.0 Documentation](https://docs.djangoproject.com/en/6.0/)
- [Bootstrap 4.5 Documentation](https://getbootstrap.com/docs/4.5/)
- [Crow Framework Documentation](https://crowcpp.org/)
- [Python 3.14 Documentation](https://docs.python.org/3.14/)

---

**Copyright 2025 Dmytro Daniuk. All rights reserved.**

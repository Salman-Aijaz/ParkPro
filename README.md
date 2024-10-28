
---

# 🚗 Parking Management System

A comprehensive parking management system designed for high-traffic parking lots. This system is built using **FastAPI** for the backend, **PostgreSQL** (via **Neon DB**) as the primary database, **Redis** for managing the queuing system (FIFO), and **Pydantic** for data validation. **Pytest** is utilized to ensure robust testing and coverage of unit tests.

## 📝 Project Overview

The Parking Management System efficiently handles parking slot allocation, vehicle registration, and parking fee calculations. A queue management feature ensures vehicles are added to a queue when all slots are occupied, processing entries in a **FIFO** (First-In, First-Out) order as spaces become available.

Key functionalities include:
- **Real-Time Slot Management**: Track and update parking slot availability.
- **Vehicle Registration and Exit**: Register vehicles upon entry and calculate fees based on duration when they exit.
- **Queue Management**: Handle overflow efficiently with a Redis-powered queuing system.
- **Error Handling and Validation**: Ensure smooth, error-free operation with validated user inputs and exception handling.

## 🔑 Key Features

### 1. Parking Slot Management
- **CRUD Operations**: Full CRUD capabilities for managing parking slots.
- **Slot Status**: Track each slot's current status (available or occupied) in real time.
- **Dynamic Allocation**: Assign the next available slot to incoming vehicles.

### 2. Vehicle Registration
- **Vehicle Entry**: Register vehicles upon entry with license plate information and timestamp.
- **Queue Integration**: If all slots are occupied, the system queues the vehicle until a slot is free.

### 3. Parking Slot Availability
- **Real-Time Tracking**: Get the current status of all parking slots.
- **Automated Updates**: When a vehicle exits, the slot is marked as available and the next queued vehicle is assigned.

### 4. Vehicle Exit and Fee Calculation
- **Time-Based Fees**: Calculate fees based on parking duration, with a default rate of $50 per hour.
- **Slot Release**: Automatically update the slot status to available upon vehicle exit.

### 5. Queue Management System
- **Redis-Backed Queue**: Store queued vehicles in Redis to handle overflow during peak times.
- **FIFO Processing**: Vehicles are processed in the order they arrived once slots become available.

## 🚀 Tech Stack

- **FastAPI**: High-performance backend framework for building APIs.
- **PostgreSQL (Neon DB)**: SQL database for storing and managing data.
- **Redis**: In-memory data store used here for the queuing system.
- **Pydantic**: Data validation and settings management.
- **Pytest**: Framework for testing, including unit tests to ensure code reliability.

## 📂 Project Structure

```plaintext
├── app/
│   ├── main.py               # Main application file
│   ├── models/               # SQLAlchemy models for database tables
│   ├── schemas/              # Pydantic schemas for request and response models
│   ├── views/                # API route definitions
│   ├── controller/           # Business logic and core functionality
│   ├── utils/                # Utility functions and calculations
│   ├── tests/                # Test files using pytest
│   ├── database.py           # Database connection setup
│   ├── config.py             # Configuration settings for environment variables
└── README.md                 # Project documentation
```

## ⚙️ Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/ParkPro.git
   cd ParkPro
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**  
   - Create a `.env` file in the root directory:
   ```plaintext
   DATABASE_URL=postgresql://<username>:<password>@<host>/<database>
   REDIS_URL=redis://localhost:6379
   ```

4. **Run the application**
   ```bash
   uvicorn app.main:app --reload
   ```

## 🔍 API Documentation

Access the interactive API documentation at: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs).

## 🧪 Testing

This project uses **Pytest** for unit tests. Ensure you have test cases set up to validate edge cases and application functionality.

1. **Run tests**
   ```bash
   pytest -v
   ```

## 🚧 Future Enhancements
- **Automated Queue Rebalancing**: Prioritize vehicles based on additional criteria (e.g., VIP status).
- **Dynamic Fee Adjustment**: Implement a tiered parking fee structure.
- **Extended Vehicle Registration Data**: Add options for vehicle types, discount codes, etc.

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Happy coding!
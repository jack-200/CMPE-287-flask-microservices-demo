# CMPE-287-flask-microservices-demo

This project demonstrates a basic microservices architecture built with Python and Flask. It features two distinct, independent services: one for managing users and another for orders. The services communicate over well-defined HTTP APIs to fulfill requests, showcasing a core principle of decoupled application design.

# Installation

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
venv\Scripts\activate

# Install dependencies
pip install Flask requests
```

# Usage

```bash
# Activate virtual environment & start the user service (port 5001)
venv\Scripts\activate && python user_service.py

# *Open a New Terminal*

# Activate virtual environment & start the order service (port 5002)
venv\Scripts\activate && python order_service.py
```

# User Service API Usage Examples

```bash
# Create a new user
curl -X POST -H "Content-Type: application/json" -d '{"name": "John Doe", "email": "john.doe@example.com"}' http://localhost:5001/users

# Expected Response:
{"user_id":3}
```

```bash
# Fetches user details for user ID 3
curl http://localhost:5001/users/3

# Expected Response:
{"email":"john.doe@example.com","name":"John Doe"}
```

# Order Service API Usage Examples

```bash
# Create a new order for user ID 1
curl -X POST -H "Content-Type: application/json" -d '{"user_id": 1, "product": "Tablet"}' http://localhost:5002/orders

# Expected Response:
{"order_id":3}
```

```bash
# Fetches order details for order ID 3
curl http://localhost:5002/orders/3

# Expected Response:
{"product":"Tablet","user":{"email":"alice@example.com","name":"Alice"},"user_id":1}
```

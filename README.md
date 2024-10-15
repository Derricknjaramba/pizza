# Pizza API

## Overview
This Flask application provides a RESTful API for managing restaurants and pizzas. It allows users to perform CRUD operations on restaurants and pizzas, as well as associate pizzas with restaurants along with pricing information.

## Features
- **CRUD Operations for Restaurants**
  - List all restaurants
  - Retrieve a specific restaurant by ID
  - Delete a restaurant by ID
- **CRUD Operations for Pizzas**
  - List all pizzas
- **Associations between Restaurants and Pizzas**
  - Create associations with pricing

## Requirements
- Python 3.x
- Flask
- Flask-SQLAlchemy
- Flask-Migrate
- SQLAlchemy-Serializer

## Installation
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Create a virtual environment and activate it:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install dependencies:
   ```bash
   pip install Flask Flask-SQLAlchemy Flask-Migrate sqlalchemy-serializer
   ```

4. Set up the database:
   ```bash
   export DB_URI=sqlite:///app.db  # Adjust for your database preference
   ```

## Database Models
### Restaurant
- `id`: Integer (Primary Key)
- `name`: String
- `address`: String
- Relationships: 
  - `restaurant_pizzas`: List of `RestaurantPizza`

### Pizza
- `id`: Integer (Primary Key)
- `name`: String
- `ingredients`: String
- Relationships: 
  - `restaurant_pizzas`: List of `RestaurantPizza`

### RestaurantPizza
- `id`: Integer (Primary Key)
- `price`: Integer (1 to 30)
- Relationships: 
  - `restaurant`: ForeignKey to `Restaurant`
  - `pizza`: ForeignKey to `Pizza`

## API Endpoints
### Restaurants
- **GET /restaurants**: Retrieve a list of all restaurants.
- **GET /restaurants/<id>**: Retrieve a specific restaurant by ID.
- **DELETE /restaurants/<id>**: Delete a specific restaurant by ID.

### Pizzas
- **GET /pizzas**: Retrieve a list of all pizzas.

### Restaurant-Pizza Associations
- **POST /restaurant_pizzas**: Create a new association between a restaurant and a pizza, specifying the price.

## Seeding the Database
To populate the database with initial data, run the seeding script:
```bash
python seeder.py
```
This script will clear existing data and add sample restaurants and pizzas.

## Running the Application
Start the Flask application:
```bash
python app.py
```
The API will be available at `http://localhost:5555`.

## Testing
Make sure to test the API using tools like Postman or cURL to ensure endpoints work as expected.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

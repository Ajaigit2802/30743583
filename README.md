# E-commerce Order Management System

This is a Java-based console application that simulates an E-commerce Order Management System. It allows users to manage products, customers, and orders through a simple menu-driven interface. The application interacts with a MySQL database using JDBC.

## Features

### Product Management
- Add a new product
- View product details
- Update product information
- Delete a product (with foreign key constraints handled)

### Customer Management
- Add a new customer
- View customer details
- Update customer information
- Delete a customer

### Order Management
- Create a new order
- View order details
- Update order information
- Cancel an order

## Database Schema

### Product Table
```sql
CREATE TABLE product (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255),
    description TEXT,
    price DOUBLE,
    quantity_in_stock INT
) ENGINE=InnoDB;
```

### Customer Table
```sql
CREATE TABLE customer (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255),
    email VARCHAR(255),
    phone_number VARCHAR(15),
    address TEXT
) ENGINE=InnoDB;
```

### Order Table
```sql
CREATE TABLE `order` (
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT,
    order_date DATETIME DEFAULT NOW(),
    total_amount DOUBLE,
    status ENUM('pending', 'confirmed', 'shipped', 'delivered', 'cancelled'),
    FOREIGN KEY (customer_id) REFERENCES customer(customer_id) ON DELETE CASCADE
) ENGINE=InnoDB;
```

### OrderItem Table
```sql
CREATE TABLE orderitem (
    order_item_id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    price DOUBLE,
    FOREIGN KEY (order_id) REFERENCES `order`(order_id) ON DELETE CASCADE,
    FOREIGN KEY (product_id) REFERENCES product(product_id) ON DELETE CASCADE
) ENGINE=InnoDB;
```

## Prerequisites
- Java 8 or higher
- MySQL Server
- JDBC Driver for MySQL

## Setup Instructions

### Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/ecommerce-order-management.git
cd ecommerce-order-management
```

### Step 2: Set Up the MySQL Database
1. Create a MySQL database:
    ```sql
    CREATE DATABASE ecommerce;
    ```
2. Switch to the new database:
    ```sql
    USE ecommerce;
    ```
3. Run the SQL scripts to create the tables using the provided schema in the "Database Schema" section above.

### Step 3: Configure Database Connection
Open `DBConnection.java` and update the database connection details:

```java
private static final String URL = "jdbc:mysql://localhost:3306/ecommerce";
private static final String USER = "your_mysql_username";
private static final String PASSWORD = "your_mysql_password";
```

### Step 4: Compile and Run the Application

## Usage
On running the application, you will be presented with a menu to manage products, customers, and orders. Navigate through the menu by entering the corresponding number for each option. Input the required details for each operation as prompted.

## Exception Handling
The application includes basic exception handling for common scenarios, such as:
- Database connection errors.
- SQL exceptions (e.g., foreign key constraints).
- Input validation errors.

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request for review.

## Contact
For any inquiries or issues, feel free to contact `ajaims2802@gmail.com`.

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

### Customer Table
```sql

CREATE TABLE customer (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255),
    email VARCHAR(255),
    phone_number VARCHAR(15),
    address TEXT
) ENGINE=InnoDB;

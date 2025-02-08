# MyFirstSQLProject
My first SQL project: A simple database with tables, queries, and basic operations.

## 📌 Project Overview  
This project is a simple SQL database built using **MariaDB**. It contains tables for customers, orders, products, and a demo table. The project focuses on database design, data relationships, and basic SQL operations.  

## 🛠️ Technologies Used  
- **Database:** MariaDB 10.1.48  
- **Query Language:** SQL  

## 📂 Project Structure  
│-- 📜 database_dump.sql # SQL dump file for database schema and data
│-- 📜 README.md # Project documentation

## 📊 Database Schema  

### **Customers Table** (`customers`)  
Stores customer details.  
| Column      | Type         | Description       |
|------------|------------|------------------|
| `id`       | `TINYINT`   | Customer ID (Primary Key) |
| `first_name` | `VARCHAR(7)` | First Name |
| `last_name`  | `VARCHAR(9)` | Last Name |
| `address`    | `VARCHAR(7)` | Address |

### **Orders Table** (`orders`)  
Stores customer orders.  
| Column       | Type         | Description       |
|-------------|------------|------------------|
| `id`        | `TINYINT`   | Order ID (Primary Key) |
| `order_number` | `SMALLINT` | Order Number |
| `customer_id` | `TINYINT` | Foreign Key → `customers.id` |
| `product_id`  | `TINYINT` | Foreign Key → `products.id` |

### **Products Table** (`products`)  
Stores product details.  
| Column    | Type         | Description       |
|----------|------------|------------------|
| `id`     | `TINYINT`   | Product ID (Primary Key) |
| `name`   | `VARCHAR(6)` | Product Name |
| `price`  | `DECIMAL(2,1)` | Product Price |
| `stock`  | `TINYINT`   | Stock Quantity |

### **Demo Table** (`demo`)  
⚠️ **Issue:** The `demo` table has `VARCHAR(0)`, which may not be valid. Consider fixing it.  
| Column  | Type | Description |
|---------|------|-------------|
| `ID`    | `VARCHAR(0)` | ⚠️ Needs valid length |
| `Name`  | `VARCHAR(0)` | ⚠️ Needs valid length |
| `Hint`  | `VARCHAR(0)` | ⚠️ Needs valid length |

## 🔍 Sample Queries  
sql
-- Fetch all customers
SELECT * FROM customers;

-- Get all orders with customer and product details
SELECT o.order_number, c.first_name, c.last_name, p.name, p.price
FROM orders o
JOIN customers c ON o.customer_id = c.id
JOIN products p ON o.product_id = p.id;

-- Find total stock value of all products
SELECT SUM(price * stock) AS total_stock_value FROM products;

🚀 How to Use
Clone the repository: git clone https://github.com/your-username/MyFirstSQLProject.git

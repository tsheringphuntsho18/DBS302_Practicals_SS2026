# DBS302 – Practical 3

## MongoDB E-Commerce Schema Design, Aggregation, and Query Optimization

## Introduction

MongoDB is a NoSQL, document-oriented database that stores data in flexible JSON-like documents. Unlike relational databases, MongoDB allows dynamic schemas, making it ideal for applications like e-commerce platforms where data structures may vary.

This practical focuses on designing an e-commerce database, performing analytical queries using the aggregation framework, and optimizing performance using indexes.

## Objectives

* Design an e-commerce schema using MongoDB
* Implement collections with sample data
* Perform aggregation queries for analytics
* Optimize queries using indexes and explain()

## Database Schema Design

### 1. Users Collection

Stores customer details.

Fields:

* name
* email
* phone
* address (embedded document)
* createdAt

### 2. Categories Collection

Stores product categories.

Fields:

* name
* slug
* parentCategoryId

### 3. Products Collection

Stores product details.

Fields:

* name
* categoryId (reference)
* price
* stock
* attributes (flexible key-value pairs)

### 4. Orders Collection

Stores customer orders.

Fields:

* userId (reference to users)
* status
* items (embedded array)
* grandTotal
* createdAt

## Embedding vs Referencing

* **Embedding**: Order items are embedded inside orders for faster read performance.
* **Referencing**: Products and users are referenced using ObjectId to avoid duplication.

## Aggregation Queries

### 1. Daily Sales Total

Calculates total revenue per day.

### 2. Top Products by Revenue

Finds best-selling products.

### 3. Average Order Value per User

Calculates spending behavior of users.

### 4. Product with Category

Joins products with categories.

## ⚡ Indexing

Indexes were created to improve query performance:

* Orders:

  * userId + createdAt
  * status + createdAt

* Products:

  * categoryId + price

Indexes help avoid full collection scans and improve query speed.

## Query Optimization using explain()

Before indexing:

* Query used **COLLSCAN**
* High execution time

After indexing:

* Query used **IXSCAN**
* Faster performance

This proves indexes significantly improve efficiency.

## Screenshots (Attach in submission)

* Collections created
* Inserted documents
* Aggregation results
* Index creation
* Explain plan (before & after)

## Common Mistakes Avoided

* Avoided relational-style design
* Used embedding for order items
* Created indexes for frequent queries

## Conclusion

This practical helped in understanding MongoDB schema design, aggregation pipelines, and performance optimization techniques. The use of indexes and explain() demonstrated how query performance can be improved significantly in real-world applications.

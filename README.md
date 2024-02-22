# Assignment: Deutsche Bahn Navigator, Tickets & Deals Database

## Overview
In this assignment, you will be tasked with creating a database system for the Deutsche Bahn (DB) Navigator, focusing on the management of train routes, ticket bookings, and promotional deals. This system aims to streamline the process of searching for train routes, booking tickets, and applying deals for customers. You will start by setting up the database environment, followed by creating the necessary schemas and tables. Additionally, you will populate the tables with sample data and perform various SQL operations to simulate real-world scenarios.

## Objectives
- Understand and implement database schemas.
- Create and manipulate tables within a database.
- Insert, update, and query data from the database.
- Apply constraints and relationships between tables.

## Part 1: Setting Up the Database Environment
1. **Create a Database**: Name the database `DBNavigator`.
2. **Create Schemas**: Create two schemas within the `DBNavigator` database:
   - `RoutesSchema` for managing train routes.
   - `BookingSchema` for handling ticket bookings and deals.

## Part 2: Creating Tables and Relationships
Within the `RoutesSchema`:
1. **Create a `Trains` Table**: This table should store information about the trains, including train ID, name, and type.
2. **Create a `Routes` Table**: This table will hold details about the routes, such as route ID, departure station, arrival station, departure time, and arrival time. Ensure to establish a relationship with the `Trains` table.

Within the `BookingSchema`:
1. **Create a `Customers` Table**: Include fields for customer ID, name, email, and phone number.
2. **Create a `Tickets` Table**: This table should contain ticket ID, customer ID (linked to the `Customers` table), route ID (linked to the `Routes` table), booking date, and price.
3. **Create a `Deals` Table**: Store deal ID, description, discount percentage, and validity period.

## Part 3: Inserting Sample Data
- Insert 50 records into each table you have created. Ensure the data is realistic and reflects the potential use case of the Deutsche Bahn Navigator system. For example, the `Routes` table should have various departure and arrival stations across Germany, different departure and arrival times, and should be linked to specific trains in the `Trains` table.

## Part 4: SQL Operations
Perform the following SQL operations:
1. **Query All Available Routes**: Write a SQL query to list all available routes, including departure and arrival stations, as well as times.
2. **Find Tickets for a Specific Route**: Create a query to find all tickets booked for a specific route.
3. **Apply a Deal to Tickets**: Write an update statement that applies a specific deal to all tickets booked within a certain period.
4. **List All Deals Valid in the Next Month**: Generate a list of all deals that will be valid in the next month.
5. **Delete Expired Deals**: Write a SQL command to delete all deals that have expired.

## Submission Guidelines
- Submit the SQL scripts for creating the database, schemas, tables, inserting sample data, and the SQL operations.
- Ensure your SQL scripts are well-commented to explain the purpose of each operation.
- Provide a brief report explaining your design decisions for the database schema and table structures.

## Evaluation Criteria
- Correctness and efficiency of the SQL scripts.
- Logical structure and organization of the database schemas and tables.
- Creativity in the sample data inserted.
- Clarity and thoroughness of the comments and report.

Good luck, and enjoy working on the Deutsche Bahn Navigator database system!

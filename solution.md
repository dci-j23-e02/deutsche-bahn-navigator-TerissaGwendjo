1.) 
Database:

CREATE DATABASE DBNavigator;

Schemas:

CREATE SCHEMA RoutesSchema;
CREATE SCHEMA BookingSchema;

2.) 

Creating Tables and Relationships

Within the RoutesSchema:
CREATE TABLE RoutesSchema.Trains (
TrainID INT PRIMARY KEY,
Name VARCHAR(255),
Type VARCHAR(100)
);

CREATE TABLE RoutesSchema.Routes (
RouteID INT PRIMARY KEY,
DepartureStation VARCHAR(255),
ArrivalStation VARCHAR(255),
DepartureTime TIMESTAMP,
ArrivalTime TIMESTAMP,
TrainID INT,
FOREIGN KEY (TrainID) REFERENCES RoutesSchema.Trains(TrainID)
);

Within the BookingSchema:

CREATE TABLE BookingSchema.Customers (
CustomerID INT PRIMARY KEY,
Name VARCHAR(255),
Email VARCHAR(255),
PhoneNumber VARCHAR(20)
);

-- Create Tickets Table
CREATE TABLE BookingSchema.Tickets (
TicketID INT PRIMARY KEY,
CustomerID INT,
RouteID INT,
BookingDate TIMESTAMP,
Price DECIMAL(10, 2),
FOREIGN KEY (CustomerID) REFERENCES BookingSchema.Customers(CustomerID),
FOREIGN KEY (RouteID) REFERENCES RoutesSchema.Routes(RouteID)
);

-- Create Deals Table
CREATE TABLE BookingSchema.Deals (
DealID INT PRIMARY KEY,
Description VARCHAR(255),
DiscountPercentage DECIMAL(5, 2),
ValidityPeriodStart TIMESTAMP,
ValidityPeriodEnd TIMESTAMP
);

3.)

For RoutesSchema.Trains:
INSERT INTO RoutesSchema.Trains (TrainID, Name, Type) VALUES
(1, 'ICE 1', 'InterCity Express'),
(2, 'IC 2', 'InterCity'),
(50, 'RB 50', 'Regionalbahn');

For RoutesSchema.Routes:
INSERT INTO RoutesSchema.Routes (RouteID, DepartureStation, ArrivalStation, DepartureTime, ArrivalTime, TrainID) VALUES
(1, 'Berlin', 'Munich', '2024-02-22 08:00:00', '2024-02-22 14:00:00', 1);

For BookingSchema.Customers:
INSERT INTO BookingSchema.Customers (CustomerID, Name, Email, PhoneNumber) VALUES
(1, 'Teri Gwe', 'teri.gwe@yahoo.com', '123-456-7890'),
(2, 'Blanche Ngu', 'ngu@yahoo.com', '987-654-3210'),
(50, 'Mary Fru', 'mary@yahoo.com', '555-555-5555');

For BookingSchema.Tickets:
INSERT INTO BookingSchema.Tickets (TicketID, CustomerID, RouteID, BookingDate, Price) VALUES
(1, 1, 1, '2024-02-22 10:00:00', 50.00);

For BookingSchema.Deals:
INSERT INTO BookingSchema.Deals (DealID, Description, DiscountPercentage, ValidityPeriodStart, ValidityPeriodEnd) VALUES
(1, 'Spring Sale', 20.00, '2024-03-01', '2024-03-31'),
(2, 'Weekend Getaway', 15.00, '2024-02-25', '2024-02-27'),
... -- Add more deals
(10, 'Summer Special', 25.00, '2024-06-01', '2024-08-31');

4.)

Query All Available Routes:
SELECT r.RouteID, r.DepartureStation, r.ArrivalStation, r.DepartureTime, r.ArrivalTime, t.Name AS TrainName, t.Type AS TrainType
FROM RoutesSchema.Routes r
JOIN RoutesSchema.Trains t ON r.TrainID = t.TrainID;

Find Tickets for a Specific Route:
SELECT *
FROM BookingSchema.Tickets
WHERE RouteID = <specific_route_id>;

Apply a Deal to Tickets:
UPDATE BookingSchema.Tickets
SET Price = Price - (Price * <deal_discount_percentage> / 100)
WHERE BookingDate BETWEEN <start_date> AND <end_date>;

List All Deals Valid in the Next Month:
SELECT *
FROM BookingSchema.Deals
WHERE ValidityPeriodStart >= CURDATE() AND ValidityPeriodEnd <= DATE_ADD(CURDATE(), INTERVAL 1 MONTH);

Delete Expired Deals:
DELETE FROM BookingSchema.Deals
WHERE ValidityPeriodEnd < CURDATE();





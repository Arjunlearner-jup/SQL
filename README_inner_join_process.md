# INNER JOIN process for Customers and Orders

This example uses an `INNER JOIN` to combine rows from the `Customers` table and the `Orders` table based on a shared key.[cite:81][cite:82]

## What INNER JOIN does

An `INNER JOIN` returns only the rows where the join condition matches in both tables.[cite:81][cite:159][cite:87]
In this script, the matching columns are `Customers.ID` and `Orders.CustomerID`.[cite:83][cite:186]
That means only customers who have at least one order appear in the result.[cite:88][cite:81]

## Step-by-step process

1. The script selects the `pract` database with `USE pract;` so the commands run in the correct database.
2. It creates the `Customers` table to store customer details such as ID, name, and city.
3. It creates the `Orders` table to store order details such as order ID, customer ID, and amount.
4. It inserts sample rows into both tables.
5. The query matches `Customers.ID = Orders.CustomerID` in the `ON` clause to connect each order to the correct customer.[cite:81][cite:83][cite:84]
6. The `SELECT` statement returns only the chosen columns: `Name`, `City`, and `Amount`.[cite:81][cite:184]

## Query used

```sql
SELECT c.Name, c.City, o.Amount
FROM Customers c
INNER JOIN Orders o ON c.ID = o.CustomerID;
```

This query uses table aliases (`c` and `o`) to make the statement shorter and easier to read.[cite:184]

## Result of this example

The output includes Alice with two orders and Bob with one order because those rows have matching IDs in both tables.[cite:83][cite:88]
Carol does not appear because there is no matching order row for `CustomerID = 3`, and `INNER JOIN` excludes unmatched rows.[cite:81][cite:159][cite:87]

## Expected output

```text
Name  | City | Amount
Alice | NYC  | 100
Bob   | LA   | 200
Alice | NYC  | 150
```


INNER JOIN is the most fundamental and widely used SQL join because it efficiently combines related data from multiple tables while excluding unmatched rows, making it perfect for normalized databases.

Key Benefits
Data Consolidation
Merges related data (customers + orders, products + inventory) into single result sets, avoiding multiple queries.

Performance Optimized
Only processes matching rows, faster than outer joins for most business queries. Works best with indexed foreign keys.

Clean Results
Automatically filters out orphaned records (customers with no orders), giving precise analytics and reports.

Relational Foundation
Essential for normalized databases where data splits across tables by design (one table per entity).

Real-World Uses
text
E-commerce: Products × Inventory × Orders
Banking:    Accounts × Transactions  
Healthcare: Patients × Appointments
Your Customers/Orders example perfectly shows this—only customers with orders appear.

Bottom line: INNER JOIN powers 90% of production queries because business logic typically needs complete records, not partial data with NULLs.
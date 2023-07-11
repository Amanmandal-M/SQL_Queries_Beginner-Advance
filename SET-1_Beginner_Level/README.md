<h1 align="center">Beginner Level SQL Queries</h1>

<br>

## In SQL, we're using a `Customers` table. Each row in the table represents one customer. Here is the schema of the `Customers` table:

```js
    CREATE TABLE Customers (
        id INT PRIMARY KEY,
        name VARCHAR(100),
        email VARCHAR(100),
        address VARCHAR(255),
        phone_number VARCHAR(50)
    );
```

## Problems : 

### Create a `Customers` table / collection with the following fields: `id` (unique identifier), `name`, `email`, `address`, and `phone_number`.

```js
    CREATE DATABASE Customer_Details;

    USE Customer_Details;

    CREATE TABLE Customers (
        id INT PRIMARY KEY,
        name VARCHAR(100),
        email VARCHAR(100),
        address VARCHAR(255),
        phone_number VARCHAR(50)
    );
```
<br>

### Insert five rows / documents into the Customers table / collection with data of your choice.

```js
    INSERT INTO Customers (id, name, email, address, phone_number)
    VALUES (1, 'Varun Bhatt', 'varunbhatt@gmail.com', 'Home', '123-456-7890'),
        (2, 'Mohsin', 'mohsin@gmail.com', 'Home', '555-678-9012'),
        (3, 'Mohit', 'mohit@gmail.com', 'Home', '777-888-9900'),
        (4, 'Faizal', 'faizal@gmail.com', 'Home', '999-000-1111'),
        (5, 'Annanya', 'annanya@gmail.com', 'Home', '222-333-4444');
```

<br>

### Write a query to fetch all data from the Customers table / collection.

```js
    SELECT * FROM Customers;
```

<br>

### Write a query to select only the name and email fields for all customers.

```js
    SELECT name, email FROM Customers;
```

<br>

### Write a query to fetch the customer with the id of 3.

```js
    SELECT * FROM Customers WHERE id = 3;
```

<br>

### Write a query to fetch all customers whose name starts with 'A'.

```js
    SELECT * FROM Customers WHERE name LIKE 'A%';
```

<br>

### Write a query to fetch all customers, ordered by name in descending order.

```js
    SELECT * FROM Customers ORDER BY name DESC;
```

<br>

### Write a query to update the address of the customer with id 

```js
    UPDATE Customers SET address = 'India' WHERE id = 1;
```

<br>

### Write a query to fetch the top 3 customers when ordered by id in ascending order.

```js
    SELECT * FROM Customers ORDER BY id ASC LIMIT 3;
```

<br>

### Write a query to delete the customer with id 2.

```js
    DELETE FROM Customers WHERE id = 2;
```

<br>

### Write a query to count the number of customers.

```js
    SELECT COUNT(*) FROM Customers;
```

<br>

### Write a query to fetch all customers except the first two when ordered by id in ascending order.

```js
    SELECT * FROM Customers ORDER BY id ASC LIMIT 2 OFFSET 2;
```

<br>

### Write a query to fetch all customers whose id is greater than 2 and name starts with 'B'.

```js
    SELECT * FROM Customers WHERE id > 2 AND name LIKE 'B%';
```

<br>

### Write a query to fetch all customers whose id is less than 3 or name ends with 's'.

```js
    SELECT * FROM Customers WHERE id < 3 OR name LIKE '%s';
```

<br>

### Write a query to fetch all customers where the phone_number field is not set or is null.

```js
    SELECT * FROM Customers WHERE phone_number IS NULL;
```
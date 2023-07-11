<h1 align="center">Beginner Level SQL Queries</h1>

<br>

We will be using a `Restaurants` table / collection for this set of problems. The schema represents a list of restaurants like one might find in a delivery app like Zomato. Each restaurant has an `id`, `name`, cuisine_type (e.g., Italian, Chinese), `location`, `average_rating`, and `delivery_available` (a boolean indicating if delivery is available).

```js
    CREATE TABLE Restaurants (
        id INT PRIMARY KEY,
        name VARCHAR(100),
        cuisine_type VARCHAR(100),
        location VARCHAR(255),
        average_rating DECIMAL(3,2),
        delivery_available BOOLEAN
    );

```

## Problems : 

### Create a `Restaurants` table / collection with the fields defined above.

```js
    CREATE DATABASE Restaurant_Details;

    USE Restaurant_Details;

    CREATE TABLE Restaurants (
        id INT PRIMARY KEY,
        name VARCHAR(100),
        cuisine_type VARCHAR(100),
        location VARCHAR(255),
        average_rating DECIMAL(3,2),
        delivery_available BOOLEAN
    );
```
<br>

### Insert five rows / documents into the `Restaurants` table / collection with data of your choice.

```js
    INSERT INTO Restaurants (id, name, cuisine_type, location, average_rating, delivery_available)
    VALUES (1, 'Haldiram', 'Italian', 'Delhi, DL', 4.5, TRUE),
           (2, 'KFC', 'American', 'Mumbai, MU', 4.0, FALSE),
           (3, 'Dominozz', 'Japanese', 'Banglore, BLR', 4.5, TRUE),
           (4, 'Pizza Hut', 'Coffee Shop', 'Goa, GA', 3.5, TRUE),
           (5, 'McDonalds', 'Fast Food', 'New York, NY', 3.0, TRUE);
```

<br>

###  Write a query to fetch all restaurants, ordered by average_rating in descending order.

```js
    SELECT * FROM Restaurants ORDER BY average_rating DESC;
```

<br>

### Write a query to fetch all restaurants that offer `delivery_available` and have an `average_rating` of more than 4.

```js
    SELECT * FROM Restaurants WHERE delivery_available = TRUE AND average_rating > 4;
```

<br>

### Write a query to fetch all restaurants where the `cuisine_type` field is not set or is null.

```js
    SELECT * FROM Restaurants WHERE cuisine_type IS NULL;
```

<br>

### Write a query to count the number of restaurants that have `delivery_available`.

```js
    SELECT COUNT(*) FROM Restaurants WHERE delivery_available = TRUE;
```

<br>

### Write a query to fetch all restaurants whose location contains 'New York'.

```js
    SELECT * FROM Restaurants WHERE location LIKE '%New York%';
```

<br>

### Write a query to calculate the average average_rating of all restaurants.

```js
    SELECT AVG(average_rating) AS average_rating FROM Restaurants;
```

<br>

### Write a query to fetch the top 5 restaurants when ordered by average_rating in descending order.

```js
    SELECT * FROM Restaurants ORDER BY average_rating DESC LIMIT 5;
```

<br>

### Write a query to fetch the top 5 restaurants when ordered by average_rating in descending order.

```js
    SELECT * FROM Restaurants WHERE delivery_available = FALSE ORDER BY average_rating DESC LIMIT 5;
```
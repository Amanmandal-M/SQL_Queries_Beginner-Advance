<h1 align="center">Intermediate Level SQL Queries</h1>

<br>

We'll continue with a `Rides` table / collection for this set of problems. The schema represents a list of rides one might find in a ride-hailing app like Uber. Each ride has an `id`, `driver_id`, `passenger_id`, `start_location`, `end_location`, `distance` (in miles), `ride_time` (in minutes), and `fare` (in dollars).

```js
    CREATE TABLE Rides (
        id INT PRIMARY KEY,
        driver_id INT,
        passenger_id INT,
        start_location VARCHAR(255),
        end_location VARCHAR(255),
        distance DECIMAL(5,2),
        ride_time DECIMAL(5,2),
        fare DECIMAL(6,2)
    );
```

## Problems : 

### Create a `Rides` table / collection with the fields defined above.

```js
    CREATE DATABASE Rides_Details;

    USE Rides_Details;

    CREATE TABLE Rides (
        id INT PRIMARY KEY,
        driver_id INT,
        passenger_id INT,
        start_location VARCHAR(255),
        end_location VARCHAR(255),
        distance DECIMAL(5,2),
        ride_time DECIMAL(5,2),
        fare DECIMAL(6,2)
    );
```

<br>

### Insert five rows / documents into the `Rides` table / collection with data of your choice.

```js
    INSERT INTO Rides (id, driver_id, passenger_id, start_location, end_location, distance, ride_time, fare)
    VALUES (1, 1, 1, 'Delhi', 'Agra', 300, 60, 250.00),
           (2, 2, 2, 'Bokaro','Daltonganj', 200, 40, 300.00),
           (3, 3, 3, 'Dugda Downtown', 'Jammu Kashmir', 1000, 200, 2000.85),
           (4, 4, 4, 'Chandrapura', 'Kanpur', 500, 100, 600.20),
           (5, 5, 5, 'Dhanbad', 'Varanasi', 400, 80, 589.87);
```

<br>

### Write a query to fetch all rides, ordered by `fare` in descending order.

```js
    SELECT * FROM Rides ORDER BY fare DESC;
```

<br>

###  Write a query to calculate the total `distance` and total `fare` for all rides.

```js
    SELECT SUM(distance) AS total_distance, SUM(fare) AS total_fare FROM Rides;
```

<br>

###  Write a query to calculate the average `ride_time` of all rides.

```js
    SELECT AVG(ride_time) AS average_ride_time FROM Rides;
```

<br>

### Write a query to fetch all rides whose `start_location` or `end_location` contains 'Downtown'.

```js
    SELECT * FROM Rides WHERE start_location LIKE '%Downtown%' OR end_location LIKE '%Downtown%';
```

<br>

### Write a query to count the number of rides for a given `driver_id`.

```js
    SELECT COUNT(*) AS number_of_rides FROM Rides WHERE driver_id = 1;
```

<br>

###  Write a query to update the `fare` of the ride with `id` 4.

```js
    UPDATE Rides SET fare = 698.00 WHERE id = 4;
```

<br>

### Write a query to calculate the total `fare` for each `driver_id`.

```js
    SELECT driver_id, SUM(fare) AS total_fare FROM Rides GROUP BY driver_id;
```

<br>

### Write a query to delete the ride with `id` 2.

```js
    DELETE FROM Rides WHERE id = 2;
```
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

### Assuming there's another collection/table `FutureRides` with the same schema as `Rides`, write a query to create a union of `Rides` and `FutureRides`.

```js
    SELECT * FROM Rides
    UNION
    SELECT * FROM FutureRides;
```

<br>

###  Write a query to rank drivers based on the total fare they've collected.

```js
    SELECT driver_id , SUM(fare) AS total_fare
    FROM Rides
    GROUP BY driver_id
    ORDER BY total_fare DESC;
```

<br>

### Write a query to find all rides where the `driver_id` is among the top 5 drivers with the most rides.

```js
    SELECT id , driver_id , COUNT(*) AS number_of_rides
    FROM Rides
    GROUP BY driver_id
    ORDER BY number_of_rides DESC
    LIMIT 5;
```

<br>

### Write a query to classify rides based on `distance`: 'Short' if the distance is less than 5 miles, 'Medium' if the distance is between 5 and 15 miles, and 'Long' for distances over 15 miles.

```js
    SELECT id , distance,
    CASE
        WHEN distance < 5 THEN 'Short'
        WHEN distance BETWEEN 5 AND 15 THEN 'Medium'
        ELSE 'Long'
    END AS ride_category
    FROM Rides;
```

<br>

### Write a query to calculate the variance and standard deviation of `fare` for each driver.

```js
    SELECT driver_id , AVG(fare) AS average_fare , VARIANCE(fare) AS variance, STDDEV(fare) AS standard_deviation
    FROM Rides
    GROUP BY driver_id;
```

<br>

### Assuming there's a `ride_date` field of date type in the `Rides` table / collection, write a query to find the busiest day of the week (when most rides happened).

```js
    SELECT DAYOFWEEK(ride_date) AS day_of_week , COUNT(*) AS number_of_rides
    FROM Rides
    GROUP BY DAYOFWEEK(ride_date)
    ORDER BY number_of_rides DESC
    LIMIT 1;
```

<br>

### Assuming there's a Rides table / collection where each ride can have a follow-up ride (`next_ride_id`), write a query to find all subsequent rides for a given ride id.

```js
  --Not available--
```

<br>

### Write a query to find the total `distance` and `fare` for each `driver_id` and `passenger_id` pair.

```js
    SELECT driver_id , passenger_id , SUM(distance) AS total_distance , SUM(fare) AS total_fare
    FROM Rides
    GROUP BY driver_id, passenger_id;
```

<br>

### Assuming there's a `tags` field in the `Rides` collection (an array of strings), write a query to find all rides that have the tag 'business'.

```js
    SELECT *
    FROM Rides
    WHERE tags @> ARRAY['business'];
```

<br>

### Assuming there's a `notes` field in the `Rides` collection/table, write a query to find all rides where the `notes` contain the word 'airport'.

```js
    SELECT *
    FROM Rides
    WHERE notes LIKE '%airport%';
```
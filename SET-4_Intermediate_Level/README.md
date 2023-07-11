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

### Write a query to find the ride with the highest and lowest `fare`.

```js
    SELECT * FROM Rides ORDER BY fare DESC LIMIT 1;
    SELECT * FROM Rides ORDER BY fare ASC LIMIT 1;
```

<br>

###  Write a query to find the average `fare` and `distance` for each `driver_id`.

```js
    SELECT driver_id, AVG(fare) AS average_fare, AVG(distance) AS average_distance
    FROM Rides
    GROUP BY driver_id;
```

<br>

### Write a query to find driver_id that have completed more than 5 rides.

```js
    SELECT driver_id, COUNT(*) AS number_of_rides
    FROM Rides
    GROUP BY driver_id
    HAVING COUNT(*) > 5;
```

<br>

### Assuming there is another collection/table called `Drivers` with `driver_id` and `name` fields, write a query to find the name of the driver with the highest `fare`.

```js
    SELECT Drivers.name, MAX(Rides.fare) AS highest_fare
    FROM Drivers
    INNER JOIN Rides ON Drivers.driver_id = Rides.driver_id
    GROUP BY Drivers.name;

```

<br>

### Write a query to find the top 3 drivers who have earned the most from fares. Return the drivers' ids and total earnings.

```js
    SELECT driver_id, SUM(fare) AS total_earnings
    FROM Rides
    GROUP BY driver_id
    ORDER BY total_earnings DESC
    LIMIT 3;
```

<br>

###  Assuming there's a `ride_date` field of date type in the `Rides` table / collection, write a query to find all rides that happened in the last 7 days.

```js
    SELECT * FROM Rides
    WHERE ride_date >= CURRENT_DATE - INTERVAL 7 DAY;
```

<br>

### Write a query to find all rides where the `end_location` is not set.

```js
    SELECT * FROM Rides
    WHERE end_location IS NULL;
```

<br>

### Write a query to calculate the fare per mile for each ride and return the ride ids and their fare per mile, ordered by fare per mile in descending order.

```js
    SELECT id, fare / distance AS fare_per_mile
    FROM Rides
    ORDER BY fare_per_mile DESC;
```

<br>

###  Assuming there's another collection/table `Passengers` with `passenger_id` and `name` fields, write a query to return a list of all rides including the driver's name and passenger's name.

```js
    SELECT r.id, r.driver_id, r.passenger_id, d.name, p.name 
    FROM Rides r
    JOIN Drivers d ON r.driver_id = d.driver_id
    JOIN Passengers p ON r.passenger_id = p.passenger_id;
```

<br>

###  Write a query to add a `tip` field to the `Rides` table / collection.

```js
    ALTER TABLE Rides
    ADD COLUMN tip DECIMAL(6,2);
```
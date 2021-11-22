# analytics-test
## SQL. Задание 1
Вывести отсортированный по количеству перелетов (по убыванию) 
и имени (по возрастанию) список пассажиров, совершивших хотя бы 1 полет
```
SELECT name, COUNT(*) AS count  
FROM Passenger
JOIN Pass_in_trip
    ON Passenger.id=Pass_in_trip.passenger
GROUP BY passenger
HAVING COUNT(trip) > 0
ORDER BY COUNT(trip) DESC, name;
```
## SQL. Задание 4
Какой(ие) кабинет(ы) пользуются самым большим спросом?
```
SELECT classroom 
FROM Schedule
GROUP BY classroom
HAVING COUNT(classroom) = 
    (SELECT COUNT(classroom) 
    FROM Schedule 
    GROUP BY classroom
    ORDER BY COUNT(classroom) DESC LIMIT 1)
```

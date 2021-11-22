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

## SQL. Задание 2
Сколько времени обучающийся будет находиться в школе, 
учась со 2-го по 4-ый уч. предмет ?
```
SELECT DISTINCT TIMEDIFF( 
                (SELECT end_pair FROM Timepair WHERE id=4),
                (SELECT start_pair FROM Timepair WHERE id=2)
                ) 
                AS time
FROM Timepair;
```

## SQL. Задание 3
Выведите список комнат, которые были зарезервированы в течение 12 недели 2020 года.
```
SELECT DISTINCT Rooms.*
FROM Rooms
JOIN Reservations ON Rooms.id=Reservations.room_id
WHERE WEEK(start_date, 1) = 12 AND YEAR(start_date)=2020;
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
    ORDER BY COUNT(classroom) DESC LIMIT 1);
```


## Математика. Задание 1
В игре «Что? Где? Когда?» в каждом раунде волчок останавливается в секторе номер n, 
где n равновероятно принимает одно из значений 0, 1,..., 13. 
При этом играет первый из секторов по часовой стрелке, который ранее не играл. Найдите вероятность того, 
что после шести раундов сыграют (в любом порядке) секторы 1, 2,..., 6.


# model-star
Создание модели данных звезда

## Таблица фактов
trips – Поездки <br>

## Таблицы измерений
drivers – Водители <br>
passengers – Пассажиры <br>
dates – Даты <br>
locations – Местоположения <br>

## Поля

### trips (Поездки)
trip_id – Идентификатор поездки <br>
driver_id – Идентификатор водителя <br>
passenger_id – Идентификатор пассажира <br>
date_id – Идентификатор даты <br>
pickup_location_id – Идентификатор места посадки <br>
dropoff_location_id – Идентификатор места высадки <br>
distance – Расстояние <br>
fare – Стоимость проезда <br>

### drivers (Водители)
driver_id – Идентификатор водителя <br>
driver_name – Имя водителя <br>
driver_license – Номер водительского удостоверения <br>

### passengers (Пассажиры)
passenger_id – Идентификатор пассажира <br>
passenger_name – Имя пассажира <br>
passenger_phone – Телефон пассажира <br>

### dates (Даты)
date_id – Идентификатор даты <br>
date – Дата <br> 
day_of_week – День недели <br>
month – Месяц <br>
year – Год <br>

### locations (Местоположения)
location_id – Идентификатор местоположения <br>
address – Адрес <br>
city – Город <br>
state – Область/штат <br>

## Схема

## SQL-скрипт
```
CREATE SCHEMA IF NOT EXISTS star;

CREATE TABLE star.drivers (
    driver_id INT PRIMARY KEY,
    driver_name VARCHAR(100),
    driver_license VARCHAR(50)
);

CREATE TABLE star.passengers (
    passenger_id INT PRIMARY KEY,
    passenger_name VARCHAR(100),
    passenger_phone VARCHAR(20)
);

CREATE TABLE star.dates (
    date_id INT PRIMARY KEY,
    date DATE,
    day_of_week VARCHAR(10),
    month VARCHAR(10),
    year INT
);

CREATE TABLE star.locations (
    location_id INT PRIMARY KEY,
    address VARCHAR(255),
    city VARCHAR(100),
    state VARCHAR(100)
);

CREATE TABLE star.trips (
    trip_id INT PRIMARY KEY,
    driver_id INT,
    passenger_id INT,
    date_id INT,
    pickup_location_id INT,
    dropoff_location_id INT,
    distance DECIMAL(10, 2),
    fare DECIMAL(10, 2),
    FOREIGN KEY (driver_id) REFERENCES star.drivers(driver_id),
    FOREIGN KEY (passenger_id) REFERENCES star.passengers(passenger_id),
    FOREIGN KEY (date_id) REFERENCES star.dates(date_id),
    FOREIGN KEY (pickup_location_id) REFERENCES star.locations(location_id),
    FOREIGN KEY (dropoff_location_id) REFERENCES star.locations(location_id)
);
```

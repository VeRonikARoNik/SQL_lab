Materiały uzupełniające:
https://egzamin-programista.pl/arkusz-praktyczny-inf03-2025-01-12 

***W programie MYSQL utwórz pierszą bazę danych***

```
CREATE DATABASE Employee;

USE Employee;

CREATE TABLE Employees (
    Id INT AUTO_INCREMENT PRIMARY KEY,
    FirstName VARCHAR(100) NOT NULL,
    LastName VARCHAR(100) NOT NULL,
    Email VARCHAR(255) UNIQUE,
    HireDate DATE NOT NULL
);

INSERT INTO Employees (FirstName, LastName, Email, HireDate)
VALUES
('Anna', 'Kowalska', 'anna.kowalska@example.com', '2023-05-10'),
('Jan', 'Nowak', 'jan.nowak@example.com', '2022-11-01'),
('Marek', 'Wiśniewski', 'marek.wisniewski@example.com', '2021-03-15');

SELECT * FROM Employees;
```
<img width="1264" height="657" alt="image" src="https://github.com/user-attachments/assets/d48cc3a3-7bd6-4e2f-b182-98dd67d8135c" />


***Operacje na gotowej bazie danych***

1. Wykonaj na bazie piekarnia cztery kwerendy:

2. wybierz pola Rodzaj, Nazwa, Gramatura, Cena dla wyrobów z rodzaju „INNE”

3. wypisz rodzaje wyrobów bez powtórzeń, malejąco

4. wybierz pola ID, Nazwa dla wyrobów, których nazwa zawiera „Chałka”

dla każdej wartości Rodzaj policz średnią cenę (zaokrągloną do 2 miejsc) jako kolumnę „Średnia cena”

**Zaimportuj baze danych**

```
CREATE DATABASE IF NOT EXISTS piekarnia CHARACTER SET utf8 COLLATE utf8_polish_ci;
USE piekarnia;

USE piekarnia;
SHOW TABLES;
SELECT * FROM wyroby LIMIT 100;
```

```
-- 1
SELECT Rodzaj, Nazwa, Gramatura, Cena
FROM wyroby
WHERE Rodzaj = 'INNE';

-- 2
SELECT DISTINCT Rodzaj
FROM wyroby
ORDER BY Rodzaj DESC;


-- 3
SELECT ID, Nazwa
FROM wyroby
WHERE Nazwa LIKE '%Chałka%';


-- 4
SELECT Rodzaj, ROUND(AVG(Cena), 2) AS `Średnia cena`
FROM wyroby
GROUP BY Rodzaj;
```



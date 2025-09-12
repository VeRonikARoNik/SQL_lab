
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



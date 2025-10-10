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

 Wykonaj na bazie piekarnia cztery kwerendy:

1. wybierz pola Rodzaj, Nazwa, Gramatura, Cena dla wyrobów z rodzaju „INNE”

2. wypisz rodzaje wyrobów bez powtórzeń, malejąco

3. wybierz pola ID, Nazwa dla wyrobów, których nazwa zawiera „Chałka”

4. dla każdej wartości Rodzaj policz średnią cenę (zaokrągloną do 2 miejsc) jako kolumnę „Średnia cena”

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

Dodaniee nowego użytkownika 
```
INSERT INTO users (name) 
VALUES ('Jan Nowak');

```

Usunięcie rekordu 
```
DELETE FROM users
WHERE name = 'Anna Kowalska';

```
Aktualizacja danych 

```
UPDATE users
SET name = 'Daria Kowalska'
WHERE name = 'Anna Kowalska';
```
Dodanie nowej kolumny 
```
ALTER TABLE users
ADD COLUMN email VARCHAR(100);

```
Uzupełnienie danych
```
UPDATE users
SET email = 'anna.kowalska@example.com'
WHERE name = 'Anna Kowalska';
```

Dodanie kolumny odrazu z danymi
```
INSERT INTO users (name, email)
VALUES ('Jan Nowak', 'jan.nowak@example.com');
```
Usuwanie kolumny 
```
ALTER TABLE users
DROP COLUMN email;
```

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
19.09.2025

**Zadanie 1**

*Pobierz bazę danych i zaimportuj do MYSQL*
*Utwórz bazę danych o nazwie konkurs, z zestawem polskich znaków (np. utf8_unicode_ci)*
*Z rozpakowanego archiwum zaimportuj tabelę z pliku baza.sql do utworzonej bazy*

*Wykonaj zrzut ekranu po imporcie. Zapisz zrzut w formacie PNG pod nazwą import. Nie kadruj zrzutu. Powinien on obejmować cały ekran monitora, z widocznym paskiem zadań. Na zrzucie powinny być widoczne elementy wskazujące na poprawnie wykonany import tabel*
*Wykonaj zapytania SQL działające na bazie konkurs. Zapytania zapisz w pliku kwerendy.txt. Wykonaj zrzuty ekranu przedstawiające wyniki działania kwerend. Zrzuty zapisz w formacie PNG i nadaj im nazwy kw1, kw2, kw3, kw4. Zrzuty powinny obejmować cały ekran monitora z widocznym paskiem zadań*

*Zapytanie 1: wybierające losowo dokładnie pięć rekordów z tabeli nagrody zawierających jedynie pola nazwa, opis i cena*

*Zapytanie 2: wybierające wszystkie pola z tabeli nagrody, dla których cena mieści się w przedziale <100, 1000>, oraz których ilość jest równa 2 sztuki*

*Zapytanie 3: usuwające te rekordy, w których cena nie została wpisana lub wynosi 0 zł*

*Zapytanie 4: wybierające jedynie nazwę, cenę i datę dodania nagród, które zostały dodane w sierpniu 2021 roku. Wyniki powinny być posortowane rosnąco według daty*

https://egzamin-programista.pl/arkusz-praktyczny-inf03-2025-01-11

Realizacja poleceń:
```
CREATE DATABASE konkurs
  CHARACTER SET utf8mb4
  COLLATE utf8mb4_unicode_ci;

USE konkurs;

USE konkurs;
SHOW TABLES;
SELECT COUNT(*) FROM nagrody;
DESCRIBE nagrody;


SELECT nazwa, opis, cena
FROM nagrody
ORDER BY RAND()
LIMIT 5;

SELECT *
FROM nagrody
WHERE cena BETWEEN 100 AND 1000
  AND ilosc = 2;


DELETE FROM nagrody
WHERE cena IS NULL OR cena = 0;

SELECT nazwa, cena, data_dodania
FROM nagrody
WHERE data_dodania >= '2021-08-01' AND data_dodania < '2021-09-01'
ORDER BY data_dodania ASC;

```





**Zadanie 2**

*Utwórz bazę danych o nazwie szachy, z zestawem polskich znaków (np. utf8_unicode_ci)*

*Z rozpakowanego archiwum zaimportuj tabelę z pliku szachy.sql do utworzonej  bazy*

*Wykonaj zrzut ekranu po imporcie. Zapisz zrzut w formacie PNG pod nazwą import. Nie kadruj zrzutu. Powinien on obejmować cały ekran monitora, z widocznym paskiem zadań. Na zrzucie powinny być widoczne elementy wskazujące na poprawnie wykonany import tabel*

*Wykonaj zapytania SQL działające na bazie szachy. Zapytania zapisz w pliku kwerendy.txt. Wykonaj zrzuty ekranu przedstawiające wyniki działania kwerend. Zrzuty zapisz w formacie PNG i nadaj im nazwy kw1, kw2, kw3, kw4. Zrzuty powinny obejmować cały ekran monitora z widocznym paskiem zadań*

*Zapytanie 1: wybierające jedynie pseudonim, tytuł, ranking i klasę dla rankingów większych od 2787, posortowane malejąco według rankingu*

*Zapytanie 2: wybierające losowo dokładnie dwa rekordy złożone z pól pseudonim i klasa z tabeli zawodnicy*

*Zapytanie 3: aktualizujące dane w kolumnie klasa. Klasa „4A” jest aktualizowana do „5A”*

*Zapytanie 4: wybierające dla zawodników z niepustym tytułem jedynie pseudonim i datę zdobycia oraz obliczające ile minęło dni od daty zdobycia tytułu do dnia dzisiejszego. Obliczona liczba dni powinna być zapisana pod nazwą kolumny (aliasem) “dni”.*

https://egzamin-programista.pl/arkusz-praktyczny-inf03-2025-01-10

```
CREATE DATABASE  szachy
  CHARACTER SET utf8mb4
  COLLATE utf8mb4_unicode_ci;

USE szachy;
SELECT pseudonim, tytul, ranking, klasa
FROM zawodnicy
WHERE ranking > 2787
ORDER BY ranking DESC;



SELECT pseudonim, klasa
FROM zawodnicy
ORDER BY RANDOM()
LIMIT 2;

SELECT pseudonim, klasa
FROM zawodnicy
ORDER BY RAND()
LIMIT 2;



UPDATE zawodnicy
SET klasa = '5A'
WHERE klasa = '4A';


SELECT pseudonim, data_zdobycia, (CURRENT_DATE - data_zdobycia) AS dni
FROM zawodnicy
WHERE tytul IS NOT NULL AND tytul <> '';


SELECT pseudonim, data_zdobycia, DATEDIFF(CURDATE(), data_zdobycia) AS dni
FROM zawodnicy
WHERE tytul IS NOT NULL AND tytul <> '';

```

**Zadanie 3**
*Utwórz bazę danych o nazwie zdobywcy, z zestawem polskich znaków (np. utf8_unicode_ci)*

*Z rozpakowanego archiwum zaimportuj tabele z pliku baza.sql do utworzonej  bazy*

*Wykonaj zrzut ekranu po imporcie. Zapisz zrzut w formacie PNG pod nazwą import. Nie kadruj zrzutu. Powinien on obejmować cały ekran monitora, z widocznym paskiem zadań. Na zrzucie powinny być widoczne elementy wskazujące na poprawnie wykonany import tabel*

*Wykonaj zapytania SQL działające na bazie zdobywcy. Zapytania zapisz w pliku kwerendy.txt. Wykonaj zrzuty ekranu przedstawiające wyniki działania kwerend. Zrzuty zapisz w formacie PNG i nadaj im nazwy kw1, kw2, kw3, kw4. Zrzuty powinny obejmować cały ekran monitora z widocznym paskiem zadań*

*Zapytanie 1: wybierające jedynie pasmo, nazwę góry i jej wysokość z tabeli gory i wyświetlające pierwszych 10 rekordów posortowanych malejąco według wysokości*

*Zapytanie 2: wybierające jedynie nazwisko, imię, funkcję i email z tabeli osoby*

*Zapytanie 3: wstawiające osiągnięcie w postaci zdobycia góry „Łysica - Skała Agaty” (id=182) przez uczestnika B. Urszula (id=4) w dniu 2024-06-08, klucz główny uzyskiwany automatycznie*

*Zapytanie 4: wstawiające nową osobę: M., Miłosz, uczestnik, m.milosz@zdobywcyxyz.pl do tabeli osoby, klucz główny uzyskiwany automatycznie*
https://egzamin-programista.pl/arkusz-praktyczny-inf03-2025-01-09

```
CREATE DATABASE IF NOT EXISTS zdobywcy CHARACTER SET utf8 COLLATE utf8_unicode_ci;
USE zdobywcy;

SELECT pasmo, nazwa, wysokosc
FROM gory
ORDER BY wysokosc DESC
LIMIT 10;

SELECT nazwisko, imie, funkcja, email
FROM osoby;

INSERT INTO osiagniecia (id_gory, id_osoby, data)
VALUES (182, 4, '2024-06-08');

INSERT INTO osoby (nazwisko, imie, funkcja, email)
VALUES ('M.', 'Miłosz', 'uczestnik', 'm.milosz@zdobywcyxyz.pl');

```

Przypomnienie jak dodać baze danych 

***Krok 1 stwórz baze***

<img width="333" height="144" alt="image" src="https://github.com/user-attachments/assets/0c0b17e9-ef85-4aea-a41e-b12578b0d9f5" />

***Krok 2 zaimportuj  pobraną baze danych***

<img width="532" height="396" alt="image" src="https://github.com/user-attachments/assets/582b7b2e-0a9a-4870-b5b4-ff2b12ca2253" />

*** Krok 3***

<img width="203" height="495" alt="Przechwytywanie" src="https://github.com/user-attachments/assets/8a5d6e51-8867-453e-9d19-346ec751f3c2" />

***Krok 4***

<img width="1209" height="709" alt="image" src="https://github.com/user-attachments/assets/760dd22a-8ee2-45eb-b31d-d79890923dd4" />

***Krok 5 wpisujemy zapytanie 1***

<img width="883" height="673" alt="image" src="https://github.com/user-attachments/assets/afa159cf-f555-4b17-ac02-15af6bcba1b5" />


<img width="885" height="304" alt="image" src="https://github.com/user-attachments/assets/5c6192cd-3983-42f8-be40-9ad3f2bcf615" />


-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
***26.09.2025***

**Zadanie 1. Mieszalnia farb**

https://egzamin-programista.pl/arkusz-praktyczny-inf03-2025-01-08

<img width="911" height="237" alt="image" src="https://github.com/user-attachments/assets/e8601e06-0056-4793-a260-b8baf6544f2b" />


Utwórz bazę danych o nazwie mieszalnia, z zestawem polskich znaków (np. utf8_unicode_ci)

Do utworzonej  bazy zaimportuj tabele z pliku mieszalnia.sql z rozpakowanego archiwum

Wykonaj zrzut ekranu po imporcie. Zapisz zrzut w formacie JPEG pod nazwą import. Nie kadruj zrzutu. Powinien on obejmować cały ekran monitora, z widocznym paskiem zadań. Na zrzucie powinny być widoczne elementy wskazujące na poprawnie wykonany import tabel

Wykonaj zapytania SQL działające na bazie mieszalnia. 

Zapytania zapisz w pliku kwerendy.txt. Wykonaj zrzuty ekranu przedstawiające wyniki działania kwerend. Zrzuty zapisz w formacie PNG i nadaj im nazwy kw1, kw2, kw3, kw4. Zrzuty powinny obejmować cały ekran monitora, z widocznym paskiem zadań

Zapytanie 1: zliczające liczbę klientów mieszalni farb

Zapytanie 2: wybierające jedynie nazwiska, imiona klientów oraz odpowiadające im numery zamówień (pole id), kody kolorów, pojemności i daty odbioru zamówień posortowane rosnąco po dacie odbioru. Należy posłużyć się relacją

Zapytanie 3: wybierające jedynie nazwiska, imiona klientów oraz odpowiadające im numery zamówień (pole id), kody kolorów, pojemności i daty odbioru zamówień posortowane rosnąco po dacie odbioru, jedynie dla zamówień, w których data odbioru jest od 5 listopada do 7 listopada 2021 roku. Należy posłużyć się relacją

Zapytanie 4: wybierające jedynie imiona i nazwiska kobiet, które są klientami mieszalni farb

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Zadanie 2 Wyszukiwanie miast**

https://egzamin-programista.pl/arkusz-praktyczny-inf03-2025-01-07

<img width="884" height="251" alt="image" src="https://github.com/user-attachments/assets/f9766ab2-cc92-4657-95c7-8546ff098276" />
 
Utwórz bazę danych o nazwie wykaz, z zestawem polskich znaków (np. utf8_unicode_ci)

Do utworzonej bazy zaimportuj tabele z pliku wykaz.sql z rozpakowanego archiwum

Wykonaj zrzut ekranu po imporcie. Zapisz zrzut w formacie PNG pod nazwą import. Nie kadruj zrzutu. Powinien on obejmować cały ekran monitora, z widocznym paskiem zadań. Na zrzucie powinny być widoczne elementy wskazujące na poprawnie wykonany import tabel

Wykonaj zapytania SQL działające na bazie wykaz. Zapytania zapisz w pliku kwerendy.txt. Wykonaj zrzuty ekranu przedstawiające wyniki działania kwerend. Zrzuty zapisz w formacie PNG i nadaj im nazwy kw1, kw2, kw3, kw4. Zrzuty powinny obejmować cały ekran monitora, z widocznym paskiem zadań

Zapytanie 1: wybierające jedynie nazwy województw, wszystkie litery w nazwach województw są zamienione na małe

Zapytanie 2: obliczające liczbę miast dla których id_wojewodztwa jest równe jeden

Zapytanie 3: wybierające jedynie nazwy miast zaczynające się od cząstki „Lu” i odpowiadające im nazwy województw, posortowane alfabetycznie po nazwie miasta. Należy posłużyć się relacją

Zapytanie 4: wybierające jedynie nazwy województw i odpowiadającą im liczbę miast, które się w nich znajdują. Kolumna z liczbą miast powinna mieć nadany alias „Liczba miast”. Należy posłużyć się relacją

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Po wykonaniu zadań prześlij dokument lub .pdf 

z kodem i zrzutem ekranu wykonanych zadań 

na maila: 

wykonanezadania100@gmail.com

podpisz dokument Imię Nazwisko data

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```
SELECT COUNT(*) AS liczba_klientow
FROM klienci;

SELECT k.Nazwisko, k.Imie, z.id, z.kod_koloru, z.pojemnosc, z.data_odbioru
FROM klienci k
JOIN zamowienia z ON k.Id = z.id_klienta
ORDER BY z.data_odbioru ASC;

SELECT k.Nazwisko, k.Imie, z.id, z.kod_koloru, z.pojemnosc, z.data_odbioru
FROM klienci k
JOIN zamowienia z ON k.Id = z.id_klienta
WHERE z.data_odbioru BETWEEN '2021-11-05' AND '2021-11-07'
ORDER BY z.data_odbioru ASC;

SELECT Imie, Nazwisko
FROM klienci
WHERE Plec = 'k';
```
rosnąco → ASC (ang. ascending)

malejąco → DESC (ang. descending)
```
-- Posortuj klientów rosnąco wg nazwiska
SELECT * FROM klienci
ORDER BY Nazwisko ASC;

-- Posortuj klientów malejąco wg nazwiska
SELECT * FROM klienci
ORDER BY Nazwisko DESC;

-- Posortuj zamówienia: najpierw najnowsze daty
SELECT * FROM zamowienia
ORDER BY data_odbioru DESC;
```

----


https://egzamin-programista.pl/arkusz-praktyczny-inf03-2025-01-04/

https://egzamin-programista.pl/arkusz-praktyczny-inf03-2025-01-05/

Arkusz 4 
```
SELECT model FROM produkt;
SELECT model, nazwa, cena, nazwa_pliku FROM buty JOIN produkt
USING(model);
SELECT nazwa, cena, kolor, kod_produktu, material, nazwa_pliku FROM
buty JOIN produkt USING(model) WHERE model = "P-59-03";
INSERT INTO kategorie VALUES (NULL, 'Sandały');
```
Arkusz 5 
```
SELECT Data, Temat FROM szkolenia ORDER BY Data ASC;
SELECT Data, Temat, Nazwisko, Imie FROM szkolenia JOIN trenerzy ON
trenerzy.Id = szkolenia.Id_trenera;
SELECT Imie, Nazwisko, COUNT(*) FROM trenerzy JOIN szkolenia ON
trenerzy.Id = Id_trenera GROUP BY trenerzy.Id;
ALTER TABLE zapisy CHANGE COLUMN Id_klienta Id_sluchacza INT;
```
----

https://egzamin-programista.pl/arkusz-praktyczny-inf03-2025-01-02/

https://egzamin-programista.pl/arkusz-praktyczny-inf03-2024-06-12/

----







```
SELECT imie, nazwisko FROM osoby WHERE imie LIKE "A%";
SELECT zadanie, data FROM zadania WHERE zadanie LIKE "%mebli%"
ORDER BY data; 

SELECT nazwisko, COUNT(zadania.id_zadania) AS "Liczba zadań" FROM
osoby JOIN zadania ON id_osoba = osoba_id GROUP BY nazwisko;

ALTER TABLE osoby DROP COLUMN telefon;
```

```
SELECT imie, pensja FROM pracownicy WHERE staz < 5;

SELECT AVG(pensja), nazwa FROM pracownicy JOIN stanowiska ON
stanowiska_id = stanowiska.id GROUP BY nazwa;

SELECT imie, nazwisko, pensja FROM pracownicy WHERE pensja =
(SELECT MAX(pensja) FROM pracownicy); dopuszcza się również zastosowanie
MAX(pensja) lub LIMIT 1

UPDATE pracownicy SET staz = staz + 1;
```

# Тема: Запросы SELECT, INSERT, UPDATE, DELETE.

## Создание таблиц с использованием скрипта запроса:

### Скрипт запроса для создания таблицы Кафедры (Departments):

* CREATE TABLE Departments (
* Id INT IDENTITY(1,1) PRIMARY KEY,
* Financing MONEY NOT NULL CHECK (Financing >= 0) DEFAULT 0,
* Name NVARCHAR(100) NOT NULL UNIQUE);

### Скрипт запроса для создания таблицы Факультеты (Faculties):

* CREATE TABLE Faculties (
* Id INT IDENTITY(1,1) PRIMARY KEY NOT NULL,
* Dean NVARCHAR(MAX) NOT NULL CHECK (Dean <> ''),
* Name NVARCHAR(100) UNIQUE NOT NULL CHECK (Name <> ''));

### Скрипт запроса для создания таблицы Группы (Groups):

* CREATE TABLE Groups (
* Id INT IDENTITY(1,1) PRIMARY KEY NOT NULL,
* Name NVARCHAR(10) NOT NULL UNIQUE CHECK (Name <> ''),
* Rating INT NOT NULL CHECK (Rating BETWEEN 0 AND 5),
* Year INT NOT NULL CHECK (Year BETWEEN 1 AND 5));

### Скрипт запроса для создания таблицы Преподаватели (Teachers):

* CREATE TABLE Teachers (
* Id INT IDENTITY(1,1) PRIMARY KEY NOT NULL,
* EmploymentDate DATE NOT NULL CHECK (EmploymentDate >= '1990-01-01'),
* IsAssistant BIT NOT NULL DEFAULT 0,
* IsProfessor BIT NOT NULL DEFAULT 0,
* Name NVARCHAR(MAX) NOT NULL CHECK (Name <> ''),
* Position NVARCHAR(MAX) NOT NULL CHECK (Position <> ''),
* Premium MONEY NOT NULL DEFAULT 0 CHECK (Premium >= 0),
* Salary MONEY NOT NULL CHECK (Salary > 0),
* Surname NVARCHAR(MAX) NOT NULL CHECK (Surname <> ''));

### Скрипты запросов для вывода всех таблиц и данных в них:
* SELECT * FROM Departments;
* SELECT * FROM Faculties;
* SELECT * FROM Groups;
* SELECT * FROM Teachers;
## Скрин с информацией о всех таблицах и данных в них:
<img width="760" alt="image" src="https://github.com/user-attachments/assets/c26261d2-56c4-4bfc-a040-b3fa1d24af1e">

## Запросы из задания и результат выполнения запросов:

1. Вывести таблицу кафедр, но расположить ее поля в обратном порядке.
### Скрипт:
* SELECT * FROM Departments ORDER BY ID DESC;
### Результат выполнения:
<img width="762" alt="image" src="https://github.com/user-attachments/assets/9a891731-31b5-4c32-91f9-a4f8cfa7d506">


2. Вывести названия групп и их рейтинги с уточнением имен полей именем таблицы.
### Скрипт:
* SELECT Name AS 'Group Name', Rating AS 'Group Rating' FROM Groups;
### Результат выполнения:
<img width="763" alt="image" src="https://github.com/user-attachments/assets/fde0cedc-2173-4e17-bbb3-c903550817cb">



3. Вывести для преподавателей их фамилию, процент ставки по отношению к надбавке и процент ставки по отношению к зарплате (сумма ставки и надбавки).
### Скрипт:
* SELECT Surname, Salary/Premium*100 AS 'Percentage to Premium', Salary/(Salary+Premium)*100 AS 'Percentage to Salary' FROM Teachers;
### Результат выполнения:
<img width="898" alt="image" src="https://github.com/user-attachments/assets/36d72d6d-072e-41d1-838b-6d18ea24709a">


4. Вывести таблицу факультетов в виде одного поля в следующем формате: “The dean of faculty [faculty] is [dean].”.
### Скрипт:
* SELECT 'The dean of faculty ' + Name + ' is ' + Dean AS Faculty FROM Faculties;
### Результат выполнения:
<img width="766" alt="image" src="https://github.com/user-attachments/assets/21d3be6e-6494-494b-8370-a67c03a2a929">


5. Вывести фамилии преподавателей, которые являются профессорами и ставка которых превышает 1050.
### Скрипт:
* SELECT Surname FROM Teachers WHERE IsProfessor = 1 AND Salary > 1050;
### Результат выполнения:
<img width="758" alt="image" src="https://github.com/user-attachments/assets/c532f0c2-d8c9-4c87-a3fa-689f3d998074">


6. Вывести названия кафедр, фонд финансирования которых меньше 11000 или больше 25000.
### Скрипт:
* SELECT Name FROM Departments WHERE Financing < 11000 OR Financing > 25000;
### Результат выполнения:
<img width="760" alt="image" src="https://github.com/user-attachments/assets/f63599f2-8d57-4353-bc64-33b6725c24d1">


7. Вывести названия факультетов кроме факультета “Computer Science”.
### Скрипт:
* SELECT Name FROM Faculties WHERE Name <> 'Computer Science';
### Результат выполнения:
<img width="760" alt="image" src="https://github.com/user-attachments/assets/64c4beeb-9bc9-431b-b711-02265ea59921">


8. Вывести фамилии и должности преподавателей, которые не являются профессорами.
### Скрипт:
* SELECT Surname, Position FROM Teachers WHERE IsProfessor = 0;
### Результат выполнения:
<img width="761" alt="image" src="https://github.com/user-attachments/assets/568bb5bd-a2fb-4200-a096-84a361faa90f">


9. Вывести фамилии, должности, ставки и надбавки ассистентов, у которых надбавка в диапазоне от 160 до 550.
### Скрипт:
* SELECT Surname, Position, Salary, Premium FROM Teachers WHERE IsAssistant = 1 AND Premium BETWEEN 160 AND 550;
### Результат выполнения:
<img width="755" alt="image" src="https://github.com/user-attachments/assets/3bcc5e14-1c88-41c1-8508-458f1e841598">


10.Вывести фамилии и ставки ассистентов.
### Скрипт:
* SELECT Surname, Salary FROM Teachers WHERE IsAssistant = 1;
### Результат выполнения:
<img width="758" alt="image" src="https://github.com/user-attachments/assets/3ebef4d4-ff9c-46a6-898a-f71cf9d9248f">


11.Вывести фамилии и должности преподавателей, которые были приняты на работу до 01.01.2000.
### Скрипт:
* SELECT Surname, Position FROM Teachers WHERE EmploymentDate < '2000-01-01';
### Результат выполнения:
<img width="756" alt="image" src="https://github.com/user-attachments/assets/f9374732-76e3-4c60-851b-32ede3f75daf">


12.Вывести названия кафедр, которые в алфавитном порядке располагаются до кафедры “Software Development”. Выводимое поле должно иметь название “Name of Department”.
### Скрипт:
* SELECT Name AS "Name of Department" FROM Departments WHERE Name < 'Software Development';
### Результат выполнения:
<img width="756" alt="image" src="https://github.com/user-attachments/assets/05807040-013d-4e17-a721-36335021a6db">

13.Вывести фамилии ассистентов, имеющих зарплату (сумма ставки и надбавки) не более 1200.
### Скрипт:
* SELECT Surname FROM Teachers WHERE IsAssistant = 1 AND (Salary + Premium) <= 1200;
### Результат выполнения:
<img width="759" alt="image" src="https://github.com/user-attachments/assets/29f9e3b3-9dc8-4f62-9702-53ea2bc9eb63">


14.Вывести названия групп 5-го курса, имеющих рейтинг в диапазоне от 2 до 4.
### Скрипт:
* SELECT Name FROM Groups WHERE Year = 5 AND Rating BETWEEN 2 AND 4;
### Результат выполнения:
<img width="757" alt="image" src="https://github.com/user-attachments/assets/32c050c9-f413-443e-97a2-65224e26ed6d">


15.Вывести фамилии ассистентов со ставкой меньше 550 или надбавкой меньше 200.   
### Скрипт:
* SELECT Surname FROM Teachers WHERE IsAssistant = 1 AND (Salary < 550 OR Premium < 200);
### Результат выполнения:
<img width="763" alt="image" src="https://github.com/user-attachments/assets/e25ef8ff-b05d-4b8c-b549-21be022a79e7">




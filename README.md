# Тема: Запросы SELECT, INSERT, UPDATE, DELETE.

## Создание таблиц с использованием скрипта запроса:

### Скрипт запроса для создания таблицы Кафедры (Departments):

CREATE TABLE Departments (
    Id INT IDENTITY(1,1) PRIMARY KEY,
    Financing MONEY NOT NULL CHECK (Financing >= 0) DEFAULT 0,
    Name NVARCHAR(100) NOT NULL UNIQUE
);

### Скрипт запроса для создания таблицы Факультеты (Faculties):

CREATE TABLE Faculties (
Id INT IDENTITY(1,1) PRIMARY KEY NOT NULL,
Dean NVARCHAR(MAX) NOT NULL CHECK (Dean <> ''),
Name NVARCHAR(100) UNIQUE NOT NULL CHECK (Name <> '')
);

### Скрипт запроса для создания таблицы Группы (Groups):

CREATE TABLE Groups (
Id INT IDENTITY(1,1) PRIMARY KEY NOT NULL,
Name NVARCHAR(10) NOT NULL UNIQUE CHECK (Name <> ''),
Rating INT NOT NULL CHECK (Rating BETWEEN 0 AND 5),
Year INT NOT NULL CHECK (Year BETWEEN 1 AND 5)
);

### Скрипт запроса для создания таблицы Преподаватели (Teachers):

  CREATE TABLE Teachers (
    Id INT IDENTITY(1,1) PRIMARY KEY NOT NULL,
    EmploymentDate DATE NOT NULL CHECK (EmploymentDate >= '1990-01-01'),
    IsAssistant BIT NOT NULL DEFAULT 0,
    IsProfessor BIT NOT NULL DEFAULT 0,
    Name NVARCHAR(MAX) NOT NULL CHECK (Name <> ''),
    Position NVARCHAR(MAX) NOT NULL CHECK (Position <> ''),
    Premium MONEY NOT NULL DEFAULT 0 CHECK (Premium >= 0),
    Salary MONEY NOT NULL CHECK (Salary > 0),
    Surname NVARCHAR(MAX) NOT NULL CHECK (Surname <> '')
);






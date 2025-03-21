-- Employee Management System Database Schema Design

-- Creating the Employees table
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL,
    Position VARCHAR(50) NOT NULL,
    ContactDetails VARCHAR(150),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);

-- Creating the Departments table
CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY AUTO_INCREMENT,
    DepartmentName VARCHAR(100) NOT NULL,
    DepartmentHead VARCHAR(100)
);

-- Creating the Salaries table
CREATE TABLE Salaries (
    SalaryID INT PRIMARY KEY AUTO_INCREMENT,
    EmployeeID INT,
    Amount DECIMAL(10, 2) NOT NULL,
    LastUpdated DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);

-- Creating the EmployeeTasks table
CREATE TABLE EmployeeTasks (
    TaskID INT PRIMARY KEY AUTO_INCREMENT,
    EmployeeID INT,
    TaskDescription TEXT NOT NULL,
    IsCompleted BOOLEAN DEFAULT FALSE,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);

-- Sample data insertion
INSERT INTO Departments (DepartmentName, DepartmentHead) VALUES ('IT', 'John Doe');
INSERT INTO Departments (DepartmentName, DepartmentHead) VALUES ('HR', 'Jane Smith');

INSERT INTO Employees (Name, Position, ContactDetails, DepartmentID) VALUES ('Alice Brown', 'Developer', 'alice@example.com', 1);
INSERT INTO Employees (Name, Position, ContactDetails, DepartmentID) VALUES ('Bob White', 'HR Specialist', 'bob@example.com', 2);

INSERT INTO Salaries (EmployeeID, Amount, LastUpdated) VALUES (1, 5000.00, '2025-03-21');
INSERT INTO Salaries (EmployeeID, Amount, LastUpdated) VALUES (2, 4000.00, '2025-03-21');

INSERT INTO EmployeeTasks (EmployeeID, TaskDescription, IsCompleted) VALUES (1, 'Complete module development.', FALSE);
INSERT INTO EmployeeTasks (EmployeeID, TaskDescription, IsCompleted) VALUES (2, 'Organize employee training.', FALSE);

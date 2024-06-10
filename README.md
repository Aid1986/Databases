Сурмач Андрей Андреевич
# Databases
# Задание_1
Сотрудники (Employees) 
sql 
 
CREATE TABLE Employees ( 
    employee_id SERIAL PRIMARY KEY, 
    last_name VARCHAR(50), 
    first_name VARCHAR(50), 
    middle_name VARCHAR(50), 
    birth_date DATE, 
    hire_date DATE, 
    job_title_id INTEGER REFERENCES JobTitles(job_title_id), 
    department_id INTEGER REFERENCES Departments(department_id), 
    project_id INTEGER REFERENCES Projects(project_id) 
); 
employee_id (идентификатор) - первичный ключ, serial 
last_name (фамилия) - varchar(50) 
first_name (имя) - varchar(50) 
middle_name (отчество) - varchar(50) 
birth_date (дата рождения) - date 
hire_date (дата приёма на работу) - date 
job_title_id (идентификатор должности) - внешний ключ, integer 
department_id (идентификатор структурного подразделения) - внешний ключ, integer 
project_id (идентификатор проекта) - внешний ключ, integer 
Должности (JobTitles) 
sql 
 
CREATE TABLE JobTitles ( 
    job_title_id SERIAL PRIMARY KEY, 
    job_title VARCHAR(50) 
); 
job_title_id (идентификатор) - первичный ключ, serial 
job_title (должность) - varchar(50) 
Структурные подразделения (Departments) 
sql 
 
CREATE TABLE Departments ( 
    department_id SERIAL PRIMARY KEY, 
    department_name VARCHAR(50), 
    manager_id INTEGER REFERENCES Employees(employee_id) 
); 
department_id (идентификатор) - первичный ключ, serial 
department_name (название подразделения) - varchar(50) 
manager_id (идентификатор менеджера) - внешний ключ, integer 
Проекты (Projects) 
sql 
 
CREATE TABLE Projects ( 
    project_id SERIAL PRIMARY KEY, 
    project_name VARCHAR(100), 
    start_date DATE, 
    end_date DATE, 
    budget NUMERIC(15, 2) 
); 
project_id (идентификатор) - первичный ключ, serial 
project_name (название проекта) - varchar(100) 
start_date (дата начала) - date 
end_date (дата окончания) - date 
budget (бюджет) - numeric(15, 2) 
Участие в проектах (ProjectParticipation) 
sql 
 
CREATE TABLE ProjectParticipation ( 
    participation_id SERIAL PRIMARY KEY, 
    project_id INTEGER REFERENCES Projects(project_id), 
    employee_id INTEGER REFERENCES Employees(employee_id), 
    role VARCHAR(50) 
); 
participation_id (идентификатор) - первичный ключ, serial 
project_id (идентификатор проекта) - внешний ключ, integer 
employee_id (идентификатор сотрудника) - внешний ключ, integer 
role (роль в проекте) - varchar(50) 
Зарплаты (Salaries) 
sql 
 
CREATE TABLE Salaries ( 
    salary_id SERIAL PRIMARY KEY, 
    employee_id INTEGER REFERENCES Employees(employee_id), 
    salary NUMERIC(15, 2), 
    effective_date DATE 
); 
salary_id (идентификатор) - первичный ключ, serial 
employee_id (идентификатор сотрудника) - внешний ключ, integer 
salary (зарплата) - numeric(15, 2) 
effective_date (дата вступления в силу) - date 
Адреса сотрудников (EmployeeAddresses) 
sql 
 
CREATE TABLE EmployeeAddresses ( 
    address_id SERIAL PRIMARY KEY, 
    employee_id INTEGER REFERENCES Employees(employee_id), 
    address VARCHAR(200), 
    city VARCHAR(50), 
    state VARCHAR(50), 
    postal_code VARCHAR(10), 
    country VARCHAR(50) 
); 
address_id (идентификатор) - первичный ключ, serial 
employee_id (идентификатор сотрудника) - внешний ключ, integer 
address (адрес) - varchar(200) 
city (город) - varchar(50) 
state (штат/область) - varchar(50) 
postal_code (почтовый индекс) - varchar(10) 
country (страна) - varchar(50) 
Отпуска (Vacations) 
sql 
 
CREATE TABLE Vacations ( 
    vacation_id SERIAL PRIMARY KEY, 
    employee_id INTEGER REFERENCES Employees(employee_id), 
    start_date DATE, 
    end_date DATE, 
    type VARCHAR(50) 
); 
vacation_id (идентификатор) - первичный ключ, serial 
employee_id (идентификатор сотрудника) - внешний ключ, integer 
start_date (дата начала отпуска) - date 
end_date (дата окончания отпуска) - date 
type (тип отпуска) - varchar(50) 

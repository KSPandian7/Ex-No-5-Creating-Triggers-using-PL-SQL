# Ex. No: 5 Creating Triggers using PL/SQL
### DATE : 31/08/2023
### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:

```ruby
DEVELOPED BY : KULASEKARAPANDIAN K
REGISTER NO : 212222240052
DEVELOPED IN: MySQL Workbench
```


### Create employee table
```sql
CREATE TABLE employee (
  empid INT,
  empname VARCHAR(19),
  dept VARCHAR(19),
  salary INT
);
```

### Create salary_log table
```sql
CREATE TABLE salary_log (
  log_id INT,
  empid INT,
  empname VARCHAR(50),
  old_salary INT,
  new_salary INT,
  update_date DATE
);
```
#### Insert values:
```sql
INSERT INTO employee VALUES(101, 'kulasekarapandian', 'AIML', 100000);
INSERT INTO employee VALUES(102, 'aravind', 'AIDS', 200000);
INSERT INTO employee VALUES(103, 'imthiyas', 'AIDS', 300000);
```

### PLSQL Trigger code
```sql
DELIMITER //
CREATE TRIGGER log_salary_update
BEFORE UPDATE ON employee
FOR EACH ROW
BEGIN
  IF NEW.salary != OLD.salary THEN
    INSERT INTO salary_log (empid, empname, old_salary, new_salary, update_date)
    VALUES (OLD.empid, OLD.empname, OLD.salary, NEW.salary, current_timestamp());
    END IF;
END //
```

### Update Table:
```sql
ALTER TABLE employee
MODIFY empname VARCHAR(19);

ALTER TABLE employee
MODIFY dept VARCHAR(19);

ALTER TABLE employee
MODIFY salary INT;

UPDATE employee SET salary = 200000 WHERE empid = 101;

UPDATE employee SET salary = 200000, empname = 'ksp' WHERE empid = 101;
```

### Run Command:
```sql
SELECT * FROM employee;

SELECT * FROM salary_log;
```


### Output:

#### Employee Table:
![employeeop](https://github.com/KSPandian7/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/113496887/9e1afbb1-1525-4228-94a5-f1faa3a7ae35)


#### Salary_log Table:
![salary_logop](https://github.com/KSPandian7/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/113496887/10f5229b-9a1a-4636-a2ec-29c9213a1032)



### Result:
THE PROGRAM HAS BEEN IMPLEMENTED SUCCESSFULLY.

# Ex. No: 5 Creating Triggers using PL/SQL
# DATE:12.9.23
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
```
NAME: R KAVIKEERTHANA
Reg.no: 212222100022
```

### Create employee table
```
SQL> create table employeeee(empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
```
![Screenshot 2023-10-08 131839](https://github.com/RKavikeerthana/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120431120/bc31707b-db02-48cd-a357-7bf4154ab335)


### Create salary_log table
```
SQL> Create table salary_log (log_id NUMBER , empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,updat
e_date DATE);
```
![image](https://github.com/RKavikeerthana/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120431120/353db50b-a50c-4384-8351-4ffd4bb55f9c)

### PLSQL Trigger code
```
SQL> create or replace trigger salary_log_update
  2  before update on employeeee
  3  for each row
  4  declare
  5  v_old_salary NUMBER;
  6  v_new_salary NUMBER;
  7  begin
  8  v_old_salary:= :old.salary;
  9  v_new_salary:= :new.salary;
 10  if v_old_salary <> v_new_salary then
 11  insert into salary_log (empid, empname, old_salary, new_salary, update_date)
 12  values(:old.empid, :old.empname, v_old_salary, v_new_salary, sysdate);
 13  end if;
 14  end;
 15  /

SQL> update employeeee set salary=15000 where empid=1;

```

### Output:
![image](https://github.com/RKavikeerthana/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120431120/3044638f-3877-45f3-85cf-1a714410f624)
![image](https://github.com/RKavikeerthana/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120431120/b00efd06-0578-4795-9e9d-72b6b5691f32)



### Result:
The program has been implemented successfully.

# Joins
[Oracle Documentation](https://docs.oracle.com/en/database/oracle/oracle-database/21/index.html)  

---

**INNER**  
Combines common between two or more tables  
```SQL
SELECT columns
FROM table1 
INNER JOIN table2
ON table1.column = table2.column;
```
**LEFT OUTER**  
Returns all rows from left table, and only rows from the other table which match left table rows  
```SQL
SELECT columns
FROM table1
LEFT [OUTER] JOIN table2
ON table1.column = table2.column;
```  
**FULL OUTER JOIN**  
Returns all rows from left and right tables with nulls in place for non-matching rows  
```SQL
SELECT columns
FROM table1
FULL [OUTER] JOIN table2
ON table1.column = table2.column
```

---

#### SELF Join  
Combines columns from single table
```SQL
SELECT col1.attribute1, col2.attribute1
FROM tableName t1, tableName t2 -- t1 and t2 reference the same table  
WHERE col1.attribute_x = col2.attribute_y
```
*An example of this is to obtain the last name of all employees and managers from a single table*  
```SQL
SELECT e1.last_name||' works for '||e2.last_name 
   "Employees and Their Managers"
   FROM employees e1, employees e2 
   WHERE e1.manager_id = e2.employee_id
      AND e1.last_name LIKE 'R%'
   ORDER BY e1.last_name;

Employees and Their Managers   
-------------------------------
Rajs works for Mourgos
Raphaely works for King
Rogers works for Kaufling
Russell works for King
```

#### ANTI Joins  
Returns rows from the left side of the predicate for which there are no corresponding rows on the right side  
```SQL
SELECT * from tableName
   WHERE attribute NOT IN 
   (SELECT attribute from attributeTableNames
      WHERE attributeColumn = 0);
```
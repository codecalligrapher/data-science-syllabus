# Group By
Groups a result into subsets matching values for one or more columns, in each group, no two rows have the same value for grouping columns  

## Rollup Syntax  
Allows multiple group-by's  
```SQL  
GROUP BY 
{
columnName [ , columnName ]*  
|
ROLLUP ( columnName [ , columnName ]* )
}
```

## Aggregate Functions
```SQL
-- find the average flying_times of flights grouped by
-- airport
SELECT AVG (flying_time), orig_airport
FROM Flights
GROUP BY orig_airport

SELECT MAX(city_name), region
FROM Cities, Countries
WHERE Cities.country_ISO_code = Countries.country_ISO_code
GROUP BY region

-- group by an a smallint
SELECT ID, AVG(SALARY)
FROM SAMP.STAFF
GROUP BY ID

-- Get the AVGSALARY and EMPCOUNT columns, and the DEPTNO column using the AS clause
-- And group by the WORKDEPT column using the correlation name OTHERS
SELECT OTHERS.WORKDEPT AS DEPTNO,
AVG(OTHERS.SALARY) AS AVGSALARY,
COUNT(*) AS EMPCOUNT
FROM SAMP.EMPLOYEE OTHERS
GROUP BY OTHERS.WORKDEPT

-- Compute sub-totals of Sales_History data, grouping it by Region, by
-- (Region, State), and by (Region, State, Product), as well as computing
-- an overall total of the sales for all Regions, States, and Products:
SELECT Region, State, Product, SUM(Sales) Total_Sales
FROM Sales_History 
GROUP BY ROLLUP(Region, State, Product)
```


# Correlation with Pearsons's $R$
*corr() returns floating-point*
```SQL 
SELECT corr(X, Y) 
    as meaninful_name_r
FROM table_name
```

# Linear Regression
```SQL
SELECT
    regr_slope(X, y)::numeric as slope,
    regr_intercept(X,y)::numeric as intercept
FROM table_name
```

# Coefficient of Determination $R^2$ 
```SQL
SELECT
    regr_r2(X,y)::numeric as r_squared
FROM table_name
```

# Ranking Things  
## Basic Rank
```SQL
SELECT 
    # other important columns,
    rank() OVER(ORDER BY column_name DESC)
FROM table_name
```
- `rank()` is a window function
- `column_name` is the attribute to rank by  
- `DESC` is the order to rank in (can use `ASC`)

## Subgroup Ranking  
```SQL
SELECT
    # otehr important columns
    rank() OVER (PARTITION BY partition_column ORDER BY rank_column DESC)
```
- `PARTIION BY` splits the ranking into sub-groups

# Basic Math 
## Creating a Rate
```SQL
SELECT
    # other important columns
    round(
        (column_1/column_2) * 100), 2
    ) AS percentage_rate
ORDER BY (column_1/column_2) * 100)
```
- The above is perfectly legal 
    
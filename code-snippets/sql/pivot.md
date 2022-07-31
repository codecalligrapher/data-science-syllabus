# Pivot Tables  
[Pivot Tables in Oracle SQL](https://www.oracletutorial.com/oracle-basics/oracle-pivot/)  
> Transforms table data from rows into columns  

```SQL
SELECT 
    select_list
FROM 
    table_name
PIVOT [XML] ( 
    pivot_clause
    pivot_for_clause
    pivot_in_clause 
);
```

## Example
For a table such as the following
| CATEGORY_NAME | STATUS | ORDER_ID |
| ------------- | ------ | -------- |
| CPU | Canceled | 67 | 
| GPU | Pending | 68 |
| CPU | Cancled | 69 |
| Motherboard | Shipped | 75 |

We return the number of orders for each product category by order status

```SQL
SELECT * FROM order_stats
PIVOT(
    COUNT(order_id) 
    FOR category_name
    IN ( 
        'CPU',
        'Video Card',
        'Mother Board',
        'Storage'
    )
)
ORDER BY status;
```

which returns a table of the of the following:  
| STATUS | CPU | GPU | MotherBoard | 
| --- | --- | --- | --- | 
| Canceled | | | 
| Pending | | |

# HAVING vs WHERE
A HAVING clause is like a WHERE clause, but applies only to groups as a whole (that is, to the rows in the result set representing groups), whereas the WHERE clause applies to individual rows. A query can contain both a WHERE clause and a HAVING clause. In that case:

The WHERE clause is applied first to the individual rows in the tables or table-valued objects in the Diagram pane. Only the rows that meet the conditions in the WHERE clause are grouped.

The HAVING clause is then applied to the rows in the result set. Only the groups that meet the HAVING conditions appear in the query output. You can apply a HAVING clause only to columns that also appear in the GROUP BY clause or in an aggregate function.

# Examples
## Generic Structure
```SQL
SELECT column1, AGGREGATE_FUNCTION(column2)
FROM tableOne INNER JOIN tableTwo
    ON tableOne.field = tableTwo.field
GROUP BY tableOne.groupColumnName
HAVING tableTwo.havingColumnName = 'some value'
```

Above selects two columns from a table join, and first filters based on common matching fields named `field`. The result is grouped by `groupColumnName` and then finally filtered by a column in the second table

## Specific Examples
Imagine that you are joining the titles and publishers tables to create a query showing the average book price for a set of publishers. You want to see the average price for only a specific set of publishers - perhaps only the publishers in the state of California. And even then, you want to see the average price only if it is over $10.00.

You can establish the first condition by including a WHERE clause, which discards any publishers that are not in California, before calculating average prices. The second condition requires a HAVING clause, because the condition is based on the results of grouping and summarizing the data. The resulting SQL statement might look like this:

```SQL
SELECT titles.pub_id, AVG(titles.price)  
FROM titles INNER JOIN publishers  
   ON titles.pub_id = publishers.pub_id  
WHERE publishers.state = 'CA'  
GROUP BY titles.pub_id  
HAVING AVG(price) > 10
```
# References 
https://quip.com/2gwZArKuWk7W

# Coding
1. Calculate the share of new and existing users. Output the month, share of new users, and share of existing users as a ratio. New users are defined as users who started using services in the current month. Existing users are users who started using services in the current month and used services in any previous month. Assume that the dates are all from the year 2020

| id | time_id | user_id | customer_id | client_id | event_types | event_id |
| --- | --- | --- | --- | --- | --- | --- |
|1|2020-02-28| 3434-AQEFN | Sendif | desktop | message_sent | 3

```SQL 
with all_users as (
    SELECT date_part('month', time_id) AS month,
           count(DISTINCT user_id) as all_users
    FROM fact_events
    GROUP BY month),
new_users as (
    SELECT date_part('month', new_user_start_date) AS month,
           count(DISTINCT user_id) as new_users
    FROM
         (SELECT user_id,
           min(time_id) as new_user_start_date
          FROM fact_events
          GROUP BY user_id) sq
    GROUP BY month
)
SELECT
  au.month,
  new_users / all_users::decimal as share_new_users,
  1- (new_users / all_users::decimal) as share_existing_users
FROM all_users au
JOIN new_users nu ON nu.month = au.month
```
[SQL Questions from Google and Amazon](https://www.nicksingh.com/posts/30-sql-and-database-design-questions-from-real-data-science-interviews)

**MoM Percent Change**  
*Context:* Oftentimes it's useful to know how much a key metric, such as monthly active users, changes between months. Say we have a table logins in the form: 

| user_id | date       |
|---------|------------|
| 1       | 2018-07-01 |
| 234     | 2018-07-02 |
| 3       | 2018-07-02 |
| 1       | 2018-07-02 |
| ...     | ...        |
| 234     | 2018-10-04 |

*Task*: Find the month-over-month percentage change for monthly active users (MAU). 
```SQL
WITH mau AS 
(
  SELECT 
   /* 
    * Typically, interviewers allow you to write psuedocode for date functions 
    * i.e. will NOT be checking if you have memorized date functions. 
    * Just explain what your function does as you whiteboard 
    *
    * DATE_TRUNC() is available in Postgres, but other SQL date functions or 
    * combinations of date functions can give you a identical results   
    * See https://www.postgresql.org/docs/9.0/functions-datetime.html#FUNCTIONS-DATETIME-TRUNC
    */ 
    DATE_TRUNC('month', date) month_timestamp,
    COUNT(DISTINCT user_id) mau
  FROM 
    logins 
  GROUP BY 
    DATE_TRUNC('month', date)
  )
 
 SELECT 
    /*
    * You don't literally need to include the previous month in this SELECT statement. 
    * 
    * However, as mentioned in the "Tips" section of this guide, it can be helpful 
    * to at least sketch out self-joins to avoid getting confused which table 
    * represents the prior month vs current month, etc. 
    */ 
    a.month_timestamp previous_month, 
    a.mau previous_mau, 
    b.month_timestamp current_month, 
    b.mau current_mau, 
    ROUND(100.0*(b.mau - a.mau)/a.mau,2) AS percent_change 
 FROM
    mau a 
 JOIN 
    /*
    * Could also have done `ON b.month_timestamp = a.month_timestamp + interval '1 month'` 
    */
    mau b ON a.month_timestamp = b.month_timestamp - interval '1 month' 
  
```

**Tree Structure Labeling** 
*Context:* Say you have a table tree with a column of nodes and a column corresponding parent nodes 

| node | parent | 
| --- | --- |
| 1 | 2 |
| 2 | 5 |
| 3 | 5 |
| 4 | 3 |
|5 | NULL | 

*Task:* Write SQL such that we label each node as a “leaf”, “inner” or “Root” node, such that for the nodes above we get: 

| node | label |
| --- | --- |
| 1      | Leaf |
| 2       | Inner |
| 3      | Inner |
| 4      | Leaf |
| 5      | Root |

```SQL
WITH join_table AS 
(
SELECT 
    a.node a_node,
    a.parent a_parent,
    b.node b_node, 
    b.parent b_parent
 FROM
    tree a 
 LEFT JOIN 
    tree b ON a.parent = b.node 
 )
 
 SELECT 
    a_node node, 
    CASE 
        WHEN b_node IS NULL and b_parent IS NULL THEN 'Root'
        WHEN b_node IS NOT NULL and b_parent IS NOT NULL THEN 'Leaf'        
        ELSE 'Inner' 
    END AS label 
 FROM 
    join_table 
```

---

**Retained Users Per Month** 
*Context:* Say we have login data in the table logins: 

| user_id | date       |
|---------|------------|
| 1       | 2018-07-01 |
| 234     | 2018-07-02 |
| 3       | 2018-07-02 |
| 1       | 2018-07-02 |
| ...     | ...        |
| 234     | 2018-10-04 |

*Task:* Write a query that gets the number of retained users per month. In this case, retention for a given month is defined as the number of users who logged in that month who also logged in the immediately previous month. 

```SQL 
SELECT 
    DATE_TRUNC('month', a.date) month_timestamp, 
    COUNT(DISTINCT a.user_id) retained_users 
 FROM 
    logins a 
 JOIN 
    logins b ON a.user_id = b.user_id 
        AND DATE_TRUNC('month', a.date) = DATE_TRUNC('month', b.date) + 
                                             interval '1 month'
 GROUP BY 
    date_trunc('month', a.date)
```

*Task:* Now we’ll take retention and turn it on its head: Write a query to find many users last month did not come back this month. i.e. the number of churned users.  
```SQL
SELECT 
    DATE_TRUNC('month', a.date) month_timestamp, 
    COUNT(DISTINCT b.user_id) churned_users 
FROM 
    logins a 
FULL OUTER JOIN 
    logins b ON a.user_id = b.user_id 
        AND DATE_TRUNC('month', a.date) = DATE_TRUNC('month', b.date) + 
                                         interval '1 month'
WHERE 
    a.user_id IS NULL 
GROUP BY 
    DATE_TRUNC('month', a.date)
```
*Context*: You now want to see the number of active users this month who have been reactivated — in other words, users who have churned but this month they became active again. Keep in mind a user can reactivate after churning before the previous month. An example of this could be a user active in February (appears in logins), no activity in March and April, but then active again in May (appears in logins), so they count as a reactivated user for May . 

*Task:* Create a table that contains the number of reactivated users per month. 

```SQL
   SELECT 
        DATE_TRUNC('month', a.date) month_timestamp,
        COUNT(DISTINCT a.user_id) reactivated_users,
        /* 
        * At least in the flavors of SQL I have used, you don't need to 
        * include the columns used in HAVING in the SELECT statement.
        * I have written them out for clarity here.  
        */ 
        MAX(DATE_TRUNC('month', b.date)) most_recent_active_previously 
     FROM 
        logins a
     JOIN
        logins b ON a.user_id = b.user_id 
                AND 
                DATE_TRUNC('month', a.date) > DATE_TRUNC('month', b.date)
     GROUP BY 
        DATE_TRUNC('month', a.date)
     HAVING 
        month_timestamp > most_recent_active_previously + interval '1 month' 
```

---

**Cumulative Sums**  
*Acknowledgement:* This problem was inspired by Sisense’s“Cash Flow modeling in SQL” (https://www.sisense.com/blog/cash-flow-modeling-in-sql/) blog post 

*Context:* Say we have a table transactions in the form:

| date       | cash_flow |
|------------|-----------|
| 2018-01-01 | -1000     |
| 2018-01-02 | -100      |
| 2018-01-03 | 50        |
| ...        | ...       |

Where cash_flow is the revenues minus costs for each day. 

*Task:* Write a query to get cumulative cash flow for each day such that we end up with a table in the form below: 

| date       | cumulative_cf |
|------------|---------------|
| 2018-01-01 | -1000         |
| 2018-01-02 | -1100         |
| 2018-01-03 | -1050         |
| ...        | ...           |

```SQL
SELECT 
    date, 
    SUM(cash_flow) OVER (ORDER BY date ASC) as cumulative_cf 
FROM
    transactions 
ORDER BY 
    date ASC
```

---

**Rolling Averages**  
*Context*: Say we have table signups in the form: 

| date       | sign_ups |
|------------|----------|
| 2018-01-01 | 10       |
| 2018-01-02 | 20       |
| 2018-01-03 | 50       |
| ...        | ...      |
| 2018-10-01 | 35       |

*Task*: Write a query to get 7-day rolling (preceding) average of daily sign ups. 

```SQL 
SELECT 
  a.date, 
  AVG(b.sign_ups) average_sign_ups 
FROM 
  signups a 
JOIN 
  signups b ON a.date <= b.date + interval '6 days' AND a.date >= b.date
GROUP BY 
  a.date
```

---

**Multiple Join Conditions**  
*Context:* Say we have a table emails that includes emails sent to and from zach@g.com:

| id | subject  | from         | to           | timestamp           |
|----|----------|--------------|--------------|---------------------|
| 1  | Yosemite | zach@g.com   | thomas@g.com | 2018-01-02 12:45:03 |
| 2  | Big Sur  | sarah@g.com  | thomas@g.com | 2018-01-02 16:30:01 |
| 3  | Yosemite | thomas@g.com | zach@g.com   | 2018-01-02 16:35:04 |
| 4  | Running  | jill@g.com   | zach@g.com   | 2018-01-03 08:12:45 |
| 5  | Yosemite | zach@g.com   | thomas@g.com | 2018-01-03 14:02:01 |
| 6  | Yosemite | thomas@g.com | zach@g.com   | 2018-01-03 15:01:05 |
| .. | ..       | ..           | ..           | ..                  |

*Task:* Write a query to get the response time per email (id) sent to zach@g.com . Do not include ids that did not receive a response from zach@g.com. Assume each email thread has a unique subject. Keep in mind a thread may have multiple responses back-and-forth between zach@g.com and another email address. 
```SQL
SELECT 
    a.id, 
    MIN(b.timestamp) - a.timestamp as time_to_respond 
FROM 
    emails a 
JOIN
    emails b 
        ON 
            b.subject = a.subject 
        AND 
            a.to = b.from
        AND 
            a.from = b.to 
        AND 
            a.timestamp < b.timestamp 
 WHERE 
    a.to = 'zach@g.com' 
 GROUP BY 
    a.id 
```

# Windowing Functions  
*Context:* Say we have a table salaries with data on employee salary and department in the following format: 

  depname  | empno | salary |     
-----------+-------+--------+
 develop   |    11 |   5200 | 
 develop   |     7 |   4200 | 
 develop   |     9 |   4500 | 
 develop   |     8 |   6000 | 
 develop   |    10 |   5200 | 
 personnel |     5 |   3500 | 
 personnel |     2 |   3900 | 
 sales     |     3 |   4800 | 
 sales     |     1 |   5000 | 
 sales     |     4 |   4800 | 

*Task*: Write a query to get the empno with the highest salary. Make sure your solution can handle ties!
```SQL
WITH max_salary AS (
    SELECT 
        MAX(salary) max_salary
    FROM 
        salaries
    )
SELECT 
    s.empno
FROM 
    salaries s
JOIN 
    max_salary ms ON s.salary = ms.max_salary 
```

--- 

*Context*: Say we have a table salaries in the format:

  depname  | empno | salary |     
-----------+-------+--------+
 develop   |    11 |   5200 | 
 develop   |     7 |   4200 | 
 develop   |     9 |   4500 | 
 develop   |     8 |   6000 | 
 develop   |    10 |   5200 | 
 personnel |     5 |   3500 | 
 personnel |     2 |   3900 | 
 sales     |     3 |   4800 | 
 sales     |     1 |   5000 | 
 sales     |     4 |   4800 | 

*Task:* Write a query that returns the same table, but with a new column that has average salary per depname. We would expect a table in the form: 

  depname  | empno | salary | avg_salary |     
-----------+-------+--------+------------+
 develop   |    11 |   5200 |       5020 |
 develop   |     7 |   4200 |       5020 | 
 develop   |     9 |   4500 |       5020 |
 develop   |     8 |   6000 |       5020 | 
 develop   |    10 |   5200 |       5020 | 
 personnel |     5 |   3500 |       3700 |
 personnel |     2 |   3900 |       3700 |
 sales     |     3 |   4800 |       4867 | 
 sales     |     1 |   5000 |       4867 | 
 sales     |     4 |   4800 |       4867 |

```SQL
SELECT 
    *, 
    /*
    * AVG() is a Postgres command, but other SQL flavors like BigQuery use 
    * AVERAGE()
    */ 
    ROUND(AVG(salary),0) OVER (PARTITION BY depname) avg_salary
FROM
    salaries
```

*Task:* Write a query that adds a column with the rank of each employee based on their salary within their department, where the employee with the highest salary gets the rank of 1. We would expect a table in the form: 

  depname  | empno | salary | salary_rank |     
-----------+-------+--------+-------------+
 develop   |    11 |   5200 |           2 |
 develop   |     7 |   4200 |           5 | 
 develop   |     9 |   4500 |           4 |
 develop   |     8 |   6000 |           1 | 
 develop   |    10 |   5200 |           2 | 
 personnel |     5 |   3500 |           2 |
 personnel |     2 |   3900 |           1 |
 sales     |     3 |   4800 |           2 | 
 sales     |     1 |   5000 |           1 | 
 sales     |     4 |   4800 |           2 | 


```SQL
SELECT 
    *, 
    RANK() OVER(PARTITION BY depname ORDER BY salary DESC) salary_rank
 FROM  
    salaries 
```

# Histograms  
*Context:* Say we have a table sessions where each row is a video streaming session with length in seconds: 

| session_id | length_seconds |
|------------|----------------|
| 1          | 23             |
| 2          | 453            |
| 3          | 27             |
| ..         | ..             |

*Task:* Write a query to count the number of sessions that fall into bands of size 5, i.e. for the above snippet, produce something akin to: 

| bucket  | count |
|---------|-------|
| 20-25   | 2     |
| 450-455 | 1     |

```SQL
WITH bin_label AS 
(SELECT 
    session_id, 
    FLOOR(length_seconds/5) as bin_label 
 FROM
    sessions 
 )
 SELECT 
    CONCATENTATE(STR(bin_label*5), '-', STR(bin_label*5+5)) bucket, 
    COUNT(DISTINCT session_id) count 
 GROUP BY 
    bin_label
 ORDER BY 
    bin_label ASC 
```

--- 

*Context:* Say we have a table state_streams where each row is a state and the total number of hours of streaming from a video hosting service: 

| state | total_streams |
|-------|---------------|
| NC    | 34569         |
| SC    | 33999         |
| CA    | 98324         |
| MA    | 19345         |
| ..    | ..            |

(In reality these kinds of aggregate tables would normally have a date column, but we’ll exclude that component in this problem) 

*Task:* Write a query to get the pairs of states with total streaming amounts within 1000 of each other. For the snippet above, we would want to see something like:

| state_a | state_b |
|---------|---------|
| NC      | SC      |
| SC      | NC      |

```SQL
SELECT
    a.state as state_a, 
    b.state as state_b 
 FROM   
    state_streams a
 CROSS JOIN 
    state_streams b 
 WHERE 
    ABS(a.total_streams - b.total_streams) < 1000
    AND 
    a.state <> b.state 
```


### How would you find the top 5 highest-selling items from a list of order histories?
### Can you explain how SQL works?
### Given three columns of data, how would you compare the first three to the last three?
### How do you calculate the median for a given column of numbers in a data set?

# Python
### How to generate a matrix that follows Bernoulli distribution in python
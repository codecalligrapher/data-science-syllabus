### What’s a SQL Running Total?

In SQL, a running total is the cumulative sum of the previous numbers in a column. Look at the example below, which presents the daily registration of users for an online shop:

|  registration\_date | registered\_users | total\_users |
| --- | --- | --- |
| 2020-03-05 | 32 | **32** |
| 2020-03-06 | 15 | **47** |
| 2020-03-07 | 6 | **53** |

The first column shows the date. The second column shows the number of users who registered on that date. The third column, _total\_users_, sums the total number of registered users on that day.

For example, on the first day (2020-03-05), 32 users registered and the total value of registered users was 32. The next day (2020-03-06) 15 users registered; the _total\_users_ value became 47 (32+15). The third day (2020-03-07), six users registered and the _total\_users_ value was 53. In other words, _total\_users_ is a running value that changes from day to day. It is the total number of users on each day.

The next example uses the _total\_running_ column to deal with company revenue in a similar way. Look at the table below:

| date | revenue | total\_revenue |
| --- | --- | --- |
| 2020-04-02 | 125 000 | **125 000** |
| 2020-04-03 | 125 000 | **250 000** |
| 2020-04-04 | 20 500 | **270 500** |
| 2020-04-05 | 101 000 | **371 500** |

For each day, the _total\_revenue_ column is calculating the amount of revenue generated up to the given day. On 2020-04-04, the company achieved a total revenue of $270,500 because that is the sum of all revenues from 2020-04-02 to 2020-04-04.

Relational databases (like [SQL Server](https://www.microsoft.com/en-us/sql-server/ "Microsoft Data Platform | Microsoft"), [Oracle](https://www.oracle.com/database/ "Database - Oracle"), [PostgreSQL](https://www.postgresql.org/ "PostgreSQL: The world's most advanced open source database"), and [MySQL](https://www.mysql.com/ "MySQL")) and even non-relational engines like [Hive](http://hive.apache.org/ "Apache Hive TM") and [Presto](https://prestodb.io/ "Presto | Distributed SQL Query Engine for Big Data") provide window functions that allow us to calculate a running total. Next, we’ll talk about the SQL query that builds such a sum and learn more about window functions.

### How to Compute a Cumulative Sum in SQL

If you would like to compute running total in SQL, you need to be familiar with the window functions provided by your database. Window functions operate on a set of rows and return an aggregate value for each row in the result set. If you are interested in learning more about window functions, try the [Window Functions](https://learnsql.com/course/window-functions/ "Window Functions - SQL online course | LearnSQL.com") course on [LearnSQL.com](https://learnsql.com/ "SQL online courses - learn with us | LearnSQL.com") platform.

The best way to learn about window functions is through practice. I recommend this [Window Functions](https://learnsql.com/course/window-functions?itm_source=lsqlBlog&itm_campaign=_default&itm_medium=text&itm_content=course-window-functions-2) course. It has 218 interactive exercises, which equals about 20 hours of coding.

The syntax of the SQL window function that computes a cumulative sum across rows is:

`window_function (` `column` `)`

`OVER ( [ PARTITION` `BY` `partition_list ] [` `ORDER` `BY` `order_list] )`

It’s mandatory to use the OVER clause in a window function, but the arguments in this clause are optional. We will discuss them in the next paragraphs of this article.

#### Example 1

In this example, we will calculate the total running sum of the registered users each day.

registration\_date

registered\_users

2020-03-05

32

2020-03-06

15

2020-03-07

6

This query ...

`SELECT` `registration_date,registred_users,`

 `SUM``(registred_users) OVER (``ORDER` `BY` `registration_date)`

 `AS` `total_users`

`FROM` `registration;`

… selects the registration date for all users. We also need the sum of all users for each day, starting from the first given day (2020-03-05) to the day in that row.

This is the result set:

registration\_date

registered\_users

total\_users

2020-03-05

57

**57**

2020-03-06

27

**84**

2020-03-07

16

**100**

To calculate the running total, we use the `SUM()` aggregate function and put the column `registered_users` as the argument; we want to obtain the cumulative sum of users from this column.

The next step is to use the OVER clause. In our example, this clause has one argument: `ORDER BY registration_date`. The rows of the result set are sorted according to this column (`registration_date`). For each value in the `registration_date` column, the total sum of the previous column values is computed (i.e. the sum of the number of users before the date in the current row) and the current value (i.e. users registered on the day of the current row) is added to it.

Notice that the total sum is shown in the new column, which we named `total_users`.

In the first step (the registration date 2020-03-05), we have 57 registered users. The sum of users registered this day is the same 57. In the next step, we add to this total value (57). What do we add? The number of users registered on the current date (2020-03-06), which is 27; this gives us a running total of 84. In the last row of the result set (for the last registration date, 2020-03-07) the running total is 100.

Thanks to SQL window functions, it is easy to find the cumulative total number of users during a given period of time. For example, during 2020-03-05 – 2020-03-06, the total number of registered users was 84.

#### Example 2

In the second example, we’ll go into more details about users. We’ll show users with their countries. Look at the table below:

country

registration\_date

registered\_users

England

2020-03-05

25

England

2020-03-06

12

England

2020-03-07

10
Poland

2020-03-05

32

Poland

2020-03-06

15

Poland

2020-03-07

6

Notice that for each day we have the number of users for each country shown separately. In this example, we will compute a separate cumulative sum of registered users for each country.

This query ...

`SELECT` `country, registration_date,registred_users,`

 `SUM``(registred_users)`

 `OVER (PARTITION` `BY` `country` `ORDER` `BY` `registration_date)`

 `AS` `total_users`

`FROM` `registration;`

… calculates the sum of users for each day, first for users from England and then for users from Poland.

Here’s the result set:

country

registration\_date

registered\_users

total\_users

England

2020-03-05

25

25

England

2020-03-06

12

37

England

2020-03-07

10

47

Poland

2020-03-05

32

32

Poland

2020-03-06

15

**47**

Poland

2020-03-07

6

**53**

For each country, each registration day gets a running total. The PARTITION BY clause in the OVER clause has the column _country_ as its argument. This partitions rows by country, allowing SQL to compute a running total for that country only (instead of both countries together). Thus, in England from 2020-03-05 to 2020-03-07, we have a total of 47 users. For the same period in Poland, the total of registered users was 53.

Tired of doing simple SQL exercises? Let's move to a more advanced level! Check out our [Advanced SQL](https://learnsql.com/track/advanced-sql?itm_source=lsqlBlog&itm_campaign=_default&itm_medium=text&itm_content=track-advanced-sql-2) track!

#### Example 3

In the last example, we’ll analyze the data in the `**competition**` table, which stores the columns _game\_id_, _gamer\_id_, _game\_level_, _competition\_date_, and _score_.

game\_id

game\_level

gamer\_id

competition\_date

score

1

3

4

2020-04-02

4

1

2

4

2020-04-03

5

1

1

4

2020-04-04

2

1

3

5

2020-04-02

1

1

2

5

2020-04-03

2

2

3

7

2020-04-07

4

2

2

7

2020-04-08

6

2

1

7

2020-04-07

2

2

3

6

2020-04-08

1

2

2

6

2020-04-09

1

2

3

8

2020-04-07

2

We need to check each gamer’s total cumulative score for each day in two different games. Look at the query below, which creates this running total:

`SELECT` `game_id,game_level,gamer_id,competition_date,score,`

 `SUM``(score)`

 `OVER (PARTITION` `BY` `game_id, gamer_id`

 `ORDER` `BY` `competition_date)`

 `AS` `total_score`

`FROM` `competition;`

The result:

game\_id

game\_level

gamer\_id

competition\_date

score

total\_score

1

3

4

2020-04-02

4

4

1

2

4

2020-04-03

5

9

1

1

4

2020-04-04

2

11

1

3

5

2020-04-02

1

1

1

2

5

2020-04-03

2

3

2

3

6

2020-04-07

1

1

2

2

6

2020-04-08

1

2

2

3

7

2020-04-07

4

4

2

2

7

2020-04-08

6

10

2

1

7

2020-04-09

2

12

2

3

8

2020-04-07

2

2

In this result table, we can read that the gamer with ID=4 starts from a score of 4 and finishes with a total score of 11. The best was the gamer with ID=7, who finished with a total score of 12.

Once again, in the OVER clause we use PARTITION BY. This time, we use a list of columns (`game_id, gamer_id`). This allows us to create two partitions: one for game 1 and one for game 2.

Next, rows were divided by _gamer\_id_ for each game. In game 1, we have the gamers 4 and 5; in game 2, we have the gamers 6, 7, and 8. Among each group (a given gamer plays in a given game), rows are sorted by _competition\_date_ and the score from each day is summed. In each group, we can observe each gamer’s changing score in a given game.
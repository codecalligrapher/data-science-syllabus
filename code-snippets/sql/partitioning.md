# Partitioning 
> Used for splitting parts of tables for management at a finer level of granularity, assists in speed of queries when large parts of the table are queried regularly 


# Advantages  
- Partition pruning and partition-wise joins
- Much faster queries  
- Partition to be updated/backed-up is current only
- Saves space  
- Higher availability  


# Oracle Data Model 
Oracle stores data in fixed number of blocks  
Extents contain multiple data-blocks   
Segments point to multiple segments  
Full table scan is too slow, and indexes work only for small subsets of data (5-10%)

# When to Partition  
- Large tables (greater than 2GB)
- Rolling/historical data, when only most recent files are editable 
- Multi-machine database 
- Maintainenance on part of data without invalidating indexes  
- Index skew reduction

## List Partitioning  
> Partitioned according to dsicrete list   
- Partitions not ordered relative to each other 
- Index created on column that is not part of partition key should be global  

```SQL 
create table table_name (
    field_type field_name,
    ...
) partition by list (field_to_partition_by) (
    PARTITION parition_name
    VALUES ('list', 'of', 'values', 'to', 'match')
    STORAGE (INITIAL 8M) --initial table size 
    TABLESPACE tbs8, --logical storage unit  

    PARTITION region_unknown --account for unknown
        VALUES (DEFAULT)
)
```

## Range Partitioning  
> Groups data via date ranges
```SQL
CREATE TABLE table_name (
    field_type field_name
)
 PARTITION BY RANGE (field_to_partition_by) ( 
     PARTITION partition_name VALUES LESS THAN (TO_DATE('01-APR-2006','dd-MON-yyyy'))
    TABLESPACE tsa
```

## Hash Partitioning 
> Aim to divide data equally across partitions  
- Not ideal for historical data  
-
```SQL
CREATE TABLE scubagear
     (id NUMBER,
      name VARCHAR2 (60))
   PARTITION BY HASH (id)
   PARTITIONS 4 
   STORE IN (gear1, gear2, gear3, gear4);
```


# Specific Examples
## List Partitioning
```SQL
CREATE TABLE sales_by_region (item# INTEGER, qty INTEGER, 
             store_name VARCHAR(30), state_code VARCHAR(2),
             sale_date DATE)
     STORAGE(INITIAL 10K NEXT 20K) TABLESPACE tbs5 
     PARTITION BY LIST (state_code) 
     (
     PARTITION region_east
        VALUES ('MA','NY','CT','NH','ME','MD','VA','PA','NJ')
        STORAGE (INITIAL 8M) 
        TABLESPACE tbs8,
     PARTITION region_west
        VALUES ('CA','AZ','NM','OR','WA','UT','NV','CO')
        NOLOGGING,
     PARTITION region_south
        VALUES ('TX','KY','TN','LA','MS','AR','AL','GA'),
     PARTITION region_central 
        VALUES ('OH','ND','SD','MO','IL','MI','IA'),
     PARTITION region_null
        VALUES (NULL),
     PARTITION region_unknown
        VALUES (DEFAULT)
     );create table table_name (
```

## Range Partitioning 
```SQL 
CREATE TABLE sales
  ( prod_id       NUMBER(6)
  , cust_id       NUMBER
  , time_id       DATE
  , channel_id    CHAR(1)
  , promo_id      NUMBER(6)
  , quantity_sold NUMBER(3)
  , amount_sold   NUMBER(10,2)
  )
 PARTITION BY RANGE (time_id)
 ( PARTITION sales_q1_2006 VALUES LESS THAN (TO_DATE('01-APR-2006','dd-MON-yyyy'))
    TABLESPACE tsa
 , PARTITION sales_q2_2006 VALUES LESS THAN (TO_DATE('01-JUL-2006','dd-MON-yyyy'))
    TABLESPACE tsb
 , PARTITION sales_q3_2006 VALUES LESS THAN (TO_DATE('01-OCT-2006','dd-MON-yyyy'))
    TABLESPACE tsc
 , PARTITION sales_q4_2006 VALUES LESS THAN (TO_DATE('01-JAN-2007','dd-MON-yyyy'))
    TABLESPACE tsd
 );
```
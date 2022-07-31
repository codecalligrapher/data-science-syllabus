# Constraints  
This is an optional part of a ```SQL CREATE`` or ```SQL ALTER``` statement, it enforces a rule to which data must conform  
## Column Constraints  
**NOT NULL**   
Specifies that this column cannot hold NULL values (constraints of this type are not nameable).  
**PRIMARY KEY**  
Specifies the column that uniquely identifies a row in the table. The identified columns must be defined as NOT NULL.  
**UNIQUE**  
Specifies that values in the column must be unique.  
**FOREIGN KEY**  
Specifies that the values in the column must correspond to values in a referenced primary key or unique key column or that they are NULL.  
**CHECK**  
Specifies rules for values in the column.


## Table Constraints  
**PRIMARY KEY**  
Specifies the column or columns that uniquely identify a row in the table. NULL values are not allowed.  

**UNIQUE**  
Specifies that values in the columns must be unique.

**FOREIGN KEY**  
Specifies that the values in the columns must correspond to values in referenced primary key or unique columns or that they are NULL.  

Note: If the foreign key consists of multiple columns, and any column is NULL, the whole key is considered NULL. The insert is permitted no matter what is on the non-null columns.  

**CHECK**  
Specifies a wide range of rules for values in the table.  


# Cursors  
Pointer than points to the result of a query  
```SQL
CURSOR cursor_name IS query
```  

**OPEN**  
Cursors must be opened before rows are fetched from the cursor  
```SQL 
OPEN cursor_name  
```  

**FETCH**  
Places the contents of the current row into variables   
```SQL 
FETCH cursor_name INTO variable_list
```  

**CLOSE**  
After fetching rows, cursor must be closed, which releases all allocated memory 
```SQL  
CLOSE cursor_name  
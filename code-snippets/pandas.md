import pandas as pd 

### Read a CSV  
```Python
df = pd.read_csv('path/to/csv', sep=',')
```
- Specify separator as TAB `\t`, COMMA `,`, etc 


### Export as a Numpy Array
```Python
df.values
```

### Subsetting Rows
#### By RAW Value
```Python
df.loc[VALUE, COLS]
```

#### By Index
Starts counting from zero from the top, returns the `IDX`th row  
```Python
df.iloc[INTEGER_IDX]
```

#### Multiple Rows
```Python
df.loc[START:END]
```

#### Multiple Rows and Subset Columns
```Python
df.loc[START:END, [COLS]]
```

#### Boolean Subset
```Python
# single
df.loc[df['COL_NAME'] == CONDITION] 

# multiple
df.loc[(df['COL1'] == CONDITION_1 & df['COL_2'] < CONDITION_2), :]
111
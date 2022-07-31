# Key Terms
**Log**  
Append-only file, most basic form of storage   
<div style="color: green">Writes are fast</div>  
<div style="color: red">Reads are slow</div>

# Index  
*Additional metadata which assists in finding required data*   
Any indexing procedure must account for **deletion, crash-recovery, partial writes** and **concurrency**  

| Hash Index | SSTables/LSMTrees | B-Trees |  
| --- | --- | --- |  
|key-value pairs <div style="color:green"> <br> near constant-time lookup</div> <div style="color:red"><br> Must be kept in memory <br> cannot easily generate range queries</div> | Sorts hash tables by key <br> Updating procedure similar to merge in merge sort<div style="color:green"> <br> Finding records faster $\log(n)$ </div> <br> <div style="color:red">Slow to find non-existent items <br> Compaction may interfere with writes as disk bandwidth need be shared between initial write and compaction </div> | Key-value pairs sorted by key <br> Number of child references known as branching factor <div style="color:green"><br> Keys exist in only one place <br> Faster than LSMTrees for reads</div> <div style="color:red"><br> Fragmentation results in wasted disk space <br>High write-amplification</div>|
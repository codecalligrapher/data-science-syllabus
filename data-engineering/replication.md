# Key Terms  
**Replica**  
A node which stores a copy of a database  

# Leader-Based Replication  
## Single-Leader
One replica receives all write requests, initiates changes in followers by sending a replication log  
A new follower updates itself bby taking a snapshot of the leader, and then requests data changes since the snapshot  

### Handling Failure
#### Leader  
A *failover* where one follower is promoted to the leader and all writes are redirected to this new leader  
The most up-to-date replica can be chosen as the new leader  

#### Follower  
Follower log is compared to the leader to update when restarted  

### Replication Logs  
**Statement based**  
Issues with NOW() and other nondeterministic functions if SQL queries are copied as is


**Row-based**  
Logical log decoupled from storage engine internals, and changes to rows/columns kept, enough information to uniquely idenetify updated, deleted, new rows**Statement

### Handling Lag  
*When followers are not up-to-date with the leader*  
**Monotonic Reads**  
If several reads from different replicas are made  
User prevented from going backwards in time (to out-of-date nodes) having made writes  

**Consistent Prefix**  
If series of writes happen in some order, reader guaranteed to read in that order, by writing casually related writes to the same ppartition

## Multi-Leader Replication  
May be useful for multi-datacenter applications  
Conflicts may occur if multiple leaders update at different times  

### Handling Write Conflicts 
**Resolving Conflicts**

1. Each write a unique ID, where most recent alone is accepted 
2. Each replica a unique ID, with predefined list of which can outvote which
3. Merge conflicts 
4. Record conflict and prompt user to fix it: can be on write or on read

# Leaderless Replication  
- Subset of replicas required to acknowledge writes meaning it does not require considerations for failure
- Read requests are also sent to multiple nodes to combat stale reads
- Falling behind significantly should generate alerts, and there is no one value to determine how stale a replica is

### Handling Incosistencies  
#### Read Repair

When client detects stale values in a replica, the stale replica updates its values. Works well for frequent reads  

#### Anti-Entropy
Background-process constantly looking for data differences, this may be significantly delayed  
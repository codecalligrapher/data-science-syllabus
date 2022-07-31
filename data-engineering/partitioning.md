*Much of this section's theory is taken from Designing Data-Intensive Applications by Martin Kleppmann, and assumes basic knowledge of certain key terms*  
# Partitioning on Primary Indexes
Necessary when size of data exceeds that which can be handled by a single physical machine, by spreading data and query load evenly across multiple machine whilst avoiding *hot-spots*
Each node can be a leader for some partitions, and a follower for others  

**Skewed** partitioning unfairly distributes data/queries across partitions  
A **hot-spot**  is a node with disproportionally high data/query load

## Key-Range Partitioning
Random assignment to partitions (in theory) may avoid hot-spots, but reads have no way of finding items  
Assumed key-value relational structure, where data are split by keys
Partition boundaries may need to adapt to data

<p style="color:red">Certain access patterns can lead to hotspots</p>   

*e.g. sensors which update a database may all access the same timestamp simultaneously, this can be worked-around by including a writer-ID in the key*  


## Hash Partitioning
A good has functoin takes skewed data and makes it uniformly distributed  
<p style="color:red">Hashes make efficient range-queries infeasible</p>

# Secondary Indexes
A secondary index doesn't uniquely identify a document, but provides a way of searching for occurences of a particular value, however they don't map neatly to partitions
## Document Based
An index is stored per-partition containing the occurences of documents containing the index's term
Also known as *scatter-gather*, as a read is sent to all partitions, partitions with terms matching read query responds 
<p style="color:red">Read queries on secondary indexes expensive</p>
<p style="color:red">Prone to tail-latency amplification</p>

## Term Based
A global index covers data in all partitions, the term being queries determines the partition of the index
Reads are more efficient, as clients need only query partitions containing the term it wants
<p style="color:red">Writes are slower, since a single document now affects multiple partition partitions of an index</p>

# Rebalancing  
- After rebalancing, the load (data storage, read and write requests) should be shared fairly between the nodes in the cluster.
- While rebalancing is happening, the database should continue accepting reads and writes
- No more data than necessary should be moved between nodes, to make rebalancing fast and to minimize the network and disk I/O load.

*The problem with the mod N approach is that if the number of nodes N changes, most of the keys will need to be moved from one node to another*

## Fixed Numbers of Partitions  
Number of partitions per node greatly exceeds initial need, and as nodes are added or removed, entire partitions scaled across  
<p style="color:red">Large partitions make rebalancing and recovery from failure expensive</p>
<p style="color:red">Small partitions incur too much overhead</p>

## Partitioning Proportionall to Nodes  
Fixed number of partitions *per node*  
Size of a partition grows with dataset sisze, but increasing the number of nodes results in partition size decrease  
A new node randomly chooses a fixed number of existing partitions to split, and takes ownership of half of each partition.

# Request Routing
How to determine which partition to read or write to? 
A current challenge is dealing with updating indexes, or how do clients learn about changes to partitions, etc

Three main approaches:
## Round Robin  
All clients can contact any node via a load-balancer, if the accessed node does not have the requested data, the node forwards the request to the appropriate node (as indexes are stored on nodes)
## Routing Tier Service
Send all requests from clients to a routing tier first, which determines the node that should handle each request and forwards it accordingly. This routing tier does not itself handle any requests; it only acts as a partition-aware load balancer
## Client-Side Partition Awareness
Every client is aware of partitioning and assignment of partitions 

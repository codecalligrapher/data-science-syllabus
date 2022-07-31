- [Hash Tables](#hash-tables)
  - [Supported Operations](#supported-operations)
    - [Hash Functions](#hash-functions)
      - [For Primitive Data Types](#for-primitive-data-types)
      - [For Compound Objects](#for-compound-objects)
      - [For Strings](#for-strings)
    - [Collision Resolution](#collision-resolution)
      - [Separate Chaining](#separate-chaining)
      - [Open Addressing](#open-addressing)
  - [<div style="color:#0A0">Advantages</div>](#div-stylecolor0a0advantagesdiv)
  - [<div style="color:#A00">Disadvantages</div>](#div-stylecolora00disadvantagesdiv)
- [Binary Trees](#binary-trees)
- [B-Trees](#b-trees)
  - [How It Works](#how-it-works)
  - [Supported Operations](#supported-operations-1)
  - [<div style="color:#0A0">Advantages</div>](#div-stylecolor0a0advantagesdiv-1)
  - [<div style="color:#A00">Disadvantages</div>](#div-stylecolora00disadvantagesdiv-1)
- [Bloom Filters](#bloom-filters)
  - [How it Works](#how-it-works-1)
  - [<div style="color:#0A0">Advantages</div>](#div-stylecolor0a0advantagesdiv-2)
  - [<div style="color:#A00">Disadvantages</div>](#div-stylecolora00disadvantagesdiv-2)
  - [Supported Operations](#supported-operations-2)
- [Linked List](#linked-list)
# Hash Tables  
Keeps track of evolving set of objects indexed via keys

## Supported Operations  

**Lookup**(a.k.a. Search): for a key k, return a pointer to an object in the hash table with key k (or report that no such object exists)  
**Insert**: given a new object x, add x to the hash table.  
**Delete**: for a key k, delete an object with key k from the hash table, if one exists.

### Hash Functions  
*Defines how keys are mapped to positions in an array*  
A good hash function must be:
- cheap to evaluate, ideally in constant time
- easy to store, ideally with constant memory
- some random functoin spreading out non-pathological data sets roughly evenly across positions. 

#### For Primitive Data Types  
*char, byte, int, float*  
Treat the bits as representation of an integer  

#### For Compound Objects 
Combines each individual hash codes of the constituent parts.  

#### For Strings  
Based on a polynomial over a prime field (evaluated modulo against some prime number *p*)

### Collision Resolution
#### Separate Chaining 
Stores a linked-list for multiple objects hashed to the same position (index). Lookup times degrade if the hash table becomes heavily populated or if the hash function results in too many collisions.
#### Open Addressing
Easier to implement than chaining (except in the $DELETE$ operation's case). Each position stores a $0$ or $1$. Each key is associated with a probe-sequence of positions (first, second, third, etc..) to suggest new positions when collisions occur. 

**Linear Probing**: new position in probe sequence is constant from last tried position.  
**Double Hashing**: two hash functions, first gives normal index position, second indicates offset.


## <div style="color:#0A0">Advantages</div> 
- Constant-time *lookups* (searches), insert and delete

## <div style="color:#A00">Disadvantages</div> 
- Cannot perform range-queries  
- Must be kept in memory

---

# Binary Trees  

---

# B-Trees
## How It Works
Extends concept of binary tree, designed to work with out-of-memory data
- Every node has $n$ keys stored in non-decreasing order  
- Node has a flag indicating whether is a leaf or not  
- Node contains $n+1$ pointers to $i=n+1$ children  
- Keys separate ranges of keys stored in each subtree  
- Every leaf has the same depth (tree-height)  
- Every node other than the root has at least $t-1$ keys (and therfore $t$ children), and at most $2t-1$ keys
- Nodes are typically matched to a magnetic disk's page size, as this is the unit of data read from and written to in everyday operations  


## Supported Operations  
**Insert**  
Position for new value is found in a node by linear search, if no children exist, value is inserted. If children exist, cannot simply insert a new leaf, as this violates the B-tree requirement. Start from root, and split every full node by its median on the way down, until required position is found. 

**Find** 
Linear search of a node, followed by reading the respective child into disk, and followed by recursive search-the-load until the key is found (or not) 
**Delete**  

## <div style="color:#0A0">Advantages</div> 
- Much lower height that typical binary or Red-Black tree  
- Handles out-of-memory data  
- Worst-case read time is $O(\log_t(n))$

## <div style="color:#A00">Disadvantages</div> 
- Increased complexity of reads and writes  
- Leaf and non-leaf nodes are of different sizes (complicating paging)

---

# Bloom Filters 
If your application requires fast lookups with a dynamically changing set of objects, space is at a premium, and a small number of false positives can be tolerated, the bloom filter is usually the data structure of choice

## How it Works  
$n$-bit string stores $1$s or $0$s. Multiple *different* hash functions set these bits to 1 when an item is inserted.

## <div style="color:#0A0">Advantages</div> 
- More space efficient than hash table 
- Guaranteed constant time operation regardless of data


## <div style="color:#A00">Disadvantages</div> 
- Deletions are complicated  
- False positives
- Cannot store actual pointer to object  


## Supported Operations  

**Lookup**(a.k.a. Search):  for a key k, return “yes” if k has been previously inserted into the bloom filter and “no” otherwise
**Insert**: add a new key $k% to the bloom filter 

# Linked List  

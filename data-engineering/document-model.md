# Relational Model  
- *SQL* based on fixed schemas
- Schema is **explicit** and pre-defined  
- Data organized into relations called *tables* where each relation is unorderded collection of *tuples*  
- May require mapping of object-oriented application concpepts by specialized software to translate to relational
- Handles both many-to-many and one-to-many relationships
 
# Document Model  
- Support for specialized queryies unsupported by traditional SQL  
- Schema is inferred by application code (**implicit** schema), advantageous for very different document types  
- More dynamic and expressive (less restrictive) than traditional fixed-type schemas    
- Better *locality*, fetching a single document is exactly that, whilst all data for a single "document" may require multiple joins across multiple tables in the relational model  
- If the database does not support *joins*, this may be jerry-rigged (not ever a good thing) in application code  
- Works better for one-to-many relationships  
- Cannot refer directly to a nested item within a document

# Open Challenges 
- Researchers working with genome data often need to perform sequence-similarity searches, which means taking one very long string (representing DNA molecule) and matching it against a large database of strings that are similar, but not identical. None of the databases described here can handle this kind of usage, which is why researchers have written specialized genome database software like GenBank 
- Particle physicists have been doing Big Data–style large-scale data analysis for decades, and projects like the Large Hadron Collider (LHC) now work with hundreds of petabytes! At such a scale custom solutions are required to stop the hardware cost from spiraling out of control 
- Full-text search is arguably a kind of data model that is frequently used alongside databases. Information retrieval is a large specialist subject that we won’t cover in great detail in this book, but we’ll touch on search indexes in Chapter 3 and Part III

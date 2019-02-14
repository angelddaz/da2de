Chapter 3. Storage and Retrieval

Fundamentally a database should be able to store data when you hand it some and retrieve it when you ask for some.

Data Structures That Power Your Database

    In order to efficiently find the value for a particular key in the database, we need an index

    an index is an additional structure that is derived from the primary data. 
    
    Any kind of index slows down writes because the index  also needs to be updated every time data is written.

    Which tables to add Indexes are chosen manually

    Log compaction means we throw away duplicate keys in the log and keep only hte most recent update for each key

    LSM trees faster for writes
    B-trees faster for reads

I understand OLTP, OLAP, and Data Warehouses so not many notes here

Summary

    storage engines fall into two broad categories OLTP and OLAP
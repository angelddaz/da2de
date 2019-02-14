# and here we start. Notes on the preface and chapter 1
Preface:
"Behind the rapid changes in technology, htere are enduring principles that remain true."

Part 1. Foundations of Data Systems
Chapter 1. Reliable, Scalable, and Maintanable Applications

Vocab:
    Databases store data so that users, or another application can find it again later.
    Caches are the result of an expensive operation, to speed up reads.
    Search indexes allow users to search data by keword or filter it in various ways
    Stream processing sends a message to another process to be handled asynchronously
    Batch Processing periodically crunches a large amount of accumulated data

Redis is a datastore that is also used as a message queue.
Apache Kafka is a message queue with database like durability guarantees.

The boundaries between data categories are blurred.


Relability
    Design systems in a way that minimizes opportunities for error.    
    Decouple the places where people make mistakes from the places where they can cause failures
    Set up detailed and clear monitoring: performance metrics and error rates.

Scalability
    Describes a system's ability to cope with increased load
    Define load parameters: requests per second to a web server, ratio of reads to writes in a database, the numbre of simultaneously active users in a chat room, hit rate on a cache
    Use percentiles, not averages, to analyze load parameters
    A system is elastic if they can automatically add ocmputing resources when they detect a load increase
    An architecture should be bulit around assumptions which operations are common and which are rare. The load parameters.

Maintainability
    Provide good visibility of runtimes
    Avoid dependency on individual machines
    Provide good documentation
    Provide good default behavior and flexibliity to override defaults when needed
    Simplicity Simplicity Simplicity Simplicity Simplicity Simplicity Simplicity 
    
Chapter 2. Data Models and Query Languages

Data Modeling is what applications are built on top of.
Data Models have layers often. Each layers reduces the complexity of the one below it by providing a more clean data model.

In this chapter we'll review:
    
    Relational model
    Document model
    and a few graph-based data models

We will also look at various query languages and compare their use cases.

Relational vs Document Models
    
    Relational databases are mostly for transactoin processing.
    
    The birth of NoSQL: greater scalability than relatoinal. When you hav ea greater need for write throughput. Specialized query operations that are not well supported by the relational model. More dynamic and expressive data model than relational, which can be restrictive.
    
    In document models, joins are not needed for one-to-many tree structures. Support for joins is often weak

The Network model

    The Conference on Data Systems Languages (CODASYL) model was a generalization on the hierarchical model. Every record could have multiple parents.

    A query in CODASYL is performed by a moving cursor through the database which follows access paths. 
    This seems very not relevant today

The main arguments for Document models is flexible schema, closer to the data structure used by some applications.
    
    Schema is not enforced. arbitrary keys and values can be added to a document. Schema-on-read means that the data structure is implicit and only interpreted when the data is read.

Main args for Relational models are support for joins. lol.
    
    Schema on write, ensures that the schema is explicit and that all written data conforms to it

MapReduce

    supported by some NoSQL datastores, including MongoDB and CouchDB as a mechanism for performing read-only queries across many documents.

    Neither a declarative query language nor a fully imperative query API. Somehwere in between. THe logic of the query is expressed with snippets of code, which are called repeatedly by the processing framework.

    Map AKA collect

    Reduce AKA fold AKA inject

    psql:

        select date_trunc('month', observation_timestamp) AS observation_month
            , sum(num_anbimals) AS total_animals
        from observations
        where family = 'sharks'
        group by observation_month
    
    MapReduce:

        db.observations.mapReduce (
            function map() {
                var year = this.observationTimestamp.getFullYear()'

                var month = this.observationTimestamp.getMonth() + 1;
                    emit(year + "-" + month, this.numAnimals);
            },
            function reduce(key, values) {
                return Array.sum(values);
            },
            {
                query: { family: "Sharks" },
                out: "monthlySharkReport"
            }
        );
    
    Usability problem with MapReduce is that you have to write two carfully coordinated JavaScript functions rather than one query in SQL.

Graph-Like Data Models

    A property graph model has entities related to others as properties of those related entities.
    For example: Country entity is related to the Continent entity as being within it.

Summary

    Document, relational, and graph models are all used today.
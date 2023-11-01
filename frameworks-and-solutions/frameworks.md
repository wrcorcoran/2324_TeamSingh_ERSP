# Frameworks

### Key Questions:
1. What frameworks exists?
2. What are they missing?
3. Can they be modified?
<br></br>
----

### Frameworks:
#### [ArangoDB](https://arangodb.com/)
- 'Ad Hoc' queries meaning it can adapt to queries on the fly.
- ArangoDB provides support for all DB features (rather than just graphs like Neo4j).
- AQL is an all-inclusive query language (includes keys/values, documents, and graphs). AQL is more syntactically similar to python / js than Cypher, but it's a query language, so it shouldn't matter too much, as it's stricly used for querying.
- ArangoDB offers a graph visualizer for the database.
- From there, ArangoDB is your standard 'graph' database.
- **Downsides:** ArangoDB isn't strictly focused on graphs. The support may be limited as they are spread across different styles of DBs, however, it seems to be pretty well documented, so that shouldn't be too much of an issue.

#### [Neo4j](https://neo4j.com/)
- All data is stored in a graph (typical for a graph database). Obviously, this speeds up retrieval time compared to index-based search.
- "Fast" K-hop querying (no exact complexity given).
- API across languages (no C / C++ / Java, but that's okay - can write our own access across languages).
- Neo4j claims to outperform in recommendations (compared to ArangoDB).
- **Cypher:** in-house query language. Syntax is incredibly similar to SQL, won't be much of a syntactical adjustment. **However,** Cypher offers pattern matching (certain relations between nodes, hops, etc.). Plenty of different traversal styles, as well. Capabilities to parse a CSV.
- Cypher is **strictly** a graph-query language.
- **Downside:** Neo4j is single modal. Also, doesn't allow you to store anything outside of basic types (would have to go to other DBs to store auxiliary data, which can slow retrieval).
- The 'practices' are typical of a DB pltform - not necessarily important to our project.

### Comparison:
![comparison](https://arangodb.com/wp-content/uploads/2023/09/UPDATE-Benchmark-2018-1.webp)
ArangoDB outperforms in all categories (with exception to shortest path).

### Modifications
Both of these frameworks have public GitHub repositories. This means we can fork to help us, however, we see fit. I have a feeling this will not be necessary, as both of these frameworks are pretty powerful databases.

### What's missing?
As far as I can tell, both of these frameworks are robust from the perspective of GraphDBs. Obviously, they have no interaction with GNNs and their querying. But as far as querying a graph, they are very strong.
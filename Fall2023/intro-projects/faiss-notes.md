# FAISS Notes
Notes on the following YouTube playlist by James Briggs: [Vector Similarity Search and Faiss Course](https://www.youtube.com/playlist?list=PLIUOU7oqGTLhlWpTz4NnuT3FekouIVlqc), which breaks down the Vector Similarity Search Tool, FAISS.
Only a couple of the videos were relevant, as he focuses quite a bit on language syntax.

### Faiss - Introduction to Similarity Search
*IndexFlatL2* - vectors are not modified in any way. $L2$ distance calculation is used.

Gives the opportunity to train or cluster data. IndexFlatL2 doesn't require training.

Voronoi cells partition the vectors into smaller groups, each with a single centroid. Searching checks against each centroid, and then search is limited to the single partition. This is an approximate search, not necessarily a guaranteed correct search.

*IndexIVFFlat* - clusters the data into voronoi cells and requires training. Sometimes gives different results than IndexFlatL2. Using $nprobe$ expands to search size.

### Choosing Indexes for Similarity Search (Faiss in Python)
#### Flat
Flat indexes focuses on search quality over search speed. This makes them not always reasonable. 

#### Locality Sensitive Hashing (LSH)
Higher nbits: higher recall, however, there is a 'curse of dimensionality'

#### Hierarchical Navigable Small World (HNSW)
Can have a very large graphs, but number of hops is small (connect between graph)
HNSW is the best method, in general, with proper tuning of parameters.


### Questions
How are we accessing the matrix while it is in the GNN? Like how do we get the representation of the latent space in order to do the querying?
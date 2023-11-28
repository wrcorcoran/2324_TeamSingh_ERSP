# Notes on CorGIE and the Cora Dataset

<!-- corgie:
- missing the ability to scale 
- and query over nodes

tasks:
- build off of corgie
    - play around with it
- load the graph data and embeddings in corgie
    - come up with a case study for the datasets

    - write a corresponding query for each failure
    - copy workflow into SQL query
    - how would you do corgie if it was an SQL like language?
        - translate any problem you see into query language steps
    - send a few datasets!

- add the usefulness of a proposed questions that can help
    - danish will send questions

- analysis of graph data -->

### General CorGIE Notes
Weirdly, it only has $2-hop$ capability, which is extremely limiting.

From my understanding, the 'global topology' is the graph, which was passed in. The latent space map is how the items have been clustered. Initially, I was a bit confused, but this seems to make sense.

The latent neighbor blocks is interesting. It's vital to see the density of neighbors within certain partitions of the GNN. From what I grasped about FAISS, there's a way to partition the latent space into blocks which can help speed up efficiency.

It is really interesting how the nodes with the most similar feature vectors get grouped. I mean, it does make sense as that is the point of the GNN. 

Extremely slow, even once it gets into the realm of $1000$ nodes. 

### Cora Notes

It's interesting, because it's just a bit-vector of size 1433 to track the node features. We see that there are some features which have almost no nodes. Meanwhile, there are some features, like feature 1177 which has 1083 nodes! There's $2708$ nodes!

Cora is kind of the perfect dataset to get introduced to this area. The feature vector is relatively similar, it's just a $1$ or $0$ whether or not a word exists in the paper. Based on these words, the papers are each classified into seven different classes. The GNN model can be built to classify papers into these seven classes.

### Case Study:
What nodes have feature \#1177 and what are the 5 nearest neighbors for each?

Currently, CorGIE can get all of the nodes which have feature 1177. It'll also show all nodes which are within $2$ hops and the number of edges. Along with this, it shows the latent neighbor blocks and the distance 

What would be an example query of this?

- Search Graph G for Nodes which have a $1$ at feature 1177, store those that do in a list
- Iterate over the list and get the $5$ nearest neighbors for each

How could this appear in SQL?

```
SELECT * FROM G
    where feature[1077] == 1
    and
    FIND 5 NEAREST 
```

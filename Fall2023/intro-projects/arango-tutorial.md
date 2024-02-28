# Here is a link to a [colab](https://colab.research.google.com/github/joerg84/Graph_Powered_ML_Workshop/blob/master/Graphs_Queries.ipynb).

It focuses on basic graph querying with ArangoDB. 

---

This is actually incredible straightforward.

For example, adding edges to the graph was as simple as "graphName.link('type', v1, v2, information about edge).

However, what is interesting is you write the query in plain text (i.e. in AQL). You pass this AQL query to ```db.AQLQuery(...)```

---

This is actually a pretty solid way of implementing a query language. Provides a pretty good illustration of a way we could do it. Rather than going through the headache of creating a language from scratch we could take it as a string through and API call, and have it work just the same.

Here is an example from the Colab:
``` Python
reachabilty_query = """WITH Cities
FOR vertex, edge, path
  IN 1..5 
  OUTBOUND 'Cities/London'
  GRAPH 'RailNetwork'
  FILTER SUM(path.edges[*].travel_time) < 5
  return 
  { 'city': vertex._key,
    'path': CONCAT_SEPARATOR(" -> ", path.edges[*]._to)
  }"""
```
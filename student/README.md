# Data: `trace.csv`

A single random walk on a hidden graph.

## The process

- The graph is **undirected**, **connected**, and **unweighted**, with no self-loops and no multiple edges.
- Nodes are labelled by integers. The labels carry no meaning.
- The walk starts at some node. At each step it moves to a neighbour of the current node, chosen **uniformly at random**.
- The walk never stays in place.

## The format

A CSV file with a header row and one row per visited node, in order:

```
step,node
0,17
1,4
2,23
...
```

| column | meaning                                             |
|--------|-----------------------------------------------------|
| `step` | time index, starting at 0, consecutive              |
| `node` | integer label of the node occupied at that step     |

Consecutive rows `(t, a)` and `(t+1, b)` mean the walk traversed the edge `{a, b}`.
The file has 20,001 rows, which is 20,000 transitions.

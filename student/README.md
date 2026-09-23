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

# Mock quiz: `trace-flawed.csv`

A practice trace. **It is not submitted and not graded.**
Use it to rehearse the tasks in [QUIZ.md](QUIZ.md) before the real quiz.

- It comes from a **different** hidden graph, built the same way as the quiz graph.
  Answers from one trace do not carry over to the other.
- It has the same format as `trace.csv` and 19,999 rows.
- **It contains a few recording errors.**
  The walk itself followed the rules above, but the recorded file does not always match it.
  The `step` column was renumbered after recording, so it does not reveal where the errors are.

Your job is to find the errors, decide how to handle them, and say in your report what you found and how.
**If you trust every row, you will get the graph wrong.**

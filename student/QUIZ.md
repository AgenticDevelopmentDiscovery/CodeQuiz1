# Code Quiz: Random Walk on a Hidden Graph

**Time:** 30 minutes. **Points:** 100.

**Tools:** any coding agent, any language and libraries.

Work *with* your agent.
You are graded on what you submit **and** on whether you checked what the agent produced.

## The data

`trace.csv` records one random walk on a hidden graph.
[README.md](README.md) explains the process and the file format. Read it first.

## Definitions

Let $\pi$ be the stationary distribution of the walk.

Let $\hat\pi_t(v)$ be the fraction of the first $t$ rows of the trace, steps $0, \dots, t-1$, that are at node $v$.

The distance between them is the total variation distance

$$
\mathrm{TV}(t) = \tfrac12 \sum_v \bigl|\hat\pi_t(v) - \pi(v)\bigr| .
$$

## Tasks

### 1. What does the graph look like? (30 pts)

a. Reconstruct the graph and write it to `submission/edges.csv`, with header `u,v` and one undirected edge per row.

b. Describe its structure in `submission/structure.json`:

```json
{
  "n_nodes": 0,
  "n_edges": 0,
  "bridges": [[0, 0]],
  "communities": [[0, 0, 0], [0, 0, 0]]
}
```

- `bridges`: every edge whose removal disconnects the graph.
- `communities`: split all nodes into the **two** densely connected groups. Each node belongs to exactly one group.

c. In the report, explain **how you know your edge list is complete**.

### 2. How fast does the empirical distribution converge? (35 pts)

Model the **expected** distance as

$$
\mathbb{E}[\mathrm{TV}(t)] \approx C\, t^{\alpha}, \qquad 1\,000 \le t \le 20\,000 ,
$$

where the expectation is over walks of this length on this graph, started at the trace's first node.

a. Estimate $\alpha$ and $C$. Write them to `submission/rate.json` as `{"alpha": ..., "C": ...}`.

b. In the report, explain your method, its uncertainty, and what property of the graph controls $C$.

### 3. Visualize (20 pts)

a. `submission/graph.png`:
- the reconstructed graph;
- node size proportional to visit count;
- the two communities and the bridges visually distinguishable.

b. `submission/convergence.png`:
- $\mathrm{TV}(t)$ for the trace, on log-log axes;
- your model $C t^\alpha$;
- a $t^{-1/2}$ reference line;
- a band showing the spread you would expect across walks.

### 4. Report and process (15 pts)

Write `submission/REPORT.md` in 15 lines or fewer. It must contain these sections:

- **Answers:** a one-line summary for each task.
- **Verification:** at least one thing you checked independently of the agent, and how.
- **Agent errors:** something the agent got wrong or overclaimed, and how you caught it. If you think it made no errors, say how you would know.
- **Reproduce:** one command that regenerates every file in `submission/`.
- **AI use:** which agent and model you used, and roughly what you delegated.

## Submission layout

```
submission/
  edges.csv
  structure.json
  rate.json
  graph.png
  convergence.png
  REPORT.md
  <your code>
```

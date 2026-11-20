# Kosaraju's Algorithm: Adjacency List vs Adjacency Matrix

Discrete Mathematics project (KSE). I implemented Kosaraju's algorithm for finding strongly connected components (SCCs) in a directed graph on two graph representations and benchmarked them against each other. The full report is in `pdf/DM_project_Ambrozyak_Zahar.pdf`.

![Graph with coloured strongly connected components](images/graph_scc.png)

## What's inside

- **Graph classes** (`graph.py`): adjacency list and adjacency matrix, random graph generation, graph reversal
- **Kosaraju's algorithm** (`algorithms.py`): two DFS passes, one implementation per representation
- **Experiments** (`experiments.py`): graphs of 20–200 vertices at edge densities 0.1–0.9, 1,000 runs per configuration, results saved to Excel and plotted
- **Visualization** (`graph_visuals.py`): draws a graph with each SCC in its own colour

## Results

Average run time at 200 vertices (`data/kosaraju_results.xlsx`):

| Edge density | Adjacency list | Adjacency matrix |
| --- | --- | --- |
| 0.1 | 0.25 ms | 1.77 ms |
| 0.5 | 0.77 ms | 2.45 ms |
| 0.9 | 1.24 ms | 2.53 ms |

The list was faster in every configuration: about 7× on sparse graphs and about 2× on dense ones. That matches the theory: the list version runs in O(V + E), while the matrix version always scans O(V²) cells.

![Run time by graph size](images/Figure_1.png)

## Run it

```bash
pip install matplotlib pandas numpy networkx openpyxl
python experiments.py     # benchmark, Excel export, plot
python graph_visuals.py   # SCC visualization
```

**Stack:** Python, pandas, NumPy, Matplotlib, NetworkX

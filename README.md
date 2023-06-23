## Refugee Migration Community Detection

This code aims to perform community detection on a refugee migration network using various algorithms. The network represents the migration flows between countries, and the goal is to identify communities or clusters of countries where refugees tend to move.

### Requirements

To run the code, you need the following libraries:

- `networkx`: A Python library for the creation, manipulation, and study of the structure, dynamics, and functions of complex networks.
- `pandas`: A data manipulation and analysis library.
- `matplotlib`: A plotting library for creating visualizations.
- `python-louvain`: A Python implementation of the Louvain community detection algorithm.

You can install these libraries using the `pip` package manager. For example:

```
pip install networkx pandas matplotlib python-louvain
```

### Dataset

The code expects the dataset file "Refugee_Migration.csv" to be present in the same directory. You can download the dataset from [this link](https://www.kaggle.com/datasets/gsaitharunkumar/refugee-migration?resource=download). The dataset provides information about the migration flows between countries, including the year, source country, target country, migration value, and geographic coordinates.

### Code Explanation

1. Import the required libraries: `networkx`, `pandas`, `matplotlib`, and `community`.

2. Read the dataset using `pd.read_csv()` function and store it in a DataFrame named `df`.

3. Create a directed graph `g_refugee` using `nx.from_pandas_edgelist()` function, specifying the source, target, and weight columns.

4. Identify the largest weakly connected component in the graph using `nx.weakly_connected_components()` and keep only that component.

5. Perform community detection using the Fast Greedy algorithm (`nx.algorithms.community.greedy_modularity_communities()`). Store the detected communities in the `communities_fast` variable.

6. Convert the directed graph to an undirected graph (`g_undirected = g_refugee.to_undirected()`).

7. Perform community detection using the Walktrap algorithm (`nx.algorithms.community.asyn_fluidc()`) on the undirected graph, with the number of communities equal to the number of communities detected by Fast Greedy algorithm. Store the detected communities in the `communities_walktrap` variable.

8. Perform community detection using the Spinglass algorithm (`nx.algorithms.community.greedy_modularity_communities()`) on the undirected graph. Store the detected communities in the `communities_spinglass` variable.

9. Perform community detection using the Girvan-Newman algorithm (`nx.algorithms.community.girvan_newman()`) on the directed graph. Store the detected communities in the `communities_gn` variable.

10. Generate a layout for the graph using `nx.spring_layout()`.

11. Plot the graph with communities for each algorithm using `plt.figure()` and `nx.draw_networkx_nodes()`, `nx.draw_networkx_edges()`, and `nx.draw_networkx_labels()` functions. Each community is color-coded for better understanding.

12. Display the graph for each algorithm using `plt.show()`.

### Results

The code generates visualizations of the refugee migration network with communities detected using different algorithms:

1. Fast Greedy Algorithm: Detects communities based on modularity optimization. Larger color-coded communities indicate groups of countries where refugees tend to move together.

2. Walktrap Algorithm: Detects communities based on random walks. There are several communities of similar sizes, indicating different migration patterns.

3. Spinglass Algorithm: Detects communities based on modularity optimization. There are three major

 communities color-coded, representing groups of countries where refugees tend to move.

4. Girvan-Newman Algorithm: Detects communities based on edge betweenness. The detected communities are shown, indicating the division of the network into distinct clusters.

### Conclusion

In this project, I have applied different community detection algorithms to understand the patterns of refugee migration. Each algorithm provides insights into the reasons why refugees move and form communities in specific regions. The visualizations help in analyzing and interpreting the migration flows and identifying significant migration patterns.

Please make sure to download the dataset from the provided link and adjust the column names if needed before running the code.

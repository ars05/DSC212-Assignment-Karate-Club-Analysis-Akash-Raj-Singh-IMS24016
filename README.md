# DSC212 Assignment — Spectral Modularity on the Karate Club Graph

###  Course: Data Science (DSC212)  
###  Assignment: Modularity & Community Detection  
###  Author: *Akash Raj Singh*  

---

##  Overview

This repository contains the complete Google Colab / Jupyter Notebook solution for the **DSC212 Modularity Assignment**.  
It implements **recursive spectral modularity bisection** on the classic **Zachary’s Karate Club** graph and visualizes community evolution and node metrics.

---

##  Problem Statement

The goal of this assignment is to:
1. Implement the **spectral modularity optimization** method using recursive bisection.
2. Apply it on **Zachary’s Karate Club graph** (a standard benchmark for community detection).
3. After each recursive split:
   - Compute and record node-level metrics:
     - Degree Centrality  
     - Betweenness Centrality  
     - Closeness Centrality  
     - Clustering Coefficient
   - Visualize the graph with communities.
   - Track how node metrics evolve across iterations.
4. Present all results neatly, with proper plots and conclusions.

---

##  Theoretical Background

### Modularity
The **modularity** \( Q \) measures how well a network is partitioned into communities:

\[
Q = \frac{1}{2m} \sum_{i,j} \Big(A_{ij} - \frac{k_i k_j}{2m}\Big)\, \delta(c_i, c_j)
\]

where:
- \( A_{ij} \) = adjacency matrix entries  
- \( k_i \) = degree of node \( i \)  
- \( m \) = number of edges  
- \( \delta(c_i, c_j) = 1 \) if nodes \( i \) and \( j \) are in the same community, else 0  

### Spectral Bisection Rule
For a community \( C \), compute the **restricted modularity matrix** \( \mathbf{B}^{(C)} \) and its largest eigenpair:

\[
\mathbf{B}^{(C)} \mathbf{v}_1^{(C)} = \lambda_1^{(C)} \mathbf{v}_1^{(C)}
\]

- If \( \lambda_1^{(C)} > 0 \), split the community based on the **sign of the eigenvector** entries.  
- If \( \lambda_1^{(C)} \le 0 \), the community is **indivisible** and recursion stops.

---

##  Methodology

The notebook performs the following:

1. **Constructs the modularity matrix**
   \[
   \mathbf{B} = \mathbf{A} - \frac{\mathbf{k}\mathbf{k}^\top}{2m}
   \]
2. **Recursively bisects** the graph based on the sign of the leading eigenvector.
3. **Applies a stopping rule** using the leading eigenvalue (\( \lambda_1 \le 0 \)).
4. **Visualizes** the network after each split using a fixed layout.
5. **Computes node metrics** (degree, betweenness, closeness, clustering) after every iteration.
6. **Plots metric evolution** to show structural role changes during community formation.
7. **Computes final modularity \( Q \)** for the detected partition.

---

##  Visualizations

The notebook automatically produces:
- Graph snapshots at every recursive split.  
- Final colored community plot.  
- Metric evolution plots:
  - Degree Centrality vs Iteration  
  - Betweenness Centrality vs Iteration  
  - Closeness Centrality vs Iteration  
  - Clustering Coefficient vs Iteration  

Each node is plotted with consistent coloring across all graphs.

---

##  Results Summary

- Successfully detected **4 major communities** in the Karate Club graph.  
- The **modularity value \( Q \)** achieved reflects meaningful structure separation.  
- Metric trends show:
  - Hubs remain central (high degree & closeness).
  - Bridge nodes have high betweenness early but drop after isolation.
  - Clustering increases within tight communities after splits.

---

##  Discussion & Insights

- Spectral modularity provides **interpretable** community divisions using only eigenstructure.
- Recursive bisection uncovers hierarchical structure naturally.
- Visualization of metrics across iterations offers insights into **node role transitions**.
- Although effective for small networks, **dense eigendecomposition** is computationally heavy for large networks — use sparse solvers for scalability.

---
##  License
This project is for academic use and submission only. Redistribution or publication without permission is prohibited. The project will be accesible until 04th January 2026.


Assignment 3
---
name: Nogaibay Symbat
group: se-2402
------

City Transportation Network Optimization
---
 Project Overview
--------
This project implements and compares Prim’s and Kruskal’s algorithms to find the Minimum Spanning Tree (MST) for optimizing city road construction costs.
The aim is to design a transportation system that connects all city districts using the minimum total road construction cost, while ensuring full connectivity and efficiency of the network.

----

Urban planners frequently face the challenge of balancing infrastructure coverage with financial constraints.
By applying MST algorithms, this project simulates how a city can decide which roads to construct first to achieve optimal cost-efficiency without isolating any district.


--------

🏗️ What This Project Does
-----
Problem Solved
---

Input: A graph where vertices represent city districts and edges represent potential roads with associated construction costs.

Output: The optimal set of roads that connects all districts with the lowest total cost.

Comparison: Detailed analysis and benchmarking of both algorithms’ efficiency, accuracy, and execution time.

-------

Algorithms Implemented
-----

Prim’s Algorithm – A greedy, vertex-based approach that builds the MST progressively from a chosen starting node by always selecting the lowest-cost edge to a new vertex.

Kruskal’s Algorithm – A greedy, edge-based approach that sorts all edges by weight and continuously adds the smallest one that does not create a cycle.

Both algorithms ultimately achieve the same result — a connected graph with minimum total cost — but differ in implementation strategy and performance characteristics.

--------

Results Summary
----
Graph 1 (5 districts, 7 possible roads)
Algorithm	Total Cost	Operations	Time
Prim	16	56	1.06 ms
Kruskal	16	61	0.26 ms

MST Roads: B–C (2), A–C (3), B–D (5), D–E (6)

Graph 2 (4 districts, 5 possible roads)
Algorithm	Total Cost	Operations	Time
Prim	6	45	0.03 ms
Kruskal	6	24	0.03 ms

MST Roads: A–B (1), B–C (2), C–D (3)


------


 Key Findings
 ----
Performance Comparison

Prim’s Algorithm tends to perform better on dense graphs, where most vertices are interconnected.

Kruskal’s Algorithm excels on sparse graphs, where the number of edges is relatively small.

Both consistently produced the same minimum total cost, confirming correctness of implementation.

-----

Time Efficiency
------

On the larger graph, Kruskal’s algorithm was faster (0.26 ms vs. 1.06 ms).

On smaller datasets, both algorithms performed nearly identically.

Prim’s algorithm performed fewer priority queue operations but had slightly higher computational overhead due to heap maintenance.

------

Scalability
----
For larger transportation networks (hundreds of districts), Kruskal’s algorithm is often more practical -
especially when edge data is pre-sorted or stored in adjacency lists.
However, with efficient heap structures, Prim’s algorithm remains competitive for fully connected (dense) city networks.

-----

Project Structure
----
src/
├── main/java/
│   ├── Main.java                 # Entry point - runs both algorithms
│   ├── algorithms/
│   │   ├── PrimAlgorithm.java    # Prim's MST implementation
│   │   └── KruskalAlgorithm.java # Kruskal's MST implementation
│   ├── model/
│   │   ├── Graph.java            # Graph data structure
│   │   └── Edge.java             # Edge with weight
│   └── utils/JsonIO.java         # JSON file handling
└── test/resources/
    ├── ass_3_input.json          # Input graphs
    └── ass_3_output.json         # Algorithm results

------

 What Main.java Does
 ---

The Main class coordinates the entire process:

Reads the input JSON file containing all city graphs;

Executes both Prim’s and Kruskal’s algorithms;

Calculates and logs:

MST edges and total cost,

Operation counts,

Execution times;

Compares the results between algorithms and writes final statistics to a JSON output file.

------

 Conclusion
 ---

Both algorithms effectively solve the Minimum Spanning Tree problem, producing identical results in terms of total cost.
While Prim’s algorithm demonstrates more consistent performance on dense networks, Kruskal’s algorithm shows superior speed and simplicity for sparser, real-world graphs.

In practical urban planning applications, Kruskal’s algorithm often provides the best balance of performance and implementation simplicity.
For very large and interconnected urban areas, Prim’s approach may be favored when optimized with priority queues or adjacency structures.

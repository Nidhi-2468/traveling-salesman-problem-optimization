\# Traveling Salesman Problem using OR-Tools and Gurobi



\## Overview



This project presents multiple approaches for solving the \*\*Traveling Salesman Problem (TSP)\*\* on a real-world road network consisting of \*\*1000 Indian cities\*\*.



The objective is to compare heuristic and exact optimization methods, evaluate their scalability, and study techniques for improving MILP performance on large-scale instances.



The project implements:



\- Google OR-Tools Heuristic

\- Mixed Integer Linear Programming (MILP) using Gurobi

\- Warm Start Optimization

\- K-Nearest Neighbour (KNN) Sparsification



\---



\## Problem Statement



Given a set of cities and pairwise road distances, determine the shortest possible tour that:



\- Visits every city exactly once

\- Returns to the starting city

\- Minimizes the total travel distance



Since the Traveling Salesman Problem is NP-Hard, exact optimization becomes computationally expensive for large instances, motivating the use of heuristic and hybrid optimization techniques.



\---



\## Dataset



\- \*\*1000 Indian Cities\*\*

\- Pairwise road distances generated using the \*\*Open Source Routing Machine (OSRM)\*\*

\- Distance Matrix Size:

&#x20; - 1000 × 1000



\---



\## Methodology



\### 1. Google OR-Tools



Implemented using:



\- PATH\_CHEAPEST\_ARC

\- GUIDED\_LOCAL\_SEARCH



Purpose:



\- Generate high-quality feasible tours quickly

\- Provide initial solutions for warm-start optimization



\---



\### 2. Exact Optimization using Gurobi



Implemented using the \*\*Miller-Tucker-Zemlin (MTZ)\*\* formulation.



Model includes:



\- Binary routing variables

\- MTZ subtour elimination constraints

\- Degree constraints

\- Objective minimization



Experiments were conducted under fixed solver time limits.



\---



\### 3. Warm Start Optimization



The feasible tour obtained from Google OR-Tools is supplied to Gurobi as a \*\*MIP Start\*\*.



This allows the solver to begin with a high-quality incumbent solution instead of constructing one from scratch.



Performance is compared against the cold-start MILP model using:



\- Objective Value

\- Runtime

\- MIP Gap



\---



\### 4. K-Nearest Neighbour (KNN) Sparsification



To improve scalability, only the \*\*K nearest neighbours\*\* of each city are retained as candidate edges.



This reduces:



\- Binary decision variables

\- Memory usage

\- Computational complexity



while maintaining competitive solution quality.



\---



\## Repository Structure



```

Traveling-Salesman-Problem/

│

├── notebook/

│   └── Traveling\_Salesman\_Problem.ipynb

│

├── data/

│   ├── distance\_matrix.csv

│   └── india\_cities.csv

│

├── output/

│   ├── Task1\_ORTools.csv

│   ├── Task2\_WarmStart.csv

│   └── Task3\_KNN.csv

│

├── report/

│   └── TSP\_Report.pdf

│

├── requirements.txt

│

└── README.md

```



\---



\## Technologies Used



\- Python

\- Google OR-Tools

\- Gurobi Optimizer

\- NumPy

\- Pandas

\- Matplotlib

\- Folium



\---



\## Results



\### OR-Tools



\- Produced high-quality tours within a fixed time limit.

\- Scaled efficiently to 1000-city instances.



\### Warm Start



Compared with solving the MILP from scratch, warm-start optimization:



\- Improved the incumbent solution quality

\- Reduced the MIP gap

\- Produced better solutions within identical time limits



\### KNN Sparsification



Restricting candidate edges to the nearest neighbours:



\- Reduced model size significantly

\- Lowered computational cost

\- Preserved good solution quality for suitable values of K



\---



\## Key Learnings



\- OR-Tools provides excellent heuristic solutions for large-scale routing problems.

\- Exact MILP methods become computationally intensive as the number of cities increases.

\- Warm-starting substantially improves branch-and-bound performance.

\- Graph sparsification is an effective strategy for improving scalability in exact optimization.



\---



\## How to Run



1\. Clone the repository



```bash

git clone https://github.com/your-username/traveling-salesman-problem.git

```



2\. Install dependencies



```bash

pip install -r requirements.txt

```



3\. Open the notebook



```

notebook/Traveling\_Salesman\_Problem.ipynb

```



4\. Execute the notebook sequentially.



\---



\## Future Improvements



\- Lazy Constraint implementation

\- Branch-and-Cut formulation

\- Christofides heuristic

\- Lin-Kernighan heuristic

\- Genetic Algorithm

\- Ant Colony Optimization

\- Vehicle Routing Problem (VRP) extensions

\- Parallel optimization for large-scale instances



\---



\## Author



\*\*Nidhi Kumari\*\*



M.S. in Quality Management Science  

Indian Statistical Institute, Bangalore



\*\*Areas of Interest\*\*



\- Operations Research

\- Mathematical Optimization

\- Machine Learning

\- Data Science

\- Supply Chain Analytics


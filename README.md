# Foundations of Operations Research - Big Project

---

### 1. Description of the Problem

Consider a long linear cycle path as Vento, or the Danube cycle path. The cycle path usually runs along the banks of a river with scarce tourist interest. However, from the main course of the cycle path, it is possible to reach places of tourist interest by making small detours.

The rapid growth of e-bike ridership is proposing the problem of deploying a suitable charging infrastructure. The charging stations should be placed in strategic positions to guarantee coverage of the whole cycle path. However, since the charging operations require a non-negligible time, the charging station should be positioned in places where alternative activities could be carried out, such as restaurants, museums, swimming pools, or other amenities. Moreover, the presence of a charging station could also induce e-cyclists to discover new places and generate positive externalities.

### 2. Decision Problem

We can represent the cycle path as a graph where the set of nodes $H = \{1,\ldots, n\}$ corresponds to the tourist sites that may host a charging station.
In addition, we are given the distances between touristic sites ($d_{ij},$ with $i,j =1,\ldots,n$). Let $c_i$ be the cost of installing a charging station in site $i, i=1\ldots,n$.

The problem is, given a budget $b$, determine the subset of sites $S\subseteq H$ where to install the charging stations so that the total cost is not higher than $b$ and the maximum distance between consecutive charging stations is minimized.
Consider that the cyclist has to visit all the tourist destinations in a consecutive way.

### 3. Mathematical Formulation

- Sets:
    - $H = \{1,\ldots, n\}$:  tourist sites that may host a charging station.
    - $N = \{0,\ldots,n+1\}$:  Nodes in the graph consist of tourist sites, along with the source and sink.
    - $A = \{(i, j) \mid i, j \in H}\$: set of arcs representing the distance between two candidate sites

- Parameters:
    - $d_{i,j}, i,j=1,\ldots,n$: distances between consecutive nodes,
    - $c_i$: cost of installing a charging station in site $i, i=1\ldots n$
    - $B$: given budget.

- Useful information:
    - $s = 0$: starting point
    - $t = n+1$: ending point

- Variables:
    - $x_i$: Binary variable, equal to 1 if a charging station is installed at node $\(i\)$, and 0 otherwise, $\(i \in H\)$.
    - $y_{ij}$: Binary variable, equal to 1 if the arc from node $\(i\)$ to node $\(j\)$ is selected, and 0 otherwise, $\(i, j \in H\)$.
 
- Constraints:
    - Budget Constraint: $\sum_{i \in H} c_i \cdot x_i \leq B$
    - Flow Conservation Constraints: <br>
  $\sum_{j \in N} y_{0,j} = 1$ <br>
  $\sum_{i \in N} y_{i,n+1} = -1$ <br>
  $\sum_{j \in N} y_{ij} - \sum_{j \in N} y_{ji} = 0 \quad \text{for all } i \in H$ <br>

- Objective functions:
    - Minimize Maximum Distance: $Minimize \( \max_{i, j \in H} d_{ij} \cdot y_{ij} \)$
  
### 4. Files Description

- **nodes.csv**:
    - dest_id
    - Commune
    - Piazza
    - x(longitude)
    - y(latitude)
    - installation_cost
- **OD.csv**:
    - origin_id
    - destination_id
    - distance

### 5. Requirements

- the maximum running time of the algorithm must be 5 minutes, so set the proper timer
- create the equivalent graph and display it on a xy-plot
- find the solution for the basic scenario, with a MIP model, displaying the solution with a xy-plot, the budget
  constrain is $b = 10000\ € $.
- Find the optimal solution for 5 different values of budget in the range $[10000, 100000]$. Select the values of the
  budget so as to have different charger locations.

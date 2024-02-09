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
    - $A = \{(i, j) \mid i, j \in H}\$: set of arcs representing the distance between two candidate sites.
    - $V =  \{(i, j) \mid i, j \in H \ \text{and} \ d_{i, j} \le D\}\$: set of arcs with distance less than or equal to the maximum allowed distance between two charging stations.

- Parameters:
    - $d_{i,j}, i,j=1,\ldots,n$: distances between consecutive nodes,
    - $c_i$: cost of installing a charging station in site $i, i=1\ldots n$
    - $B$: given budget.
    - $D$: maximum allowed distance between two charging stations.

- Useful information:
    - $s = 0$: starting point
    - $t = n+1$: ending point

- Variables:
    - $y_{ij}$: Binary variable, equal to 1 if there is a charging station in sites $i$ and $j$, and 0 otherwise, $\(i, j \in V\)$.
    - $z$: is a continuous dummy variable representing the total distance of the installation.
 
- Constraints:
    - Budget Constraint: $\sum_{(i, j) \in V} c_i \cdot y_{ij} \leq B - C_{first_site}$ where $\(C_{first_site}\)$ is the cost of installation at the first site.
    - Distance Constraint: is applied in $V$.
    - Dummy Variable Constraint: $d_{ij} - M \cdot (1 - y_{ij}) \leq z \quad \forall (i, j) \in V$ where \(M\) is a large constant.
    - Flow Conservation Constraints: $\sum_{i \in H: (i,j) \in V} y_{ij} -  \sum_{j \in H: (j,i) \in V} y_{ji} = b_i, \forall i\in H\\
  , y_{ij} \ge 0, \forall (i,j) \in V$
    
- Objective functions:
    - $\text{Minimize: } z$ where $z$ is a continuous variable representing the maximum total distance of the installation. 
  
### 4. Files Description

- **nodes.csv**:
    - tourist_dest_id
    - Comune
    - Piazza
    - x (longitude)
    - y (latitude)
    - Cost_of_installation [€]
- **OD.csv**:
    - origin_id
    - destination_id
    - distance [m]

### 5. Requirements

- the maximum running time of the algorithm must be 5 minutes, so set the proper timer
- create the equivalent graph and display it on a xy-plot
- find the solution for the basic scenario, with a MIP model, displaying the solution with a xy-plot, the budget
  constrain is $b = 10000\ € $.
- Find the optimal solution for 5 different values of budget in the range $[10000, 100000]$. Select the values of the
  budget so as to have different charger locations.

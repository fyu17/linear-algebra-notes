# **Chapter 4 - Clustering**

## **4.1 Clustering**
The goal of *clustering* $N$ $n$-vectors is to group or partition the vectors into $k$ groups or clusters, with the vectors in each group close to each other. Normally $k$ is much smaller than $N$. 

## **4.2 A clustering objective**

### **Specifying the cluster assignments**
$c_i$ is the group number $(1, \dots, k)$ that the vector $x_i$ is assigned to.

$G_j$ is the set of indices corresponding to group $j$.

Formally,
$$
G_j = \{i | c_i = j\}
$$

### **Group representatives**
For each of the groups, a *group representative* $n$-vector is denoted as $z_1, \dots, z_k$. These representatives can be any $n$-vectors; they do not need to be one of the given vectors. 

We want to minimize
$$
||x_i - {z_c}_i||,
$$
$i.e.$, we want each representative to be close to the vectors in its associated group. 

### **A clustering objective**
$$
J^{\text{clust}} = (||x_1 -  {z_c}_1||^2 + \dots + ||x_N -  {z_c}_N||^2)/N, 
$$
$i.e.$, the mean square distance from the vectors to their associated representatives.

### **Optimal and suboptimal clustering**
We seek a clustering, $i.e.$, assignments $c_1, \dots, c_N$ and representatives $z_1, \dots, z_k$ that minimizes $J^{\text{clust}}$. We call such a clustering optimal. Unfortunately, it's practically impossible to find an optimal clustering due to growing amount of computation. 

Nevertheless, the **$k$-means algorithm** requires far less computation and often finds a very good, if not the absolute best, clustering. We say that the clustering choices found by the $k$-means algorithm are *suboptimal*, which means that they might note give the lowest possible value of $J^{\text{clust}}$. 

## **4.3 The $k$-means algorithm**

### **Partitioning the vectors with the representatives fixed**
Suppose that the group representatives $z_1, \dots, z_k$ are fixed, and we seek the group assignments $c_1, \dots, c_n$ to minimize $J^{\text{clust}}$. We simply assign each vector to its nearest group representative, giving
$$
||x_i - {z_c}_i|| = \min_{j=1,\dots,k}||x_i - z_j||
$$

### **Optimizing the group representatives with the assignment fixed**
Suppose that the assignments are fixed, and we seek the group representatives. We simply choose the group representative $z_j$ to be the average of the vectors $x_i$ in group j:
$$
z_j = (1/|G_j|)\sum_{i\in G_j}x_i
$$

### **The $k$-means algorithm**
given a list of $N$ vectors $x_1, \dots, x_N$, and an initial list of $k$ group representative vectors $z_1, \dots, z_k$, repeat until convergence:

1. Partition the vectors into k groups. 
2. Update representatives. 
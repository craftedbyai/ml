### **Aim:**: To implement the DBSCAN clustering algorithm

---

### **Theory:**

**DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** is an **unsupervised clustering algorithm** that groups together data points that are closely packed (dense regions) and marks points that lie alone in low-density regions as **noise or outliers**.

Unlike K-Means, DBSCAN does not require the number of clusters to be specified in advance and can detect clusters of arbitrary shapes.

---

### **Key Concepts:**

1. **Epsilon (ε):**
   The maximum distance between two points for them to be considered neighbors.

2. **MinPts (Minimum Samples):**
   The minimum number of neighboring points required to form a dense region (cluster).

3. **Core Point:**
   A point that has at least `MinPts` points within a radius of `ε`.

4. **Border Point:**
   A point that lies within the ε-neighborhood of a core point but does not itself have enough points to be a core point.

5. **Noise Point (Outlier):**
   A point that is not reachable from any core point.

6. **Directly Density-Reachable:**
   A point `q` is **directly density-reachable** from a point `p` if `p` is a core point and `q` lies within its ε-neighborhood.

7. **Density-Reachable:**
   A point `q` is **density-reachable** from a point `p` if there exists a chain of points `p1, p2, ..., pn`,
   where `p1 = p` and `pn = q`, such that each point is directly density-reachable from the previous one.

8. **Density-Connected:**
   Two points `p` and `q` are **density-connected** if there exists a point `o` such that both `p` and `q` are density-reachable from `o`.

---

### **Algorithm Steps:**

1. For each unvisited point, find all neighboring points within distance ε.
2. If the number of neighbors ≥ MinPts, mark it as a **core point** and form a new cluster.
3. Expand the cluster by recursively including all **density-reachable** points.
4. Continue until all points are visited.
5. Points not assigned to any cluster are marked as **noise** (`label = -1`).

---

### **Advantages:**

* Finds clusters of arbitrary shape and size.
* Automatically identifies noise and outliers.
* No need to specify the number of clusters beforehand.

### **Disadvantages:**

* Sensitive to the choice of `eps` and `MinPts`.
* Struggles when clusters have different densities.

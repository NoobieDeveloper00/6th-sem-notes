# 🔹 Problem Set 1: Trees

---

## Problem 1

Prove that a tree with ( n ) vertices has exactly ( n - 1 ) edges.

### What Examiner Wants:

Induction proof or structural argument.

### Expected Answer Structure:

1. Base case:  
    n = 1 → edges = 0 ✓
    
2. Assume true for n = k
    
3. Any tree has at least one leaf  
    Remove leaf → remaining graph has k vertices
    
4. By induction → edges = k − 1
    
5. Add removed edge back → total edges = k
    

So edges = n − 1.

Clean. Logical. Full marks.

---

## Problem 2

Prove that in a tree there is exactly one path between any two vertices.

### Core Logic:

If two distinct paths exist → combine them → form a cycle.  
But tree has no cycles.  
Contradiction.  
Hence exactly one path.

Short and elegant.

---

## Problem 3

Show that every tree with at least 2 vertices has at least 2 pendant vertices.

Hint logic:

- Take the longest path in the tree.
    
- Its endpoints must be degree 1.
    
- Otherwise, path could extend further.
    

Classic textbook proof.

---

# 🔹 Problem Set 2: Spanning Trees & Fundamental Circuits

---

## Problem 4

Let G be a connected graph with n vertices and m edges.  
Show that number of fundamental circuits = m − n + 1.

### Solution Idea:

Spanning tree has n−1 edges.

Remaining edges:  
m − (n−1) = m − n + 1

Each cotree edge produces one fundamental circuit.

Done.

---

## Problem 5

Show that in a tree every edge is a cut edge.

### Solution Idea:

Remove any edge.

Since tree has exactly one path between endpoints,  
removing it disconnects the graph.

Therefore every edge is a bridge.

---

# 🔹 Problem Set 3: Planar Graphs

Now we get serious.

---

## Problem 6

Use Euler’s formula to prove that a simple planar graph with V ≥ 3 satisfies:

$$  
E ≤ 3V − 6  
$$

### Outline:

1. Euler formula:  
    V − E + F = 2
    
2. Each face has at least 3 edges  
    So: 3F ≤ 2E
    
3. Substitute:  
    F ≤ 2E/3
    
4. Put in Euler:  
    V − E + 2E/3 ≥ 2
    
5. Solve:  
    E ≤ 3V − 6
    

Professors love this proof.

---

## Problem 7

Show that K₅ is non-planar.

![Image](https://www.researchgate.net/publication/333098829/figure/fig2/AS%3A961741601132565%401606308474728/The-complete-graph-K5documentclass12ptminimal-usepackageamsmath.png)

![Image](https://www.researchgate.net/publication/381748691/figure/fig1/AS%3A11431281369251890%401744303133377/Five-mutually-non-isomorphic-drawings-of-K5-a-only-one-crossing-b-additional.tif)

![Image](https://www.researchgate.net/publication/373437937/figure/fig1/AS%3A11431281184015281%401693192162883/a-A-min-2-planar-drawing-of-K5-5-b-A-planar-drawing-G-of-the-truncated-icosahedral.png)

![Image](https://i.sstatic.net/WvrBv.png)

Edges in K₅:

5×4/2 = 10

But planar bound gives:

E ≤ 3V − 6 = 3×5 − 6 = 9

10 > 9

So violates condition.

Therefore non-planar.

Clean numeric proof.

---

## Problem 8

Show that K₃,₃ is non-planar.

![Image](https://www.researchgate.net/publication/371659025/figure/fig3/AS%3A11431281388353162%401745162401188/The-complete-bipartite-graph-K3-3-with-vertex-sets-1-2-3-and-4-5-6.tif)

![Image](https://upload.wikimedia.org/wikipedia/commons/thumb/3/39/3_utilities_problem_torus.svg/250px-3_utilities_problem_torus.svg.png)

![Image](https://miro.medium.com/1%2A6IlnSzn93Zot7DuH0qrzpQ.png)

![Image](https://www.rodhilton.com/assets/k33andk5.png)

For bipartite planar graphs:

E ≤ 2V − 4

Here:  
V = 6  
So E ≤ 2×6 − 4 = 8

But K₃,₃ has 9 edges.

9 > 8

So non-planar.

---

# 🔹 Problem Set 4: Cut Vertices & Cut Sets

---

## Problem 9

Find all cut vertices of a given graph.

Strategy:

Remove vertex one by one.  
Check if number of components increases.

In trees:  
All internal vertices are cut vertices.

Leaves are not.

---

## Problem 10

Let G be a connected graph. Show that if G has no cut vertex, then for any two vertices there exist two internally disjoint paths.

This relates to 2-connectivity.

More advanced but very common exam question.

---

# 🔹 Problem Set 5: Metric Dimension

---

## Problem 11

Find metric dimension of:

### (a) Path graph Pₙ

Answer:  
1

One endpoint resolves all vertices.

---

### (b) Cycle graph Cₙ

Answer:  
2

One vertex is not enough because symmetry.  
Two break symmetry.

Classic question.

---
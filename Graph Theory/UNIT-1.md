
We proceed in layers:

1. Graph Basics
    
2. Isomorphism
    
3. Walks, Paths, Circuits
    

---

# 1. Graph Basics

## 1.1 Definition of a Graph

A **graph** is an ordered pair:

$$

G = (V, E)  
$$

V = non-empty finite set of vertices
E  = set of edges, each edge joining two vertices

If edges are unordered pairs → **undirected graph**  
If edges are ordered pairs → **directed graph (digraph)**

---

## 1.2 Types of Graphs

### (a) Simple Graph

- No loops
    
- No parallel edges
    

### (b) Multigraph

- Parallel edges allowed
    
- No loops
    

### (c) Pseudograph

- Loops allowed
    
- Parallel edges allowed
    

If your exam question says “graph” without specification, assume **simple graph** unless stated otherwise. Professors enjoy that trap.

---

## 1.3 Basic Terminology

Let: 
$$
( G = (V,E) ).
$$

### Degree of a Vertex

For undirected graphs:

$$
\deg(v) = \text{number of edges incident to } v  
$$

- Loop contributes **2** to degree.
    
- Isolated vertex → degree 0.
    
- Pendant vertex → degree 1.
    

### Handshaking Lemma

$$
\sum_{v \in V} \deg(v) = 2|E|  
$$


Why? Every edge contributes 2 to total degree.

Immediate consequence:  
Number of vertices of odd degree is **even**.

Examiners love asking you to prove that.

---

## 1.4 Adjacent and Incident

- Two vertices are **adjacent** if connected by an edge.
    
- An edge is **incident** to its end vertices.
    

---

## 1.5 Subgraphs

A graph H = (V', E') is a subgraph of ( G ) if:

$$
V' \subseteq V
$$

$$
E' \subseteq E
$$

Special cases:

- **Spanning subgraph**: contains all vertices.
    
- **Induced subgraph**: contains all edges between chosen vertices.
    

---

# 2. Isomorphism of Graphs

This is where people get overconfident and lose marks.

## 2.1 Definition

Two graphs 
$$
G_1 = (V_1, E_1) 
$$
$$
( G_2 = (V_2, E_2) ) 
$$
are **isomorphic** if there exists a bijection:
$$
f : V_1 \to V_2  
$$

such that:
$$
{u,v} \in E_1 \iff {f(u), f(v)} \in E_2  
$$

In plain language:  
They are structurally identical, only vertex labels differ.

---

## 2.2 Necessary Conditions for Isomorphism

If two graphs are isomorphic, they must have:

- Same number of vertices
    
- Same number of edges
    
- Same degree sequence
    
- Same number of connected components
    
- Same number of cycles of each length
    

Important:  
These are **necessary but not sufficient** conditions.

Same degree sequence ≠ guaranteed isomorphic.

Classic trap.

---

## 2.3 Invariants

Properties preserved under isomorphism are called **graph invariants**:

- Degree sequence
    
- Number of triangles
    
- Chromatic number
    
- Connectivity

If any invariant differs → graphs are NOT isomorphic.

---

## 2.4 Why Isomorphism is Hard

Graph isomorphism problem is computationally non-trivial.  
Not known to be NP-complete.  
Recently quasi-polynomial time algorithm found (Babai, 2015).

For your exam:  
You’ll likely be asked to check isomorphism manually using degree matching and structural reasoning.

---

# 3. Walks, Paths, and Circuits

This is foundational. Many later theorems depend on this.
$$
Let ( G = (V,E) ).
$$

---

## 3.1 Walk

A **walk** is a sequence:
$$
[  
v_0, v_1, v_2, ..., v_k  
]
$$

such that each consecutive pair is connected by an edge.

Vertices and edges may repeat.

Length of walk = number of edges = ( k ).

---

## 3.2 Trail

A walk with **no repeated edges**.

Vertices may repeat.

---

## 3.3 Path

A walk with **no repeated vertices**.

Except possibly first and last in case of closed path.

This is important:

- Path ⇒ Trail ⇒ Walk
    
- Reverse is not always true
    

---

## 3.4 Closed Walk

A walk where:
$$
v_0 = v_k  
$$

Start = end.

---

## 3.5 Circuit

A closed trail.

- No repeated edges
    
- Start = end
    

---

## 3.6 Cycle

A closed path.

- No repeated vertices except first = last
    
- Length ≥ 3 in simple graphs
    

---

## 3.7 Connected Graph

A graph is **connected** if there exists a path between every pair of vertices.

If not → disconnected.

Connected components = maximal connected subgraphs.

---

# Important Theoretical Results

### Theorem 1

If there is a walk between two vertices, then there exists a path between them.

Proof idea:  
Remove repeated vertices from walk → obtain path.

Exam favorite.

---

### Theorem 2

A graph is connected iff there is a path between every pair of vertices.

Definition-level but they may ask proof.

---

# Common Exam Questions

1. Prove Handshaking Lemma.
    
2. Prove number of odd degree vertices is even.
    
3. Determine if two given graphs are isomorphic.
    
4. Classify given sequences as walk, trail, path, circuit.
    
5. Prove that a graph with minimum degree ≥ (n−1)/2 is connected. (Sometimes appears.)

---
# Strategy for Isomorphism Questions

In order:

1. Compare number of vertices
    
2. Compare number of edges
    
3. Compare degree sequence
    
4. Compare structure (cycles, components)
    
5. Attempt explicit mapping
---
# 1. What is a Tree?

## Formal Definition

A **tree** is a connected graph with no cycles.

That’s it.

Two conditions:

1. Connected
    
2. Acyclic (no cycles)
    

If either fails → not a tree.

---

# 2. Intuition

Think of:

- A family tree
    
- A company hierarchy
    
- A file system
    

There is exactly one way to go from one vertex to another.

No loops. No alternate routes.

If you can go around in a circle → not a tree.

---

# 3. Very Important Theorems About Trees

These are exam gold. Memorize logic, not just statements.

---

## Theorem 1

A tree with ( n ) vertices has exactly:  n - 1  edges.

This is THE defining numerical property.

---

### Why is this true?

Intuition:

Start with one vertex → 0 edges.

Every time you add a new vertex and want to keep it connected but avoid cycles:

You must add exactly one edge.

So:  
1 vertex → 0 edges  
2 vertices → 1 edge  
3 vertices → 2 edges  
...  
n vertices → n−1 edges

Add even one extra edge → you create a cycle.

---

## Theorem 2

If a connected graph has ( n ) vertices and ( n-1 ) edges, then it is a tree.

So:

Connected + (n−1 edges) ⇒ Tree

This is often used to prove something is a tree.

---

## Theorem 3

In a tree, there is exactly one simple path between any two vertices.

This is extremely important.

Why?

If there were two different paths between same vertices,  
you could combine them and form a cycle.

But trees cannot have cycles.

So only one path exists.

---

# 4. Equivalent Definitions of a Tree

All of these mean the same thing:

A graph is a tree if:

1. It is connected and acyclic.
    
2. It is connected and has n−1 edges.
    
3. It has n−1 edges and no cycles.
    
4. There is exactly one path between any two vertices.
    

Examiners LOVE asking:  
“Prove that the following are equivalent.”

---

# 5. Leaves (Pendant Vertices)

A **leaf** is a vertex of degree 1.

Important theorem:

Every tree with at least 2 vertices has at least 2 leaves.

You cannot have a tree shaped like a circle.  
There must be ends.

---

# 6. Removing Edges in Trees

In a tree:

- Removing any edge disconnects the graph.
    
- Adding any new edge creates exactly one cycle.
    

Trees are extremely fragile.

Remove one edge → breaks into two components.

Add one edge → cycle appears.

---

# 7. Special Types of Trees

### (a) Path Graph

Looks like a straight line.

### (b) Star Graph

One central vertex connected to all others.

Center has degree n−1.  
All others have degree 1.

---

# 8. Spanning Tree

This is very important.

Given a connected graph G,  
a **spanning tree** is:

A subgraph that:

- Contains all vertices
    
- Is a tree
    

Meaning:  
You remove just enough edges to kill all cycles,  
but keep it connected.

Every connected graph has at least one spanning tree.

---

# 9. Why Trees Matter

They appear everywhere:

- Network design
    
- Minimum Spanning Tree (Kruskal, Prim)
    
- Routing
    
- Data structures (binary trees)
    
- Optimization problems
    

Trees are the skeleton of connected graphs.

---

# 10. Quick Proof Example (Exam Style)

Prove:  
A tree with n vertices has n−1 edges.

Proof idea (by induction):

Base case:  
n = 1 → edges = 0 ✓

Induction:  
Assume true for n=k.

Take tree with k+1 vertices.

Remove a leaf.  
Remaining graph is a tree with k vertices.  
By assumption → k−1 edges.

Add the removed edge back → total edges = k.

So formula holds.

Done.

---
You’re getting way too comfortable. Focus before I turn your tree into a disconnected forest.

We move forward properly.

Next topics from Unit 1:

- Properties of Trees (deeper structural results)
    
- Cotrees
    
- Fundamental Circuits
    
- Cut Sets
    
- Fundamental Cut Sets
    
- Cut Vertices
    

This is where graph theory starts feeling elegant instead of just definitions.

---

# 1. Deeper Properties of Trees

We already know:

- Tree ⇔ connected + acyclic
    
- Tree with n vertices has n−1 edges
    
- Exactly one path between any two vertices
    

Now let’s go one level deeper.

---

## Property 1: Trees are Minimally Connected

A tree is a **minimally connected graph**.

Meaning:

If you remove any edge → graph becomes disconnected.

Why?

Because in a tree there is exactly one path between two vertices.

If you remove an edge, that unique path is broken.

No alternate route exists.

---

## Property 2: Trees are Maximally Acyclic

Add any new edge to a tree → exactly one cycle forms.

Why exactly one?

Because between the two endpoints of the new edge,  
there was already one path.

Adding the new edge closes that path into a cycle.

---

## Property 3: Sum of Degrees in Tree

Using Handshaking Lemma:

Sum of degrees = 2(n−1)

Useful for solving degree-based problems.

---

# 2. Spanning Trees (Very Important)

Given a connected graph G:

A **spanning tree** is a subgraph that:

- Includes all vertices
    
- Has n−1 edges
    
- Is acyclic
    

Think of it as the backbone of the graph.

You remove just enough edges to destroy all cycles.

---

## Key Fact

If original graph has:

n vertices  
m edges

Then number of edges removed to get spanning tree =

m − (n−1)

That number is important when we discuss cotrees.

---

# 3. Cotree

Let:

T = a spanning tree of graph G.

The edges that are NOT in T  
are called **chords** or **links**.

The subgraph formed by those remaining edges is called the **cotree**.

In simple words:

Original Graph = Tree edges + Cotree edges

Tree edges = n−1  
Cotree edges = m − (n−1)

---

# 4. Fundamental Circuits

This is a beautiful concept.

Take:

A spanning tree T.

Now pick one cotree edge (one extra edge not in T).

Add that edge back to T.

What happens?

Exactly one cycle is formed.

That cycle is called a:

**Fundamental Circuit (with respect to T)**

Important:

Each cotree edge produces exactly one fundamental circuit.

Number of fundamental circuits =  
Number of cotree edges =  
m − (n−1)

---

## Why Exactly One Cycle?

Because between the two endpoints of the added edge,  
there is exactly one path in the tree.

Add the extra edge → closes that path → one cycle.

No more. No less.

---

# 5. Cut Sets

A **cut set** is a set of edges whose removal disconnects the graph.

Minimal cut set:  
If removing any smaller subset does NOT disconnect.

In a tree:

Every single edge is a cut edge.

Because removing any one disconnects it.

---

# 6. Cut Vertex (Articulation Point)

A **cut vertex** is a vertex whose removal disconnects the graph.

Important facts:

- Trees with more than 2 vertices always have cut vertices.
    
- Leaves are NOT cut vertices.
    
- Internal vertices in trees usually are.
    

Example:

In a path:  
All internal vertices are cut vertices.

Remove them → graph splits.

---

# 7. Fundamental Cut Sets

This is the dual concept to fundamental circuits.

Take a spanning tree T.

Pick one tree edge.

Remove that tree edge.

Tree splits into two components.

Now collect all edges in original graph that connect those two components.

That set is the:

**Fundamental Cut Set (with respect to T)**

Each tree edge produces exactly one fundamental cut set.

Number of fundamental cut sets = number of tree edges = n−1.

---

# Summary of Duality

Tree edge → fundamental cut set  
Cotree edge → fundamental circuit

Count comparison:

Tree edges = n−1  
Cotree edges = m − (n−1)

Fundamental cut sets = n−1  
Fundamental circuits = m − (n−1)

There’s symmetry here. Professors love asking you to explain it.

---
# 1. Planar Graphs

## 1.1 Definition

A graph is **planar** if it can be drawn on a plane such that:

No two edges intersect except at vertices.

Important detail:

“Can be drawn” matters.

Even if your first drawing has crossings,  
if it is possible to redraw it without crossings → it is planar.

---

## 1.2 Example Intuition

- A triangle → planar
    
- A square → planar
    
- A tree → always planar
    

Trees are innocent. They never cause crossing drama.

---

## 1.3 Euler’s Formula (Extremely Important)

For any connected planar graph:

$$
V - E + F = 2  
$$

Where:

V = number of vertices  
E = number of edges  
F = number of faces

Face = region formed by drawing (including outer infinite region).

This formula is exam gold. Proof often asked.

---

### Why is this powerful?

It restricts how many edges a planar graph can have.

---

## 1.4 Important Consequence

From Euler’s formula:

For any simple connected planar graph with ( V ≥ 3 ):

$$
E ≤ 3V - 6  
$$

If a graph violates this inequality → it is NOT planar.

Immediate test.

---

## 1.5 Special Case (No triangles)

If graph has no cycles of length 3:

$$  
E ≤ 2V - 4  
$$

Even stricter.

---

# 1.6 Non-Planar Graphs

Two famous non-planar graphs:

## Complete Graph on 5 vertices

K₅

## Complete Bipartite Graph

K₃,₃

These two are fundamental.

Kuratowski’s Theorem says:

A graph is non-planar iff it contains a subdivision of K₅ or K₃,₃.

For B.Tech level:  
You mostly need to recognize these two.

---

## What is K₅?

Every vertex connected to every other vertex.

Total edges:

5×4/2 = 10

10 > 3×5 − 6 = 9

Violates planar inequality.

So non-planar.

---

## What is K₃,₃?

Two sets of 3 vertices.  
Every vertex in one set connects to all in other set.

No connections within same set.

Classic "utility problem".

Cannot draw without crossing.

---

# 2. Dual Graphs

Now things get elegant.

Given a planar graph drawn without crossings:

You create a new graph by:

- Placing one vertex inside each face
    
- Connect two new vertices if their faces share an edge
    

This new graph is called the **dual graph**.

---

## Key Idea

Original graph:  
Vertices connected by edges.

Dual graph:  
Faces become vertices.

Edges correspond.

Beautiful symmetry.

---

## Properties

- Number of dual vertices = number of faces in original
    
- Dual of dual returns original (if connected and simple enough)
    
- Edges correspond one-to-one
    

---

# 3. Metric Representation of Graphs

Now slightly more niche but important.

This involves distances.

---

## 3.1 Distance

Distance between two vertices:

Length of shortest path between them.

Denoted as:

d(u, v)

---

## 3.2 Resolving Set

A set of vertices W is called a resolving set if:

Every vertex in graph is uniquely identified by its distances to vertices in W.

---

## 3.3 Metric Dimension

The minimum size of a resolving set.

That number is called:

Metric dimension of graph.

---

### Intuition

Imagine placing GPS sensors at certain vertices.

Every vertex is uniquely determined by how far it is from those sensors.

Minimum number of sensors needed = metric dimension.

---

# Why This Appears in Exams

They may ask:

- Verify Euler’s formula
    
- Prove inequality E ≤ 3V−6
    
- Show K₅ or K₃,₃ is non-planar
    
- Construct dual graph
    
- Find metric dimension of simple graph (path, cycle)
    

---

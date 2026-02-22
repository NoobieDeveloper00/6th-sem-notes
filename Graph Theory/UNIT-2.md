# 🎨 Graph Coloring (Vertex Coloring)

Let’s build it cleanly.

---

# 1️⃣ What is Graph Coloring?

A **proper vertex coloring** of a graph is:

An assignment of colors to vertices such that  
no two adjacent vertices have the same color.

That’s it.

Adjacent vertices must have different colors.

We are NOT coloring edges yet. Just vertices.

---

## Why do we care?

Real-world meaning:

- Exam scheduling (no two clashing subjects same slot)
    
- Register allocation in compilers
    
- Frequency assignment in networks
    
- Map coloring
    

Basically: “things that conflict must differ.”

---

# 2️⃣ Chromatic Number

The **chromatic number** of a graph ( G ), written:
$$ 
\chi(G)  
$$

is the **minimum number of colors** needed for a proper coloring.

Minimum is important.

Not “can I color with 7 colors.”  
Question is:  
What is the least number needed?

---

# 3️⃣ Basic Examples

---

## (a) Path Graph ($P_n$)

Like:

A — B — C — D

Two colors are enough:

Color alternately.

So:                                                                                $\chi(P_n) = 2$  


(Except if n=1 → then 1)

---

## (b) Cycle Graph ( $C_n$ )

Case 1: n even

You can alternate colors around.

So:

$$
\chi(C_n) = 2  
$$

Case 2: n odd

When you come back to start, conflict occurs.

So need 3 colors.
$$
\chi(C_n) = 3  
$$

Classic exam question.

---

## (c) Complete Graph ( $K_n$ )

![Image](https://www.researchgate.net/publication/382770470/figure/fig1/AS%3A11431281264381530%401722550930857/A-Complete-graph-K4.ppm)

![Image](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Complete_graph_K5.svg/250px-Complete_graph_K5.svg.png)





Every vertex connected to every other vertex.

So no two vertices can share color.

Thus:
$$
\chi(K_n) = n  
$$

Maximum possible.

---

## (d) Bipartite Graph

If graph is bipartite (vertices can be divided into two sets such that no edge within same set):

Then:
$$
\chi(G) = 2  
$$

Provided at least one edge exists.

Trees are bipartite.  
So every tree (with ≥2 vertices) has chromatic number 2.

---

# 4️⃣ Important Theorems

---

## Theorem 1

For any graph G:

$$
\chi(G) ≥ \omega(G)  
$$

Where:
$$
\omega(G) = \text{size of largest complete subgraph (clique).}
$$
Because if you have a Kₖ inside,  
you need at least k colors.

---

## Theorem 2

If maximum degree of G is Δ, then:

$$
\chi(G) ≤ Δ + 1  
$$

This is an upper bound.

(Brooks’ theorem refines this, but that’s usually extra depth.)

---

# 5️⃣ Coloring Strategy (Greedy Algorithm)

Procedure:

1. Pick a vertex.
    
2. Assign smallest available color.
    
3. Move sequentially.
    

Greedy coloring never uses more than Δ + 1 colors.

But it does NOT always give minimum coloring.

Exam trick:  
They may ask you to color using greedy and compare.

---

# 6️⃣ Typical Exam Questions

1. Find chromatic number of given graph.
    
2. Prove that a tree has chromatic number 2.
    
3. Show that odd cycle requires 3 colors.
    
4. Prove χ(G) ≥ clique number.
    
5. Use greedy coloring on specific vertex ordering.
    

---

# Let’s Test You Lightly

If graph contains a triangle,  
minimum colors required?

At least 3.

Because triangle = K₃.

Even if rest of graph is simple.

---

Coloring seems simple.

It becomes hard very quickly.

Computing chromatic number for arbitrary graph is NP-hard.

---

# 🎨 1️⃣ Chromatic Partitioning

This is just another way of looking at coloring.

Instead of thinking “assign colors,”  
think:

Partition the vertex set into independent sets.

---

## 🔹 What is an Independent Set?

An independent set is a set of vertices such that:

No two vertices in it are adjacent.

So no edges inside that set.

---

## 🔹 Chromatic Partition

A **chromatic partition** is:

A partition of vertices into the minimum number of independent sets.

That minimum number is:
$$\chi(G)  $$

So:

Color classes = independent sets.

Coloring and partitioning are the same idea, just different viewpoint.

---

## Example

Triangle K₃:

Each vertex adjacent to others.

So independent sets can only contain one vertex each.

Thus:

Partition = {v1}, {v2}, {v3}

So:
$$\chi(K_3) = 3  $$


---

# 🎨 2️⃣ Chromatic Polynomial

Now things get elegant.

Instead of asking:

“What is minimum number of colors?”

We ask:

“How many ways can we color the graph using k colors?”

That function is called:
$$  
P(G, k)  
$$

Chromatic Polynomial.

---

## 🔹 Definition

(P(G, k)) = number of proper colorings of G using at most k colors.

It is actually a polynomial in k.

Yes. A real polynomial.

---

## 🔹 Example 1: No edges (n isolated vertices)

Each vertex can be colored independently.

So:

$$
P(G,k) = k^n  
$$

---

## 🔹 Example 2: Complete Graph ($K_n$)

First vertex → k choices  
Second → k−1  
Third → k−2  
...

So:

$$
P(K_n, k) = k(k-1)(k-2)...(k-n+1)  
$$

---

## 🔹 Example 3: Tree with n vertices

Important result:

$$
P(T, k) = k (k-1)^{n-1}  
$$

Why?

- Choose color for root → k choices
    
- Each other vertex → must differ from parent → k−1 choices
    

Trees behave nicely. As usual.

---

## 🔹 Deletion–Contraction Formula

This is the powerful recursive tool.

For any edge e:

$$
P(G, k) = P(G - e, k) - P(G / e, k)
$$


Where:

G − e = graph with edge removed  
G / e = graph with edge contracted

This formula is often asked in exams.

---

# 🤝 3️⃣ Matching

Now we shift gears.

A **matching** is:

A set of edges with no common vertices.

No vertex can belong to two edges in matching.

---

## 🔹 Types

- Maximum matching → largest possible size
    
- Perfect matching → covers all vertices
    

Perfect matching possible only if number of vertices even.

---

## 🔹 Example: Complete Bipartite Graph ($K_{m,n}$)

Maximum matching size = min(m,n)

---

## 🔹 Hall’s Theorem (Very Important)

For bipartite graph:

There exists a perfect matching iff:

For every subset S of left part:
$$|N(S)| ≥ |S|  $$

Where N(S) = neighbors of S.

This appears frequently in exams.

---

# 🛡 4️⃣ Vertex Cover

A **vertex cover** is a set of vertices such that:

Every edge has at least one endpoint in the set.

---

## Relationship in Bipartite Graphs

Very important theorem:

In bipartite graphs:

Size of maximum matching = size of minimum vertex cover

(Kőnig’s Theorem)

This is exam gold.

---

# 🌍 5️⃣ Four Color Problem

Statement:

Every planar graph can be colored with at most 4 colors.

Equivalent to:

Any planar map can be colored using 4 colors such that adjacent regions differ.

---

## Important Facts

- First conjectured in 1852.
    
- Proven in 1976 using computer assistance.
    
- Very deep theorem.
    

For B.Tech:

You only need:

Planar graph ⇒ χ(G) ≤ 4

---

# 🔥 Typical Exam Problems from Unit 2

1. Find chromatic number of given graph.
    
2. Find chromatic polynomial of simple graph.
    
3. Use deletion–contraction to compute polynomial.
    
4. Find maximum matching.
    
5. Apply Hall’s theorem.
    
6. Prove χ(K_n) = n.
    
7. Show tree has chromatic polynomial k(k−1)^{n−1}.
    

---
Graph theory one minute, self-balancing binary search trees the next. Your syllabus has commitment issues.

Fine. We switch to **AVL Trees**. Clean. Deterministic. No emotional instability allowed, unlike some students I know.

---

# 🌳 What is an AVL Tree?

An **AVL Tree** is a self-balancing Binary Search Tree (BST).

Named after:  
Georgy Adelson-Velsky  
Evgenii Landis

### Core Rule:

For every node,
$$
\text{Balance Factor} = \text{height(left)} - \text{height(right)}  
$$

Must be:
$$
-1, 0, +1  
$$

If it becomes:

- +2 → left heavy
    
- −2 → right heavy
    

We perform rotations.

---

# 🔁 The 4 AVL Rotations

There are exactly four cases.

---

## 1️⃣ LL Rotation (Single Right Rotation)

Happens when:

- Inserted into left subtree
    
- Of left child
    

Heavy on left-left.

### Before:

```
        30
       /
      20
     /
    10
```

### After Right Rotation:

```
        20
       /  \
     10    30
```

![Image](https://pages.cs.wisc.edu/~qingyi/Ratation.png)

![Image](https://raw.githubusercontent.com/HebleV/valet_parking/master/images/avl_right_rotation.jpg)

![Image](https://i.sstatic.net/h3rB1.jpg)

![Image](https://iq.opengenus.org/content/images/2018/05/avl_left_rotation.jpg)

---

## 2️⃣ RR Rotation (Single Left Rotation)

Mirror of LL.

Inserted into:

- Right subtree
    
- Of right child
    

### Before:

```
    10
       \
        20
           \
            30
```

### After Left Rotation:

```
        20
       /  \
     10    30
```

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AeYEkh7esJ1P6J0ggd0skmQ.png)

![Image](https://www.tutorialspoint.com/data_structures_algorithms/images/LR_Rotation.jpg)

![Image](https://raw.githubusercontent.com/HebleV/valet_parking/master/images/avl_right_rotation.jpg)

![Image](https://iq.opengenus.org/content/images/2018/05/avl_right_rotation.jpg)

---

## 3️⃣ LR Rotation (Left-Right)

Inserted into:

- Right subtree
    
- Of left child
    

Two rotations:

1. Left rotation on child
    
2. Right rotation on root
    

### Before:

```
        30
       /
      10
         \
          20
```

### Step 1: Left rotate at 10

### Step 2: Right rotate at 30

### After:

```
        20
       /  \
     10    30
```

![Image](https://www.tutorialspoint.com/data_structures_algorithms/images/RL_Rotations.jpg)

![Image](https://www.tutorialspoint.com/data_structures_algorithms/images/LR_Rotation.jpg)

![Image](https://i.sstatic.net/fYxU7.jpg)

![Image](https://i.sstatic.net/2MfG6.png)

---

## 4️⃣ RL Rotation (Right-Left)

Mirror of LR.

Inserted into:

- Left subtree
    
- Of right child
    

Two rotations:

1. Right rotation on child
    
2. Left rotation on root
    

### Before:

```
      10
         \
          30
         /
        20
```

### After:

```
        20
       /  \
     10    30
```

![Image](https://www.tutorialspoint.com/data_structures_algorithms/images/RL_Rotations.jpg)

![Image](https://www.tutorialspoint.com/data_structures_algorithms/images/LR_Rotation.jpg)

![Image](https://i.sstatic.net/2MfG6.png)

![Image](https://i.sstatic.net/0kXfL.png)

---

Now let’s do what you actually asked.

Two comprehensive examples.

---

# 🌟 Example 1: Insertion with Multiple Rotations

Insert in order:

10, 20, 30, 40, 50, 25

---

### Step 1: Insert 10

Balanced.

### Step 2: Insert 20

Still balanced.

### Step 3: Insert 30

Now imbalance at 10 → RR case.

Left rotation at 10.

Tree becomes:

```
      20
     /  \
   10   30
```

---

### Step 4: Insert 40

Still balanced.

---

### Step 5: Insert 50

Imbalance at 30 → RR case.

Left rotation at 30.

---

### Step 6: Insert 25

Now imbalance at 20.  
This is RL case.

Perform:

1. Right rotate at 40
    
2. Left rotate at 20
    

Final balanced tree:

```
          30
        /    \
      20      40
     /  \       \
   10   25      50
```

Multiple rotations triggered correctly.

---

# 🌟 Example 2: Deletion with Rebalancing

Insert:

50, 30, 70, 20, 40, 60, 80, 10

Tree is balanced.

Now delete 80.

Still balanced.

Now delete 70.

Now imbalance appears at 50.

Left subtree height = 3  
Right subtree height = 1

Balance factor = +2 → LL case.

Right rotation at 50.

Tree becomes:

```
        30
       /  \
     20    50
    /     /  \
  10    40   60
```

Balanced again.

Deletion can also trigger LR or RL depending on structure.

Important:  
After deletion, we must check balance factor while moving upward.

Insertion may cause one rotation.  
Deletion may cause multiple rebalances up the path.

---

# 🔥 Important Notes for Exams

1. Always compute balance factor.
    
2. Identify which of 4 cases.
    
3. Apply correct rotation(s).
    
4. Update heights properly.
    

Time complexity:  
O(log n) for insert and delete.

Because height always stays O(log n).

---

# 📘 Matching and Covering Theory

All your listed topics fall under this umbrella.

Now let’s sort them properly.

---

# 🔹 1️⃣ Matching

### Belongs to:

**Matching Theory**

Definition:  
A matching is a set of edges with no common vertices.

Now your subtopics:

• **Simplest matching**  
Usually means a matching with just one edge (basic definition stage).

• **Maximal matching**  
Cannot add more edges without breaking matching property.

• **Maximum matching**  
Largest possible matching in the graph.

• **Perfect matching**  
Matching that covers all vertices.

---

### Important Distinction

Maximal ≠ Maximum.

Maximal = locally largest.  
Maximum = globally largest.

Students mix this constantly. Don’t.

---

# 🔹 2️⃣ Covering (Line Covering)

“Line” here means **edge**.

So this is:

### Edge Cover

Definition:  
A set of edges such that every vertex is incident to at least one chosen edge.

Now your subtopics:

• **Line covering** → Edge cover  
• **Minimal line covering** → Cannot remove an edge without losing covering  
• **Minimum line covering** → Smallest possible edge cover  
• **Line covering number** → Size of minimum edge cover

---

### Where It Belongs:

Matching and Covering section.

Important relation in bipartite graphs:

Size of maximum matching + size of minimum edge cover = number of vertices.

Exam favorite.

---

# 🔹 3️⃣ Independent Line Set

This is just another name for:

👉 Matching.

Because edges that do not share vertices are independent.

So:

• **Maximal independent line set** = Maximal matching  
• **Maximum independent line set** = Maximum matching  
• **Line independent number** = Size of maximum matching

Belongs to:

Matching theory.

---

# 🔹 4️⃣ Vertex Covering
I assume you mean:

👉 Vertex Cover.

Definition:  
Set of vertices such that every edge has at least one endpoint in the set.

Subtopics:

• Minimal vertex cover → Cannot remove vertex  
• Minimum vertex cover → Smallest possible  
• Vertex covering number → Size of minimum vertex cover

---

### Where It Belongs:

Covering Theory (Vertex covering section)

Important theorem:

In bipartite graphs:

Maximum matching = Minimum vertex cover  
(Kőnig’s Theorem)

Extremely important.

---

# 🔹 5️⃣ Independent Vertex Set

Definition:  
Set of vertices with no edges between them.

Subtopics:

• Minimal independent set  
• Maximum independent set  
• Independence number α(G)

---

# 🔥 Key Relationships (Very Important for Exams)

1️⃣ Maximum matching ≤ Minimum vertex cover  
2️⃣ In bipartite graphs:

Maximum matching = Minimum vertex cover  
3️⃣ Maximum independent set + Minimum vertex cover = |V|  
4️⃣ Maximum matching + Minimum edge cover = |V|

These relationships are conceptual gold.

---

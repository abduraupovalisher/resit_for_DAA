# CS212 — RESIT EXAM CHEAT SHEET
### Design and Analysis of Algorithms
---

# ━━━ PART 1: SORTING ALGORITHMS ━━━

## All Algorithms at a Glance
```
Algorithm      │ Best      │ Worst     │ Stable │ In-place │ Technique
───────────────┼───────────┼───────────┼────────┼──────────┼────────────
Selection Sort │ O(n²)     │ O(n²)     │  ❌    │   ✅     │ Incremental
Bubble Sort    │ O(n)      │ O(n²)     │  ✅    │   ✅     │ Incremental
Insertion Sort │ O(n)      │ O(n²)     │  ✅    │   ✅     │ Incremental
Merge Sort     │ O(n log n)│ O(n log n)│  ✅    │   ❌     │ D&C
Heapsort       │ O(n log n)│ O(n log n)│  ❌    │   ✅     │ Heap
Quicksort(rand)│ O(n log n)│ O(n²)     │  ❌    │   ✅     │ D&C
Counting Sort  │ O(n+k)    │ O(n+k)    │  ✅    │   ❌     │ Counting
Radix Sort     │ O(d(n+k)) │ O(d(n+k)) │  ✅    │   ❌     │ Digit
Bucket Sort    │ O(n)      │ O(n²)     │  ✅    │   ❌     │ Distribution
```

## Key Facts
```
🔑 Selection Sort: ONLY algorithm where best=worst=O(n²), NOT stable
🔑 Heapsort: in-place + O(n log n) but NOT stable
🔑 Merge Sort: ONLY guaranteed O(n log n) + stable (but needs O(n) space)
🔑 Quicksort: expected O(n log n), worst O(n²) when pivot=min/max every time
🔑 Randomized Quicksort: O(n log n) expected for ANY input

Non-comparison sorts (beat Ω(n log n)):
  Counting Sort → integers in [0,k]
  Radix Sort    → d-digit numbers in base k
  Bucket Sort   → real numbers, uniform in [0,1)

Comparison Sort Lower Bound = Ω(n log n)
  Proof: Decision tree needs ≥ n! leaves → height ≥ log(n!) = Θ(n log n)
```

---

# ━━━ PART 2: RECURRENCES ━━━

## Master Theorem: T(n) = aT(n/b) + f(n)
```
Compute: n^(log_b a)

Case 1: f(n) = O(n^(log_b a − ε))  →  T(n) = Θ(n^(log_b a))
Case 2: f(n) = Θ(n^(log_b a))      →  T(n) = Θ(n^(log_b a) · log n)
Case 3: f(n) = Ω(n^(log_b a + ε))  →  T(n) = Θ(f(n))
```

## Must-Know Recurrences
```
T(n) = 2T(n/2) + n     → Θ(n log n)   [Merge Sort]
T(n) = T(n/2) + 1      → Θ(log n)     [Binary Search]
T(n) = T(n-1) + n      → Θ(n²)        [Insertion Sort worst]
T(n) = 4T(n/2) + n     → Θ(n²)        [Case 1]
T(n) = 3T(n/3) + n     → Θ(n log n)   [Case 2]
T(n) = 2T(n/4) + √n   → Θ(√n · log n) [Case 2]
```

---

# ━━━ PART 3: HEAP & HEAPSORT ━━━

```
Max-Heap property: A[parent(i)] ≥ A[i]
  parent(i)=⌊i/2⌋  left(i)=2i  right(i)=2i+1

Operations:
  MAX-HEAPIFY(A,i)  →  O(log n)   push node down
  BUILD-MAX-HEAP(A) →  O(n)       ← NOT O(n log n)!
  HEAPSORT(A)       →  Θ(n log n) ← BUILD + n×EXTRACT-MAX
  EXTRACT-MAX       →  O(log n)
  INSERT            →  O(log n)
```

---

# ━━━ PART 4: BFS & DFS ━━━

## BFS — Breadth First Search
```
Data structure: QUEUE (FIFO)
Gives: shortest distances d(v) by edge count
Time: Θ(V+E)
Colors: WHITE(unseen) → GRAY(in queue) → BLACK(done)

v.d = distance from s to v
v.π = parent in BFS tree
```

## DFS — Depth First Search
```
Data structure: STACK / recursion (LIFO)
Gives: discovery(d) and finish(f) times
Time: Θ(V+E)

Parenthesis theorem: intervals [u.d,u.f] either nested or disjoint
```

## 🔑 EDGE CLASSIFICATION (most tested!)
```
When exploring edge (u → v), look at color of v:

  v = WHITE          →  TREE EDGE
  v = GRAY           →  BACK EDGE  ← CYCLE!
  v = BLACK, u.d < v.d → FORWARD EDGE
  v = BLACK, u.d > v.d → CROSS EDGE

UNDIRECTED GRAPH: only TREE and BACK edges (no forward/cross!)
BACK EDGE found  → CYCLE EXISTS
No BACK EDGE     → Graph is a DAG
```

## Topological Sort
```
Method 1 (DFS): List vertices in DECREASING finish time
Method 2 (Kahn's): Repeatedly remove indegree-0 vertices
Time: Θ(V+E)
Only works on DAGs!
```

---

# ━━━ PART 5: SCC & BIPARTITENESS ━━━

## Strongly Connected Components
```
SCC = maximal set where every vertex can reach every other

Kosaraju's Algorithm (2 DFS passes):
  Step 1: DFS on G → record finish times f[v]
  Step 2: Build G^T (reverse ALL edges)
  Step 3: DFS on G^T in DECREASING f[v] order
  Step 4: Each DFS tree = one SCC
  Time: Θ(V+E)

G_SCC (component graph) is ALWAYS a DAG!
```

## Bipartiteness
```
Bipartite ⟺ 2-colorable ⟺ NO odd-length cycle

Test: BFS coloring — assign alternating colors
  If conflict found → NOT bipartite
  If no conflict   → IS bipartite (give the two partitions)

Trees are ALWAYS bipartite!
Even cycles: bipartite ✅
Odd cycles:  NOT bipartite ❌
```

---

# ━━━ PART 6: SHORTEST PATHS ━━━

## Algorithm Selection
```
┌─────────────────────────────┬──────────────────┬───────────────────┐
│  Situation                  │  Algorithm       │  Time             │
├─────────────────────────────┼──────────────────┼───────────────────┤
│  Unweighted (edge count)    │  BFS             │  Θ(V+E)           │
│  DAG (any weights)          │  DAG-SP          │  Θ(V+E)  ← FAST!  │
│  Non-negative, dense        │  Dijkstra(array) │  Θ(V²)            │
│  Non-negative, sparse       │  Dijkstra(heap)  │  O(E log V)       │
│  Negative weights, no cycle │  Bellman-Ford    │  Θ(V·E)           │
│  All-pairs, any weights     │  Floyd-Warshall  │  Θ(V³)            │
│  All-pairs, sparse+negative │  Johnson's       │  O(VE log V)      │
└─────────────────────────────┴──────────────────┴───────────────────┘

Array vs Heap Dijkstra:
  Array faster when: E ≥ V²/log V  (dense graphs)
  Heap faster when:  E < V²/log V  (sparse graphs)
```

## RELAX operation (used by ALL algorithms)
```
RELAX(u, v, w):
  if v.d > u.d + w(u,v):
      v.d = u.d + w(u,v)
      v.π = u
```

## Dijkstra (non-negative weights only!)
```
1. Initialize: s.d=0, all others=∞
2. EXTRACT-MIN from queue → vertex u
3. RELAX all outgoing edges of u
4. Repeat until queue empty

Why fails with negative weights:
  Once vertex u is finalized, its d[u] is NEVER updated again.
  A negative edge could create a shorter path to a finalized vertex.
  Dijkstra will miss this. → WRONG ANSWER
```

## Bellman-Ford (handles negative weights)
```
1. Initialize: s.d=0, all others=∞
2. Repeat V-1 times: relax EVERY edge
3. Extra pass: if any edge still relaxes → NEGATIVE CYCLE! (return FALSE)

Why V-1 passes: shortest path has ≤ V-1 edges
```

## Floyd-Warshall (all-pairs)
```
D^(0)[i,j] = w(i,j)   (direct edge weight, 0 on diagonal, ∞ if no edge)

D^(k)[i,j] = min( D^(k-1)[i,j],
                   D^(k-1)[i,k] + D^(k-1)[k,j] )

Run k=1 to n. Final answer: D^(n).
Time: Θ(n³)  Space: Θ(n²)
Negative cycle detected if D[i][i] < 0 after completion.
```

## Johnson's Algorithm
```
1. Add vertex s, connect s→v with w=0 for all v
2. Run Bellman-Ford from s → get h(v) = δ(s,v)
3. Reweight: ŵ(u,v) = w(u,v) + h(u) - h(v)   ← all ≥ 0!
4. Run Dijkstra from every vertex using ŵ
5. Recover: δ(u,v) = δ̂(u,v) + h(v) - h(u)

Why ŵ ≥ 0:  By triangle inequality: h(v) ≤ h(u)+w(u,v)
             → w(u,v)+h(u)-h(v) ≥ 0 ✅

Why paths preserved:  ŵ(path) = w(path) + h(start) - h(end)
                       h-terms telescope → same path is optimal ✅
```

---

# ━━━ PART 7: DYNAMIC PROGRAMMING ━━━

## Two Hallmarks of DP
```
1. OPTIMAL SUBSTRUCTURE — optimal solution contains optimal subproblem solutions
2. OVERLAPPING SUBPROBLEMS — same subproblems solved repeatedly

Memoization (top-down) vs Tabulation (bottom-up):
  Same asymptotic complexity, tabulation usually faster in practice.
```

## 5 Core Recurrences (MEMORIZE!)
```
① Weighted Interval Scheduling:
   OPT(0) = 0
   OPT(j) = max( v_j + OPT(p(j)),  OPT(j-1) )
   p(j) = largest i < j where interval i ends ≤ start of j
   Time: O(n log n)

② 0/1 Knapsack:
   OPT(i,w) = OPT(i-1,w)                         if w_i > w
   OPT(i,w) = max(OPT(i-1,w), v_i+OPT(i-1,w-w_i)) if w_i ≤ w
   Base: OPT(0,w)=0, OPT(i,0)=0
   Time: Θ(n·W) — PSEUDO-POLYNOMIAL

③ Rod Cutting:
   r[0] = 0
   r[n] = max{ p[i] + r[n-i] : 1 ≤ i ≤ n }
   Time: Θ(n²)

④ Matrix Chain Multiplication:
   m[i,i] = 0
   m[i,j] = min{ m[i,k]+m[k+1,j]+p_{i-1}·p_k·p_j : i≤k<j }
   Time: Θ(n³)

⑤ Floyd-Warshall:
   D^(k)[i,j] = min(D^(k-1)[i,j], D^(k-1)[i,k]+D^(k-1)[k,j])
   Time: Θ(n³)
```

## Traceback Template
```
Knapsack:
  if OPT[i][w] ≠ OPT[i-1][w] → item i TAKEN, go to OPT[i-1][w-w_i]
  else                         → item i NOT taken, go to OPT[i-1][w]

WIS:
  if v_j + OPT[p(j)] ≥ OPT[j-1] → interval j TAKEN, go to p(j)
  else                             → interval j NOT taken, go to j-1
```

---

# ━━━ PART 8: GREEDY ALGORITHMS ━━━

## Two Proof Techniques
```
1. GREEDY STAYS AHEAD — show greedy is ≥ as good after each step
2. EXCHANGE ARGUMENT  — show any optimal can be swapped toward greedy
                        without getting worse
```

## Interval Scheduling (maximize #intervals)
```
Rule: Always pick EARLIEST FINISHING TIME
  Sort by finish time → greedily pick compatible ones
  Time: O(n log n)

Why NOT earliest start?   [0,100],[1,2],[3,4] → picks [0,100] → 1 interval (wrong!)
Why NOT shortest duration? Can be shown to fail by counterexample
```

## Minimize Maximum Lateness (EDF)
```
lateness = max(0, finish - deadline)
Rule: Earliest Deadline First (EDF)
  Sort by deadline → schedule back-to-back
  Time: O(n log n)

Proof: Exchange argument
  Inversion = adjacent pair (i,j) where d_j < d_i but i before j
  Swapping inversion never increases max lateness → EDF optimal
```

## Coin Change — Greedy FAILS!
```
Coins {1,4,6}, n=8:
  Greedy: 6+1+1 = 3 coins
  Optimal: 4+4  = 2 coins ← GREEDY FAILS!

Use DP for optimal coin change.
Greedy works for US coins {1,5,10,25} but NOT general denominations.
```

## Minimum Spanning Tree
```
Kruskal:  Sort edges by weight, add if no cycle (Union-Find)
          Time: O(E log E) = O(E log V)
          Better for SPARSE graphs

Prim:     Grow from root, always add minimum-weight crossing edge
          Time: O((V+E) log V) with heap, O(V²) with array
          Better for DENSE graphs

Both produce MST with V-1 edges.
```

---

# ━━━ PART 9: QUICK REFERENCE TABLES ━━━

## SSSP (Single Source)
```
BFS             Θ(V+E)      Unweighted only
DAG-SP          Θ(V+E)      DAG, ANY weights ← fastest!
Dijkstra(array) Θ(V²)       Non-negative, dense
Dijkstra(heap)  O(E log V)  Non-negative, sparse
Bellman-Ford    Θ(V·E)      Negative weights OK
```

## APSP (All Pairs)
```
Floyd-Warshall  Θ(V³)       Any weights, simple
Johnson's       O(VE log V) Sparse + negative → beats FW
n × Dijkstra    O(VE log V) Non-negative, sparse
```

## DP Complexity
```
Weighted IS     O(n log n)
0/1 Knapsack    Θ(n·W)       pseudo-polynomial!
Rod Cutting     Θ(n²)
Matrix Chain    Θ(n³)
```

---

# ━━━ PART 10: ⚠️ EXAM TRAPS ━━━

```
❌ Dijkstra → needs NON-NEGATIVE weights (not "directed" or "DAG"!)
❌ Floyd-Warshall → Θ(n³) NOT Θ(n²)
❌ Topological sort → only for DAGs, NOT all directed graphs
❌ Bipartite ≠ no cycle → bipartite means no ODD cycle
❌ Kosaraju = exactly 2 DFS (not 1, not 3)
❌ BFS uses QUEUE(FIFO), DFS uses STACK(LIFO) — never mix!
❌ Interval Scheduling = earliest FINISH time (not start, not shortest)
❌ Greedy coin change FAILS for arbitrary denominations
❌ BUILD-MAX-HEAP = O(n), NOT O(n log n)
❌ GRAY vertex in DFS = BACK EDGE (not cross!)
❌ Undirected DFS: ONLY tree + back edges (no forward, no cross!)
❌ BACK EDGE = CYCLE (not forward or cross!)
❌ DAG-SP handles NEGATIVE weights — don't say it needs non-negative
❌ Selection Sort NOT stable — even if all elements are distinct
❌ Pseudo-polynomial: Θ(nW) is exponential in bit-length of W
❌ SCC component graph is ALWAYS a DAG (even if G has cycles)
```

---

# ━━━ PART 11: HAND-TRACE CHECKLISTS ━━━

## DFS Trace Checklist
```
□ Start from given vertex, visit neighbors in given order
□ Record d[v] when first visited (GRAY)
□ Record f[v] when all neighbors done (BLACK)
□ For each edge (u→v), check v's COLOR at that moment
□ If BLACK: compare u.d with v.d to distinguish forward/cross
□ Any BACK edge? → state "cycle exists"
□ No BACK edge?  → state "graph is a DAG"
```

## Dijkstra Trace Checklist
```
□ Initialize: s.d=0, all others=∞
□ Each step: EXTRACT-MIN (lowest d[v] in queue)
□ For each neighbor: check if new path is shorter
□ Update d[v] and π[v] if shorter found
□ Mark extracted vertex as FINALIZED (won't change)
□ Final: report d[v] and π[v] for all vertices
□ Reconstruct paths using π pointers
```

## Floyd-Warshall Trace Checklist
```
□ Build D^(0): direct edges (0 diagonal, ∞ if no edge)
□ For k=1,2,...: check every (i,j) pair
□ Update D[i][j] = min(D[i][j], D[i][k]+D[k][j])
□ Only update if D[i][k]+D[k][j] is STRICTLY SMALLER
□ Show which cells changed at each k step
```

## Knapsack Trace Checklist
```
□ Build table: rows = items (0 to n), cols = weight (0 to W)
□ Row 0: all zeros
□ Each row i: copy row i-1, then check if taking item i helps
□ OPT[i][w] = max(OPT[i-1][w], v_i + OPT[i-1][w-w_i]) if w≥w_i
□ Traceback: start at OPT[n][W], compare with OPT[i-1][w]
□ Verify: selected items' weight ≤ W, values sum correctly
```

---

*Good luck on your resit exam! Trust the algorithms.* 🎯

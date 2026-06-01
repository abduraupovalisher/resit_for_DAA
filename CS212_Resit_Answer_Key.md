# CS212 — Design and Analysis of Algorithms
## RESIT EXAM — COMPLETE ANSWER KEY
### (Instructor Use Only)

---

## PART 1 — MCQ Answer Key (30 points)

| Q | Answer | Key Reasoning |
|---|--------|---------------|
| 1 | **C** | Insertion Sort worst case = O(n²) — reverse-sorted input |
| 2 | **C** | Merge Sort (stable, comparison) + Insertion Sort (stable, comparison). Heapsort is NOT stable. Counting Sort is NOT comparison-based. |
| 3 | **C** | a=4, b=2 → n^(log₂4) = n². f(n)=n = O(n^(2−ε)) → Case 1 → T(n) = Θ(n²) |
| 4 | **C** | Heapsort: O(n log n) worst case, in-place (O(1) extra space), NOT stable, NOT divide-and-conquer |
| 5 | **C** | BUILD-MAX-HEAP = O(n) — tighter analysis using geometric series |
| 6 | **C** | Randomized Quicksort = O(n log n) expected |
| 7 | **D** | Counting Sort does NOT compare elements — it counts frequencies |
| 8 | **D** | Counting Sort: O(n+k). If k=100, this is O(n). |
| 9 | **D** | GRAY vertex = currently being processed = ancestor → back edge |
| 10 | **C** | Topological ordering ↔ DAG (no cycles) |
| 11 | **D** | Bipartite ↔ 2-colorable ↔ no odd-length cycle |
| 12 | **C** | Dijkstra's invariant (greedy finalization) breaks with negative edges |
| 13 | **D** | Floyd-Warshall: 3 nested loops over n vertices = Θ(n³) |
| 14 | **C** | Earliest Finish Time — proven optimal via "Greedy Stays Ahead" |
| 15 | **C** | DP requires: (1) optimal substructure + (2) overlapping subproblems |

---

## PART 2 — Short Answer Answer Key (60 points)

---

### Q1 Answer — Sorting Algorithm Analysis (10 pts)

**(a)** [4 pts] — 0.5 pts per cell:

| Algorithm | Worst-Case Time | Best-Case Time | Stable? | In-Place? |
|-----------|----------------|----------------|---------|-----------|
| Insertion Sort | O(n²) | O(n) | ✅ Yes | ✅ Yes |
| Merge Sort | O(n log n) | O(n log n) | ✅ Yes | ❌ No (O(n) space) |
| Heapsort | O(n log n) | O(n log n) | ❌ No | ✅ Yes |
| Quicksort (random pivot) | O(n²) | O(n log n) | ❌ No | ✅ Yes (O(log n) stack) |

**(b)** [3 pts] Decision Tree argument:

A comparison-based sort can be modeled as a **binary decision tree** where each internal node represents a comparison (a[i] ≤ a[j]?) and each leaf represents one of the n! possible permutations of the input.

- The tree must have **at least n! leaves** (one for each possible input ordering).
- A binary tree of height h has **at most 2^h leaves**.
- Therefore: 2^h ≥ n! → h ≥ log₂(n!)
- By Stirling's approximation: log₂(n!) = Θ(n log n)
- Since h is the worst-case number of comparisons, **any comparison sort needs Ω(n log n) comparisons** in the worst case.

**(c)** [3 pts]

Use **Counting Sort**:
- Since all integers are in [1, 100], set k = 100.
- Time complexity: **O(n + k) = O(n + 100) = O(n)**.
- This beats comparison-based sorts because we exploit the known integer range — we don't need to compare elements, just count their frequencies.
- It is also **stable**.

*Deduct 1 pt if student says Radix Sort without justification. Accept Radix Sort with correct reasoning.*

---

### Q2 Answer — Recurrences (10 pts)

**(a)** [4 pts — 2 pts each]

**(i)** T(n) = 2T(n/4) + √n
- a = 2, b = 4, f(n) = n^(1/2)
- n^(log_b a) = n^(log₄ 2) = n^(1/2)
- f(n) = Θ(n^(1/2)) = Θ(n^(log_b a)) → **Case 2** applies
- **T(n) = Θ(n^(1/2) · log n) = Θ(√n · log n)**

**(ii)** T(n) = 3T(n/3) + n
- a = 3, b = 3, f(n) = n
- n^(log_b a) = n^(log₃ 3) = n^1 = n
- f(n) = Θ(n) = Θ(n^(log_b a)) → **Case 2** applies
- **T(n) = Θ(n log n)**

**(b)** [3 pts] Merge Sort recurrence: **T(n) = 2T(n/2) + cn**

Recursion Tree:
```
Level 0:        cn                           = cn
Level 1:    cn/2 + cn/2                      = cn
Level 2:  cn/4+cn/4+cn/4+cn/4               = cn
...
Level k:  (2^k)(cn/2^k)                      = cn
...
Level log₂n:  n leaves each cost Θ(1)        = Θ(n)
```
- There are log₂(n) + 1 levels.
- Cost per level = cn (except last level = Θ(n)).
- **Total = cn · log n + Θ(n) = Θ(n log n)**

**(c)** [3 pts] T(n) = T(n−1) + n, T(1) = 1

**Guess:** T(n) = Θ(n²). More precisely, T(n) = n(n+1)/2.

**Proof by substitution (induction):**
- Base case: T(1) = 1 = 1(2)/2 = 1 ✓
- Inductive step: Assume T(k) = k(k+1)/2 for all k < n.
  - T(n) = T(n−1) + n = (n−1)n/2 + n = n(n−1)/2 + 2n/2 = n(n+1)/2 ✓
- Therefore T(n) = n(n+1)/2 = **Θ(n²)**

---

### Q3 Answer — BFS and DFS (10 pts)

Graph edges: 1→2, 1→3, 2→4, 2→5, 3→5, 4→6, 5→4, 6→3

**(a)** [5 pts] DFS from vertex 1 (children visited in increasing order):

```
Visit 1 (d=1)
  → Visit 2 (d=2)
      → Visit 4 (d=3)
          → Visit 6 (d=4)
              → Visit 3 (d=5)
                  → Visit 5 (d=6)
                      → edge 5→4: 4 is BLACK, 5.d=6 > 4.d=3 → CROSS edge
                      Finish 5 (f=7)
                  Finish 3 (f=8)
              Finish 6 (f=9)
          Finish 4 (f=10)
      → edge 2→5: 5 is BLACK, 2.d=2 < 5.d=6 → FORWARD edge
      Finish 2 (f=11)
  → edge 1→3: 3 is BLACK, 1.d=1 < 3.d=5 → FORWARD edge
  Finish 1 (f=12)
```

**Discovery/Finish Times:**
| Vertex | d | f |
|--------|---|---|
| 1 | 1 | 12 |
| 2 | 2 | 11 |
| 3 | 5 | 8 |
| 4 | 3 | 10 |
| 5 | 6 | 7 |
| 6 | 4 | 9 |

**Edge Classification:**
| Edge | Type |
|------|------|
| 1→2 | Tree |
| 1→3 | Forward |
| 2→4 | Tree |
| 2→5 | Forward |
| 3→5 | Tree |
| 4→6 | Tree |
| 5→4 | Cross |
| 6→3 | Tree |

**(b)** [3 pts]

The DFS found **no back edges**. Since a directed graph has a cycle **if and only if** DFS produces at least one back edge (a back edge (u,v) means v is an ancestor of u, completing a cycle), and we found none, **this graph has no cycle**.

*(Award full credit only if student correctly links "no back edge ↔ no cycle")*

**(c)** [2 pts]

Since the graph is a **DAG** (no cycles), a topological sort **IS possible**. We can obtain one by listing vertices in **decreasing finish time** from the DFS:
> 1, 2, 4, 6, 3, 5

*(Verify: every edge goes from left to right in this order.)*

---

### Q4 Answer — SCCs & Bipartiteness (10 pts)

Graph edges: 1→2, 2→3, 3→1, 2→4, 4→5, 5→2, 5→6

**(a)** [5 pts] Kosaraju's Algorithm:

**Step 1: DFS on G, compute finishing times**

DFS from 1 (visiting in increasing order):
```
Visit 1(d=1) → 2(d=2) → 3(d=3) → 1 is GRAY → back edge
  Finish 3(f=4)
  → 4(d=5) → 5(d=6) → 2 is GRAY → back edge
    → 6(d=7) Finish 6(f=8)
    Finish 5(f=9)
  Finish 4(f=10)
  Finish 2(f=11)
Finish 1(f=12)
```

Finishing order (increasing): 3, 6, 5, 4, 2, 1
**Decreasing finishing order: 1, 2, 4, 5, 6, 3**

**Step 2: Transpose G^T** (reverse all edges):
```
2→1, 3→2, 1→3, 4→2, 5→4, 2→5, 6→5
```

**Step 3: DFS on G^T in decreasing finish order (1, 2, 4, 5, 6, 3)**

- Start DFS from 1: can reach 3 (via 1→3), then 2 (via 3→2), then 5 (via 2→5), then 4 (via 5→4). **SCC 1 = {1, 2, 3, 4, 5}?**

Wait — let's be careful:
- From 1 in G^T: 1→3, 3→2, 2→1 (cycle), 2→5, 5→4, 4→2 (cycle). 6→5 but not reachable from 1 in G^T.

Actually re-examining: **{1,2,3}** are mutually reachable in G (1→2→3→1). **{2,4,5}** — 2→4→5→2, also a cycle. But 1→2 and 3→1 means 1 is in the {1,2,3} SCC. 2→4→5→2 means {2,4,5} form an SCC, but 2 is already in {1,2,3}.

Let me trace carefully:
- Original G: 1→2→3→1 (cycle) so {1,2,3} ⊆ one SCC
- 2→4→5→2 (cycle via G: 4→5→2) so {2,4,5} ⊆ one SCC
- Since 2 is in both, **{1,2,3,4,5}** is one SCC
- Vertex 6: 5→6 but there is no path from 6 back to 5 (6 has no outgoing edges in G). **SCC: {6}**

**Final SCCs: {1, 2, 3, 4, 5} and {6}**

*(Accept: 2 SCCs — award 4/5 if student correctly identifies the two groups but has minor error in Kosaraju steps. Award 3/5 if SCCs are right but no Kosaraju steps shown.)*

**(b)** [3 pts] Undirected edges: {1,2}, {2,3}, {3,4}, {4,5}, {5,2}

Attempt 2-coloring starting from vertex 1:
```
Color 1 = WHITE
Neighbor 2 → Color 2 = BLACK
Neighbor 3 (of 2) → Color 3 = WHITE
Neighbor 4 (of 3) → Color 4 = BLACK
Neighbor 5 (of 4) → Color 5 = WHITE
Check edge {5,2}: Color 5 = WHITE, Color 2 = BLACK → DIFFERENT ✓ ... wait
```

Check the cycle 2→3→4→5→2:
- This cycle has **4 edges** (even length) → bipartite test passes for this cycle.

But wait — we must check ALL edges. All edges check out with the coloring:
- {1,2}: W–B ✓
- {2,3}: B–W ✓
- {3,4}: W–B ✓
- {4,5}: B–W ✓
- {5,2}: W–B ✓

**The graph IS bipartite.**
- Partition X = {1, 3, 5}, Y = {2, 4}

**(c)** [2 pts]

An undirected graph G is bipartite **if and only if G contains no odd-length cycle**.

*(Also accept: "if and only if G is 2-colorable")*

---

### Q5 Answer — Shortest Paths (10 pts)

Graph: S→A(6), S→B(3), B→A(2), A→C(1), B→C(5), B→D(4), C→D(2), A→D(7)

**(a)** [5 pts] Dijkstra from S:

**Initial:** d(S)=0, d(A)=∞, d(B)=∞, d(C)=∞, d(D)=∞. Queue={S,A,B,C,D}

**Step 1: Extract S (d=0)**
- Relax S→A(6): d(A)=6, π(A)=S
- Relax S→B(3): d(B)=3, π(B)=S
- Table: S=0✓, A=6, B=3, C=∞, D=∞

**Step 2: Extract B (d=3)**
- Relax B→A(2): d(A) = min(6, 3+2) = 5. Update: d(A)=5, π(A)=B
- Relax B→C(5): d(C)=3+5=8, π(C)=B
- Relax B→D(4): d(D)=3+4=7, π(D)=B
- Table: S=0✓, B=3✓, A=5, C=8, D=7

**Step 3: Extract A (d=5)**
- Relax A→C(1): d(C) = min(8, 5+1) = 6. Update: d(C)=6, π(C)=A
- Relax A→D(7): d(D) = min(7, 5+7) = 7. No update.
- Table: S=0✓, B=3✓, A=5✓, C=6, D=7

**Step 4: Extract C (d=6)**
- Relax C→D(2): d(D) = min(7, 6+2) = 7. No update (tie).
- Table: S=0✓, B=3✓, A=5✓, C=6✓, D=7

**Step 5: Extract D (d=7)**
- No outgoing edges from D.
- **Done.**

**Final Result:**
| Vertex | δ(S,v) | π(v) | Path |
|--------|--------|------|------|
| S | 0 | NIL | S |
| A | 5 | B | S→B→A |
| B | 3 | S | S→B |
| C | 6 | A | S→B→A→C |
| D | 7 | B | S→B→D |

**(b)** [3 pts]

With S→A = −2, the true shortest distances are:
- δ(S,A) = −2 (direct edge S→A)
- δ(S,B) = 3
- δ(S,C) = −2+1 = −1 (path S→A→C)
- δ(S,D) = −2+1+2 = 1 (path S→A→C→D)

**What Dijkstra computes:**
- It extracts S first, sets d(A)=−2, d(B)=3.
- Next it extracts A (d=−2, smallest). Sets d(C)=−1, d(D)=5.
- Extracts C (d=−1). Sets d(D)=min(5,1)=1.
- Extracts B (d=3). Tries B→A: d(A)=min(−2, 3+2)=−2, no change. But A is already finalized!

Actually in this case Dijkstra may or may not give a wrong answer depending on implementation. The issue: **Dijkstra's correctness proof breaks** because with negative edges, a vertex finalized early may later receive a shorter path. Specifically:

Dijkstra extracts B last (d=3) and tries B→A: since A is already in S with d=−2, it is never re-relaxed. If instead S→B=−5 and B has outgoing edges to already-finalized vertices, Dijkstra gives wrong answers. 

**Clear counterexample within this graph:** If we trace carefully here, Dijkstra actually gives correct answers for this particular instance. For full credit, students should explain the *general* reason:

> Dijkstra's invariant states that once a vertex u is extracted (added to S), u.d = δ(S,u) is finalized and never updated. A negative-weight edge can create a shorter path to a vertex already in S, which Dijkstra will never revisit. This violates the invariant.

*(Award 2/3 if student gives correct explanation without specific counterexample. Award 1/3 for mentioning "negative edges break Dijkstra" with no further reasoning.)*

**(c)** [2 pts]

Use **Bellman-Ford**:
- Time complexity: **Θ(V · E)** = Θ(n · m)
- It handles negative edge weights (as long as there are no negative-weight cycles reachable from S)

---

### Q6 Answer — Dynamic Programming (10 pts)

**(a)** [5 pts] 0/1 Knapsack, W=6, items: (w=1,v=2), (w=3,v=5), (w=4,v=8), (w=5,v=9)

**DP Table OPT[i][w]:**

|  | w=0 | w=1 | w=2 | w=3 | w=4 | w=5 | w=6 |
|--|-----|-----|-----|-----|-----|-----|-----|
| i=0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| i=1 (w=1,v=2) | 0 | 2 | 2 | 2 | 2 | 2 | 2 |
| i=2 (w=3,v=5) | 0 | 2 | 2 | 5 | 7 | 7 | 7 |
| i=3 (w=4,v=8) | 0 | 2 | 2 | 5 | 8 | 10 | 10 |
| i=4 (w=5,v=9) | 0 | 2 | 2 | 5 | 8 | 10 | 11 |

**Key computations:**
- OPT[2][4] = max(OPT[1][4], 5+OPT[1][1]) = max(2, 5+2) = 7
- OPT[3][5] = max(OPT[2][5], 8+OPT[2][1]) = max(7, 8+2) = 10
- OPT[4][6] = max(OPT[3][6], 9+OPT[3][1]) = max(10, 9+2) = 11

**Maximum value = 11**

**Traceback:**
- OPT[4][6]=11 > OPT[3][6]=10 → **Item 4 taken** (w=5,v=9). Recurse on (3, 6−5)=(3,1).
- OPT[3][1]=2 = OPT[2][1]=2 → Item 3 NOT taken. Recurse on (2,1).
- OPT[2][1]=2 = OPT[1][1]=2 → Item 2 NOT taken. Recurse on (1,1).
- OPT[1][1]=2 > OPT[0][1]=0 → **Item 1 taken** (w=1,v=2).

**Selected items: {1, 4} — total weight = 1+5 = 6 ✓, total value = 2+9 = 11 ✓**

**(b)** [3 pts] dp[n] = 3·dp[n−1] − dp[n−2], dp[0]=0, dp[1]=1:

| n | dp[n] |
|---|-------|
| 0 | 0 |
| 1 | 1 |
| 2 | 3(1) − 0 = **3** |
| 3 | 3(3) − 1 = **8** |
| 4 | 3(8) − 3 = **21** |
| 5 | 3(21) − 8 = **55** |
| 6 | 3(55) − 21 = **144** |

**dp[6] = 144**

*(Interesting: these are Fibonacci numbers — F(12)=144!)*

**(c)** [2 pts]

1. **Optimal Substructure**: An optimal solution to the problem contains optimal solutions to its subproblems. (If you remove one element from an optimal solution, what remains is still optimal for the reduced subproblem.)

2. **Overlapping Subproblems**: The recursive algorithm revisits the same subproblems many times. (Unlike Divide-and-Conquer, the subproblems are not independent — they share sub-subproblems, making memoization or tabulation worthwhile.)

---

## PART 3 — Algorithm Design Answer Key (10 pts)

### Q7 Answer — EDF Greedy (10 pts)

**(a)** [2 pts] Schedule A→B→C→D:

| Task | t | d | Start | Finish | Lateness |
|------|---|---|-------|--------|----------|
| A | 3 | 6 | 0 | 3 | max(0, 3−6) = 0 |
| B | 2 | 4 | 3 | 5 | max(0, 5−4) = **1** |
| C | 1 | 3 | 5 | 6 | max(0, 6−3) = **3** |
| D | 4 | 10 | 6 | 10 | max(0, 10−10) = 0 |

**Maximum lateness L = 3**

**(b)** [3 pts] EDF Algorithm:

> Sort all tasks by deadline in non-decreasing order. Schedule them back-to-back in that order.

Sort by deadline: C(d=3), B(d=4), A(d=6), D(d=10)

Schedule: **C → B → A → D**

| Task | t | d | Start | Finish | Lateness |
|------|---|---|-------|--------|----------|
| C | 1 | 3 | 0 | 1 | max(0, 1−3) = 0 |
| B | 2 | 4 | 1 | 3 | max(0, 3−4) = 0 |
| A | 3 | 6 | 3 | 6 | max(0, 6−6) = 0 |
| D | 4 | 10 | 6 | 10 | max(0, 10−10) = 0 |

**Maximum lateness L = 0** (EDF achieves perfect scheduling here!)

**(c)** [3 pts] Exchange Argument:

**Definition of inversion:** A schedule has an *inversion* if task i is scheduled immediately before task j, but d_j < d_i (i.e., j has an earlier deadline but comes later).

**Claim:** Swapping an inverted pair (i before j, but d_j < d_i) → (j before i) does **not increase** the maximum lateness.

**Proof:**
- In the original schedule: i finishes at time f, j finishes at time f + t_j.
  - l_i = f − d_i
  - l_j = (f + t_j) − d_j
- After swapping: j finishes at f − t_i + t_j... no wait, let both tasks start at time s.
  - Original: i finishes at s+t_i, j finishes at s+t_i+t_j
  - Swapped: j finishes at s+t_j, i finishes at s+t_j+t_i
  - Note: i finishes at the same time in both: **s+t_i+t_j**
  - Only j's finish time changes (earlier in swapped).
- In original: l_j = (s + t_i + t_j) − d_j
- In swapped: l_j = (s + t_j) − d_j (j finishes earlier → l_j decreases or stays same)
- In original: l_i = (s + t_i) − d_i  
- In swapped: l_i = (s + t_i + t_j) − d_i (i finishes later)
  - But since d_i > d_j, and the new l_i = (s+t_i+t_j)−d_i < (s+t_i+t_j)−d_j = original l_j
  - So the new max lateness ≤ old max lateness. ✓

**Conclusion:** We can swap any inversion without increasing maximum lateness. Repeating this process (like bubble sort), we eliminate all inversions and converge to EDF order. Therefore EDF is optimal.

**(d)** [2 pts]

- **Sorting step**: O(n log n) — sort n tasks by deadline
- **Scheduling step**: O(n) — assign back-to-back slots in order
- **Total time complexity: O(n log n)**

The sorting dominates. Once sorted, we simply compute cumulative finish times in O(n).

---

## GRADING SUMMARY

| Part | Max | Notes |
|------|-----|-------|
| Part 1 MCQ | 30 | 2 pts each, no partial credit |
| Q1 Sorting | 10 | 0.5 per cell in table (a); partial credit for (b)(c) |
| Q2 Recurrences | 10 | 2 pts each in (a); show work for (b)(c) |
| Q3 BFS/DFS | 10 | -0.5 per wrong edge classification; -1 per wrong d/f time |
| Q4 SCC/Bipartite | 10 | Show Kosaraju steps; accept correct SCCs for 3/5 in (a) |
| Q5 Shortest Paths | 10 | Show table updates; -1 per missing step |
| Q6 DP | 10 | Full table required for (a); show traceback |
| Q7 Algorithm Design | 10 | Partial credit for correct EDF table without proof |
| **TOTAL** | **100** | Passing grade: 40 |

---

## COMMON MISTAKES TO WATCH FOR

1. **Q3**: Students may confuse cross and forward edges. Remember:
   - Forward: (u,v) where v is a **descendant** of u (v.d > u.d, both in same DFS tree)
   - Cross: everything else (v already finished, different subtree)

2. **Q4**: SCC graph is always a DAG — students sometimes miss this.

3. **Q5**: Dijkstra trace — ensure students show the priority queue state after EACH extract, not just final answer.

4. **Q6**: Traceback must go from OPT[n][W] back to OPT[0][0] — not just state the answer.

5. **Q7**: Exchange argument — must define "inversion" clearly and show lateness does not increase after swap.

---

*Answer Key prepared for CS212 Resit Exam*
*Dr. Bugra Caskurlu — School of Computing, New Uzbekistan University*

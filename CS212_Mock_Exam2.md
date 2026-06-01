# CS212 — Design and Analysis of Algorithms
## MOCK EXAM 2 — RESIT PREPARATION

| Course | CS212 — Design and Analysis of Algorithms |
|--------|------------------------------------------|
| Duration | 120 minutes |
| Total | 100 points · Passing: 40 |
| Format | 15 MCQ (30 pts) + 14 Short Answer (70 pts) |
| Materials | **None permitted** |

> **Strategy:** ~1 min per MCQ · ~5 min per short answer

---

# PART 1 — MULTIPLE CHOICE (30 points)


**Q1.** Which sorting algorithm has **O(n)** best-case time and is **stable** and **in-place**?
- A. Heapsort
- B. Merge Sort
- C. Selection Sort
- D. Insertion Sort

**Answer: ____**

---

**Q2.** What is the time complexity of `BUILD-MAX-HEAP` on an array of n elements?
- A. O(n log n)
- B. O(n)
- C. O(log n)
- D. O(n²)

**Answer: ____**

---

**Q3.** Solve T(n) = 3T(n/3) + n using the Master Theorem:
- A. Θ(n)
- B. Θ(n log n)
- C. Θ(n²)
- D. Θ(log n)

**Answer: ____**

---

**Q4.** Which of the following sorting algorithms is **NOT stable**?
- A. Insertion Sort
- B. Merge Sort
- C. Counting Sort
- D. Heapsort

**Answer: ____**

---

**Q5.** Randomized Quicksort has which expected running time?
- A. O(n²) in all cases
- B. Θ(n log n) expected for any input
- C. Θ(n) expected
- D. O(n log² n) expected

**Answer: ____**

---

**Q6.** In DFS of a directed graph, edge (u,v) where v is **BLACK** and **u.d > v.d** is:
- A. Tree edge
- B. Back edge
- C. Forward edge
- D. Cross edge

**Answer: ____**

---

**Q7.** Which statement about BFS is TRUE?
- A. BFS uses a stack (LIFO)
- B. BFS finds shortest paths in weighted graphs
- C. BFS finds shortest paths by number of edges
- D. BFS runs in O(V²) always

**Answer: ____**

---

**Q8.** A directed graph has a cycle if and only if DFS finds:
- A. A forward edge
- B. A cross edge
- C. A back edge
- D. More tree edges than vertices

**Answer: ____**

---

**Q9.** Which algorithm runs in Θ(V+E) and correctly handles **negative edge weights**?
- A. Dijkstra (binary heap)
- B. Bellman-Ford
- C. DAG Shortest Path (topological sort + relax)
- D. Floyd-Warshall

**Answer: ____**

---

**Q10.** In 0/1 Knapsack DP, OPT(i, w) = OPT(i-1, w) when:
- A. v_i > w
- B. w_i > w  ← item weight exceeds current capacity
- C. OPT(i-1, w) = 0
- D. i = 0

**Answer: ____**

---

**Q11.** The Weighted Interval Scheduling recurrence is:
- A. OPT(j) = max(v_j + OPT(j-1), OPT(j-2))
- B. OPT(j) = max(v_j + OPT(p(j)), OPT(j-1))
- C. OPT(j) = v_j + OPT(p(j))
- D. OPT(j) = OPT(j-1) + OPT(j-2)

**Answer: ____**

---

**Q12.** Johnson's algorithm is preferred over Floyd-Warshall when:
- A. The graph has negative cycles
- B. The graph is dense (m close to V²)
- C. The graph is sparse and has negative weights
- D. The graph is undirected

**Answer: ____**

---

**Q13.** In the Earliest Deadline First (EDF) algorithm, what is being minimized?
- A. Total completion time
- B. Number of late jobs
- C. Maximum lateness
- D. Average waiting time

**Answer: ____**

---

**Q14.** Counting Sort requires which condition on the input?
- A. Input must be floating point numbers
- B. Input must be integers in a known range [0, k]
- C. Input must be already partially sorted
- D. Input must have no duplicate values

**Answer: ____**

---

**Q15.** Which of the following is TRUE about Kosaraju's algorithm?
- A. It uses 3 DFS passes
- B. The second DFS runs on the original graph G
- C. Vertices are processed in decreasing finish-time order in the second DFS on G^T
- D. It finds shortest paths in directed graphs

**Answer: ____**

---


# PART 2 — SHORT ANSWER (70 points)
*5 points each. Show ALL work.*

---

**Q16.** *(5 pts)*

Recurrence: **dp[n] = 2·dp[n-1] + dp[n-2]**, base cases dp[0]=1, dp[1]=2

Compute **dp[5]**. Show every intermediate value.

---

**Q17.** *(5 pts)*

0/1 Knapsack, capacity **W=5**, items:
```
Item 1: weight=1, value=2
Item 2: weight=2, value=6
Item 3: weight=3, value=9
Item 4: weight=4, value=7
```
Build the complete DP table. What is the maximum value?
Which items are selected? Show your full traceback.

---

**Q18.** *(5 pts)*

Directed graph: **1→2, 2→3, 3→4, 4→2, 1→4, 3→5**

Run DFS from vertex **1** (visit neighbors in increasing order).
- Record **d** and **f** for every vertex
- Classify every edge as: Tree / Back / Forward / Cross

---

**Q19.** *(5 pts)*

Undirected graph: **1—2, 1—3, 2—4, 3—4, 4—5, 3—5**

Run BFS from vertex **1** (neighbors in increasing order).
- Report **d(v)** from vertex 1 to every vertex
- List all **tree edges**

---

**Q20.** *(5 pts)*

DAG edges: **1→2, 2→4, 1→3, 3→4, 4→5, 4→6**

How many valid topological orderings exist? List them all.

---

**Q21.** *(5 pts)*

Directed graph: **1→2, 2→1, 2→3, 3→4, 4→5, 5→3, 5→6, 6→7, 7→6**

How many SCCs? List vertices in each SCC.

---

**Q22.** *(5 pts)*

Run Dijkstra from **S**:
```
S→A(5), S→B(1), B→A(2), B→C(4),
A→C(1), A→D(6), C→D(3)
```
Show each EXTRACT-MIN step. Report final **δ(S,v)** and **π(v)** for all vertices.

---

**Q23.** *(5 pts)*

Graph: **S→A(1), S→B(4), A→B(−3)**

**(a)** What is the correct δ(S,B)?

**(b)** Trace Dijkstra step by step on this graph. What does it compute for δ(S,B)?

**(c)** Which algorithm should be used instead, and why?

---

**Q24.** *(5 pts)*

4-vertex graph with weights:
```
w(1,2)=2,  w(2,3)=3,  w(3,1)=−4,
w(1,3)=6,  w(2,4)=5,  w(3,4)=1
```
Compute **D^(0)**, **D^(1)**, and **D^(2)** for Floyd-Warshall.
Show exactly which cells are updated at each step.

---

**Q25.** *(5 pts)*

You have a graph with **V=1000 vertices** and **E=400,000 edges**.

**(a)** Which is faster for Dijkstra: array or binary heap? Show the calculation.

**(b)** Is this graph sparse or dense? Justify.

---

**Q26.** *(5 pts)*

Coins: **{1, 3, 4}**, make change for **n=6**.

**(a)** Trace the greedy algorithm (largest coin first). How many coins?

**(b)** Is this optimal? If not, give the optimal solution.

**(c)** What algorithm finds the optimal solution for ANY coin set?

---

**Q27.** *(5 pts)*

5 jobs with (processing time, deadline):
```
J1=(4, 4),  J2=(1, 2),  J3=(3, 8),
J4=(2, 6),  J5=(2, 12)
```
**(a)** Apply EDF. Show the schedule with start/finish times and lateness of each job.

**(b)** What is the maximum lateness?

**(c)** Is there any schedule with lower maximum lateness? Why or why not?

---

**Q28.** *(5 pts)*

7 intervals (start, finish):
```
I1=(0,3), I2=(1,5), I3=(2,4),
I4=(4,7), I5=(5,8), I6=(6,9), I7=(3,6)
```
Apply the **greedy interval scheduling** algorithm.
- Sort intervals and show the sorted order
- Show each selection/rejection decision
- Report the maximum-size non-overlapping set

---

**Q29.** *(5 pts)*

Bellman-Ford on this graph from source **S**:
```
S→A(6),  S→B(7),  A→C(−3),  B→A(−2),  C→B(4)
```
**(a)** Run **2 passes** of Bellman-Ford. Show the distance table after each pass.

**(b)** Does this graph contain a negative-weight cycle reachable from S? How do you check?

---

# ✅ ANSWER KEY

## Part 1 — MCQ Answers

```
Q1:  D    Q2:  B    Q3:  B    Q4:  D    Q5:  B
Q6:  D    Q7:  C    Q8:  C    Q9:  C    Q10: B
Q11: B    Q12: C    Q13: C    Q14: B    Q15: C
```

### MCQ Explanations:


```
Q1:  D — Insertion Sort: best=O(n), stable ✅, in-place ✅
Q2:  B — BUILD-MAX-HEAP = O(n) — geometric series proof
Q3:  B — a=3,b=3 → n^(log₃3)=n = f(n) → Case 2 → Θ(n log n)
Q4:  D — Heapsort is NOT stable (swaps break relative order)
Q5:  B — Randomized Quicksort = Θ(n log n) expected ANY input
Q6:  D — BLACK + u.d > v.d = CROSS edge
Q7:  C — BFS finds shortest path by EDGE COUNT (unweighted)
Q8:  C — Back edge ↔ cycle exists in directed graph
Q9:  C — DAG-SP: Θ(V+E), handles negative weights (no cycles in DAG)
Q10: B — If w_i > w (item heavier than current capacity) → can't take
Q11: B — OPT(j) = max(v_j + OPT(p(j)), OPT(j-1))
Q12: C — Johnson's beats Floyd-Warshall on SPARSE graphs with negative weights
Q13: C — EDF minimizes MAXIMUM LATENESS
Q14: B — Counting Sort needs integers in known range [0,k]
Q15: C — Second DFS on G^T in DECREASING finish time order
```

---

## Part 2 — Answer Key

### Q16 — Recurrence dp[n] = 2·dp[n-1] + dp[n-2]
```
dp[0] = 1
dp[1] = 2
dp[2] = 2(2) + 1  = 5
dp[3] = 2(5) + 2  = 12
dp[4] = 2(12) + 5 = 29
dp[5] = 2(29) + 12 = 70

Answer: dp[5] = 70
```

### Q17 — 0/1 Knapsack W=5
```
        w=0  w=1  w=2  w=3  w=4  w=5
i=0:     0    0    0    0    0    0
i=1(1,2):0    2    2    2    2    2
i=2(2,6):0    2    6    8    8    8
i=3(3,9):0    2    6    9   11   15
i=4(4,7):0    2    6    9   11   15

Maximum value = 15

Traceback:
OPT[4][5]=15 = OPT[3][5]=15 → item 4 NOT taken
OPT[3][5]=15 ≠ OPT[2][5]=8  → item 3 TAKEN (w=3,v=9), go OPT[2][2]
OPT[2][2]=6  ≠ OPT[1][2]=2  → item 2 TAKEN (w=2,v=6), go OPT[1][0]
OPT[1][0]=0  = OPT[0][0]=0  → item 1 NOT taken

Selected: {item 2, item 3}
Weight: 2+3=5 ✅   Value: 6+9=15 ✅
```

### Q18 — DFS: 1→2, 2→3, 3→4, 4→2, 1→4, 3→5
```
Visit 1(d=1) → 2(WHITE) TREE
  Visit 2(d=2) → 3(WHITE) TREE
    Visit 3(d=3) → 4(WHITE) TREE
      Visit 4(d=4) → 2(GRAY, 4.d=4 > 2.d=2) BACK EDGE ← CYCLE!
      Finish 4(f=5)
    → 5(WHITE) TREE
    Visit 5(d=6), no neighbors
    Finish 5(f=7)
  Finish 3(f=8)
  Finish 2(f=9)
→ 4(BLACK, 1.d=1 < 4.d=4) FORWARD EDGE
Finish 1(f=10)

Vertex:  1    2    3    4    5
d:       1    2    3    4    6
f:      10    9    8    5    7

Edges:
1→2: TREE    2→3: TREE    3→4: TREE
3→5: TREE    4→2: BACK    1→4: FORWARD

CYCLE EXISTS: 2→3→4→2 (detected by back edge 4→2)
```

### Q19 — BFS from 1: 1—2, 1—3, 2—4, 3—4, 4—5, 3—5
```
Process 1: neighbors 2,3
  2: WHITE → d(2)=1, π=1  TREE 1—2
  3: WHITE → d(3)=1, π=1  TREE 1—3

Process 2: neighbors 1,4
  1: BLACK → skip
  4: WHITE → d(4)=2, π=2  TREE 2—4

Process 3: neighbors 1,4,5
  1: BLACK → skip
  4: GRAY  → skip (non-tree edge 3—4)
  5: WHITE → d(5)=3, π=3  TREE 3—5

Process 4: neighbors 2,3,5
  2,3: BLACK → skip
  5: GRAY  → skip (non-tree edge 4—5)

Process 5: done

Distances: d(1)=0, d(2)=1, d(3)=1, d(4)=2, d(5)=3
Tree edges: 1—2, 1—3, 2—4, 3—5
Non-tree:   3—4, 4—5
```

### Q20 — Topological orderings: 1→2, 2→4, 1→3, 3→4, 4→5, 4→6
```
Step 1: sources={1} → must pick 1
Step 2: sources={2,3} → 2 choices

Branch A: pick 2 → sources={3}
  → must pick 3 → sources={4}
  → must pick 4 → sources={5,6} → 2 choices
    → 4,5: [1,2,3,4,5,6]
    → 4,6: [1,2,3,4,6,5]

Branch B: pick 3 → sources={2}
  → must pick 2 → sources={4}
  → must pick 4 → sources={5,6} → 2 choices
    → [1,3,2,4,5,6]
    → [1,3,2,4,6,5]

Total: 4 valid topological orderings:
  1. [1, 2, 3, 4, 5, 6]
  2. [1, 2, 3, 4, 6, 5]
  3. [1, 3, 2, 4, 5, 6]
  4. [1, 3, 2, 4, 6, 5]
```

### Q21 — SCCs: 1→2, 2→1, 2→3, 3→4, 4→5, 5→3, 5→6, 6→7, 7→6
```
{1,2}: 1→2→1 cycle
{3,4,5}: 3→4→5→3 cycle
{6,7}: 6→7→6 cycle

Answer: 3 SCCs:
  SCC1 = {1, 2}
  SCC2 = {3, 4, 5}
  SCC3 = {6, 7}
```

### Q22 — Dijkstra from S
```
Graph: S→A(5), S→B(1), B→A(2), B→C(4), A→C(1), A→D(6), C→D(3)

Initial: S=0, A=∞, B=∞, C=∞, D=∞

Step 1: Extract S(0) → A=5(π=S), B=1(π=S)
Step 2: Extract B(1) → A=min(5,1+2)=3(π=B), C=min(∞,1+4)=5(π=B)
Step 3: Extract A(3) → C=min(5,3+1)=4(π=A), D=min(∞,3+6)=9(π=A)
Step 4: Extract C(4) → D=min(9,4+3)=7(π=C)
Step 5: Extract D(7) → done

Final:
  δ(S,S)=0   π=NIL    path: S
  δ(S,A)=3   π=B      path: S→B→A
  δ(S,B)=1   π=S      path: S→B
  δ(S,C)=4   π=A      path: S→B→A→C
  δ(S,D)=7   π=C      path: S→B→A→C→D
```

### Q23 — Dijkstra with negative edge
```
(a) Correct δ(S,B):
  Path S→B direct: cost=4
  Path S→A→B: cost = 1 + (−3) = −2
  δ(S,B) = −2

(b) Dijkstra trace:
  Extract S(0) → A=1(π=S), B=4(π=S)
  Extract A(1) → Relax A→B: B=min(4,1−3)=−2 ← update!
  Extract B(−2) → done
  Dijkstra computes δ(S,B)=−2 ✓ (correct here by coincidence)

  Better: if we add B→A(−3):
  S→A(1), S→B(4), A→B(−3), B→A(−3) → negative cycle!
  Dijkstra would loop or give wrong answer.

  Key explanation: Dijkstra's invariant breaks because a
  finalized vertex could receive a shorter path via a
  negative edge discovered later.

(c) Use Bellman-Ford: Θ(V·E), handles negative weights,
  detects negative cycles.
```

### Q24 — Floyd-Warshall D^(0), D^(1), D^(2)
```
Vertices 1-4. w(1,2)=2, w(2,3)=3, w(3,1)=−4, w(1,3)=6, w(2,4)=5, w(3,4)=1

D^(0):
     1    2    3    4
1  [ 0    2    6    ∞ ]
2  [ ∞    0    3    5 ]
3  [ −4   ∞    0    1 ]
4  [ ∞    ∞    ∞    0 ]

D^(1) — allow vertex 1 as intermediate:
  D[2][2]: D[2][1]+D[1][2] = ∞ → no change
  D[3][2]: D[3][1]+D[1][2] = −4+2=−2  ← UPDATE (was ∞)
  D[3][3]: D[3][1]+D[1][3] = −4+6=2   no change (was 0)
  D[3][4]: no change (∞)

D^(1):
     1    2    3    4
1  [ 0    2    6    ∞ ]
2  [ ∞    0    3    5 ]
3  [ −4  −2    0    1 ]
4  [ ∞    ∞    ∞    0 ]

D^(2) — also allow vertex 2:
  D[1][3]: D[1][2]+D[2][3] = 2+3=5 < 6  ← UPDATE
  D[1][4]: D[1][2]+D[2][4] = 2+5=7 < ∞  ← UPDATE
  D[3][3]: D[3][2]+D[2][3] = −2+3=1 no change (0)
  D[3][4]: D[3][2]+D[2][4] = −2+5=3 > 1 no change

D^(2):
     1    2    3    4
1  [ 0    2    5    7 ]   ← [1][3] and [1][4] updated
2  [ ∞    0    3    5 ]
3  [ −4  −2    0    1 ]
4  [ ∞    ∞    ∞    0 ]
```

### Q25 — Array vs Heap for Dijkstra
```
V=1000, E=400,000

Array:       Θ(V²) = Θ(1000²) = 1,000,000 ops
Binary heap: O(E log V) = O(400,000 × log 1000)
                        = O(400,000 × 10) = 4,000,000 ops

(a) Array is FASTER here! 1M < 4M ops

(b) Dense or sparse?
  Max edges for V=1000: V² = 1,000,000
  E = 400,000 = 0.4 × V²  → moderately DENSE graph

Condition for array faster: E ≥ V²/log V
  V²/log V = 1,000,000/10 = 100,000
  E = 400,000 ≥ 100,000 ✅ → array is better
```

### Q26 — Coin Change {1,3,4}, n=6
```
(a) Greedy (largest first):
  Remaining=6: pick 4 → remaining=2
  Remaining=2: pick 1 → remaining=1
  Remaining=1: pick 1 → remaining=0
  Greedy: 3 coins {4,1,1}

(b) NOT optimal.
  Optimal: {3,3} = 2 coins ✅
  Greedy gives 3, optimal is 2 → GREEDY FAILS ❌

(c) Dynamic Programming (DP) — O(n·k) where k=|denominations|
```

### Q27 — EDF Scheduling
```
Sort by deadline: J2(d=2), J1(d=4), J4(d=6), J3(d=8), J5(d=12)

Job  │  t  │  d  │ Start │ Finish │ Lateness
J2   │  1  │  2  │   0   │   1    │ max(0,1−2)=0
J1   │  4  │  4  │   1   │   5    │ max(0,5−4)=1
J4   │  2  │  6  │   5   │   7    │ max(0,7−6)=1
J3   │  3  │  8  │   7   │  10    │ max(0,10−8)=2
J5   │  2  │ 12  │  10   │  12    │ max(0,12−12)=0

(b) Maximum lateness L = 2  (job J3)

(c) No — EDF is provably optimal by exchange argument.
  Any other schedule has max lateness ≥ 2.
```

### Q28 — Interval Scheduling
```
Sort by finish time:
  I1(f=3), I3(f=4), I2(f=5), I7(f=6), I4(f=7), I5(f=8), I6(f=9)

Selection:
  I1: start=0 ≥ 0 ✅ PICK   last_finish=3
  I3: start=2 < 3 ❌ skip
  I2: start=1 < 3 ❌ skip
  I7: start=3 ≥ 3 ✅ PICK   last_finish=6
  I4: start=4 < 6 ❌ skip
  I5: start=5 < 6 ❌ skip
  I6: start=6 ≥ 6 ✅ PICK   last_finish=9

Selected: {I1, I7, I6}   Maximum size = 3
```

### Q29 — Bellman-Ford
```
Graph: S→A(6), S→B(7), A→C(−3), B→A(−2), C→B(4)
Edge processing order: (S,A), (S,B), (A,C), (B,A), (C,B)

Initial: S=0, A=∞, B=∞, C=∞

Pass 1:
  (S,A,6):  A = 0+6 = 6,    π(A)=S
  (S,B,7):  B = 0+7 = 7,    π(B)=S
  (A,C,−3): C = 6+(−3)= 3,  π(C)=A
  (B,A,−2): A = min(6, 7−2)=5, π(A)=B  ← update
  (C,B,4):  B = min(7, 3+4)=7  no change

After pass 1: S=0, A=5, B=7, C=3

Pass 2:
  (S,A,6):  A = min(5, 6) = 5   no change
  (S,B,7):  B = min(7, 7) = 7   no change
  (A,C,−3): C = min(3, 5−3)=2   ← update
  (B,A,−2): A = min(5, 7−2)=5   no change
  (C,B,4):  B = min(7, 2+4)=6   ← update

After pass 2: S=0, A=5, B=6, C=2

(b) Negative cycle check (extra pass):
  After V−1=4 passes, run one more pass.
  If any distance decreases → negative cycle.
  In this graph: no negative cycle (returns TRUE).
```

---

## 📊 SCORE CARD

```
PART 1 MCQ (30 pts):
  Q1-Q15:  ___ / 30   (2 pts each)

PART 2 SHORT ANSWER (70 pts):
  Q16: ___ / 5    Q17: ___ / 5    Q18: ___ / 5
  Q19: ___ / 5    Q20: ___ / 5    Q21: ___ / 5
  Q22: ___ / 5    Q23: ___ / 5    Q24: ___ / 5
  Q25: ___ / 5    Q26: ___ / 5    Q27: ___ / 5
  Q28: ___ / 5    Q29: ___ / 5

TOTAL: ___ / 100     PASS ≥ 40
```

---

## 🔴 TRAP QUESTIONS IN THIS EXAM

```
Q6:  BLACK + u.d > v.d = CROSS (not forward!)
Q9:  DAG-SP is Θ(V+E) AND handles negative weights ← often missed!
Q10: w_i > w means can't fit → must skip item
Q20: 4 orderings (not 2!) because 4→5 and 4→6 both free
Q28: 3 intervals selected (not 2!) — careful with I7 start=3
Q26: {3,3}=2 coins is optimal — greedy picks {4,1,1}=3 coins
```

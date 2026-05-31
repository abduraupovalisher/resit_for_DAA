# CS212 — Design and Analysis of Algorithms
## RESIT EXAMINATION

| | |
|---|---|
| **Course** | CS212 — Design and Analysis of Algorithms |
| **Instructor** | Dr. Bugra Caskurlu |
| **Duration** | 120 minutes |
| **Total Points** | 100 |
| **Passing Grade** | 40 |

### Exam Structure
| Part | Type | Questions | Points |
|------|------|-----------|--------|
| Part 1 | Multiple Choice | 15 questions × 2 pts | 30 pts |
| Part 2 | Short Answer | 6 questions × 10 pts | 60 pts |
| Part 3 | Algorithm Design | 1 question | 10 pts |

### Instructions
- Read every question carefully before answering.
- For MCQs, write only the letter of your answer (A, B, C, or D).
- For short-answer questions, **show all your work**. A correct answer without reasoning receives no credit.
- No additional materials are permitted.
- Manage your time: ~1 min per MCQ, ~10 min per short-answer, ~12 min for algorithm design.

---

## PART 1 — Multiple Choice Questions (30 points)
*Each question is worth 2 points. Choose exactly one answer.*

---

### PRE-MIDTERM TOPICS (Questions 1–8)

**1.** Which of the following correctly describes the worst-case time complexity of **Insertion Sort**?

- A. O(n log n)
- B. O(n)
- C. **O(n²)**
- D. O(n³)

**Answer: ____**

---

**2.** Which sorting algorithms below are both **stable** and **comparison-based**?

- A. Heapsort and Quicksort
- B. Merge Sort and Heapsort
- C. **Merge Sort and Insertion Sort**
- D. Counting Sort and Merge Sort

**Answer: ____**

---

**3.** Consider the recurrence T(n) = 4T(n/2) + n. Using the **Master Theorem**, what is T(n)?

- A. Θ(n log n)
- B. Θ(n²)
- C. **Θ(n²)**
- D. Θ(n log² n)

> Note: a=4, b=2, f(n)=n, n^(log_b a) = n^2. Since f(n) = n = O(n^(2-ε)), Case 1 applies → T(n) = Θ(n²).

**Answer: ____**

---

**4.** Which of the following statements about **Heapsort** is TRUE?

- A. Heapsort is stable
- B. Heapsort requires O(n) extra space
- C. **Heapsort runs in O(n log n) in the worst case and is in-place**
- D. Heapsort uses the divide-and-conquer paradigm

**Answer: ____**

---

**5.** In a **Max-Heap** of n elements, what is the time complexity of `BUILD-MAX-HEAP`?

- A. O(n log n)
- B. O(log n)
- C. **O(n)**
- D. O(n²)

**Answer: ____**

---

**6.** **Quicksort** with a randomly chosen pivot has which expected running time?

- A. O(n²) in all cases
- B. O(n) expected
- C. **O(n log n) expected**
- D. O(n log² n) expected

**Answer: ____**

---

**7.** Which of the following sorting algorithms is **NOT a comparison-based sort**?

- A. Merge Sort
- B. Heapsort
- C. Quicksort
- D. **Counting Sort**

**Answer: ____**

---

**8.** You need to sort n integers all in the range [1, k]. Which algorithm achieves **O(n + k)** time?

- A. Merge Sort
- B. Quicksort
- C. Radix Sort
- D. **Counting Sort**

**Answer: ____**

---

### POST-MIDTERM TOPICS (Questions 9–15)

**9.** In a **Depth-First Search (DFS)** of a directed graph, when edge (u, v) is explored and vertex v is currently **GRAY**, what type of edge is (u, v)?

- A. Tree edge
- B. Forward edge
- C. Cross edge
- D. **Back edge**

**Answer: ____**

---

**10.** A directed graph G has a **topological ordering** if and only if:

- A. G is connected
- B. G has an even number of vertices
- C. **G is a Directed Acyclic Graph (DAG)**
- D. G is bipartite

**Answer: ____**

---

**11.** An undirected graph G is **bipartite** if and only if:

- A. G has no cycles at all
- B. G has an even number of vertices
- C. G is connected
- D. **G has no odd-length cycle**

**Answer: ____**

---

**12.** **Dijkstra's algorithm** produces correct shortest-path distances when:

- A. The graph is a DAG
- B. The graph is undirected
- C. **All edge weights are non-negative**
- D. The graph is bipartite

**Answer: ____**

---

**13.** What is the time complexity of the **Floyd-Warshall** all-pairs shortest paths algorithm on a graph with n vertices?

- A. Θ(n²)
- B. Θ(n² log n)
- C. Θ(n · m)
- D. **Θ(n³)**

**Answer: ____**

---

**14.** In the **Interval Scheduling** problem (maximize the number of non-overlapping intervals), the correct greedy strategy is:

- A. Always pick the interval with the earliest start time
- B. Always pick the shortest interval
- C. **Always pick the interval with the earliest finishing time**
- D. Always pick the interval that overlaps with the fewest others

**Answer: ____**

---

**15.** Which of the following is a defining property that makes **Dynamic Programming** applicable to a problem?

- A. The input must be sorted
- B. All subproblems must have equal size
- C. **Optimal substructure combined with overlapping subproblems**
- D. The problem must have a unique optimal solution

**Answer: ____**

---

## PART 2 — Short Answer Questions (60 points)
*Each question is worth 10 points. Show all work for full credit.*

---

### Q1 (10 pts) — Sorting Algorithm Analysis

**(a)** [4 pts] Fill in the table below:

| Algorithm | Worst-Case Time | Best-Case Time | Stable? | In-Place? |
|-----------|----------------|----------------|---------|-----------|
| Insertion Sort | | | | |
| Merge Sort | | | | |
| Heapsort | | | | |
| Quicksort (random pivot) | | | | |

**(b)** [3 pts] Explain in your own words why **no comparison-based sorting algorithm** can run faster than Ω(n log n) in the worst case. Use the concept of a decision tree in your explanation.

**(c)** [3 pts] You are given an array of n integers where each integer is in the range [1, 100]. Which sorting algorithm would you use, and what would be its time complexity? Justify your answer.

---

### Q2 (10 pts) — Recurrences and Divide-and-Conquer

**(a)** [4 pts] Use the **Master Theorem** to solve the following recurrences. Show which case applies and why.

- (i)  T(n) = 2T(n/4) + √n
- (ii) T(n) = 3T(n/3) + n

**(b)** [3 pts] Write the recurrence for **Merge Sort** and solve it using the **Recursion Tree method**. Show at least 3 levels of the tree.

**(c)** [3 pts] Consider the recurrence T(n) = T(n−1) + n, with T(1) = 1. Solve it using the **substitution method** and prove your answer is correct.

---

### Q3 (10 pts) — BFS and DFS

Consider the directed graph G with the following edges:
```
1→2,  1→3,  2→4,  2→5,  3→5,  4→6,  5→4,  6→3
```

**(a)** [5 pts] Run **DFS** starting from vertex **1**, visiting neighbors in **increasing numerical order**. For each vertex, record the **discovery time (d)** and **finish time (f)**. Then classify **every edge** as: Tree, Back, Forward, or Cross edge.

**(b)** [3 pts] Using your DFS result from part (a), does this graph contain a **cycle**? Justify your answer using edge classification.

**(c)** [2 pts] Is a **topological sort** of this graph possible? Why or why not?

---

### Q4 (10 pts) — Strongly Connected Components & Bipartiteness

**(a)** [5 pts] Consider the directed graph with edges:
```
1→2,  2→3,  3→1,  2→4,  4→5,  5→2,  5→6
```
Find all **Strongly Connected Components (SCCs)** using **Kosaraju's algorithm**. Show:
1. The DFS finishing order on the original graph G
2. The transpose graph G^T
3. The DFS on G^T in decreasing finishing order
4. The final SCCs

**(b)** [3 pts] Consider the undirected graph with edges:
```
{1,2}, {2,3}, {3,4}, {4,5}, {5,2}
```
Is this graph **bipartite**? Show your work by attempting a 2-coloring, or identify an odd-length cycle if it is not bipartite.

**(c)** [2 pts] State the theorem: an undirected graph G is bipartite **if and only if** _____________.

---

### Q5 (10 pts) — Shortest Paths

Consider the weighted directed graph with vertices {S, A, B, C, D} and edges:
```
S→A (6),  S→B (3),  B→A (2),  A→C (1),  B→C (5),  B→D (4),  C→D (2),  A→D (7)
```

**(a)** [5 pts] Run **Dijkstra's algorithm** from source **S**. Show the state of the priority queue and the distance table **after each EXTRACT-MIN step**. Report the final shortest distances δ(S, v) and predecessor π(v) for all vertices.

**(b)** [3 pts] Now suppose the edge **S→A** has weight **−2** (all other weights unchanged). Explain why Dijkstra's algorithm would give an **incorrect result** on this modified graph. Provide the exact incorrect distance it would compute for some vertex.

**(c)** [2 pts] Which algorithm would you use instead to find shortest paths in the modified graph (with S→A = −2)? State its time complexity.

---

### Q6 (10 pts) — Dynamic Programming

**(a)** [5 pts] **0/1 Knapsack**: You have a knapsack with weight capacity **W = 6** and the following items:

| Item | Weight | Value |
|------|--------|-------|
| 1 | 1 | 2 |
| 2 | 3 | 5 |
| 3 | 4 | 8 |
| 4 | 5 | 9 |

Build the complete DP table OPT[i][w] for i = 0..4 and w = 0..6. What is the maximum value? Which items are selected? Show your traceback.

**(b)** [3 pts] Consider the following recurrence with base cases dp[0] = 0, dp[1] = 1:
```
dp[n] = 3·dp[n−1] − dp[n−2]
```
Compute **dp[6]**. Show every intermediate value.

**(c)** [2 pts] What are the **two key properties** a problem must have for Dynamic Programming to be applicable? Give a one-sentence definition of each.

---

## PART 3 — Algorithm Design (10 points)

### Q7 (10 pts) — Design a Greedy Algorithm

You are given **n tasks**, each with a **processing time** t_i (in hours) and a **deadline** d_i (in hours from now). All tasks must be scheduled back-to-back on a **single machine** starting at time 0. The **lateness** of task i is defined as:

> l_i = max(0, f_i − d_i)

where f_i is the time at which task i **finishes**.

Your goal is to find a schedule that **minimizes the maximum lateness** L = max_i(l_i).

**(a)** [2 pts] Consider the following 4 tasks:

| Task | Processing Time (t) | Deadline (d) |
|------|---------------------|--------------|
| A | 3 | 6 |
| B | 2 | 4 |
| C | 1 | 3 |
| D | 4 | 10 |

What is the maximum lateness of the schedule **A → B → C → D**? Show the finish time and lateness of each task.

**(b)** [3 pts] State the **Earliest Deadline First (EDF)** greedy algorithm. Apply it to the 4 tasks above. Show the resulting schedule, finish times, and lateness of each task. What is the maximum lateness?

**(c)** [3 pts] Prove (using an **exchange argument**) that EDF is optimal. Specifically:
- Define what an "inversion" is in a schedule.
- Show that swapping an inverted pair does not increase the maximum lateness.
- Conclude why this implies EDF is optimal.

**(d)** [2 pts] What is the **time complexity** of the EDF algorithm (including the sorting step)? Justify briefly.

---

*End of Exam*

---
*Good luck!*

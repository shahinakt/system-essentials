# Phase 1 — Complete Study Package
## Core Computer Science
### Chapter Reading Lists · Weekly Schedules · Graded Problem Sets

---

> **Prerequisites before starting Phase 1:** All three Phase 0 milestone assessments passed at threshold. You should be fluent in formal proof, modular arithmetic, probability, and linear algebra. Phase 1 builds the intellectual infrastructure of CS — algorithms, software design, networking, theory, and databases. Every module here is a direct prerequisite to one or more Phase 2–4 modules.

---

# MODULE 1.1 — Programming Foundations (Python)

**Duration:** 6–8 weeks | **Hours/week:** 12–15 | **Total hours:** ~100

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Downey — *Think Python*, 2nd ed. (free at greenteapress.com)

---

#### Chapter 1 — The Way of the Program
**Read:** Entire chapter.
Focus on: the concept of a program as a formal specification; what an interpreter does; values and types. Pay attention to the distinction between a syntax error, a runtime error, and a semantic error — this taxonomy will guide your debugging for years.

#### Chapter 2 — Variables, Expressions, and Statements
**Read:** Entire chapter.
Focus on: assignment as binding a name to a value (not equality); operator precedence; the difference between an expression and a statement.

#### Chapter 3 — Functions
**Read:** Entire chapter.
Focus on: the function as an abstraction barrier; parameters vs arguments; local vs global scope; the call stack as a concrete data structure in memory. Draw the call stack diagram for every recursive example.

#### Chapter 4 — Case Study: Interface Design
**Read:** Entire chapter.
Focus on: incremental development; encapsulation; generalization. Study how a function evolves from specific to general through refactoring. This is software engineering thinking applied early.

#### Chapter 5 — Conditionals and Recursion
**Read:** Entire chapter.
Focus on: recursion as a function calling itself; the base case as the termination condition; the relationship between recursion and induction (the recursive call is the inductive step). Trace every recursive example by hand — draw the call stack.

#### Chapter 6 — Fruitful Functions
**Read:** Entire chapter.
Focus on: return values; incremental development with debugging output; Boolean functions. The concept of a function as a value-returning computation (vs a procedure that has side effects) is fundamental to functional programming and will reappear in compiler design.

#### Chapter 7 — Iteration
**Read:** Entire chapter.
Focus on: the while loop; the relationship between iteration and recursion (they are equivalent in power); infinite loops and the halting problem connection.

#### Chapter 8 — Strings
**Read:** Entire chapter.
Focus on: strings as immutable sequences; slicing; string methods; traversal with indices. These operations underpin web security input parsing.

#### Chapter 9 — Case Study: Word Play
**Read:** Entire chapter.
Focus on: working with files; searching; using a dictionary for word lookup. This chapter teaches the workflow of solving a problem methodically.

#### Chapter 10 — Lists
**Read:** Entire chapter.
Focus on: lists as mutable sequences; aliasing (two names for the same object — a source of bugs); list methods and their in-place modification semantics; list comprehensions.

#### Chapter 11 — Dictionaries
**Read:** Entire chapter.
Focus on: the dictionary as a hash table (preview of Module 1.2); key-value pairs; using dictionaries to count, invert, and look up. The efficiency characteristics (O(1) average access) are explained by hashing.

#### Chapter 12 — Tuples
**Read:** Entire chapter.
Focus on: tuples as immutable sequences; tuple assignment (unpacking); returning multiple values; using tuples as dictionary keys.

#### Chapter 13 — Case Study: Data Structure Selection
**Read:** Entire chapter.
Focus on: choosing the right data structure; when to use a list vs dictionary vs set; the memo pattern for memoization (preview of dynamic programming in Module 1.2).

#### Chapter 14 — Files
**Read:** Entire chapter.
Focus on: file objects; reading and writing; the context manager (`with` statement); working with CSV and JSON formats. File I/O is the foundation of log analysis and forensic tooling.

#### Chapter 15 — Classes and Objects
**Read:** Entire chapter.
Focus on: the class as a user-defined type; attributes as data attached to an object; the `__init__` method.

#### Chapter 16 — Classes and Functions
**Read:** Entire chapter.
Focus on: pure functions vs modifiers; the trade-offs between functional and imperative style; prototype-and-patch development.

#### Chapter 17 — Classes and Methods
**Read:** Entire chapter.
Focus on: the `self` parameter; operator overloading via dunder methods; the Pythonic object model.

#### Chapter 18 — Inheritance
**Read:** Entire chapter.
Focus on: inheritance as code reuse and specialization; method resolution order; the difference between `is-a` and `has-a` relationships.

#### Chapter 19 — The Goodies
**Read:** Sections on list comprehensions, generator expressions, `any`/`all`, named tuples, `enumerate`, `zip`, `*args`/`**kwargs`.
Focus on: writing idiomatic Python that is readable and efficient.

---

### Supplementary Text: Lutz — *Learning Python*, 5th ed.
Use for deeper reference on any topic covered in Think Python. Key chapters:

- **Part III (Statements and Syntax):** Ch. 11–14 for precise statement semantics
- **Part IV (Functions):** Ch. 16–21 for closures, decorators, generators in depth
- **Part V (Modules):** Ch. 22–25 for package structure and import system
- **Part VI (Classes and OOP):** Ch. 26–32 for the complete Python object model, metaclasses

---

### Supplementary: MIT 6.0001 OCW
**Watch:** Lectures 1–12 (all)
**Do:** Problem Sets 1–5

---

### Python Official Documentation
Read these sections completely, not as a reference but as a curriculum:
- **Data Model** (docs.python.org/3/reference/datamodel.html) — understand how dunder methods work
- **Built-in Types** (docs.python.org/3/library/stdtypes.html) — every container type
- **`itertools`** and **`functools`** module documentation
- **`unittest`** module documentation

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Foundations: Values, Control Flow, Functions
- **Day 1:** Think Python Ch. 1–3. Set up your development environment. Write 10 small programs — one for each concept.
- **Day 2:** Think Python Ch. 4–5. Recursion focus. Trace 5 recursive calls by hand. Draw the call stack for each.
- **Day 3:** Think Python Ch. 6–7. Write both iterative and recursive solutions for: factorial, Fibonacci, GCD, power, sum of list.
- **Day 4:** MIT 6.0001 Lectures 1–4. Do all finger exercises.
- **Day 5:** Problem Set 1.1 Tier 1, problems 1–10.
- **Day 6:** Build Project 1 — text adventure game skeleton (menus, room navigation, state).
- **Day 7:** Rest.

### Week 2 — Data Structures: Strings, Lists, Dictionaries
- **Day 1:** Think Python Ch. 8–9. Implement all string operations without using built-in methods where instructed.
- **Day 2:** Think Python Ch. 10–11. Implement a word frequency counter using a dictionary.
- **Day 3:** Think Python Ch. 12–13. Implement the Fibonacci memoization example. Understand aliasing with a diagram.
- **Day 4:** MIT 6.0001 Lectures 5–8.
- **Day 5:** Problem Set 1.1 Tier 1, problems 11–20.
- **Day 6:** Build Project 1 — add inventory system (dictionary), save/load game state (file I/O).
- **Day 7:** Rest.

### Week 3 — File I/O, Error Handling, Modules
- **Day 1:** Think Python Ch. 14. Read/write CSV files. Handle missing data gracefully.
- **Day 2:** Python docs — `try`/`except`/`finally`; exception hierarchy; raising custom exceptions.
- **Day 3:** Python docs — modules, packages, `__init__.py`, relative imports.
- **Day 4:** MIT 6.0001 Lectures 9–12. Do Problem Set 3.
- **Day 5:** Problem Set 1.1 Tier 2, problems 1–6.
- **Day 6:** Build Project 2 — CSV data analyzer: load, clean, summarize, and report on a dataset.
- **Day 7:** Rest.

### Week 4 — Object-Oriented Programming
- **Day 1:** Think Python Ch. 15–16. Build a `Point` and `Rectangle` class. Test every method.
- **Day 2:** Think Python Ch. 17. Operator overloading — implement `__add__`, `__str__`, `__repr__`, `__eq__` for a `Vector` class.
- **Day 3:** Think Python Ch. 18. Inheritance — build a `Shape` hierarchy with `Circle`, `Rectangle`, `Triangle` subclasses.
- **Day 4:** Lutz Ch. 28–30 (OOP in depth). Study method resolution order and multiple inheritance.
- **Day 5:** Problem Set 1.1 Tier 2, problems 7–14.
- **Day 6:** Build Project 3 — recursive maze solver with OOP-modeled maze and solver.
- **Day 7:** Rest.

### Week 5 — Advanced Python: Generators, Decorators, Testing
- **Day 1:** Think Python Ch. 19 (goodies). Write 5 generator functions. Understand lazy evaluation.
- **Day 2:** Lutz Ch. 38–39 (decorators). Write 3 decorators: timer, memoizer, retry-on-exception.
- **Day 3:** Python docs — `unittest`. Write a full test suite for your maze solver from Week 4.
- **Day 4:** MIT 6.0001 Lectures (remaining). Do Problem Sets 4–5.
- **Day 5:** Problem Set 1.1 Tier 2, problems 15–20.
- **Day 6:** Build Project 4 — personal finance tracker (OOP design, file persistence, reporting).
- **Day 7:** Rest.

### Week 6 — Integration, Debugging, and Milestone
- **Days 1–2:** Complete all four projects. Ensure each has a full `unittest` test suite.
- **Day 3:** Debugging lab — fix 10 deliberately broken programs (see Lab 1.1.A).
- **Day 4:** Code review lab — review a peer's or open-source project's Python; document 5 issues and 5 strengths.
- **Day 5:** Problem Set 1.1 Tier 3, problems 1–10.
- **Day 6:** Milestone assessment attempt.
- **Day 7:** Remediation.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Write a function `is_prime(n)` that returns `True` if `n` is prime. Use trial division. Then write `primes_up_to(n)` using the Sieve of Eratosthenes. Compare the runtime of both for n = 10,000.

**Problem 2.** Write a recursive function `flatten(lst)` that takes a nested list of arbitrary depth and returns a flat list. Example: `flatten([1, [2, [3, 4], 5]])` → `[1, 2, 3, 4, 5]`.

**Problem 3.** Write `binary_search(lst, target)` iteratively and recursively. Both must run in O(log n). Write unit tests that cover: found at start, found at end, found in middle, not found, empty list, single element.

**Problem 4.** Implement a `Stack` class using a Python list as the underlying storage. Include: `push`, `pop`, `peek`, `is_empty`, `size`. Write unit tests for each. Then implement a `Queue` using two stacks (the classic interview problem — `enqueue` is O(1), `dequeue` is amortized O(1)).

**Problem 5.** Write a function `word_frequency(text)` that returns a dictionary mapping each word to its count. Ignore punctuation and case. Print the top 10 most frequent words in a text file of your choice.

**Problem 6.** Write a function `caesar_cipher(text, shift)` that encrypts using the Caesar cipher. Write `caesar_decrypt(text, shift)`. Then write `caesar_crack(ciphertext)` that tries all 26 shifts and returns the most likely plaintext (use letter frequency analysis).

**Problem 7.** Implement `merge_sort(lst)` recursively. Trace through the execution on `[5, 2, 8, 1, 9, 3]`, drawing the call tree. Write unit tests.

**Problem 8.** Write a `Matrix` class that supports `+`, `*` (matrix multiplication), transpose, and `__str__`. Test matrix multiplication correctness against NumPy.

**Problem 9.** Write a decorator `@retry(max_attempts, delay)` that retries a function up to `max_attempts` times with `delay` seconds between attempts if it raises an exception. Test it with a function that randomly fails.

**Problem 10.** Read a CSV file of student names and grades. Compute mean, median, standard deviation, and the grade distribution. Write the summary to a new CSV file. Use only the standard library (no pandas).

**Problem 11.** Write a generator `infinite_primes()` that yields primes indefinitely. Use it with `itertools.islice` to get the first 1000 primes.

**Problem 12.** Implement a simple in-memory key-value store class with `set(key, value, ttl=None)`, `get(key)`, and `delete(key)`. Keys with a TTL should expire after the given number of seconds.

**Problem 13.** Write a function `anagram_groups(words)` that groups anagrams together. Return a list of lists. Hint: the sorted characters of a word are a canonical key.

**Problem 14.** Implement `memoize(f)` as a decorator that caches the return value of `f` for each unique set of arguments. Test it by memoizing a recursive Fibonacci function and comparing speed with/without memoization for n=35.

**Problem 15.** Write a context manager `Timer` (using `__enter__` and `__exit__`) that prints the elapsed time of the block it wraps. Use it to time 5 different operations.

**Problem 16.** Implement a simple ROT13 cipher and its inverse. Then write a generic `substitution_cipher(text, key)` where `key` is a 26-character permutation of the alphabet.

**Problem 17.** Write `power_set(s)` that returns all subsets of a given set, using recursion. For `s = {1, 2, 3}`, verify you get 8 subsets. Analyze the time complexity.

**Problem 18.** Write a Python class `Graph` with adjacency list representation. Implement BFS and DFS as methods. Find all connected components. Test on 3 example graphs.

**Problem 19.** Write a `FileMonitor` class that watches a directory and prints a message whenever a file is added, removed, or modified (poll every second). Use `os` and `time` only.

**Problem 20.** Write comprehensive unit tests (using `unittest`) for the `Graph` class from Problem 18. Aim for 100% method coverage. Include edge cases: empty graph, single node, self-loop, disconnected graph.

---

### Tier 2 — Intermediate

**Problem 1.** Implement a `LRUCache` class with `get(key)` and `put(key, value, capacity)`. Both operations must be O(1). Use an `OrderedDict` or a custom doubly-linked list with a hash map.

**Problem 2.** Write a parser for simple mathematical expressions (no parentheses) following operator precedence: `*` and `/` before `+` and `-`. Input: `"3 + 4 * 2 - 1"` → 10. Implement using a recursive descent parser.

**Problem 3.** Write a complete Vigenère cipher: `encrypt(plaintext, key)` and `decrypt(ciphertext, key)`. Then implement `crack_vigenere(ciphertext)` using the index of coincidence to determine key length and frequency analysis to find the key.

**Problem 4.** Implement a simple interpreter for a tiny stack-based language with 5 instructions: `PUSH n`, `POP`, `ADD`, `MUL`, `PRINT`. Execute programs from a text file.

**Problem 5.** Write a `ThreadSafeQueue` class using Python's `threading.Lock` and a list. Implement `enqueue`, `dequeue`, `is_empty`, and `size`. Write a producer-consumer test using `threading.Thread`.

**Problem 6.** Build a simple HTTP client from scratch using the `socket` module (no `urllib`). It should: open a TCP connection to a host on port 80, send a valid HTTP/1.1 GET request, receive the response, parse headers, and return the body. Test against `example.com`.

**Problem 7.** Implement a Huffman encoding/decoding system. Build the frequency table, construct the Huffman tree using a priority queue, generate codes, encode a string, and decode it back. Verify round-trip correctness.

---

### Tier 3 — Advanced

**Problem 1.** Build a complete mini test framework (like a tiny `unittest`) from scratch. It should support: test case classes, `setUp`/`tearDown`, `assert_equal`, `assert_raises`, test discovery by naming convention, and a summary report of pass/fail/error counts.

**Problem 2.** Implement a `coroutine`-based pipeline: write generators for `read_lines(filename)`, `filter_lines(pattern)`, `transform_lines(f)`, and `write_lines(filename)`. Chain them using `yield from` to process a log file: filter lines containing "ERROR", extract timestamps, and write them to a new file.

**Problem 3.** Write a pure-Python Merkle tree implementation. Given a list of data blocks, build the tree, compute the root hash (using SHA-256), and implement `get_proof(index)` and `verify_proof(root, proof, index, data)`. Test that any modification to a block invalidates the proof.

---

### Milestone Assessment — Module 1.1
*Pass threshold: 80%. Time: 3 hours. No AI assistance. External documentation allowed.*

1. Write a `LinkedList` class with: `append`, `prepend`, `delete(value)`, `reverse` (in-place), `__len__`, `__str__`. Write unit tests for all methods including edge cases.
2. Write a recursive function `count_paths(grid)` that counts the number of paths from the top-left to the bottom-right of an m×n grid, moving only right or down. Then implement a memoized version.
3. Implement a simple tokenizer for arithmetic expressions: given `"(3 + 4) * (2 - 1)"`, return `['(', '3', '+', '4', ')', '*', '(', '2', '-', '1', ')']`. Handle integers, operators, and parentheses. Write 10 unit tests.
4. Write a decorator `@rate_limit(calls, period)` that raises an exception if a function is called more than `calls` times in `period` seconds.
5. Read a log file line by line (too large for memory). Count occurrences of each HTTP status code. Return results sorted by count descending. Use generators throughout.

---

---

# MODULE 1.2 — Data Structures & Algorithm Design

**Duration:** 12–14 weeks | **Hours/week:** 12–15 | **Total hours:** ~175

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: CLRS — *Introduction to Algorithms*, 4th ed.

This is the most important textbook in this curriculum. Read every proof. Do not skip.

---

#### Part I — Foundations (Chapters 1–5)

**Chapter 1 — The Role of Algorithms in Computing**
Read entirely. Focus on: the definition of an algorithm as a well-specified computational procedure; the RAM model of computation; what it means for an algorithm to solve a problem correctly. This is the philosophical foundation.

**Chapter 2 — Getting Started**
Read entirely. Focus on:
- Insertion sort — the loop invariant technique: identify what is true before each iteration, prove it holds after each step, use it to prove correctness. This is the standard method for proving iterative algorithm correctness.
- Merge sort — divide-and-conquer paradigm; the recurrence T(n) = 2T(n/2) + Θ(n).
- **Do every exercise in §2.1–2.3.** These establish the habits of proof and analysis.

**Chapter 3 — Characterizing Running Times**
Read entirely. Focus on:
- Formal definitions of O, Ω, Θ, o, ω — know all five, not just Big-O.
- Prove the relationships between them using the formal definitions.
- The limit characterization: f(n) = O(g(n)) iff lim sup f(n)/g(n) < ∞.
- Growth rate hierarchy: log n ≪ n^ε ≪ n^c ≪ n^{log n} ≪ c^n ≪ n!

**Chapter 4 — Divide-and-Conquer**
Read entirely. Focus on:
- The substitution method: guess a bound and verify by induction.
- The recursion tree method: draw the tree, sum each level, sum across levels.
- The Master Theorem: know all three cases and their conditions. Prove Case 1 (the dominant case intuition).
- Strassen's matrix multiplication: understand why it's O(n^{2.81}) — the key insight that 7 multiplications beat 8.

**Chapter 5 — Probabilistic Analysis and Randomized Algorithms**
Read entirely. Focus on:
- Indicator random variables — one of the most powerful tools for average-case analysis.
- Hiring problem expected cost analysis.
- Randomized quicksort expected running time analysis using indicator variables.
- Balls-and-bins, birthday paradox, and streak problems — connect to probability (Module 0.3).

---

#### Part II — Sorting and Order Statistics (Chapters 6–9)

**Chapter 6 — Heapsort**
Read entirely. Focus on:
- The max-heap property: A[parent(i)] ≥ A[i].
- `MAX-HEAPIFY` — prove the O(log n) time bound using the height of the heap.
- `BUILD-MAX-HEAP` — prove the O(n) time bound (a crucial non-obvious result; the analysis uses a geometric series).
- Priority queue operations: `INSERT`, `EXTRACT-MAX`, `INCREASE-KEY` — all O(log n).

**Chapter 7 — Quicksort**
Read entirely. Focus on:
- Worst case O(n²) on sorted input — understand why and when this occurs.
- Expected case O(n log n) — the analysis using indicator variables (§7.4) is beautiful and important.
- Randomized quicksort — why randomizing the pivot gives O(n log n) expected time regardless of input.
- Partitioning as a general technique (used in median finding).

**Chapter 8 — Sorting in Linear Time**
Read entirely. Focus on:
- The comparison sort lower bound Ω(n log n) — the decision tree proof is elegant and important.
- Counting sort: O(n + k) time; stable; requires integer keys in [0, k].
- Radix sort: O(d(n + k)) time; why sorting digit-by-digit from least significant works (correctness proof).
- Bucket sort: O(n) average time for uniform input.

**Chapter 9 — Medians and Order Statistics**
Read entirely. Focus on:
- Randomized selection in O(n) expected time.
- Worst-case O(n) selection using median-of-medians (understand the partition argument).

---

#### Part III — Data Structures (Chapters 10–14)

**Chapter 10 — Elementary Data Structures**
Read entirely. Focus on:
- Array-based stacks and queues — amortized analysis of dynamic array resizing.
- Linked lists — the pointer operations; sentinel nodes as a simplification trick.
- Rooted tree representations.

**Chapter 11 — Hash Tables**
Read entirely. Focus on:
- Division and multiplication hash functions.
- Chaining: expected O(1) search under simple uniform hashing — prove this.
- Open addressing: linear probing, quadratic probing, double hashing.
- Load factor α and its effect on performance.
- Perfect hashing — O(1) worst-case guarantee.
- **Security note:** Hash DoS attacks — why an adversary knowing the hash function can force O(n) collisions; universal hashing as the defense.

**Chapter 12 — Binary Search Trees**
Read entirely. Focus on:
- BST property and its invariant.
- Search, insert, delete operations — all O(h) where h is height.
- Prove: in a random BST (keys inserted in random order), expected height is O(log n).
- Predecessor and successor.

**Chapter 13 — Red-Black Trees**
Read entirely. Focus on:
- The four red-black properties and why they imply height ≤ 2 log(n+1).
- Rotations (left-rotate, right-rotate) as the basic restructuring operation.
- Insertion: the cases (uncle is red; uncle is black with specific child configuration). Trace through 3 full insertion examples.
- Deletion: the most complex BST operation in the book — work through at least 2 full examples.

**Chapter 14 — Augmenting Data Structures**
Read §14.1–14.2. Focus on order-statistic trees (rank and select in O(log n)) and interval trees. Understand the methodology: choose augmentation, prove it's efficiently maintainable.

---

#### Part IV — Advanced Design and Analysis (Chapters 15–17)

**Chapter 15 — Dynamic Programming**
Read entirely — this is the most important chapter in the book for algorithm design.
- **Methodology:** optimal substructure → overlapping subproblems → memoization or tabulation.
- Rod cutting: the canonical example. Prove optimal substructure from first principles.
- Matrix chain multiplication: understand the O(n³) DP vs O(n!) naive enumeration.
- Longest Common Subsequence (LCS): reconstruct the actual sequence, not just its length.
- Optimal binary search trees.
- **Do exercises 15.1 through 15.5 completely.**

**Chapter 16 — Greedy Algorithms**
Read entirely. Focus on:
- Activity selection: the greedy choice property and optimal substructure — prove both for this problem.
- Huffman codes: the correctness proof using an exchange argument.
- Matroid theory (§16.4): the general framework that explains when greedy works. Understand the definition of a matroid and why weighted matroid intersection gives the optimal greedy solution.

**Chapter 17 — Amortized Analysis**
Read entirely. Focus on:
- Aggregate analysis: table doubling (dynamic arrays) — the total cost of n insertions is O(n), so amortized O(1) each.
- Accounting method: assign "credits" to cheap operations that pay for expensive ones.
- Potential method: define a potential function Φ; amortized cost = actual cost + ΔΦ.
- Understand all three methods for the same examples (table doubling, multi-pop stack).

---

#### Part V — Advanced Data Structures (Chapters 19–20)

**Chapter 19 — Fibonacci Heaps**
Read §19.1–19.3. Focus on: the amortized cost of operations; why DECREASE-KEY is O(1) amortized (enabling Dijkstra's O(V log V + E) bound). The implementation details matter less than the amortized analysis.

**Chapter 20 — van Emde Boas Trees** *(optional)*
Skim §20.1–20.2 for the idea of achieving O(log log U) operations.

---

#### Part VI — Graph Algorithms (Chapters 22–25)

**Chapter 22 — Elementary Graph Algorithms**
Read entirely. Focus on:
- BFS: prove the d[v] values are correct (the shortest-path distances). The proof is a model of correctness argument by invariant.
- DFS: discovery and finish timestamps; the parenthesis theorem; the white-path theorem.
- Topological sort: via DFS finish order — prove correctness.
- Strongly connected components: Kosaraju's algorithm and Tarjan's algorithm — understand both.

**Chapter 23 — Minimum Spanning Trees**
Read entirely. Focus on:
- The blue rule and red rule as the unified theoretical foundation.
- Kruskal's: union-find data structure; O(E log E) time.
- Prim's: priority queue implementation; O(E + V log V) with Fibonacci heaps.
- Prove the cut property (the key correctness theorem).

**Chapter 24 — Single-Source Shortest Paths**
Read entirely. Focus on:
- Relaxation as the universal operation; the triangle inequality.
- Bellman-Ford: handles negative weights; detects negative cycles. Prove correctness.
- Dijkstra's: requires non-negative weights; O(V log V + E) with Fibonacci heaps. Prove via greedy argument.
- DAG shortest paths: linear time using topological order.

**Chapter 25 — All-Pairs Shortest Paths**
Read entirely. Focus on:
- Floyd-Warshall: O(V³) DP; understand the recurrence W(k)[i][j] = min(W(k-1)[i][j], W(k-1)[i][k] + W(k-1)[k][j]).
- Johnson's algorithm: reweighting via Bellman-Ford, then Dijkstra from every vertex.

---

#### Part VII — Selected Advanced Topics

**Chapter 26 — Maximum Flow** *(read §26.1–26.2)*
Focus on: residual graphs; augmenting paths; the max-flow min-cut theorem. Applications: bipartite matching, network reliability.

**Chapter 32 — String Matching**
Read §32.1–32.3. Focus on:
- Naive matching: O((n-m+1)m).
- Rabin-Karp: rolling hash; O(n+m) expected.
- KMP: the failure function; O(n+m) worst case. Prove the failure function computation is correct.

**Chapter 34 — NP-Completeness** *(read §34.1–34.4)*
Focus on: P vs NP (precise definitions); polynomial-time reduction; the Cook-Levin theorem (3-SAT is NP-complete); proving new problems NP-complete by reduction. This chapter bridges to Module 1.5.

---

### Supplementary Text: Sedgewick & Wayne — *Algorithms*, 4th ed.
Use for: Java implementations that complement CLRS's pseudocode; Section 6 (Context) for practical applications; the string processing chapters (5) for tries and suffix arrays.

### Supplementary Text: Skiena — *The Algorithm Design Manual*, 3rd ed.
Use for: Chapter 1–2 (algorithm design methodology); the "war stories" for intuition; the catalog (Part II) as a reference for recognizing problem types.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Foundations: Asymptotic Analysis & Proofs
- **Day 1:** CLRS Ch. 1, Ch. 3. Formal definitions of O, Ω, Θ. Prove 5 complexity relationships from definition.
- **Day 2:** CLRS Ch. 2.1–2.2. Insertion sort — write the loop invariant proof completely. Implement in Python.
- **Day 3:** CLRS Ch. 2.3. Merge sort — recurrence setup and Master Theorem solution. Implement and test.
- **Day 4:** CLRS Ch. 4.1–4.2. Substitution and recursion tree methods. Solve 10 recurrences.
- **Day 5:** CLRS Ch. 4.5 (Master Theorem). Apply to 10 recurrences — identify the case for each.
- **Day 6:** Problem Set 1.2 Tier 1, problems 1–5.
- **Day 7:** Rest.

### Week 2 — Sorting Algorithms
- **Day 1:** CLRS Ch. 6 (Heapsort). Implement `BUILD-MAX-HEAP` and heapsort. Prove the O(n) build time.
- **Day 2:** CLRS Ch. 7 (Quicksort). Implement with Lomuto and Hoare partition. Measure worst-case behavior on sorted input.
- **Day 3:** CLRS Ch. 5 (Probabilistic analysis). Indicator RV analysis of randomized quicksort expected time.
- **Day 4:** CLRS Ch. 8 (Linear-time sorting). Implement counting sort and radix sort. Prove the lower bound.
- **Day 5:** CLRS Ch. 9 (Order statistics). Implement randomized selection.
- **Day 6:** Problem Set 1.2 Tier 1, problems 6–12.
- **Day 7:** Lab — benchmark all sorting algorithms on random, sorted, and reverse-sorted input; plot results.

### Week 3 — Elementary Data Structures
- **Day 1:** CLRS Ch. 10. Implement stack, queue, doubly linked list from scratch (no Python lists for the core).
- **Day 2:** CLRS Ch. 11. Implement hash table with chaining. Analyze load factor effect on performance empirically.
- **Day 3:** Universal hashing — implement a universal hash family. Test collision rates.
- **Day 4:** CLRS Ch. 17 (Amortized analysis). Dynamic array with doubling — potential method proof.
- **Day 5:** Problem Set 1.2 Tier 1, problems 13–18.
- **Day 6:** Lab — hash table collision analysis at varying load factors (plot).
- **Day 7:** Rest.

### Week 4 — Binary Search Trees & Balanced BSTs
- **Day 1:** CLRS Ch. 12 (BST). Implement BST with insert, search, delete, predecessor, successor. All cases.
- **Day 2:** CLRS Ch. 13 (Red-Black Trees). Study rotations. Trace 3 insertion examples in detail.
- **Day 3:** Red-Black Tree deletion — trace 2 examples. Understand all cases.
- **Day 4:** CLRS Ch. 14 (Augmentation). Implement order-statistic tree (rank and select).
- **Day 5:** Problem Set 1.2 Tier 2, problems 1–5.
- **Day 6:** Implement AVL tree (alternative to red-black); compare rotation counts with red-black on same input sequence.
- **Day 7:** Rest.

### Week 5 — Dynamic Programming
- **Day 1:** CLRS §15.1 (Rod cutting). Implement both top-down (memoized) and bottom-up solutions.
- **Day 2:** CLRS §15.2 (Matrix chain). Implement O(n³) DP. Reconstruct optimal parenthesization.
- **Day 3:** CLRS §15.4 (LCS). Implement with full reconstruction. Test on DNA sequences.
- **Day 4:** Edit distance (Levenshtein). Implement DP solution. Use for spell-checker.
- **Day 5:** 0/1 Knapsack DP. Implement with reconstruction. Analyze space optimization (1D DP).
- **Day 6:** Problem Set 1.2 Tier 2, problems 6–10.
- **Day 7:** Spell-checker project — trie + edit distance.

### Week 6 — Greedy Algorithms & More DP
- **Day 1:** CLRS §16.1–16.2 (Activity selection, Huffman). Implement Huffman coder/decoder.
- **Day 2:** Coin change (greedy failure + DP). Interval scheduling variants.
- **Day 3:** Longest increasing subsequence (O(n log n) patience sorting approach).
- **Day 4:** DP on strings: regular expression matching; wildcard matching.
- **Day 5:** Problem Set 1.2 Tier 2, problems 11–16.
- **Day 6:** Huffman compression tool — full encoder and decoder with file I/O.
- **Day 7:** Rest.

### Week 7 — Graph Algorithms I: BFS, DFS, Topological Sort, SCCs
- **Day 1:** CLRS §22.1–22.2 (BFS). Implement BFS with distance tracking. Prove correctness theorem.
- **Day 2:** CLRS §22.3–22.4 (DFS, topological sort). Implement DFS with timestamps.
- **Day 3:** CLRS §22.5 (SCCs). Implement Kosaraju's algorithm. Test on 3 DAGs.
- **Day 4:** Implement Tarjan's SCC algorithm (compare to Kosaraju's).
- **Day 5:** Problem Set 1.2 Tier 2, problems 17–20.
- **Day 6:** Graph traversal lab — apply BFS/DFS to a real-world graph dataset (e.g., social network edges).
- **Day 7:** Rest.

### Week 8 — Graph Algorithms II: Shortest Paths & MST
- **Day 1:** CLRS §24.1 (Bellman-Ford). Implement. Construct a negative-cycle example.
- **Day 2:** CLRS §24.3 (Dijkstra). Implement with min-heap. Prove correctness.
- **Day 3:** CLRS §25.2 (Floyd-Warshall). Implement. Detect negative cycles via diagonal.
- **Day 4:** CLRS §23 (MST). Implement Kruskal's (with union-find) and Prim's.
- **Day 5:** Problem Set 1.2 Tier 3, problems 1–5.
- **Day 6:** Pathfinding visualizer (Dijkstra + A*) on a grid map.
- **Day 7:** Rest.

### Week 9 — String Algorithms, Flow, and NP-Completeness
- **Day 1:** CLRS §32.1–32.3. Implement KMP and Rabin-Karp. Benchmark both.
- **Day 2:** Trie implementation: insert, search, prefix search, autocomplete.
- **Day 3:** CLRS §26.1–26.2 (Max-flow). Implement Ford-Fulkerson with BFS augmentation (Edmonds-Karp).
- **Day 4:** CLRS §34.1–34.4 (NP-completeness). Reduction from 3-SAT to INDEPENDENT-SET.
- **Day 5:** Problem Set 1.2 Tier 3, problems 6–10.
- **Day 6:** Suffix array construction — implement O(n log n) suffix array for string search.
- **Day 7:** Rest.

### Weeks 10–12 — Project Work, Integration, and Milestone

- **Week 10:** Implement every data structure from scratch — complete and test all: dynamic array, linked list, stack, queue, deque, hash table (chaining + open addressing), BST, red-black tree, heap, trie, union-find. All with full test suites.
- **Week 11:** Complete module-level capstone: choose a real-world problem (routing, scheduling, pattern matching, compression), design a solution using the algorithms from this module, implement it, analyze complexity, and write a 3-page technical report.
- **Week 12:** Milestone assessment and remediation.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Prove from the formal definition: n² + 3n + 7 = O(n²). Find explicit c and n₀.

**Problem 2.** Rank the following functions in asymptotic order (from slowest to fastest growth): n!, 2^n, n³, n^{1.5}, n log² n, √n, log n, n log n, n, 1.

**Problem 3.** Solve the recurrences using the Master Theorem or recursion tree. State which case applies.
(a) T(n) = 4T(n/2) + n
(b) T(n) = 4T(n/2) + n²
(c) T(n) = 4T(n/2) + n³
(d) T(n) = 3T(n/3) + n

**Problem 4.** Write the loop invariant for the following algorithm and use it to prove correctness:
```
FIND-MAX(A, n):
  max = A[1]
  for i = 2 to n:
    if A[i] > max:
      max = A[i]
  return max
```

**Problem 5.** Implement a min-heap from scratch (array representation). Include: `insert`, `extract_min`, `decrease_key`, `build_heap`. Prove the O(n) `build_heap` time bound.

**Problem 6.** Implement open-addressing hash table with linear probing. Demonstrate the clustering problem empirically: measure average probe length at load factors 0.5, 0.7, 0.9.

**Problem 7.** Implement merge sort and count the number of inversions in an array (pairs (i,j) where i < j but A[i] > A[j]). An O(n log n) solution is required. Prove its correctness.

**Problem 8.** Given a BST, implement: (a) `floor(k)` — largest key ≤ k; (b) `ceiling(k)` — smallest key ≥ k; (c) `rank(k)` — number of keys less than k; (d) `select(r)` — key of rank r.

**Problem 9.** Prove the correctness of BFS shortest-path distances: for all vertices v reachable from source s, d[v] = δ(s, v) after BFS completes. (Reproduce the proof from CLRS §22.2 in your own words and notation.)

**Problem 10.** Implement Dijkstra's algorithm. Run it on the following graph (adjacency list with weights) and trace through the priority queue state at each step:
Vertices: {A, B, C, D, E}
Edges: A-B:4, A-C:2, B-C:1, B-D:5, C-D:8, C-E:10, D-E:2

**Problem 11.** Implement the 0/1 Knapsack problem using DP. Reconstruct which items are included. Analyze time and space complexity.

**Problem 12.** Implement LCS (Longest Common Subsequence) with full reconstruction. Test on: (a) "ABCBDAB" and "BDCAB", (b) two DNA sequences of your choice.

**Problem 13.** Implement union-find (disjoint set union) with both path compression and union by rank. Prove that any sequence of m operations on n elements takes O(m α(n)) time (state the theorem; the full proof is in CLRS Ch. 21).

**Problem 14.** Implement Kruskal's MST algorithm using your union-find from Problem 13. Test on a graph with 8 vertices and 12 edges.

**Problem 15.** Implement Floyd-Warshall. Detect if a graph has a negative cycle (check the diagonal). Test on: a graph with no negative cycle, and a graph with one.

**Problem 16.** Implement KMP string matching. Trace through the failure function computation for pattern `"ABABACA"`. Then trace through a complete match/search on text `"ABABABCABABACA"`.

**Problem 17.** Prove the comparison sort lower bound: any comparison-based sorting algorithm requires Ω(n log n) comparisons in the worst case. Your proof must use the decision tree model.

**Problem 18.** Prove the activity selection greedy choice: always selecting the earliest finishing activity leads to an optimal solution. (Use the exchange argument.)

**Problem 19.** Implement heapsort in-place. Verify it sorts correctly and uses O(1) extra space.

**Problem 20.** Implement `SELECT(A, i)` (finding the i-th smallest element) in O(n) worst case using the median-of-medians algorithm. Verify it returns the correct element for all i on arrays of size 1, 5, 10, 50.

---

### Tier 2 — Intermediate

**Problem 1.** Design an O(n log n) algorithm to determine if any two intervals in a set of n intervals overlap. Prove its correctness and analyze its complexity.

**Problem 2.** Implement a trie (prefix tree). Support `insert`, `search`, `starts_with`, `delete`, and `autocomplete(prefix)` returning all words with that prefix. Use it to build a spell-checker with at most O(L) operations per word where L is word length.

**Problem 3.** Implement Huffman coding. Given the character frequencies for a text: {a:45, b:13, c:12, d:16, e:9, f:5}, build the Huffman tree, compute codes, and find the compression ratio vs fixed-width encoding.

**Problem 4.** Given a directed graph G, design an algorithm to determine if it contains a cycle. If it does, output the cycle. Prove correctness and analyze complexity.

**Problem 5.** The single-source shortest path problem on a graph with negative weights (but no negative cycles) can be solved with Bellman-Ford. Prove that after V-1 iterations, all shortest path distances are correct. Then show that if a V-th iteration changes any distance, there is a negative cycle.

**Problem 6.** Edit distance with full operation reconstruction: implement the DP for edit distance (insert, delete, substitute) and reconstruct the sequence of operations. Apply it to `"kitten"` → `"sitting"`.

**Problem 7.** Implement a segment tree that supports: point update and range sum query, both in O(log n). Generalize to range minimum query (RMQ).

**Problem 8.** Prove that a red-black tree with n internal nodes has height at most 2 log₂(n+1). (Reproduce the proof from CLRS §13.1 in your own words.)

**Problem 9.** Design an O(n log n) algorithm that, given n points on a 2D plane, finds the closest pair of points. Implement it and test on 1000 random points.

**Problem 10.** Prove the max-flow min-cut theorem: the maximum value of a flow equals the minimum capacity of a cut. Use the augmenting path algorithm's termination condition.

---

### Tier 3 — Advanced

**Problem 1.** Implement a fully persistent binary search tree (every update creates a new version sharing structure with the old). Use path copying. Show that each update costs O(log n) time and space.

**Problem 2.** Implement a skip list with O(log n) expected time for search, insert, and delete. Analyze the expected space usage. Compare empirically to a red-black tree.

**Problem 3.** Design and implement an O(n) time suffix array construction algorithm (SA-IS or the DC3/skew algorithm). Use it to solve the longest repeated substring problem in O(n) total time.

**Problem 4.** Prove that 3-COLORABILITY is NP-complete by reduction from 3-SAT. Give an explicit gadget construction and prove: (a) if the 3-SAT formula is satisfiable, then the graph is 3-colorable; (b) if the graph is 3-colorable, then the formula is satisfiable.

**Problem 5.** Implement a van Emde Boas tree for integers in [0, U). Support insert, delete, predecessor, successor in O(log log U). Benchmark against a red-black tree on U = 2^20.

**Problem 6.** (Capstone) Design, implement, and analyze a complete in-memory database index that supports: exact lookup, range query, predecessor/successor, insertion, and deletion — all in O(log n). Your implementation must handle duplicates correctly. Write a 2-page complexity analysis and correctness argument.

---

### Milestone Assessment — Module 1.2
*Pass threshold: 75%. Time: 4 hours. Notes allowed; no code execution.*

1. Prove: The height of a red-black tree with n internal nodes is at most 2 log₂(n+1).
2. Given T(n) = 2T(n/4) + √n: solve with Master Theorem, state the case, and verify with the recursion tree.
3. Implement (pseudocode) Dijkstra's algorithm. Trace on a 5-vertex graph. State the invariant maintained by the algorithm.
4. Explain (with proof sketch) why `BUILD-MAX-HEAP` runs in O(n) despite calling O(log n) `MAX-HEAPIFY` n times.
5. Describe the 5 cases in red-black tree insertion and explain what rotation/recoloring each requires.
6. Given the LCS DP recurrence, fill in the DP table for "AGGTAB" and "GXTXAYB". Reconstruct the LCS.
7. Write the exchange argument proof for the greedy activity selection algorithm.
8. Prove the comparison sort lower bound using decision trees.
9. Explain the 3 cases of the Master Theorem with examples of each.
10. Give a polynomial-time reduction from VERTEX-COVER to INDEPENDENT-SET.

---

---

# MODULE 1.3 — Systems Thinking: Unix/Linux Fundamentals

**Duration:** 4–6 weeks | **Hours/week:** 10 | **Total hours:** ~55

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Shotts — *The Linux Command Line*, 2nd ed. (free at linuxcommand.org)

---

#### Part I — Learning the Shell (Chapters 1–10)
**Read entirely.** These chapters build the foundational vocabulary.

- **Ch. 1:** Shell navigation. `ls`, `cd`, `pwd`. File types. Understand: everything in Linux is a file.
- **Ch. 2:** Navigation. Absolute vs relative paths. Directory shortcuts (`.`, `..`, `~`, `-`).
- **Ch. 3:** Exploring the system. `file`, `less`. The `/proc` and `/sys` pseudo-filesystems as gateways to kernel data.
- **Ch. 4:** Manipulating files. `cp`, `mv`, `rm`, `mkdir`, `ln` (hard vs symbolic links — understand the inode distinction).
- **Ch. 5:** Commands. `type`, `which`, `man`, `help`. Understanding the `$PATH` and how the shell resolves commands.
- **Ch. 6:** Redirection. `>`, `>>`, `<`, `2>`, `2>&1`, `/dev/null`. Piping as Unix philosophy.
- **Ch. 7:** Seeing the world as the shell sees it. Globbing, brace expansion, tilde expansion, command substitution `$()`, arithmetic expansion `$(())`.
- **Ch. 8:** Advanced keyboard tricks. Readline key bindings — know them; they are universal.
- **Ch. 9:** Permissions. `chmod` (octal and symbolic), `chown`, `chgrp`. SUID, SGID, sticky bit — understand the security implications of each. `umask`.
- **Ch. 10:** Processes. `ps`, `top`, `htop`, `kill`, `jobs`, `bg`, `fg`. Process states. Signals. Why SIGKILL cannot be caught.

#### Part II — Configuration and the Environment (Chapters 11–12)
- **Ch. 11:** The environment. `printenv`, `set`. `.bashrc` vs `.bash_profile`. `export`. PATH modification.
- **Ch. 12:** A gentle introduction to vi. Know: insert mode vs normal mode, basic navigation, saving, search.

#### Part III — Common Tasks and Essential Tools (Chapters 14–20)
- **Ch. 14:** Package management. `apt`/`dpkg` (Debian family). `rpm`/`dnf`/`yum` (Red Hat family). Package dependencies and security implications (supply chain attacks on packages).
- **Ch. 15:** Storage media. `mount`, `umount`, `df`, `du`, `fdisk`, `mkfs`, `fsck`. Filesystem types and their security trade-offs.
- **Ch. 16:** Networking. `ping`, `traceroute`, `ip addr`, `ss`, `netstat`. `ftp`, `wget`, `curl`. `ssh` — key-based authentication, `~/.ssh/config`, agent forwarding (and why it's dangerous).
- **Ch. 17:** Searching. `find` (with all its predicates: `-name`, `-mtime`, `-perm`, `-exec`). `locate`. `grep` (basic and extended regex). Using find for security auditing.
- **Ch. 18:** Archiving and backup. `tar` (know all common flag combinations), `gzip`, `bzip2`, `xz`, `zip`. Integrity verification with `sha256sum`.
- **Ch. 19:** Regular expressions. Character classes, anchors, quantifiers, alternation, grouping. Understand the difference between basic regex (BRE) and extended regex (ERE).
- **Ch. 20:** Text processing. `cat`, `sort`, `uniq`, `cut`, `paste`, `join`, `comm`, `diff`, `patch`, `tr`, `sed` (substitution, deletion, in-place edit), `awk` (field processing, pattern-action).

#### Part IV — Writing Shell Scripts (Chapters 24–36)
- **Ch. 24:** First script. Shebang line, `chmod +x`, `$PATH`.
- **Ch. 25:** Project inception. Design before coding (applies to scripts too).
- **Ch. 26:** Top-down design. Functions in bash. Local variables.
- **Ch. 27:** Flow control: if. String comparison, integer comparison, file tests (`-f`, `-d`, `-r`, `-w`, `-x`, `-s`, `-e`).
- **Ch. 28:** Reading keyboard input. `read`, positional parameters `$1`, `$@`, `$#`, `$0`. `getopts` for option parsing.
- **Ch. 29:** Flow control: while/until loops.
- **Ch. 30:** Troubleshooting scripts. `set -x` for tracing; `set -e` for fail-fast; `set -u` for unbound variable detection.
- **Ch. 31:** Flow control: case statements.
- **Ch. 32:** Positional parameters. `$*` vs `$@` — the subtle difference.
- **Ch. 33:** Flow control: for loops.
- **Ch. 34:** Strings and numbers. Parameter expansion tricks (`${var:-default}`, `${var:0:5}`, `${#var}`).
- **Ch. 36:** Arrays.

---

### Supplementary: Kerrisk — *The Linux Programming Interface*, Ch. 1–4
Read for the system programming perspective: how the kernel is organized, the POSIX standard, the role of system calls, and the C library wrapper functions. This is the bridge to Phase 3.

### Supplementary: OverTheWire Bandit
Complete levels 0–25. These are not optional. Each level teaches a Linux concept by requiring you to use it under light adversarial pressure.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Shell Fundamentals
- **Day 1:** Ch. 1–5. Navigate the filesystem. Create a directory hierarchy. Hard vs symbolic links.
- **Day 2:** Ch. 6–8. Redirection and pipes. Build a 5-step pipeline that processes a log file.
- **Day 3:** Ch. 9. Permissions deep-dive. Set SUID on a binary; observe behavior. Understand why SUID root is dangerous.
- **Day 4:** Ch. 10. Process management. Kill processes by name. Understand the signal table.
- **Day 5:** OverTheWire Bandit levels 0–10.
- **Day 6:** Problem Set 1.3 Tier 1, problems 1–8.
- **Day 7:** Rest.

### Week 2 — Text Processing & Networking
- **Day 1:** Ch. 16–18. SSH key setup. `find` for security auditing — find all SUID binaries on your system.
- **Day 2:** Ch. 19–20. Regex with grep. Write 10 regex patterns for log parsing.
- **Day 3:** `sed` deep dive — 10 sed one-liners. `awk` — field processing, aggregation, conditional actions.
- **Day 4:** Build a log analyzer in bash: parse `/var/log/auth.log` to summarize failed vs successful logins by IP.
- **Day 5:** OverTheWire Bandit levels 11–20.
- **Day 6:** Problem Set 1.3 Tier 1, problems 9–15.
- **Day 7:** Rest.

### Week 3 — Shell Scripting
- **Day 1:** Ch. 24–28. Write your first complete script: parse arguments, validate input, handle errors.
- **Day 2:** Ch. 29–33. Loops and case statements. Rewrite the log analyzer as a proper script.
- **Day 3:** Ch. 34, 36. Arrays and string manipulation. Write a script that manages a list of IP addresses with add/remove/search.
- **Day 4:** `cron` jobs — schedule the log analyzer to run daily. `systemd` timers as an alternative.
- **Day 5:** OverTheWire Bandit levels 21–25.
- **Day 6:** Problem Set 1.3 Tier 2, problems 1–7.
- **Day 7:** Rest.

### Week 4 — System Administration & Projects
- **Day 1:** System hardening script — audit users, permissions, SUID binaries, open ports, weak passwords.
- **Day 2:** Automated backup script — incremental, with SHA-256 integrity verification.
- **Day 3:** `systemd` — write a unit file for a custom service. Enable, start, check status.
- **Day 4:** `iptables`/`nftables` basics — write a simple firewall ruleset. Understand filter table, INPUT/OUTPUT/FORWARD chains.
- **Day 5:** Problem Set 1.3 Tier 2, problems 8–15.
- **Day 6:** Milestone assessment attempt.
- **Day 7:** Remediation.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Write a one-liner that finds all files modified in the last 24 hours under `/var/log`, sorts them by size (largest first), and prints the filename and size.

**Problem 2.** Write a one-liner that extracts all unique IP addresses from an Apache access log (`/var/log/apache2/access.log` format) and counts how many times each appears, sorted by frequency.

**Problem 3.** Write a bash script that: accepts a directory as an argument; recursively finds all files with SUID bit set; prints their full paths and owners; exits with code 1 if any are found.

**Problem 4.** Using `awk`, process a CSV file with columns `name,score,grade`. Print the name and score of everyone with a score above 85, formatted as `Name: Alice | Score: 92`.

**Problem 5.** Explain with examples: the difference between `2>`, `2>&1`, `|&`, and `>/dev/null 2>&1`. When would you use each?

**Problem 6.** Write a bash function `retry(n, cmd)` that runs `cmd` up to `n` times, stopping on success. It should print "Attempt i of n" before each try and "Failed after n attempts" if all fail.

**Problem 7.** What is the difference between a hard link and a symbolic link? What happens to each when the original file is deleted? Demonstrate both using `ln` and verify with `ls -li`.

**Problem 8.** Write a script that watches a directory and prints a line whenever a file is added or removed. Use a polling loop (no `inotifywait` — implement with `ls` and `diff`).

**Problem 9.** Using `sed` only: in a file of email addresses, replace all `@domain.com` with `@newdomain.org`. Ensure only the domain part is replaced (not any `@` in local parts).

**Problem 10.** Write a bash script that generates a random 20-character password using only `/dev/urandom`, `tr`, and `head`. No Python, no external tools.

**Problem 11.** Explain what each field means in the output of `ps aux`. What does the `S`, `R`, `D`, `Z` state indicator mean? How do you identify a zombie process?

**Problem 12.** Write a script that monitors CPU usage every 5 seconds and logs a warning to a file if any process exceeds 80% CPU. Use `ps` or `top -b -n 1`.

**Problem 13.** Using `find`, locate all files owned by root with the SUID bit set in `/usr/bin`. For each, print: path, permissions (octal), and file type.

**Problem 14.** Write a complete argument parser in bash that accepts: `-v` (verbose), `-o outfile` (output file), and one positional argument (input file). Validate that the input file exists.

**Problem 15.** Explain how SSH public key authentication works. What files are involved on the client and server? What permissions must they have? Why are the permissions required?

---

### Tier 2 — Intermediate

**Problem 1.** Write a bash script that detects if a host is up (ping), then enumerates its open TCP ports (using `/dev/tcp` — no nmap). For each open port, attempt a banner grab.

**Problem 2.** Write a log rotation script: rename `app.log` to `app.log.1`, compress the old log, delete logs older than 7 days, and restart a service. Handle errors at each step.

**Problem 3.** Using `awk`, implement a simple word-count program that reads from stdin and prints the top 10 words by frequency, excluding common stop words (a, the, is, are, ...).

**Problem 4.** Write a script that compares two directory trees and reports: files only in tree A, files only in tree B, and files in both that differ (by SHA-256 hash, not just timestamp).

**Problem 5.** Explain the Linux permission model completely: user/group/other bits, SUID, SGID, sticky bit. Give one legitimate and one security-relevant use case for each of SUID, SGID, and sticky bit.

**Problem 6.** Write a cron job that every hour: checks disk usage; if any partition exceeds 85%, sends a report to a log file with timestamp, partition name, usage percent, and the top 5 largest directories.

**Problem 7.** Using only bash built-ins and standard POSIX tools (no Python), implement a simple key-value store backed by a flat file. Support: `set key value`, `get key`, `delete key`, `list`.

---

---

# MODULE 1.4 — Object-Oriented Design & Software Engineering

**Duration:** 8–10 weeks | **Hours/week:** 10–12 | **Total hours:** ~100

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Martin — *Clean Code* (Prentice Hall)

---

**Chapter 1 — Clean Code**
Read entirely. Focus on: the definition of clean code from multiple master programmers. Understand why unclean code has a measurable cost. The key insight: "leaving the campsite cleaner than you found it."

**Chapter 2 — Meaningful Names**
Read entirely. Apply immediately to your own code. Rules: intention-revealing names, avoid disinformation, use pronounceable names, use searchable names, avoid encodings, pick one word per concept.

**Chapter 3 — Functions**
Read entirely. Rules: small (< 20 lines is ideal), do one thing, one level of abstraction per function, no side effects, prefer exceptions to error codes. These rules are directly applicable to security code where predictability is critical.

**Chapter 4 — Comments**
Read entirely. Key insight: good code rarely needs comments; comments often signal that code needs refactoring. Exception: public API documentation and explaining intent that cannot be expressed in code.

**Chapter 5 — Formatting**
Skim. Follow your language's style guide (PEP 8 for Python).

**Chapter 6 — Objects and Data Structures**
Read entirely. Focus on: the Law of Demeter; the distinction between objects (hide data, expose behavior) and data structures (expose data, have no significant behavior).

**Chapter 7 — Error Handling**
Read entirely. Focus on: use exceptions rather than return codes; provide context with exceptions; don't return null; don't pass null.

**Chapter 8 — Boundaries**
Read entirely. Focus on: how to use third-party code safely; the adapter pattern as a boundary; writing tests at the boundary.

**Chapter 9 — Unit Tests**
Read entirely. TDD laws: (1) write no production code before a failing test; (2) write only enough of a test to fail; (3) write only enough production code to pass the test. The F.I.R.S.T. principles: Fast, Independent, Repeatable, Self-Validating, Timely.

**Chapter 10 — Classes**
Read entirely. Single Responsibility Principle: a class should have one, and only one, reason to change. Cohesion: methods should use instance variables. Organizing for change.

**Chapter 11 — Systems**
Read entirely. Focus on: separating construction from use (dependency injection); scaling up; test-driving system architecture.

**Chapter 12 — Emergence**
Read entirely. Kent Beck's four rules of simple design: runs all tests; no duplication; expresses intent; minimizes classes and methods.

**Chapters 13–17 (Concurrency, Refactoring, Smells):**
Read 13 (Concurrency — a preview of Module 3.4), 17 (Smells and Heuristics — this is a reference to keep).

---

### Primary Text: Gamma, Helm, Johnson, Vlissides — *Design Patterns* (GoF)

---

**Introduction**
Read entirely. Focus on: the definition of a design pattern (name, problem, solution, consequences); the two principles (program to an interface, favor composition over inheritance); how to read the pattern catalog.

**Chapter 3 — Creational Patterns**
- **Abstract Factory:** Creates families of related objects. Understand the interface-based creation.
- **Builder:** Separates construction of a complex object from its representation. Used for: SQL query builders, test fixture builders, config builders.
- **Factory Method:** Defines an interface for object creation but lets subclasses decide the class. Connects to the Template Method pattern.
- **Prototype:** Creates objects by copying an existing instance. Understand deep vs shallow copy implications.
- **Singleton:** Ensures a single instance. Understand: when it's appropriate (global configuration, logging), when it's an anti-pattern (hard to test, tight coupling). Thread-safety implications.

**Chapter 4 — Structural Patterns**
- **Adapter:** Converts an interface to another. Canonical use: wrapping third-party libraries.
- **Bridge:** Decouples abstraction from implementation, both can vary independently.
- **Composite:** Treats individual objects and compositions uniformly. Use: file system, AST nodes in compiler, UI hierarchies.
- **Decorator:** Adds responsibilities dynamically without subclassing. Python's `@decorator` is a linguistic instantiation.
- **Facade:** Unified interface to a set of interfaces in a subsystem. Focus on: how it reduces coupling.
- **Flyweight:** Shares fine-grained objects efficiently. Relevant in JVM string interning, glyph rendering.
- **Proxy:** Surrogate for another object. Types: virtual, protection, remote, caching. Security proxies appear in access control.

**Chapter 5 — Behavioral Patterns**
- **Chain of Responsibility:** Pass request along chain until handler found. Use: middleware, event handlers.
- **Command:** Encapsulates a request as an object. Enables undo, queuing, logging.
- **Iterator:** Sequential access without exposing underlying structure. Python's iterator protocol.
- **Mediator:** Centralizes complex communications between objects.
- **Memento:** Captures and restores an object's state without violating encapsulation.
- **Observer:** One-to-many dependency — when one object changes, dependents are notified automatically. Event systems, MVC, reactive programming.
- **State:** Allows object to alter behavior when internal state changes. FSM implementation pattern.
- **Strategy:** Defines a family of algorithms, encapsulates each, makes them interchangeable. Security algorithms are natural strategies.
- **Template Method:** Defines algorithm skeleton in a base class; subclasses fill in steps. The "Hollywood Principle": don't call us, we'll call you.
- **Visitor:** Add operations to an object structure without modifying it. Used in AST traversal (compilers).

---

### Supplementary: Fowler — *Refactoring*, 2nd ed.
**Read:** Chapter 1 (the complete worked example — read every step), Chapter 2 (principles), Chapter 3 (bad smells — reference), then any 10 refactoring techniques from the catalog.

### Supplementary: McConnell — *Code Complete*, 2nd ed.
**Read:** Part II (Working Classes), Part III (Variables), Part IV (Statements), Chapter 22 (Developer Testing), Chapter 23 (Debugging). These provide the depth that Martin's book covers more concisely.

---

## Part B: Week-by-Week Study Schedule

### Weeks 1–2 — Clean Code Principles
- Read Clean Code Ch. 1–12. For each chapter, identify 3 violations in code you've previously written and refactor them.
- Lab: Code smell identification — take a 200-line "dirty" script and refactor it to Clean Code standards.
- TDD cycle: write all Module 1.3 projects using TDD from this point.

### Weeks 3–4 — Design Patterns I (Creational + Structural)
- Read GoF Introduction + Ch. 3–4. Implement each creational and structural pattern with a motivating example.
- Each pattern implementation: (1) identify a real scenario where it applies; (2) implement without the pattern; (3) implement with the pattern; (4) document what changed and why.

### Weeks 5–6 — Design Patterns II (Behavioral)
- Read GoF Ch. 5. Implement all behavioral patterns.
- Refactoring lab: given a 500-line class, decompose it using Observer, Strategy, and Command patterns.

### Weeks 7–8 — Git, Testing, CI, and Capstone
- Git deep-dive: branching strategies (Gitflow, trunk-based), rebase vs merge, bisect, stash, cherry-pick.
- Testing: property-based testing with `hypothesis`; mutation testing with `mutmut`.
- Build the library management system capstone using TDD + design patterns.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Design Pattern Recognition and Application

**Problem 1.** The following code violates the Single Responsibility Principle. Identify the violations and refactor into multiple classes, each with a single responsibility:
```python
class UserManager:
    def create_user(self, name, email, password):
        # validates email format
        # hashes password
        # writes to database
        # sends welcome email
        # logs the action
        pass
```

**Problem 2.** Implement the Observer pattern for a stock price monitor. `StockMarket` is the subject. Observers include: `PortfolioTracker` (updates portfolio value), `AlertSystem` (fires alert if price drops >10%), `Logger` (logs every price change). Write unit tests.

**Problem 3.** Implement the Strategy pattern for a data compression system. Strategies: `GZipStrategy`, `ZLibStrategy`, `NoCompressionStrategy`. The `FileCompressor` class accepts a strategy at construction time and applies it. Strategies must implement a common interface.

**Problem 4.** Implement the Decorator pattern for a security logging system. Base class: `DataStore` with `read(key)` and `write(key, value)`. Decorators: `EncryptedDataStore` (encrypts on write, decrypts on read), `LoggedDataStore` (logs all access), `CachedDataStore` (caches reads). These must be stackable in any order.

**Problem 5.** Identify 10 code smells in a provided piece of code (instructor-provided or an open-source project of your choice). For each: name the smell, explain why it is problematic, and describe how to fix it with reference to a specific refactoring technique from Fowler.

**Problem 6.** Implement the Command pattern for a text editor with unlimited undo/redo. Commands: `InsertText`, `DeleteText`, `ReplaceText`. Each command must implement `execute()` and `undo()`. Write unit tests for sequences of operations followed by complete undo.

**Problem 7.** Refactor a switch-on-type code block into the State pattern. Original:
```python
def handle_connection(conn, state):
    if state == "CONNECTING":  ...
    elif state == "CONNECTED":  ...
    elif state == "CLOSING":  ...
```
Implement each state as a class. Ensure state transitions are enforced.

**Problem 8.** Implement the Builder pattern for constructing HTTP requests. A `HttpRequestBuilder` should allow chaining: `.method("GET").url("...").header("k","v").body("...").build()`. The resulting `HttpRequest` object should be immutable.

**Problem 9.** Write a loop invariant and use it to prove the correctness of the following refactored binary search implementation. Then write 10 unit tests including boundary conditions:
```python
def binary_search(arr, target):
    lo, hi = 0, len(arr) - 1
    while lo <= hi:
        mid = (lo + hi) // 2
        if arr[mid] == target: return mid
        elif arr[mid] < target: lo = mid + 1
        else: hi = mid - 1
    return -1
```

**Problem 10.** Design a plugin system using the Abstract Factory pattern. The system loads "security scanner" plugins at runtime. Each plugin family implements: `Scanner` (scans a target), `Reporter` (formats findings), `Remediator` (applies fixes). Write the factory interface and two concrete families: `NetworkScannerFactory` and `WebScannerFactory`.

---

---

# MODULE 1.5 — Theory of Computation

**Duration:** 8–10 weeks | **Hours/week:** 10–12 | **Total hours:** ~100

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Sipser — *Introduction to the Theory of Computation*, 3rd ed.

This book is a model of mathematical clarity. Read every proof word-for-word at least once. Then restate it in your own words.

---

#### Chapter 0 — Introduction
Read entirely. Focus on: mathematical preliminaries (sets, sequences, tuples, functions, graphs, strings, languages). Understand: a **language** is a set of strings; a **computational problem** is a language; a **machine** accepts or rejects strings. This framing makes the entire book coherent.

#### Chapter 1 — Regular Languages

**Section 1.1 — Finite Automata**
Focus on: the formal definition of a DFA (5-tuple: Q, Σ, δ, q₀, F); the extended transition function δ*; the language L(M) accepted by M. Trace through DFA computation on 5 input strings before reading the examples. Design a DFA for: strings over {0,1} with an even number of 1s; strings ending in "01".

**Section 1.2 — Nondeterminism**
Focus on: the NFA formal definition; nondeterministic computation as a tree of possibilities; ε-transitions. The key theorem: every NFA has an equivalent DFA (subset construction). Work through the subset construction completely for 2 NFA examples. Prove that the number of states can grow exponentially (but exponential is still finite).

**Section 1.3 — Regular Expressions**
Focus on: the formal definition (base cases + union, concatenation, Kleene star); the equivalence of regex and NFAs. Be able to convert any regular expression to an NFA and vice versa. Design regex for: email addresses (simplified), IP addresses (simplified), C-style identifiers.

**Section 1.4 — Nonregular Languages**
Focus on: the Pumping Lemma for regular languages — understand it as a necessary condition for regularity (not sufficient); how to use it to prove a language is NOT regular. Prove the following are non-regular: {0^n 1^n | n ≥ 0}, {w | w has equal numbers of 0s and 1s}, {ww | w ∈ {0,1}*}.

---

#### Chapter 2 — Context-Free Languages

**Section 2.1 — Context-Free Grammars**
Focus on: the formal definition of a CFG (4-tuple: V, Σ, R, S); derivations; parse trees; ambiguity. Design CFGs for: arithmetic expressions, balanced parentheses, palindromes over {a,b}.

**Section 2.2 — Pushdown Automata**
Focus on: the formal definition of a PDA (6-tuple); the stack as the added power over finite automata; nondeterminism is essential for PDAs (unlike DFAs). Trace 3 PDA computations by hand.

**Section 2.3 — Non-Context-Free Languages**
Focus on: the Pumping Lemma for CFLs — harder to apply than the regular version. Prove {a^n b^n c^n | n ≥ 0} is not context-free.

**Section 2.4 — Deterministic Context-Free Languages**
Skim. Key point: DCFLs are a proper subset of CFLs. LR parsing (covered in Module 2.5) recognizes a subset of DCFLs.

---

#### Chapter 3 — The Church-Turing Thesis

**Section 3.1 — Turing Machines**
Focus on: the formal definition of a TM (7-tuple: Q, Σ, Γ, δ, q₀, q_accept, q_reject); computation; the tape as unbounded memory. Trace 3 TM computations by hand (yes, this is tedious — do it anyway). Design a TM that decides {0^{2^n} | n ≥ 0}.

**Section 3.2 — Variants of Turing Machines**
Focus on: multitape TMs (polynomial simulation by single-tape TMs); nondeterministic TMs; the equivalence of all reasonable computational models. Church-Turing Thesis: every effective computation is captured by a Turing machine.

**Section 3.3 — The Definition of Algorithm**
Skim. The key point: Hilbert's Entscheidungsproblem and why it matters for computability.

---

#### Chapter 4 — Decidability

**Section 4.1 — Decidable Languages**
Focus on: A_DFA (DFA acceptance problem), A_NFA, A_REX, E_DFA, EQ_DFA are all decidable — understand the algorithm for each and its time complexity. A_CFG is decidable; E_CFG is decidable; EQ_CFG is NOT decidable.

**Section 4.2 — Undecidability**
Focus on: A_TM (TM acceptance) is Turing-recognizable but NOT decidable. The diagonalization proof: construct a TM D that disagrees with every TM on its own encoding — this is one of the most profound proofs in mathematics. Make sure you can reconstruct this proof from memory.

---

#### Chapter 5 — Reducibility

**Section 5.1 — Undecidable Problems from Language Theory**
Focus on: HALT_TM is undecidable (reduce A_TM to HALT_TM). The reduction technique: to show language B is undecidable, assume B is decidable and use a decider for B to decide A_TM (contradiction).

**Section 5.3 — Mapping Reducibility**
Focus on: the formal definition of mapping reducibility (≤_m); the reduction as a computable function. Know: if A ≤_m B and B is decidable, then A is decidable. Contrapositive: if A is undecidable and A ≤_m B, then B is undecidable.

---

#### Chapter 7 — Time Complexity

**Section 7.1 — Measuring Complexity**
Focus on: time complexity for TMs; the class TIME(t(n)); polynomial time as a robust complexity class (invariant across reasonable models).

**Section 7.2 — The Class P**
Focus on: P = problems solvable in polynomial time. Examples: PATH (graph reachability), RELPRIME (gcd = 1), CFG membership (CYK algorithm). Why P is robust and important.

**Section 7.3 — The Class NP**
Focus on: the two equivalent definitions — verifier-based (certificate + polynomial verifier) and nondeterministic TM. Understand: NP is the class of languages with polynomial-time verifiable certificates. Examples: CLIQUE, HAMPATH, SUBSET-SUM.

**Section 7.4 — NP-Completeness**
Focus on: polynomial-time reduction; NP-hardness and NP-completeness; the Cook-Levin theorem: 3-SAT is NP-complete. Understanding the proof structure of NP-completeness is essential for security (intractability assumptions underpin cryptography).

**Section 7.5 — Additional NP-Complete Problems**
Focus on: reductions VERTEX-COVER, HAMPATH, UHAMPATH, SUBSET-SUM. Be able to construct a reduction for any two of these from memory.

---

#### Chapter 8 — Space Complexity *(read §8.1–8.3)*
Focus on: PSPACE, L, NL, coNL; Savitch's theorem; TQBF is PSPACE-complete. Understand the complexity hierarchy: L ⊆ NL ⊆ P ⊆ NP ⊆ PSPACE ⊆ EXPTIME.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Finite Automata
- **Day 1:** Sipser §1.1. Design 5 DFAs. Write formal 5-tuples, not just diagrams.
- **Day 2:** Sipser §1.2. Subset construction on 2 NFAs. Prove equivalence of DFAs and NFAs.
- **Day 3:** Sipser §1.3. Convert 3 regex to NFA. Convert 2 NFA to regex.
- **Day 4:** Build DFA/NFA simulator in Python. Accepts a formal automaton description and an input string.
- **Day 5:** Problem Set 1.5 Tier 1, problems 1–6.
- **Day 6:** JFLAP lab — build and test 5 automata.
- **Day 7:** Rest.

### Week 2 — Regular Languages: Limits
- **Day 1:** Sipser §1.4. Pumping Lemma. Prove 3 languages non-regular.
- **Day 2:** Closure properties of regular languages (under union, concatenation, complement, intersection). Prove each.
- **Day 3:** Myhill-Nerode theorem — a more powerful characterization of regular languages. Apply to minimize a DFA.
- **Day 4:** Problem Set 1.5 Tier 1, problems 7–12.
- **Day 5:** Connect to Module 2.5 preview: regular languages → lexical analysis → compilers.
- **Day 6:** Implement DFA minimization using the table-filling algorithm.
- **Day 7:** Rest.

### Week 3 — Context-Free Languages
- **Day 1:** Sipser §2.1. Design 5 CFGs. Derive 5 strings from each.
- **Day 2:** Sipser §2.2. Design 3 PDAs from CFGs. Trace computations.
- **Day 3:** Sipser §2.3. Pumping Lemma for CFLs. Prove 2 languages non-context-free.
- **Day 4:** Implement the CYK algorithm (O(n³) CFG membership test).
- **Day 5:** Problem Set 1.5 Tier 1, problems 13–18.
- **Day 6:** Design the grammar for a subset of Python arithmetic expressions. Parse several inputs manually.
- **Day 7:** Rest.

### Week 4 — Turing Machines & Decidability
- **Day 1:** Sipser §3.1. Design 3 TMs. Trace computations step by step.
- **Day 2:** Sipser §3.2. Multitape TMs. Simulate a 2-tape TM on a 1-tape TM.
- **Day 3:** Sipser §4.1. Decidable languages. The decider for A_DFA and A_CFG.
- **Day 4:** Sipser §4.2. Diagonalization proof that A_TM is undecidable. Reconstruct from memory.
- **Day 5:** Problem Set 1.5 Tier 2, problems 1–5.
- **Day 6:** Implement a TM simulator. Encode a TM as a string and simulate it.
- **Day 7:** Rest.

### Week 5 — Reducibility & Undecidability
- **Day 1:** Sipser §5.1. Reduction A_TM ≤_m HALT_TM. Reduction to E_TM.
- **Day 2:** Rice's theorem — prove it, understand its implications for static analysis.
- **Day 3:** Mapping reducibility — formal definition and 3 examples.
- **Day 4:** Problem Set 1.5 Tier 2, problems 6–10.
- **Day 5:** Connect to security: why antivirus cannot perfectly detect all malware (Rice's theorem).
- **Day 6:** Rest.
- **Day 7:** Rest.

### Week 6 — Complexity Theory
- **Day 1:** Sipser §7.1–7.2. P definition and examples.
- **Day 2:** Sipser §7.3. NP — verifier definition and NTM definition. Prove equivalence.
- **Day 3:** Sipser §7.4. Cook-Levin theorem — 3-SAT is NP-complete. Work through the encoding.
- **Day 4:** Sipser §7.5. Reductions: 3-SAT → CLIQUE, 3-SAT → VERTEX-COVER.
- **Day 5:** Problem Set 1.5 Tier 2, problems 11–15.
- **Day 6:** Sipser §8.1–8.3. PSPACE and the complexity hierarchy.
- **Day 7:** Rest.

### Weeks 7–8 — Integration, Proofs Portfolio, and Milestone
- Complete all Tier 3 problems.
- Write a 2-page essay: "Why NP-Completeness matters for cryptography and security."
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Design a DFA over Σ = {0,1} that accepts all strings where the number of 0s is divisible by 3. Give the formal 5-tuple and the state transition diagram.

**Problem 2.** Convert the following NFA to an equivalent DFA using the subset construction. NFA: states {q0, q1, q2}, alphabet {a, b}, transitions: δ(q0,a) = {q0,q1}, δ(q0,b) = {q0}, δ(q1,b) = {q2}, start: q0, accept: {q2}.

**Problem 3.** Use the Pumping Lemma to prove that L = {0^n 1^n | n ≥ 0} is not regular.

**Problem 4.** Design a CFG for the language L = {a^i b^j c^k | i = j or j = k, i,j,k ≥ 0}.

**Problem 5.** Use the Pumping Lemma for CFLs to prove that L = {a^n b^n c^n | n ≥ 1} is not context-free.

**Problem 6.** Describe a Turing Machine that decides L = {w#w | w ∈ {0,1}*}. Give the states, transitions for key cases, and explain the operation.

**Problem 7.** Prove that A_TM = {⟨M,w⟩ | M is a TM that accepts w} is Turing-recognizable but not decidable.

**Problem 8.** Prove: if A ≤_m B and B is decidable, then A is decidable. Use this to show: if A is undecidable and A ≤_m B, then B is undecidable.

**Problem 9.** Prove CLIQUE is in NP. Give an explicit polynomial-time verifier (certificate structure and verification algorithm).

**Problem 10.** Prove that VERTEX-COVER is NP-complete by reduction from CLIQUE.

---

### Tier 2 — Intermediate

**Problem 1.** Prove the Myhill-Nerode theorem: A language L is regular if and only if it has a finite number of equivalence classes under the relation x ~_L y iff (∀z: xz ∈ L ↔ yz ∈ L). Use this to prove {0^n 1^n} is non-regular without the Pumping Lemma.

**Problem 2.** Prove that the class of regular languages is closed under complementation, intersection, and reversal. For each: describe the construction and prove its correctness.

**Problem 3.** Show that the Post Correspondence Problem (PCP) is undecidable by reducing A_TM to it. (You may follow the proof outline in Sipser §5.2; write it in your own words.)

**Problem 4.** State Rice's Theorem formally. Prove it. Apply it: explain why no algorithm can always correctly determine whether an arbitrary program contains a buffer overflow.

**Problem 5.** Prove that SUBSET-SUM is NP-complete. (Reduce from 3-SAT or from EXACT-COVER.)

**Problem 6.** Prove: PSPACE is closed under complementation. (Use the fact that NPSPACE = PSPACE by Savitch's theorem.)

**Problem 7.** Explain the connection between context-free grammars and pushdown automata. Prove that if a language is accepted by a PDA, it is generated by some CFG. (Give the construction.)

---

---

# MODULES 1.6 & 1.7 — Computer Networks & Databases

*Due to the substantial length of Modules 1.1–1.5 above, the full reading lists, weekly schedules, and problem sets for Modules 1.6 and 1.7 follow below in condensed-but-complete form.*

---

# MODULE 1.6 — Computer Networks

**Duration:** 10–12 weeks | **Hours/week:** 10–12 | **Total hours:** ~130

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Kurose & Ross — *Computer Networking: A Top-Down Approach*, 8th ed.

---

**Chapter 1 — Computer Networks and the Internet**
Read entirely. Focus on: the packet switching vs circuit switching distinction and why packet switching wins for data; the layered architecture and what each layer's service model is; propagation delay vs transmission delay vs processing delay — derive the formula and apply it. The "what's the internet" framing at the start sets up the entire book.

**Chapter 2 — Application Layer**
Read §2.1–2.5, §2.7. Focus on:
- §2.1: Client-server vs P2P architecture. The socket as the abstraction boundary between application and transport layers.
- §2.2: HTTP — non-persistent vs persistent connections; HTTP request/response format; HTTP methods (GET, POST, PUT, DELETE, HEAD, OPTIONS, PATCH); status codes (memorize 200, 301, 302, 400, 401, 403, 404, 500, 503); cookies; web caching.
- §2.3: DNS — resource record types (A, AAAA, MX, CNAME, NS, SOA, TXT, PTR); the full resolution chain (recursive vs iterative); caching and TTL. Understand: DNS queries are the backbone of C2 channel analysis in Module 4.6.
- §2.4: SMTP — the three phases; MIME extensions; POP3 vs IMAP.
- §2.5: Socket programming with UDP and TCP.
- §2.7: P2P file distribution — BitTorrent protocol; DHT (Distributed Hash Table).

**Chapter 3 — Transport Layer**
Read entirely — this is the most important chapter for security.
- §3.1–3.2: Multiplexing and demultiplexing; UDP — the header format; when to use UDP.
- §3.3: Connectionless transport: UDP.
- §3.4: Principles of reliable data transfer: rdt 1.0 → 2.0 → 2.1 → 2.2 → 3.0 → Go-Back-N → Selective Repeat. Follow each protocol's state machine.
- §3.5: Connection-oriented transport: TCP — the segment structure; the three-way handshake; the four-way teardown; sequence and acknowledgment numbers; RTT estimation and timeout; Nagle algorithm. Know the TCP state machine completely (LISTEN, SYN_SENT, SYN_RCVD, ESTABLISHED, FIN_WAIT_1, FIN_WAIT_2, CLOSE_WAIT, CLOSING, LAST_ACK, TIME_WAIT, CLOSED).
- §3.6–3.7: Flow control (receive window); congestion control (slow start, congestion avoidance, fast retransmit, fast recovery — CUBIC and BBR as modern alternatives).

**Chapter 4 — The Network Layer: Data Plane**
Read §4.1–4.3. Focus on:
- §4.1: Overview — data plane vs control plane distinction.
- §4.2: Router architecture: input ports, switching fabric, output ports, scheduling; head-of-line blocking.
- §4.3: IPv4 — datagram format (every field); fragmentation and reassembly; IPv4 addressing (subnetting, CIDR notation, longest prefix match); NAT (and its security implications — how it breaks end-to-end connectivity and how attackers abuse it).

**Chapter 5 — The Network Layer: Control Plane**
Read §5.1–5.4.
- §5.2: Routing algorithms — link-state (Dijkstra) vs distance-vector (Bellman-Ford). Understand the count-to-infinity problem and split horizon fix.
- §5.3: OSPF (link-state) — authentication, flooding, areas.
- §5.4: BGP — eBGP vs iBGP; path attributes (AS_PATH, NEXT_HOP, LOCAL_PREF, MED); route filtering; BGP security issues (route hijacking).

**Chapter 6 — The Link Layer and LANs**
Read §6.1–6.4.
- §6.1: Link layer services; error detection (parity, CRC — understand CRC computation and why it detects burst errors).
- §6.3: Multiple access protocols — CSMA/CD (Ethernet), CSMA/CA (WiFi).
- §6.4: Switched LAN — MAC addresses; ARP protocol and its cache; Ethernet frame format; VLANs; spanning tree protocol (STP).

**Chapter 7 — Wireless and Mobile Networks**
Read §7.1–7.4.
- §7.1: Introduction to wireless links and characteristics (hidden terminal problem).
- §7.2: WiFi (802.11) — 802.11 frame format; association; WPA2/WPA3 overview (detailed in Module 4.2).
- §7.3: Cellular networks overview.
- §7.4: Mobility management.

**Chapter 8 — Security in Computer Networks**
Read entirely — this directly connects to Phase 4.
- §8.1: Principles: confidentiality, authentication, message integrity, access and availability.
- §8.2: Cryptography basics (connect to Module 4.1 — treat this as a preview).
- §8.3: Message integrity: cryptographic hash functions, MACs, digital signatures.
- §8.4: Endpoint authentication: challenge-response; nonces.
- §8.5: Email security: PGP.
- §8.6: TLS — the TLS handshake at this level of detail. (Full TLS 1.3 analysis in Module 4.1.)
- §8.7: Network layer security: IPSec (AH and ESP).
- §8.8: Operational security: firewalls (packet filters, stateful, application-level gateways); IDS.

---

### Supplementary: Stevens, Fenner & Rudoff — *Unix Network Programming, Vol. 1*, 3rd ed.
**Read:** Ch. 1–6 (socket API, TCP connection lifecycle), Ch. 8 (UDP sockets), Ch. 14–15 (advanced I/O), Ch. 26 (threads and sockets). This bridges networking theory to systems programming in Phase 3.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Application Layer
- K&R Ch. 1 (overview) + Ch. 2 (HTTP, DNS). Implement an HTTP/1.1 client in Python raw sockets.
- DNS resolver walkthrough: trace a resolution with Wireshark. Identify every packet type.

### Week 2 — Transport Layer: UDP and TCP
- K&R Ch. 3 (entire). Implement UDP echo server/client. Implement TCP echo server with concurrent connections.
- TCP state machine lab: use Wireshark to capture a TCP handshake, FIN teardown, RST.

### Week 3 — TCP Internals: Reliability, Flow Control, Congestion
- Study rdt protocol evolution. Write a simulated reliable transport over an unreliable channel.
- Congestion control: trace CWND evolution through slow start, congestion avoidance, and recovery.

### Week 4 — Network Layer: IP, NAT, Routing
- K&R Ch. 4–5. Subnetting exercises (30 subnets, compute network, broadcast, host range for each).
- Implement longest-prefix-match lookup for an IP routing table in Python.
- BGP hijacking: research the Pakistan Telecom / YouTube incident (2008).

### Week 5 — Link Layer, ARP, Ethernet, WiFi
- K&R Ch. 6–7. ARP poisoning theory (connected to Module 4.2).
- CRC computation by hand on a 4-byte example.
- Build a simple ARP monitor in Python using raw sockets.

### Week 6 — Security Preview
- K&R Ch. 8. TLS handshake walkthrough. Read RFC 8446 §2 (TLS 1.3 overview section).

### Weeks 7–9 — Projects and Capstone
- **Project 1:** HTTP/1.1 server from raw TCP (handle GET, HEAD, 404, 403).
- **Project 2:** TCP port scanner with banner grabbing.
- **Project 3:** PCAP analyzer — parse a `.pcap` file and report protocol statistics.
- **Project 4:** DNS resolver — full iterative resolution chain.

### Weeks 10–12 — Network Simulation, Review, Milestone
- GNS3/EVE-NG lab: build a 3-router topology, configure OSPF, verify routing tables.
- Network monitoring agent capstone.
- Milestone assessment.

---

## Part C: Graded Problem Sets (Selected)

**Problem 1.** A file of 1 MB is to be transmitted over a link with bandwidth 1 Mbps and propagation delay 10ms. (a) What is the transmission delay? (b) Total delay? (c) If the file is split into 1000 packets of 1KB each, and each hop takes 20ms propagation delay, compute the end-to-end delay for a 3-hop path assuming store-and-forward switching.

**Problem 2.** Write the HTTP request and expected HTTP response for: (a) GET request for `/index.html` on `example.com`; (b) POST request with JSON body to `/api/login`.

**Problem 3.** Trace the complete DNS resolution for `www.cs.mit.edu` from a client with no cache. List every DNS server queried and every response type.

**Problem 4.** Subnet the network `192.168.10.0/24` into 8 equal subnets. For each subnet: network address, broadcast address, first and last host addresses, subnet mask.

**Problem 5.** Trace the TCP three-way handshake between client (port 54321) and server (port 443). Write out each segment with SYN/ACK/FIN flags, sequence numbers, and acknowledgment numbers (start with ISN = 1000 for client, ISN = 5000 for server).

**Problem 6.** Explain ARP poisoning: what ARP packets does an attacker send, what happens to victim A's ARP cache, and what does the attacker now receive? What is the correct defense?

**Problem 7.** Implement in Python (using raw sockets or `scapy`): a function that sends an ICMP echo request to a host and measures round-trip time. Handle timeouts. Test against 3 hosts.

**Problem 8.** Explain BGP route hijacking. In the 2008 YouTube incident, how did Pakistan Telecom's announcement of a more-specific prefix cause global routing disruption? What is RPKI and how does it prevent this?

**Problem 9.** A TCP sender is in slow start with a window size of 1 MSS. Describe the window growth for the first 6 RTTs, assuming no loss. At what window size does it switch to congestion avoidance (ssthresh = 16 MSS)?

**Problem 10.** Implement an HTTP/1.1 server in Python using raw `socket` (no `http.server`). It must: handle GET and HEAD requests; serve files from a configurable directory; return 404 for missing files; return 403 for files outside the serving directory (path traversal prevention). Write 5 integration tests.

---

# MODULE 1.7 — Databases & Storage Systems

**Duration:** 8–10 weeks | **Hours/week:** 10 | **Total hours:** ~90

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Ramakrishnan & Gehrke — *Database Management Systems*, 3rd ed.

---

**Chapter 1 — Overview of Database Systems**
Read entirely. Focus on: why databases over flat files (data independence, concurrent access, crash recovery, security); the three-schema architecture; the roles of DBA, application programmer, end user.

**Chapter 2 — Introduction to the Relational Model**
Read entirely. Focus on: the relation as a mathematical set of tuples; domain, attribute, schema, instance; keys (superkey, candidate key, primary key, foreign key); integrity constraints. The relational model is grounded in first-order logic — connect to Module 0.1.

**Chapter 3 — Relational Algebra and Calculus**
Read §3.1–3.4. Focus on: selection σ, projection π, cross product ×, rename ρ, union ∪, difference −, join ⋈. Understand: SQL is syntactic sugar over relational algebra. Translate SQL queries to relational algebra and back.

**Chapter 4 — Relational Data Schemas**
Read §4.1–4.3. Focus on: defining database schemas in SQL DDL; constraints (NOT NULL, UNIQUE, PRIMARY KEY, FOREIGN KEY, CHECK); referential integrity actions (CASCADE, SET NULL, SET DEFAULT).

**Chapter 5 — SQL: Queries, Constraints, Triggers**
Read entirely — this is the practical core of the module.
- §5.1–5.2: Basic SQL — SELECT, FROM, WHERE, DISTINCT, ORDER BY, LIMIT. The difference between WHERE (row filter) and HAVING (group filter).
- §5.3: UNION, INTERSECT, EXCEPT.
- §5.4–5.5: Nested subqueries — correlated vs uncorrelated; EXISTS; IN; ANY/ALL.
- §5.6: Aggregation: GROUP BY, COUNT, SUM, AVG, MIN, MAX.
- §5.7: NULL handling — three-valued logic (TRUE, FALSE, UNKNOWN); IS NULL vs = NULL.
- §5.8: Triggers — BEFORE/AFTER INSERT/UPDATE/DELETE; row-level vs statement-level.
- **Window functions** (supplement with PostgreSQL documentation): ROW_NUMBER(), RANK(), DENSE_RANK(), LAG(), LEAD(), FIRST_VALUE(), SUM OVER (PARTITION BY ... ORDER BY ...).
- **Recursive CTEs** (supplement): WITH RECURSIVE for hierarchical data.

**Chapter 6 — Database Application Development**
Read §6.1–6.2. Focus on: embedded SQL; dynamic SQL; SQL injection — understand EXACTLY why string interpolation into SQL queries is dangerous and why parameterized queries fix it.

**Chapter 8 — Overview of Storage and Indexing**
Read entirely. Focus on: heap files; page layout (N-ary storage model); slotted page structure; buffer pool (LRU replacement policy); I/O cost model; the distinction between clustered and unclustered indexes.

**Chapter 9 — Storing Data: Disks and Files**
Read §9.1–9.3. Focus on: disk geometry (seek time, rotational latency, transfer time); the disk I/O cost model; RAID levels (0, 1, 5, 6, 10) and their trade-offs.

**Chapter 10 — Tree-Structured Indexing**
Read entirely. Focus on:
- B+ tree structure: internal nodes (search keys + pointers), leaf nodes (search keys + record pointers + sibling pointer), root.
- Invariant: every internal node between root and leaf is at least half-full.
- Search: O(log_d n) where d is the order.
- Insertion: find leaf, insert, split if overflow, propagate up.
- Deletion: find leaf, delete, redistribute or merge if underflow.
- Clustered vs unclustered B+ tree: a clustered index forces the heap file to be sorted by the index key.

**Chapter 11 — Hash-Based Indexing**
Read §11.1–11.4. Focus on: static hashing, extendible hashing, linear hashing. Understand when hash indexes outperform B+ trees (equality queries) and when they don't (range queries).

**Chapter 12 — External Sorting**
Read §12.1–12.4. Focus on: external merge sort (the basis for sort-merge join); pass 0 (sort runs); passes 1..k (merge B-1 runs at a time); I/O cost analysis.

**Chapter 13 — Evaluation of Relational Operators**
Read §13.1–13.4. Focus on: nested loop join, block nested loop join, index nested loop join, sort-merge join, hash join. Know the I/O cost formula for each.

**Chapter 14 — A Typical Relational Query Optimizer**
Read §14.1–14.3. Focus on: the query optimization pipeline (parse → logical plan → physical plan → execute); the EXPLAIN command output; statistics (relation cardinality, histogram-based selectivity estimation).

**Chapter 16 — Overview of Transaction Management**
Read entirely. Focus on: ACID properties (atomicity, consistency, isolation, durability) — define each precisely; transactions and schedules; serializability as the gold standard.

**Chapter 17 — Concurrency Control**
Read §17.1–17.3. Focus on: lock-based concurrency control; two-phase locking (2PL) and its guarantee of conflict serializability; deadlock detection and prevention; timestamp-based protocols; MVCC (Multi-Version Concurrency Control) as used by PostgreSQL.

**Chapter 18 — Crash Recovery**
Read §18.1–18.4. Focus on: the steal/no-steal and force/no-force policies; write-ahead logging (WAL); the ARIES recovery algorithm (Analysis → Redo → Undo).

---

### Supplementary: Kleppmann — *Designing Data-Intensive Applications* (O'Reilly)
**Read:** Ch. 1 (Reliable, Scalable, Maintainable), Ch. 2 (Data Models), Ch. 3 (Storage and Retrieval — LSM trees vs B-trees), Ch. 5 (Replication — leader-follower, multi-leader, leaderless), Ch. 6 (Partitioning), Ch. 7 (Transactions — isolation levels in depth), Ch. 9 (Consistency and Consensus — CAP theorem properly explained).

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Relational Model and SQL Basics
- R&G Ch. 1–3. Relational algebra. Translate 10 SQL queries to relational algebra.
- Set up PostgreSQL. Load sample databases (Northwind, Chinook, or IMDB).

### Weeks 2–3 — SQL in Depth
- R&G Ch. 5. Write 30 SQL queries covering all features. Use `EXPLAIN ANALYZE` on each.
- Window functions: 10 queries using ROW_NUMBER, LAG, LEAD, PARTITION BY.
- Recursive CTEs: organizational hierarchy traversal, graph shortest path in SQL.

### Week 4 — Storage Internals
- R&G Ch. 8–11. B+ tree implementation (insert and search). Visualize page splits.
- External merge sort implementation — sort a 1 GB file using only 10 MB of memory.

### Week 5 — Query Processing and Optimization
- R&G Ch. 12–14. Implement nested loop join and hash join; benchmark on 10K × 10K rows.
- `EXPLAIN` analysis: for 5 complex queries, explain the query plan chosen by PostgreSQL.

### Week 6 — Transactions and Recovery
- R&G Ch. 16–18. Simulate a crash in a write-ahead log implementation.
- Reproduce isolation level anomalies: dirty read, non-repeatable read, phantom read using PostgreSQL isolation level settings.

### Weeks 7–8 — NoSQL and Security
- Kleppmann Ch. 2, 5, 9. Set up MongoDB and Redis; implement the same data model in both.
- SQL injection lab: exploit DVWA's SQL injection module with 5 different attack vectors.
- Implement a parameterized query library that prevents SQL injection.

### Weeks 9–10 — Projects and Milestone
- B+ tree from scratch — complete project.
- Mini relational database engine.
- SQL injection exploit and fix.
- Milestone assessment.

---

## Part C: Graded Problem Sets (Selected)

**Problem 1.** Write SQL to: (a) find the top 5 customers by total order value in the last 6 months; (b) for each customer, show their rank, running total, and percentage of total revenue — use window functions.

**Problem 2.** Explain the difference between a clustered and unclustered B+ tree index. When would you choose one over the other? Give a concrete example where choosing wrong leads to a 10× performance regression.

**Problem 3.** Describe a schedule of 2 transactions that is conflict-serializable but not view-serializable. Draw the precedence graph and verify there are no cycles.

**Problem 4.** Explain the ARIES recovery algorithm's three phases. What is the purpose of the dirty page table and the transaction table during recovery?

**Problem 5.** Design a normalized relational schema (to BCNF) for a university course registration system. Include: students, courses, sections, instructors, enrollments, and grades. List all functional dependencies and show they are all in BCNF.

**Problem 6.** Given the SQL query:
```sql
SELECT c.name, COUNT(o.id), SUM(o.amount)
FROM customers c
LEFT JOIN orders o ON c.id = o.customer_id
WHERE o.created_at > '2024-01-01'
GROUP BY c.name
HAVING SUM(o.amount) > 1000
ORDER BY 3 DESC;
```
(a) Convert to relational algebra. (b) Explain what happens to customers with no orders after 2024-01-01. (c) Explain whether the LEFT JOIN actually behaves as a LEFT JOIN here and why.

**Problem 7.** Explain in detail how this SQL query is vulnerable to SQL injection and how parameterized queries prevent it:
```python
query = f"SELECT * FROM users WHERE username = '{user_input}' AND password = '{pw_input}'"
```
Show 3 different injection payloads that would bypass authentication.

---

# Phase 1 — Global Capstone Projects

Complete all three before beginning Phase 2.

---

## Capstone 1-A: Complete Algorithm Library

**Objective:** A production-quality Python package implementing every algorithm and data structure from Module 1.2, with:
- Full test suites (≥95% coverage, including edge cases)
- Comprehensive docstrings with complexity analysis
- Benchmarking harness that produces plots comparing algorithms on varying input sizes
- A CLI tool that, given a problem description and input size, recommends the appropriate algorithm with justification

---

## Capstone 1-B: Mini Network Protocol Implementation

**Objective:** Implement the following from raw TCP/UDP sockets (no framework libraries):
- An HTTP/1.1 server that serves static files, handles concurrent connections with threading, correctly implements path traversal prevention, and returns appropriate status codes
- A DNS stub resolver that performs full iterative resolution
- A TCP port scanner that identifies open ports and grabs service banners
- A simple packet sniffer (using `socket.AF_PACKET` on Linux) that parses Ethernet, IP, and TCP headers and prints a one-line summary per packet

All tools must include man-page style usage documentation and handle errors gracefully.

---

## Capstone 1-C: Mini Relational Database Engine

**Objective:** Implement in Python:
- A SQL-like query parser (subset: SELECT, FROM, WHERE, ORDER BY, LIMIT, JOIN)
- A logical query plan (relational algebra tree)
- A physical execution engine (nested loop join, sequential scan, index scan)
- A B+ tree index
- A simple heap file storage with page-level management
- A write-ahead log for atomicity

The database must correctly store, retrieve, and query a 100,000-row dataset without loading it all into memory at once.

---

*End of Phase 1 Complete Study Package*
*Next: Phase 2 — Computer Engineering & Architecture*

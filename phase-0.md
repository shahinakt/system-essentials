# Phase 0 — Complete Study Package
## Mathematical & Logical Foundations
### Chapter Reading Lists · Weekly Schedules · Graded Problem Sets

---

> **How to use this document**
> Each module has three sections: (1) the chapter-by-chapter reading list with focus notes, (2) a week-by-week study schedule, and (3) a graded problem set with difficulty tiers. Work sequentially within each module. Do not begin Module 0.2 until you pass the Module 0.1 milestone assessment. Phase 0 has no shortcuts — every concept here reappears in Phases 1–4.

---

# MODULE 0.1 — Discrete Mathematics & Logic

**Duration:** 8–10 weeks | **Hours/week:** 10–12 | **Total hours:** ~100

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Rosen — *Discrete Mathematics and Its Applications*, 8th ed.

---

#### Chapter 1 — The Foundations: Logic and Proofs

**Read:** Sections 1.1–1.8 (entire chapter)

**Section 1.1 — Propositional Logic**
Focus on: truth tables for all five connectives (¬, ∧, ∨, →, ↔); the precise semantics of implication (p → q is only false when p is true and q is false — this trips most beginners); tautologies and contradictions. Do every example before reading the solution.

**Section 1.2 — Applications of Propositional Logic**
Focus on: translating English sentences into propositional logic. This is a skill that requires practice, not just reading. Spend extra time on system specifications and logic puzzles.

**Section 1.3 — Propositional Equivalences**
Focus on: De Morgan's laws (memorize and prove); the distributive laws; contrapositive vs converse vs inverse (only the contrapositive is logically equivalent to the original). These recur constantly in algorithm correctness proofs and hardware design.

**Section 1.4 — Predicates and Quantifiers**
Focus on: the difference between ∀ and ∃; the meaning of nested quantifiers; the scope of quantifiers; translating between English and predicate logic. Pay close attention to the order of ∀x∃y vs ∃y∀x — they mean different things.

**Section 1.5 — Nested Quantifiers**
Focus on: constructing and negating nested quantifier statements. Negating "For all x, there exists y such that P(x,y)" requires methodical application of De Morgan's for quantifiers. Work all examples by hand.

**Section 1.6 — Rules of Inference**
Focus on: modus ponens, modus tollens, hypothetical syllogism, disjunctive syllogism, addition, simplification, conjunction, resolution. These are the atomic operations of formal proof. Identify which rule justifies each step in the provided examples.

**Section 1.7 — Introduction to Proofs**
Focus on: the structure of a direct proof; when to use proof by contraposition vs direct proof; the key insight that a proof is a sequence of justified steps, not an argument. Read carefully — this section is foundational to everything that follows.

**Section 1.8 — Proof Methods and Strategy**
Focus on: proof by contradiction (assume ¬p, derive a contradiction); exhaustive proof; proof by cases; existence proofs (constructive vs non-constructive). Understand why √2 is irrational — this proof appears in almost every advanced textbook.

---

#### Chapter 2 — Basic Structures: Sets, Functions, Sequences, Sums, and Matrices

**Read:** Sections 2.1–2.5

**Section 2.1 — Sets**
Focus on: set-builder notation; Venn diagrams as intuition only (proofs require logic, not pictures); subset vs proper subset; power set; Cartesian product. Know the cardinality of a power set: |P(A)| = 2^|A|.

**Section 2.2 — Set Operations**
Focus on: union, intersection, difference, complement; De Morgan's laws for sets (parallel to propositional logic — note this carefully); symmetric difference. Prove set identities using membership tables and element-chasing proofs (both methods, not just one).

**Section 2.3 — Functions**
Focus on: domain, codomain, range (these three are distinct); injective (one-to-one), surjective (onto), bijective; composition; inverse functions. The condition for invertibility is bijectivity. This section has direct application to cryptography (bijective functions as permutations, surjectivity in hash functions).

**Section 2.4 — Sequences and Summations**
Focus on: arithmetic and geometric progressions; summation notation and closed-form evaluation; telescoping sums. These appear in every algorithm analysis (summing a geometric series to analyze recursion trees).

**Section 2.5 — Cardinality of Sets**
Focus on: countable vs uncountable sets; the diagonal argument (Cantor) showing ℝ is uncountable. This connects to computability in Module 1.5.

**Skip:** Section 2.6 (matrices) — covered more thoroughly in Module 0.2.

---

#### Chapter 3 — Algorithms

**Read:** Sections 3.1–3.3 only (algorithmic complexity is covered more deeply in Module 1.2)

**Section 3.1 — Algorithms**
Read as a warm-up and orientation. Focus on the concept of a well-defined procedure and pseudocode conventions used throughout the rest of the book.

**Section 3.2 — The Growth of Functions**
Focus on: Big-O definition (formal ε-δ style); Big-Omega; Big-Theta; the hierarchy of growth rates (1 < log n < n < n log n < n² < 2^n < n!). Do not just memorize — prove the relationships using the definitions.

**Section 3.3 — Complexity of Algorithms**
Skim. The deep treatment is in Module 1.2.

---

#### Chapter 4 — Number Theory and Cryptography

**Read:** Sections 4.1–4.6 (entire chapter — critical for cryptography in Phase 4)

**Section 4.1 — Divisibility and Modular Arithmetic**
Focus on: the division algorithm (a = dq + r); divisibility properties; modular arithmetic defined as equivalence classes; modular addition and multiplication. This is the algebraic foundation of every symmetric cipher.

**Section 4.2 — Integer Representations and Algorithms**
Focus on: base conversion algorithms; binary arithmetic; hex representation. Understand why two's complement works — connect it to Module 2.1.

**Section 4.3 — Primes and Greatest Common Divisors**
Focus on: the Fundamental Theorem of Arithmetic (unique prime factorization); the Euclidean algorithm for GCD — understand why it terminates and why it's correct; the Extended Euclidean Algorithm for finding Bézout coefficients. This is directly used in RSA key generation.

**Section 4.4 — Solving Congruences**
Focus on: linear congruences; the Chinese Remainder Theorem (proof and application); solving systems of congruences. CRT is used in RSA optimization (Garner's formula) and in competitive programming.

**Section 4.5 — Applications of Congruences**
Focus on: hashing applications; check digit schemes. Skim pseudorandom number generation — covered more in Module 0.3.

**Section 4.6 — Cryptography**
Focus on: Caesar cipher (trivial but illustrates substitution); affine cipher; the RSA algorithm as presented. This is a preview — the full cryptographic treatment is Module 4.1. Here, focus on understanding the mathematical structure, not the security analysis.

---

#### Chapter 5 — Induction and Recursion

**Read:** Sections 5.1–5.4 (entire chapter — essential)

**Section 5.1 — Mathematical Induction**
Focus on: the structure of an inductive proof (base case, inductive hypothesis, inductive step); why it works (well-ordering principle); common mistakes (forgetting the base case, assuming what you're trying to prove). Prove every example independently before reading the solution.

**Section 5.2 — Strong Induction and Well-Ordering**
Focus on: when strong induction is needed vs weak induction; the equivalence of strong induction, weak induction, and the well-ordering principle; using strong induction to prove properties of recursive algorithms.

**Section 5.3 — Recursive Definitions and Structural Induction**
Focus on: defining sets and functions recursively; structural induction as induction over recursive structure. This connects directly to how abstract syntax trees (compilers) and grammars (Module 1.5) are defined.

**Section 5.4 — Recursive Algorithms**
Focus on: writing and reasoning about recursive algorithms; the merge sort correctness proof; the Euclidean algorithm as a recursive algorithm. Do not skip the recursive binary search proof — it is a model for how to reason about recursive correctness.

---

#### Chapter 6 — Counting

**Read:** Sections 6.1–6.6

**Section 6.1 — The Basics of Counting**
Focus on: product rule, sum rule, subtraction principle, division principle. These are the combinatorial axioms from which everything else follows.

**Section 6.2 — The Pigeonhole Principle**
Focus on: the generalized pigeonhole principle; applications to computer science (hash collision lower bounds, birthday paradox). The birthday attack on hash functions (Module 4.1) is a direct application.

**Section 6.3 — Permutations and Combinations**
Focus on: P(n,r) and C(n,r) — their formulas and the combinatorial argument for each; Pascal's identity; the binomial theorem. Derive the formulas from first principles, not from memorization.

**Section 6.4 — Binomial Coefficients and Identities**
Focus on: Pascal's triangle; the binomial theorem proof by induction; Vandermonde's identity. These appear in probability (Module 0.3) and algorithm analysis.

**Section 6.5 — Generalized Permutations and Combinations**
Focus on: permutations and combinations with repetition; distributing objects into boxes. The "stars and bars" technique is extremely useful.

**Section 6.6 — Generating Permutations and Combinations**
Skim — algorithmic treatment covered in Module 1.2.

---

#### Chapter 8 — Advanced Counting Techniques

**Read:** Sections 8.1–8.2 only

**Section 8.1 — Applications of Recurrence Relations**
Focus on: setting up and solving linear recurrence relations; the Fibonacci recurrence and its closed form (Binet's formula); recurrence relations for algorithm analysis. Understand the connection to the Master Theorem (Module 1.2).

**Section 8.2 — Solving Linear Recurrence Relations**
Focus on: characteristic roots method for homogeneous recurrences; particular solutions for non-homogeneous recurrences. This provides the mathematical basis for solving algorithm recurrences.

---

#### Chapter 9 — Relations

**Read:** Sections 9.1, 9.3, 9.5, 9.6

**Section 9.1 — Relations and Their Properties**
Focus on: reflexivity, symmetry, antisymmetry, transitivity — definitions and counterexamples; the relation as a set of ordered pairs.

**Section 9.3 — Representing Relations**
Focus on: matrix representation; digraph representation. These are the two representations of graphs used throughout the curriculum.

**Section 9.5 — Equivalence Relations**
Focus on: equivalence classes and partitions; the quotient set; the connection to modular arithmetic (integers mod n form equivalence classes).

**Section 9.6 — Partial Orderings**
Focus on: partial orders vs total orders; Hasse diagrams; topological sort as a linearization of a partial order. Topological sort (Module 1.2) is an algorithm on partial orders.

---

#### Chapter 10 — Graphs

**Read:** Sections 10.1–10.5, 10.7, 10.8

**Section 10.1 — Graphs and Graph Models**
Focus on: simple graphs, multigraphs, directed graphs, weighted graphs; real-world modeling.

**Section 10.2 — Graph Terminology and Special Graph Types**
Focus on: degree, handshaking theorem (Σdeg(v) = 2|E|); complete graphs K_n; bipartite graphs; subgraphs; graph isomorphism.

**Section 10.3 — Representing Graphs and Graph Isomorphism**
Focus on: adjacency matrices and adjacency lists — understand the space and time trade-offs for both.

**Section 10.4 — Connectivity**
Focus on: paths, cycles, connected components, strongly connected components in directed graphs; cut vertices and bridges.

**Section 10.5 — Euler and Hamilton Paths**
Focus on: the characterization of Eulerian circuits (all vertices even degree) — proof required, not just memorization; Hamilton cycles as an NP-complete problem (preview of Module 1.5).

**Section 10.7 — Planar Graphs**
Focus on: Euler's formula (V − E + F = 2 for connected planar graphs); K_5 and K_{3,3} are non-planar (Kuratowski's theorem, conceptual).

**Section 10.8 — Graph Coloring**
Focus on: chromatic number; the four color theorem (statement only); greedy coloring; connection to register allocation in compilers (Module 2.5).

---

#### Chapter 11 — Trees

**Read:** Sections 11.1–11.4

**Section 11.1 — Introduction to Trees**
Focus on: rooted trees; depth, height, leaves, internal nodes; full binary trees; the fact that a tree with n vertices has n−1 edges (prove by induction).

**Section 11.2 — Applications of Trees**
Focus on: binary search trees; decision trees; prefix codes and Huffman encoding (preview of Module 1.2).

**Section 11.3 — Tree Traversal**
Focus on: preorder, inorder, postorder traversal; expression trees; Polish notation.

**Section 11.4 — Spanning Trees**
Focus on: definition of spanning tree; BFS spanning tree; DFS spanning tree. Prim's and Kruskal's are covered in Module 1.2.

---

### Supplementary Text: Lehman, Leighton & Meyer — *Mathematics for Computer Science* (MIT OCW, free)

Use this alongside Rosen for deeper proof rigor and CS-specific framing. It is freely available as a PDF.

**Read chapters in parallel with Rosen:**
- Ch. 1–3: Propositions, Induction, Number Theory (parallel to Rosen Ch. 1, 4, 5)
- Ch. 4–5: Graph Theory (parallel to Rosen Ch. 10–11)
- Ch. 6: Directed Graphs and Partial Orders (parallel to Rosen Ch. 9)
- Ch. 14–16: Probability (bridge to Module 0.3)

The MCS text has more programming-relevant framing and harder problems. Treat it as the primary source for proof writing style.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Propositional Logic & Proof Foundations
**Reading:** Rosen 1.1–1.4; MCS Ch. 1
**Daily breakdown:**
- Day 1: Rosen 1.1–1.2. Master all five connectives. Build truth tables for 10 compound statements by hand.
- Day 2: Rosen 1.3. Prove 8 logical equivalences using equivalence laws (no truth tables — use algebraic manipulation).
- Day 3: Rosen 1.4–1.5. Translate 15 English sentences to predicate logic. Negate 5 nested quantifier statements.
- Day 4: MCS Ch. 1. Read and do all in-text exercises.
- Day 5: Problem session — Problem Set 0.1 Tier 1 (problems 1–10, listed in Part C).
- Day 6: Review weak points. Redo any problem answered incorrectly.
- Day 7: Rest or light review only.

### Week 2 — Rules of Inference & Direct Proof
**Reading:** Rosen 1.6–1.8; MCS Ch. 2 (pp. 1–30)
**Daily breakdown:**
- Day 1: Rosen 1.6. Write out all 9 inference rules. Construct 5 formal proofs identifying every rule used.
- Day 2: Rosen 1.7. Study the 4 proof strategies. Prove: if n² is odd, then n is odd (contraposition).
- Day 3: Rosen 1.8. Proof by contradiction, cases, existence. Prove √2 irrational. Prove there are infinitely many primes.
- Day 4: MCS Ch. 2 (proofs). Read and annotate every proof. Identify the strategy used.
- Day 5: Problem Set 0.1 Tier 1 (problems 11–20).
- Day 6: Review. Attempt 3 problems from MCS end-of-chapter exercises.
- Day 7: Rest.

### Week 3 — Sets, Functions, Sequences
**Reading:** Rosen 2.1–2.5; MCS Ch. 4 (sets and functions)
**Daily breakdown:**
- Day 1: Rosen 2.1–2.2. Prove 5 set identities using element-chasing (not Venn diagrams).
- Day 2: Rosen 2.3. Prove that composition of two injective functions is injective. Prove the inverse function theorem.
- Day 3: Rosen 2.4–2.5. Evaluate 10 summations in closed form. Understand Cantor's diagonal argument.
- Day 4: Work through all MCS function and set exercises.
- Day 5: Problem Set 0.1 Tier 2 (problems 1–8).
- Day 6: Programming exercise — implement the set operations (union, intersection, difference, power set) in Python and verify against test cases.
- Day 7: Rest.

### Week 4 — Number Theory
**Reading:** Rosen 4.1–4.6; MCS Ch. 3 (Number Theory)
**Daily breakdown:**
- Day 1: Rosen 4.1–4.2. Prove properties of modular arithmetic (reflexivity, symmetry, transitivity of congruence). Implement modular exponentiation.
- Day 2: Rosen 4.3. Prove the Euclidean algorithm correct using strong induction. Implement it.
- Day 3: Rosen 4.4. Solve 10 linear congruences. Implement CRT solver.
- Day 4: Rosen 4.5–4.6. Study RSA structure. Understand why it requires large primes.
- Day 5: Programming project — Extended GCD implementation with unit tests. Verify Bézout coefficients.
- Day 6: Problem Set 0.1 Tier 2 (problems 9–16).
- Day 7: Rest.

### Week 5 — Mathematical Induction
**Reading:** Rosen 5.1–5.4; MCS Ch. 2 (induction sections)
**Daily breakdown:**
- Day 1: Rosen 5.1. Write 5 proofs by weak induction, fully formatted with explicit base case, hypothesis, step.
- Day 2: Rosen 5.2. Write 3 proofs by strong induction. Prove the Fundamental Theorem of Arithmetic using strong induction.
- Day 3: Rosen 5.3. Define a context-free grammar recursively. Prove a property by structural induction.
- Day 4: Rosen 5.4. Prove merge sort correct using induction on input size.
- Day 5: Problem Set 0.1 Tier 2 (problems 17–24).
- Day 6: Practice — write 5 induction proofs on your own from MCS exercises.
- Day 7: Rest.

### Week 6 — Counting & Combinatorics
**Reading:** Rosen 6.1–6.6, 8.1–8.2
**Daily breakdown:**
- Day 1: Rosen 6.1–6.2. Prove the generalized pigeonhole principle. Apply it to hash collision bounds.
- Day 2: Rosen 6.3–6.4. Derive C(n,r) from first principles. Prove Pascal's identity by induction.
- Day 3: Rosen 6.5–6.6. Stars and bars — solve 10 distribution problems.
- Day 4: Rosen 8.1–8.2. Set up and solve 5 recurrence relations using the characteristic root method.
- Day 5: Problem Set 0.1 Tier 2 (problems 25–30).
- Day 6: Derive the closed form of Fibonacci numbers using the characteristic root method.
- Day 7: Rest.

### Week 7 — Relations & Graph Theory (Part 1)
**Reading:** Rosen 9.1, 9.3, 9.5–9.6; Rosen 10.1–10.5
**Daily breakdown:**
- Day 1: Rosen 9.1, 9.5. Prove that the transitive closure of a symmetric relation is an equivalence relation.
- Day 2: Rosen 9.6. Draw Hasse diagrams for 4 partial orders. Identify topological orderings.
- Day 3: Rosen 10.1–10.3. Model 3 real-world problems as graphs. Implement adjacency list and matrix.
- Day 4: Rosen 10.4–10.5. Implement BFS and DFS. Characterize Eulerian circuits on 5 graphs.
- Day 5: Problem Set 0.1 Tier 3 (problems 1–6).
- Day 6: Programming — graph traversal visualizer.
- Day 7: Rest.

### Week 8 — Graph Theory (Part 2) & Trees
**Reading:** Rosen 10.7–10.8, 11.1–11.4; MCS Ch. 5–6
**Daily breakdown:**
- Day 1: Rosen 10.7. Prove Euler's formula by induction on the number of edges.
- Day 2: Rosen 10.8. Greedy coloring algorithm — implement and test on 5 graphs. Analyze chromatic number.
- Day 3: Rosen 11.1–11.2. Prove: a tree with n vertices has exactly n−1 edges (by strong induction).
- Day 4: Rosen 11.3–11.4. Implement all three tree traversals. Build a simple expression evaluator from an expression tree.
- Day 5: Problem Set 0.1 Tier 3 (problems 7–15).
- Day 6: Full review session — re-read your weakest chapter.
- Day 7: Rest.

### Week 9 — Integration, Review & Milestone Assessment
**Daily breakdown:**
- Days 1–2: Complete all remaining problem set problems (Tier 3, problems 16–20).
- Day 3: Write proofs for 5 randomly selected problems from Chapters 1, 4, 5, 10 without notes.
- Day 4: Programming capstone — finalize the graph traversal visualizer; implement Euclidean GCD; implement truth table generator.
- Day 5: Full milestone assessment attempt (see Part C, Milestone section).
- Day 6: Review graded assessment. Identify gaps.
- Day 7: Plan targeted remediation for any missed concepts before starting Module 0.2.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational (Logic, Proofs, Basic Structures)
*Target: 90% correct before advancing. These problems require proofs, not just answers.*

**Problem 1.** Construct a truth table for ((p → q) ∧ (q → r)) → (p → r). Is this a tautology? Prove it is (or isn't) using logical equivalences only — no truth table.

**Problem 2.** Prove or disprove: "If n is an integer and n³ is even, then n is even." State which proof strategy you use and justify your choice.

**Problem 3.** Let P(x): "x is prime" and Q(x): "x is odd." Express each statement in predicate logic and negate it formally:
  (a) Every prime greater than 2 is odd.
  (b) There exists an odd prime.
  (c) Not all odd numbers are prime.

**Problem 4.** Prove using the definition of Big-O: 3n² + 7n + 4 = O(n²). Find explicit constants c and n₀.

**Problem 5.** Prove that for any sets A, B, C: A ∩ (B ∪ C) = (A ∩ B) ∪ (A ∩ C) using element-chasing (no Venn diagrams).

**Problem 6.** Prove that the composition of two surjective functions is surjective.

**Problem 7.** Use the Euclidean Algorithm to find gcd(1071, 462). Then use the Extended Euclidean Algorithm to find integers s, t such that 1071s + 462t = gcd(1071, 462). Show all steps.

**Problem 8.** Prove by induction: ∑(i=1 to n) i² = n(n+1)(2n+1)/6 for all n ≥ 1.

**Problem 9.** Prove by contradiction: There is no largest prime number. (Euclid's proof — write it in full formal style.)

**Problem 10.** Solve the system of congruences using CRT: x ≡ 2 (mod 3), x ≡ 3 (mod 5), x ≡ 2 (mod 7). Show all computation.

**Problem 11.** Prove by strong induction: Every integer n ≥ 2 can be expressed as a product of primes.

**Problem 12.** Let R be a relation on ℤ defined by aRb iff 5 | (a − b). Prove R is an equivalence relation. How many distinct equivalence classes does R have? Describe them.

**Problem 13.** How many ways can 8 students be arranged in a row if 3 specific students must be adjacent? Show your reasoning step by step.

**Problem 14.** Prove: In any group of 13 people, at least two share a birth month. State explicitly which principle you are using.

**Problem 15.** A simple graph G has 15 edges and every vertex has degree 3. How many vertices does G have? Prove your answer using the handshaking theorem.

**Problem 16.** Prove by induction that a complete binary tree with height h has 2^(h+1) − 1 total nodes.

**Problem 17.** Solve the recurrence: T(n) = 2T(n−1) + 1, T(0) = 0. Find a closed form and prove it by induction.

**Problem 18.** Solve the recurrence: T(n) = 5T(n−1) − 6T(n−2), T(0) = 1, T(1) = 5 using the characteristic root method.

**Problem 19.** Is the graph K_{3,3} planar? Prove your answer using Euler's formula and the edge-count argument.

**Problem 20.** Prove that every tree is bipartite. (Hint: use the fact that trees contain no odd cycles.)

---

### Tier 2 — Intermediate (Deeper Proof Technique)
*Target: 80% correct. Problems require multi-step reasoning and proof construction.*

**Problem 1.** Define f: ℕ × ℕ → ℕ by f(m, n) = 2^m · (2n + 1) − 1. Prove f is a bijection. (This encodes pairs of naturals as a single natural — a key technique in computability theory.)

**Problem 2.** Prove that √3 is irrational. Then prove that √(p) is irrational for any prime p.

**Problem 3.** Prove by induction: The number of subsets of an n-element set is 2^n.

**Problem 4.** Let G = (V, E) be a connected graph. Prove that G has a spanning tree. (Hint: use the fact that if G has a cycle, removing a cycle edge preserves connectivity.)

**Problem 5.** Prove the following using contraposition: For integers a and b, if ab is even, then a is even or b is even.

**Problem 6.** RSA setup: Let p = 61, q = 53. Compute n, φ(n). Choose e = 17. Find d (the modular inverse of e mod φ(n)) using the Extended Euclidean Algorithm. Encrypt the message m = 65 and decrypt it. Show every arithmetic step.

**Problem 7.** Prove that for all n ≥ 1, the Fibonacci number F(n) satisfies F(n) < 2^n using strong induction.

**Problem 8.** A bipartite graph G = (X ∪ Y, E) has |X| = |Y| = n. Prove that G has a perfect matching if and only if Hall's condition holds: for every subset S ⊆ X, |N(S)| ≥ |S|. (State and use Hall's theorem — prove the necessary condition direction.)

**Problem 9.** Prove Euler's formula V − E + F = 2 for any connected planar graph by induction on the number of edges.

**Problem 10.** Let T(n) = T(⌊n/2⌋) + T(⌈n/2⌉) + n for n > 1, T(1) = 0. Show that T(n) = O(n log n). (This is the merge sort recurrence — solve it by the recursion tree method and verify with the Master Theorem.)

**Problem 11.** Prove that a graph G is bipartite if and only if it contains no odd-length cycle.

**Problem 12.** Derive a formula for the number of strings of length n over a 3-letter alphabet that contain no two consecutive identical characters. Set up and solve a recurrence.

**Problem 13.** Prove that the chromatic number of a graph G satisfies χ(G) ≥ |V|/α(G), where α(G) is the maximum independent set size.

**Problem 14.** An integer is called "nice" if its digit sum is divisible by 9. Prove that a positive integer n is divisible by 9 if and only if n is nice. (Use modular arithmetic and the fact that 10 ≡ 1 (mod 9).)

**Problem 15.** Let R be a relation on the set A = {1, 2, 3, 4}. Write down a relation that is reflexive and transitive but not symmetric. Compute its transitive closure.

**Problem 16.** Prove that for any positive integers a, b: gcd(a, b) · lcm(a, b) = a · b.

**Problem 17.** In how many ways can we select a committee of 3 men and 4 women from 6 men and 8 women such that a specific man and a specific woman cannot both be on the committee? Solve using inclusion-exclusion.

**Problem 18.** Use generating functions to find the number of ways to distribute 10 identical balls into 4 distinct boxes where each box contains at most 4 balls.

**Problem 19.** Define a relation on ℤ by a ~ b iff a² ≡ b² (mod 8). Is this an equivalence relation? If so, describe all equivalence classes.

**Problem 20.** A graph has degree sequence (3, 3, 3, 3, 2, 2, 2, 2). Does such a graph exist? If yes, draw it and prove it satisfies the handshaking theorem. If no, prove no such graph can exist.

---

### Tier 3 — Advanced (Integration & Research-Level Problems)
*Target: 70% correct. Expect to spend 30–60 minutes per problem.*

**Problem 1.** Prove Ramsey's theorem R(3, 3) = 6: In any 2-coloring of the edges of K₆, there is a monochromatic triangle. Then prove R(3, 3) > 5 by exhibiting a 2-coloring of K₅ with no monochromatic triangle.

**Problem 2.** The Diffie-Hellman key exchange uses the discrete logarithm problem. Let p = 23, g = 5 (a generator mod 23). Alice chooses a = 6, Bob chooses b = 15. Compute the shared secret. Now suppose you know p and g but not a or b. Given g^a mod p = 8 and g^b mod p = 19, verify the shared secret matches without knowing a or b. Discuss why computing a from g^a mod p is computationally hard when p is large.

**Problem 3.** Prove the following graph coloring theorem: If G is a graph with maximum degree Δ, then χ(G) ≤ Δ + 1. (Brook's theorem states χ(G) ≤ Δ unless G is a complete graph or an odd cycle — prove the weaker version by induction.)

**Problem 4.** Construct a formal proof system argument: Given that a security protocol requires all messages to satisfy invariant P, and the initial state satisfies P, and every protocol step preserves P — prove by structural induction that all reachable protocol states satisfy P. Model a simple 3-message protocol and carry out the proof.

**Problem 5.** Prove the Chinese Remainder Theorem in full: If m₁, m₂, ..., mₖ are pairwise coprime, then the system x ≡ a₁ (mod m₁), ..., x ≡ aₖ (mod mₖ) has a unique solution mod M = m₁ · m₂ · ... · mₖ. Prove both existence and uniqueness.

**Problem 6.** Let G be a directed acyclic graph (DAG). Prove that G has a topological ordering. Construct a topological ordering algorithm, prove its correctness, and analyze its time complexity.

**Problem 7.** Prove the Pumping Lemma for finite languages: if a language L is finite, then there exists a constant p such that for all strings s in L with |s| ≥ p, s can be pumped. (Preview of Module 1.5 — use what you know about graph paths to reason about FSM accepting paths.)

**Problem 8.** The birthday paradox: Using the inclusion-exclusion principle and approximations of the exponential function, prove that in a group of k people, the probability that at least two share a birthday exceeds 0.5 when k ≥ 23. Derive the general formula for the collision threshold in a universe of N equally likely outcomes.

**Problem 9.** Prove that the Euler totient function φ is multiplicative: for gcd(m, n) = 1, φ(mn) = φ(m)φ(n). Then derive the formula φ(n) = n · ∏(p | n) (1 − 1/p). Compute φ(3600).

**Problem 10.** Design a formal proof (by induction on the number of steps) that any algorithm described as a sequence of assignments and conditionals over a finite variable set, with no loops, terminates. Then explain why adding while loops changes the situation (connect to the Halting Problem, Module 1.5).

**Problem 11.** Prove that determining whether a graph has a Hamiltonian cycle is NP-complete. You may assume that 3-SAT is NP-complete. Construct the reduction explicitly.

**Problem 12.** Implement (in code) a complete propositional logic theorem prover using resolution refutation. Given a set of clauses, your prover should determine if the formula is satisfiable (SAT) or unsatisfiable (UNSAT). Test on at least 10 formulas including tautologies and contradictions.

**Problem 13.** Given a simple connected planar graph with V vertices, E edges, and F faces, prove V − E + F = 2. Then prove the corollary: for any simple planar graph, E ≤ 3V − 6. Use this to prove K₅ is non-planar.

**Problem 14.** Prove that for any equivalence relation R on a set A, the equivalence classes partition A (they are non-empty, pairwise disjoint, and their union is A). Then prove the converse: any partition of A defines an equivalence relation.

**Problem 15.** A cryptographic hash function maps inputs to 256-bit outputs. Prove (using counting/probability arguments) that:
  (a) A preimage attack requires at least Ω(2^256) expected operations.
  (b) A collision attack requires at least Ω(2^128) expected operations.
  Explain why (b) requires fewer operations than (a).

**Problem 16.** Prove by induction that the number of edges in a complete graph K_n is n(n−1)/2.

**Problem 17.** Define the concept of a "proof of knowledge" informally: Alice wants to convince Bob she knows a secret x such that f(x) = y, without revealing x. Using the concepts of completeness, soundness, and zero-knowledge from Module 0.1's proof background, analyze whether a simple interactive protocol achieves this. (Preview of ZKP content in Module 4.1.)

**Problem 18.** Prove the Master Theorem for the case T(n) = aT(n/b) + O(n^c) where log_b(a) > c: show T(n) = O(n^(log_b a)). Use the recursion tree method.

**Problem 19.** Prove Dilworth's theorem: In any finite partially ordered set, the minimum number of chains needed to cover the set equals the size of the largest antichain. Apply it to determine the minimum number of sorting passes needed to merge k sorted sequences.

**Problem 20.** (Capstone proof) Prove that every finite integral domain is a field. This requires: defining integral domain (commutative ring, no zero divisors), showing every nonzero element has a multiplicative inverse using a pigeonhole argument, and connecting to the structure of ℤ_p for prime p — which underlies finite field cryptography.

---

### Milestone Assessment — Module 0.1
*Pass threshold: 80% (16/20 problems). Required before starting Module 0.2.*
*Time limit: 3 hours (open notes — but no computational tools for proof problems)*

**Assessment Problem 1.** Prove: For all integers n, if n² is divisible by 3, then n is divisible by 3.

**Assessment Problem 2.** Let f: A → B and g: B → C be functions. Prove: if g∘f is injective, then f is injective.

**Assessment Problem 3.** Use the Euclidean Algorithm to compute gcd(17017, 5005). Factor the result into primes.

**Assessment Problem 4.** Prove by strong induction: Every postage amount of 8 cents or more can be made using only 3-cent and 5-cent stamps.

**Assessment Problem 5.** Prove the handshaking theorem: The sum of all vertex degrees in a graph equals twice the number of edges.

**Assessment Problem 6.** How many 8-bit strings contain exactly three 1s? How many contain at least six 1s?

**Assessment Problem 7.** Solve the recurrence T(n) = 3T(n−1) − 2, T(1) = 1. Find a closed form and verify by induction.

**Assessment Problem 8.** Prove: A graph G is Eulerian (has an Eulerian circuit) if and only if G is connected and every vertex has even degree. (Prove both directions.)

**Assessment Problem 9.** Let R be a relation on {1, 2, 3, 4, 5} defined as R = {(a,b): a divides b}. Is R a partial order? A total order? Draw the Hasse diagram.

**Assessment Problem 10.** In a RSA system with n = pq, explain why knowing φ(n) is equivalent to factoring n. (No proof required — argue informally but rigorously from the definitions.)

---

# MODULE 0.2 — Linear Algebra

**Duration:** 6–8 weeks | **Hours/week:** 8–10 | **Total hours:** ~70

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Strang — *Introduction to Linear Algebra*, 5th ed.

---

#### Chapter 1 — Introduction to Vectors

**Read:** Sections 1.1–1.3

**Section 1.1 — Vectors and Linear Combinations**
Focus on: column vector notation; linear combinations as the fundamental operation; geometric intuition in 2D and 3D. Understand that linear algebra is about linear combinations — this framing makes everything else coherent.

**Section 1.2 — Lengths and Dot Products**
Focus on: dot product as a measure of alignment; the relationship between dot product and angle (cosine formula); unit vectors; perpendicular vectors (dot product = 0). The dot product reappears in cryptography (lattice problems) and machine learning security tools.

**Section 1.3 — Matrices**
Focus on: matrix-vector multiplication as a linear combination of columns; the column space intuition; matrix-matrix multiplication as composition of linear maps.

---

#### Chapter 2 — Solving Linear Equations

**Read:** Sections 2.1–2.7

**Section 2.1 — Vectors and Linear Equations**
Focus on: two views of Ax = b (row picture: intersection of hyperplanes; column picture: linear combination of columns). The column picture is the more fundamental one for linear algebra.

**Section 2.2 — The Idea of Elimination**
Focus on: forward elimination producing an upper triangular matrix; the pivot concept; the relationship between elimination and the matrix factorization A = LU.

**Section 2.3 — Elimination Using Matrices**
Focus on: elementary matrices; how elimination corresponds to left-multiplication by elementary matrices. This is the algebraic foundation for LU decomposition.

**Section 2.4 — Rules for Matrix Operations**
Focus on: matrix multiplication is not commutative; the transpose rules; block matrix multiplication.

**Section 2.5 — Inverse Matrices**
Focus on: conditions for invertibility (nonsingular ↔ pivot in every row and column); the 2×2 inverse formula; the connection between invertibility and the system Ax = b having a unique solution.

**Section 2.6 — Elimination = Factorization: A = LU**
Focus on: the LU decomposition as a record of elimination steps; how to compute L and U; solving Ly = b then Ux = y. This factorization is used in numerical software everywhere.

**Section 2.7 — Transposes and Permutations**
Focus on: permutation matrices; the LU decomposition with partial pivoting (PA = LU); symmetric matrices and their special properties.

---

#### Chapter 3 — The Four Fundamental Subspaces

**Read:** Sections 3.1–3.6 (the conceptual heart of linear algebra)

**Section 3.1 — Spaces of Vectors**
Focus on: the definition of a vector space (8 axioms); subspaces (closed under addition and scalar multiplication); the column space C(A) and the null space N(A) as subspaces.

**Section 3.2 — The Null Space of A: Solving Ax = 0**
Focus on: the null space as a subspace; free variables and special solutions; reduced row echelon form (RREF) via Gauss-Jordan elimination.

**Section 3.3 — The Rank and the Row Reduced Form**
Focus on: rank as the number of pivots; rank(A) = rank(A^T); the relationship between rank, null space dimension, and column space dimension.

**Section 3.4 — The Complete Solution to Ax = b**
Focus on: the particular solution + homogeneous solution structure; when Ax = b has no solution / one solution / infinitely many solutions. This is the complete answer to the linear system problem.

**Section 3.5 — Independence, Basis, and Dimension**
Focus on: linear independence (formal definition and the test); basis as a minimal spanning set; dimension as the number of basis vectors; the Rank-Nullity Theorem (r + (n−r) = n). Memorize: dim(C(A)) + dim(N(A)) = n.

**Section 3.6 — Dimensions of the Four Subspaces**
Focus on: all four subspaces (C(A), N(A), C(A^T), N(A^T)) and their dimensions; the orthogonal complement relationships. This section unifies the entire theory.

---

#### Chapter 4 — Orthogonality

**Read:** Sections 4.1–4.4

**Section 4.1 — Orthogonality of the Four Subspaces**
Focus on: N(A) ⊥ C(A^T) and N(A^T) ⊥ C(A); the big picture of the four subspaces fitting together.

**Section 4.2 — Projections**
Focus on: projection onto a line (p = (a^T b / a^T a) a); projection matrix P = aa^T / a^T a; projection onto a subspace. The normal equations A^T Ax = A^T b for least-squares arise from projection.

**Section 4.3 — Least Squares Approximations**
Focus on: the least-squares problem Ax = b when no solution exists; the normal equations; the pseudoinverse. Least squares is ubiquitous in data fitting and machine learning.

**Section 4.4 — Orthonormal Bases and Gram-Schmidt**
Focus on: orthonormal vectors; the Gram-Schmidt process for constructing an orthonormal basis; the QR factorization A = QR. Gram-Schmidt is used in lattice reduction (relevant to post-quantum crypto in Module 4.1).

---

#### Chapter 5 — Determinants

**Read:** Sections 5.1–5.3

**Section 5.1 — The Properties of Determinants**
Focus on: the 3 defining properties of the determinant (sign changes on row swap, linear in each row, det(I) = 1); deriving all other properties from these three.

**Section 5.2 — Permutations and Cofactors**
Focus on: the cofactor expansion formula; the sign of a permutation; the relationship between determinant and volume.

**Section 5.3 — Cramer's Rule, Inverses, and Volumes**
Focus on: the geometric interpretation (determinant = signed volume of parallelepiped); Cramer's rule (important conceptually, not computationally); the adjugate formula for the inverse.

---

#### Chapter 6 — Eigenvalues and Eigenvectors

**Read:** Sections 6.1–6.5

**Section 6.1 — Introduction to Eigenvalues**
Focus on: the eigenvalue equation Ax = λx; characteristic polynomial det(A − λI) = 0; eigenvalues as roots of the characteristic polynomial. Understand why eigenvalues describe the behavior of iterated matrix application (key for Markov chains in Module 0.3).

**Section 6.2 — Diagonalizing a Matrix**
Focus on: diagonalization A = SΛS⁻¹; when diagonalization is possible (n independent eigenvectors); the condition for a matrix to be diagonalizable.

**Section 6.3 — Systems of Differential Equations**
Skim only — the continuous-time perspective. Focus on the conceptual parallel between A^n and e^{At}.

**Section 6.4 — Symmetric Matrices**
Focus on: symmetric matrices have real eigenvalues and orthogonal eigenvectors; the spectral theorem (A = QΛQ^T for symmetric A); positive definite matrices. PSD matrices appear in cryptographic lattice theory.

**Section 6.5 — Positive Definite Matrices**
Focus on: tests for positive definiteness (all eigenvalues > 0; all pivots > 0; all upper-left determinants > 0); the Cholesky factorization A = R^T R.

---

#### Chapter 7 — The Singular Value Decomposition (SVD)

**Read:** Section 7.1–7.2

**Section 7.1 — Image Processing by Linear Algebra**
Read as motivation — understand how SVD enables low-rank approximation.

**Section 7.2 — Bases and Matrices in the SVD**
Focus on: the SVD A = UΣV^T; the interpretation of singular values; rank-r approximation using the top r singular values; the pseudoinverse via SVD. SVD is used in anomaly detection and dimensionality reduction for security analytics.

---

### Supplementary: Axler — *Linear Algebra Done Right*, 3rd ed. (free PDF)

Use for the proof-oriented perspective. Read alongside Strang:
- Ch. 1: Vector spaces (rigorous definition)
- Ch. 2: Finite-dimensional vector spaces (basis and dimension proofs)
- Ch. 5: Eigenvalues and eigenvectors (invariant subspace approach)
- Ch. 7: Operators on inner product spaces (spectral theorem proof)

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Vectors, Systems, Elimination
- Day 1: Strang Ch. 1. Row and column pictures. Geometric intuition. All examples by hand.
- Day 2: Strang 2.1–2.3. Forward elimination on 5 systems. Identify pivots and free variables.
- Day 3: Strang 2.4–2.6. LU decomposition of 4 matrices (3×3 and 4×4). Solve Ly=b, Ux=y.
- Day 4: Strang 2.7. Permutation matrices. Partial pivoting on a system that requires it.
- Day 5: Problem Set 0.2 Tier 1, problems 1–8.
- Day 6: Programming — implement Gaussian elimination with partial pivoting in Python (no NumPy for the core algorithm).
- Day 7: Rest.

### Week 2 — The Four Subspaces
- Day 1: Strang 3.1–3.2. Null space computation via RREF. Find N(A) for 3 matrices.
- Day 2: Strang 3.3–3.4. Rank-nullity theorem verification on 4 matrices.
- Day 3: Strang 3.5–3.6. Basis finding. Draw the four-subspace diagram for 2 matrices.
- Day 4: Axler Ch. 2. Read the basis and dimension proofs.
- Day 5: Problem Set 0.2 Tier 1, problems 9–15.
- Day 6: Programming — null space computation from scratch.
- Day 7: Rest.

### Week 3 — Orthogonality & Least Squares
- Day 1: Strang 4.1–4.2. Projection derivation. Compute projections for 4 examples.
- Day 2: Strang 4.3. Solve 3 least-squares problems via normal equations and verify.
- Day 3: Strang 4.4. Gram-Schmidt on 3 sets of vectors. Verify orthonormality.
- Day 4: Problem Set 0.2 Tier 2, problems 1–6.
- Day 5: Programming — Gram-Schmidt implementation; QR factorization.
- Day 6: Application — use least squares to fit a polynomial to noisy data and analyze residuals.
- Day 7: Rest.

### Week 4 — Determinants & Eigenvalues
- Day 1: Strang 5.1–5.3. Prove 5 determinant properties from the 3 axioms. Cofactor expansion.
- Day 2: Strang 6.1–6.2. Find eigenvalues and eigenvectors for 5 matrices. Check diagonalizability.
- Day 3: Strang 6.4–6.5. Symmetric matrix examples. Cholesky factorization of 2 PD matrices.
- Day 4: Axler Ch. 5. Read the invariant subspace treatment of eigenvalues.
- Day 5: Problem Set 0.2 Tier 2, problems 7–14.
- Day 6: Programming — power iteration for dominant eigenvalue/eigenvector; verify against NumPy.
- Day 7: Rest.

### Week 5 — SVD & Applications
- Day 1: Strang 7.1–7.2. Compute SVD for 2 small matrices by hand.
- Day 2: Application: use SVD for image compression. Implement rank-k approximation.
- Day 3: Hamming code — implement from linear algebra perspective (generator and parity check matrix).
- Day 4: Problem Set 0.2 Tier 3, problems 1–6.
- Day 5: Review all factorizations: LU, QR, eigendecomposition, SVD — know when to use each.
- Day 6: 2D graphics transformation engine project.
- Day 7: Rest.

### Week 6 — Integration & Milestone Assessment
- Days 1–2: Remaining Tier 3 problems.
- Day 3: Full written review — explain all major theorems in your own words.
- Day 4: Milestone assessment attempt.
- Days 5–6: Review, remediation, and project finalization.
- Day 7: Rest.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Solve the system and express the solution set: 2x + y − z = 3, x − y + 2z = 1, 3x + 2y − z = 4. Identify whether the solution is unique, infinite, or nonexistent.

**Problem 2.** Compute the LU decomposition (without pivoting) of A = [[2,1,1],[4,3,3],[8,7,9]]. Verify A = LU.

**Problem 3.** Find a basis for the null space of A = [[1,2,3,4],[2,4,5,6],[3,6,8,10]]. State the rank and nullity and verify rank + nullity = n.

**Problem 4.** Project the vector b = (1, 1, 1) onto the column space of A = [[1,0],[1,1],[1,2]]. Find the least-squares solution to Ax = b.

**Problem 5.** Apply Gram-Schmidt to the vectors v₁ = (1, 1, 0), v₂ = (1, 0, 1), v₃ = (0, 1, 1). Produce an orthonormal basis.

**Problem 6.** Find all eigenvalues and eigenvectors of A = [[4,1],[2,3]]. Is A diagonalizable? If yes, write A = SΛS⁻¹.

**Problem 7.** Compute det(A) for a 3×3 matrix using cofactor expansion along the first row. Verify using the product of pivots from LU decomposition.

**Problem 8.** Prove: If A is invertible, then A^T is invertible and (A^T)⁻¹ = (A⁻¹)^T.

**Problem 9.** A = [[2,−1],[−1,2]]. Prove A is positive definite using all three tests (eigenvalues, pivots, upper-left determinants).

**Problem 10.** Given A has singular values σ₁ = 5, σ₂ = 3, σ₃ = 0, state the rank of A, the dimensions of all four fundamental subspaces, and ‖A‖₂.

---

### Tier 2 — Intermediate

**Problem 1.** Prove the Rank-Nullity theorem: for A ∈ ℝ^{m×n}, rank(A) + nullity(A) = n.

**Problem 2.** Implement the Hamming(7,4) error correcting code. Construct the generator matrix G and parity check matrix H. Encode the message (1,0,1,1), introduce a single-bit error, and use H to identify and correct it.

**Problem 3.** Prove: For any matrix A, N(A) ⊥ C(A^T). (Use the definition of orthogonal complement and the property of Ax = 0.)

**Problem 4.** The Google PageRank algorithm models the web as a Markov chain with transition matrix P. State the linear algebra problem that PageRank solves (finding the stationary distribution). Given a 4-page toy web graph, compute PageRank by finding the eigenvector of P^T corresponding to eigenvalue 1.

**Problem 5.** Prove the spectral theorem for symmetric matrices: if A = A^T, then A has real eigenvalues and its eigenvectors can be chosen to be orthonormal.

**Problem 6.** Show that the set of all n×n matrices with trace 0 forms a vector subspace of ℝ^{n×n}. Find its dimension.

**Problem 7.** Apply the SVD to solve an overdetermined least-squares problem: find the best-fit line through the points (0,1), (1,2), (2,4), (3,4). Compare to the normal equation solution.

---

### Tier 3 — Advanced

**Problem 1.** Prove: the rank of a matrix product satisfies rank(AB) ≤ min(rank(A), rank(B)).

**Problem 2.** Lattice cryptography preview: A lattice in ℝ^n is the set L(B) = {Bx : x ∈ ℤ^n} for a basis matrix B. Given B = [[2,1],[0,3]], list 8 lattice points near the origin. Explain why finding the shortest vector in L(B) is hard for large n — connect to the SVP (Shortest Vector Problem) used in post-quantum crypto.

**Problem 3.** Prove that det(AB) = det(A) · det(B) using the properties of the determinant (not cofactor expansion).

**Problem 4.** Using the SVD, derive the pseudoinverse A⁺ = VΣ⁺U^T. Show that A⁺ satisfies all four Moore-Penrose conditions.

---

# MODULE 0.3 — Calculus & Probability for Computing

**Duration:** 8–10 weeks | **Hours/week:** 10 | **Total hours:** ~90

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Ross — *A First Course in Probability*, 10th ed.

---

#### Chapter 1 — Combinatorial Analysis

**Read:** Sections 1.1–1.6

Focus on: the multiplication principle; permutations and combinations (the same coverage as Rosen Ch. 6 — treat this as reinforcement and consider the worked examples carefully as they differ from Rosen's). The binomial theorem proof.

---

#### Chapter 2 — Axioms of Probability

**Read:** Sections 2.1–2.7

**Section 2.2 — Sample Space and Events**
Focus on: the triple (Ω, F, P); events as subsets of Ω; the event algebra (union, intersection, complement). Think of this as a set theory application.

**Section 2.3 — Axioms of Probability**
Focus on: Kolmogorov's three axioms; countable additivity; derived properties. Prove: P(A^c) = 1 − P(A); P(A ∪ B) = P(A) + P(B) − P(A ∩ B).

**Section 2.4 — Some Simple Propositions**
Focus on: inclusion-exclusion for probability; the union bound (P(A ∪ B) ≤ P(A) + P(B)) — this is widely used in cryptographic security proofs.

**Section 2.5 — Sample Spaces Having Equally Likely Outcomes**
Focus on: computing probabilities via counting (Classical probability). All problems here reduce to combinatorics.

**Sections 2.6–2.7 — Probability as a Continuous Set Function; Probability as a Measure of Belief**
Read both. The second interpretation matters for Bayesian reasoning (Section 3.3 applies it).

---

#### Chapter 3 — Conditional Probability and Independence

**Read:** Sections 3.1–3.5 (entire chapter — the most important chapter in this book for security)

**Section 3.1 — Conditional Probability**
Focus on: P(A|B) = P(A ∩ B)/P(B); the conditional probability as a valid probability measure; updating beliefs on new evidence. This is the mathematical foundation of Bayesian reasoning, spam filtering, and intrusion detection.

**Section 3.2 — Bayes' Formula**
Focus on: the law of total probability; Bayes' theorem P(A|B) = P(B|A)P(A)/P(B); prior, likelihood, posterior. Memorize the structure and understand each term. Work every example problem.

**Section 3.3 — Independent Events**
Focus on: the definition P(A ∩ B) = P(A)P(B) — this is a definition, not a theorem; mutual independence vs pairwise independence (they are not equivalent — this matters for cryptographic security).

**Section 3.4 — P(A|B) = P(A|B,C)?**
Read carefully — conditional independence is subtle and critical for probabilistic reasoning in ML-based security tools.

**Section 3.5 — The Gambler's Ruin Problem**
Work through the solution carefully — it is an excellent application of the law of total probability and a model for analyzing random walk processes (relevant to protocol analysis).

---

#### Chapter 4 — Random Variables

**Read:** Sections 4.1–4.10

**Section 4.1 — Random Variables**
Focus on: random variable as a function from Ω to ℝ; the distribution of a random variable; discrete vs continuous RVs.

**Section 4.2 — Discrete Random Variables**
Focus on: the probability mass function (PMF); CDF for discrete RVs; expected value as a weighted average.

**Section 4.3 — Expected Value**
Focus on: E[X] definition; linearity of expectation (E[X + Y] = E[X] + E[Y] always, even if X and Y are dependent — this is one of the most powerful tools in probability).

**Section 4.4 — Expectation of a Function of a Random Variable**
Focus on: E[g(X)]; variance Var(X) = E[X²] − (E[X])².

**Section 4.5 — Variance**
Focus on: variance as a measure of spread; standard deviation; Var(aX + b) = a²Var(X); Var(X + Y) = Var(X) + Var(Y) only when X and Y are independent.

**Sections 4.6–4.10 — The Bernoulli, Binomial, Poisson, Geometric, Negative Binomial, Hypergeometric Distributions**
For each: know the PMF; the mean and variance (derive, not memorize); the physical model (what kind of experiment does this distribution model?); at least one security-relevant application.

---

#### Chapter 5 — Continuous Random Variables

**Read:** Sections 5.1–5.7

**Section 5.1 — Introduction**
Focus on: the PDF and its relationship to CDF (PDF = CDF'); the fact that P(X = a) = 0 for continuous RVs.

**Section 5.2 — Expectation and Variance of Continuous Random Variables**
Focus on: computing E[X] and Var(X) via integration.

**Section 5.3 — The Uniform Distribution**
Focus on: U(a,b) as the maximum entropy distribution over a bounded interval; application to random number generation.

**Section 5.4 — Normal Distributions**
Focus on: the standard normal N(0,1); the 68-95-99.7 rule; standardization; why the normal appears everywhere (Central Limit Theorem, Section 8.3).

**Section 5.5 — Exponential Distributions**
Focus on: the memoryless property (P(X > s+t | X > s) = P(X > t)); the connection between Poisson process and exponential inter-arrival times. Network packet interarrival times are approximately exponential.

**Sections 5.6–5.7 — Gamma and Other Distributions**
Skim — understand the Gamma as a generalization of Exponential.

---

#### Chapter 6 — Jointly Distributed Random Variables

**Read:** Sections 6.1–6.5

**Section 6.1 — Joint Distribution Functions**
Focus on: joint PMF and joint PDF; marginal distributions as integrals/sums of joint distributions.

**Section 6.2 — Independent Random Variables**
Focus on: the factorization criterion for independence: f(x,y) = f_X(x) · f_Y(y).

**Section 6.3 — Sums of Independent Random Variables**
Focus on: convolution; sum of Poisson RVs is Poisson; sum of normals is normal.

**Section 6.4 — Conditional Distributions**
Focus on: conditional PDF f(x|y) = f(x,y)/f_Y(y); Bayesian updating with continuous priors.

**Section 6.5 — Order Statistics**
Skim — useful but not critical at this stage.

---

#### Chapter 7 — Properties of Expectation

**Read:** Sections 7.1–7.5

**Section 7.2 — Covariance, Variance of Sums, and Correlations**
Focus on: Cov(X,Y) = E[XY] − E[X]E[Y]; correlation coefficient; the fact that independence implies zero covariance but not vice versa.

**Section 7.4 — Moment Generating Functions**
Focus on: the MGF definition; why it uniquely determines a distribution; the MGF of sums of independent RVs. Used in proving the CLT.

---

#### Chapter 8 — Limit Theorems

**Read:** Sections 8.1–8.4

**Section 8.2 — Chebyshev's Inequality**
Focus on: P(|X − μ| ≥ k) ≤ Var(X)/k²; the Markov inequality; using these to bound probabilities without knowing the distribution. These appear in cryptographic security arguments.

**Section 8.3 — The Central Limit Theorem**
Focus on: the statement of the CLT (proof is optional but beautiful); what "in distribution" means; the normal approximation to sums. The CLT explains why Gaussian noise models arise universally.

**Section 8.4 — The Strong Law of Large Numbers**
Focus on: the statement and interpretation; difference from weak law.

---

### Supplementary: Cover & Thomas — *Elements of Information Theory*, 2nd ed.

**Read:** Chapter 2 (Entropy, Relative Entropy, Mutual Information)

Focus on:
- Shannon entropy H(X) = −∑ p(x) log₂ p(x) — memorize and understand its properties
- Joint entropy, conditional entropy, mutual information
- Data processing inequality (information cannot be created by processing)
- The relationship between entropy and lossless compression (source coding theorem, conceptual only)
- AEP (Asymptotic Equipartition Property) — conceptual understanding

Connect entropy to security: a file with entropy close to 1 bit/byte is highly redundant (plaintext); close to 8 bits/byte is maximally random (encrypted or compressed).

---

### Supplementary: MIT 6.041 OCW — Probabilistic Systems Analysis

**Watch:** Lecture 1–12 (probability axioms through Bayesian inference)
**Do:** Problem sets 1–6 from OCW

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Probability Foundations
- Day 1: Ross Ch. 1–2. Counting review; probability axioms. Prove the inclusion-exclusion principle.
- Day 2: Ross 3.1–3.2. Conditional probability and Bayes' theorem. Solve 5 Bayes' theorem problems.
- Day 3: Ross 3.3–3.4. Independence. Find an example where pairwise independence does not imply mutual independence.
- Day 4: Birthday attack calculator — implement and analyze.
- Day 5: Problem Set 0.3 Tier 1, problems 1–8.
- Day 6: MIT 6.041 Lectures 1–4.
- Day 7: Rest.

### Week 2 — Discrete Random Variables
- Day 1: Ross 4.1–4.4. Derive E[X] and Var(X) for Bernoulli and Binomial.
- Day 2: Ross 4.5–4.7. Poisson and Geometric distributions. Derive memoryless property of Geometric.
- Day 3: Ross 4.8–4.10. Negative Binomial, Hypergeometric. Applications.
- Day 4: MIT 6.041 Lectures 5–8.
- Day 5: Problem Set 0.3 Tier 1, problems 9–15.
- Day 6: Simulate all 5 discrete distributions in Python; plot PMFs; verify mean and variance empirically.
- Day 7: Rest.

### Week 3 — Continuous Random Variables
- Day 1: Ross 5.1–5.2. PDFs, CDFs, continuous expectation and variance.
- Day 2: Ross 5.3–5.5. Uniform, Normal, Exponential. Derive memoryless property of Exponential.
- Day 3: Normal distribution applications — compute probabilities using Z-scores.
- Day 4: MIT 6.041 Lectures 9–12.
- Day 5: Problem Set 0.3 Tier 2, problems 1–6.
- Day 6: Plot Normal and Exponential distributions; demonstrate CLT empirically by summing dice rolls.
- Day 7: Rest.

### Week 4 — Joint Distributions & Limit Theorems
- Day 1: Ross 6.1–6.4. Joint distributions. Compute marginals and conditionals.
- Day 2: Ross 7.2, 7.4. Covariance and MGFs.
- Day 3: Ross 8.2–8.4. Chebyshev, CLT, LLN. Apply Chebyshev to bound a security-relevant probability.
- Day 4: Bayesian spam filter project — implement from scratch.
- Day 5: Problem Set 0.3 Tier 2, problems 7–14.
- Day 6: Entropy analysis project — compute Shannon entropy on different file types.
- Day 7: Rest.

### Week 5 — Information Theory & Applications
- Day 1: Cover & Thomas Ch. 2. Shannon entropy. Prove H(X) ≥ 0 and H(X) ≤ log₂|X|.
- Day 2: Mutual information and data processing inequality.
- Day 3: Markov chains — transition matrices, stationary distributions. (Use Strang's eigenvalue treatment from Module 0.2.)
- Day 4: Problem Set 0.3 Tier 3, problems 1–6.
- Day 5: Markov chain simulation — implement and find stationary distribution by power iteration.
- Day 6: Review — connect probability to cryptography, network analysis, and forensics.
- Day 7: Rest.

### Weeks 6–7 — Integration, Capstone Projects, Milestone Assessment
- Complete all remaining problem set problems
- Finish all 3 programming projects (birthday attack calculator, Bayesian spam filter, entropy analyzer)
- Milestone assessment

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** A bag contains 4 red and 6 blue balls. Two balls are drawn without replacement. Find: (a) P(both red), (b) P(first red and second blue), (c) P(at least one red).

**Problem 2.** A test for a disease has 99% sensitivity (P(positive|disease) = 0.99) and 95% specificity (P(negative|no disease) = 0.95). The disease affects 1% of the population. A person tests positive. What is the probability they have the disease? (This is a famous result — the answer surprises most people.)

**Problem 3.** Three events A, B, C are pairwise independent. Give an example where they are not mutually independent.

**Problem 4.** A random variable X has PMF P(X = k) = c/k² for k = 1, 2, 3, 4. Find c, E[X], and Var[X].

**Problem 5.** The number of packets arriving at a router per millisecond follows a Poisson distribution with λ = 3. Find: (a) P(X = 0), (b) P(X ≥ 2), (c) E[X] and Var[X].

**Problem 6.** X ~ Exponential(λ = 2). Find: (a) P(X > 1), (b) P(X > 3 | X > 1), (c) E[X] and Var[X]. Verify the memoryless property.

**Problem 7.** X ~ N(50, 100) (mean 50, variance 100). Find P(40 < X < 60) using the standard normal table.

**Problem 8.** The CLT: A sample of n = 100 is drawn from a distribution with mean 5 and variance 4. By the CLT, approximate P(X̄ > 5.4), where X̄ is the sample mean.

**Problem 9.** Using Chebyshev's inequality: Given E[X] = 10 and Var[X] = 4, bound P(|X − 10| ≥ 4).

**Problem 10.** Compute the Shannon entropy of: (a) a fair coin (b) a biased coin with P(H) = 0.9 (c) a fair 6-sided die. Which is highest? Why?

---

### Tier 2 — Intermediate

**Problem 1.** RSA security via probability: If an attacker tries random 1024-bit numbers until they find a prime, what is the expected number of trials? (Use the Prime Number Theorem: π(n) ≈ n/ln(n) primes below n.)

**Problem 2.** Birthday attack: In a system using 80-bit nonces, an attacker wants to find a collision. Approximately how many nonces must they generate for a 50% probability of collision? Show all work using the birthday paradox formula.

**Problem 3.** A web server log shows that successful logins happen at a rate of λ = 10 per hour and failed logins at μ = 50 per hour. Both follow Poisson processes. An IDS rule fires when failures exceed 100 in an hour. What is the probability the rule fires even in normal operation?

**Problem 4.** You observe a file and compute Shannon entropy H ≈ 7.9 bits/byte. Is this file more likely to be plaintext, compressed, or encrypted? Justify using information theory.

**Problem 5.** Derive the formula for the variance of a Geometric(p) random variable from first principles (generating function or direct computation).

**Problem 6.** Let X₁, X₂, ..., Xₙ be i.i.d. Uniform[0,1]. What is the distribution of max(X₁, ..., Xₙ)? What is E[max(X₁, ..., Xₙ)]? Interpret this in the context of a "last packet arrival" model.

**Problem 7.** Bayesian update: A threat intelligence system has a prior belief P(attack) = 0.01. It observes an anomalous event with P(event|attack) = 0.9 and P(event|no attack) = 0.1. Compute the posterior P(attack|event). Now observe a second independent anomalous event with the same likelihoods. Compute the updated posterior.

---

### Tier 3 — Advanced

**Problem 1.** Prove the weak law of large numbers using Chebyshev's inequality: for i.i.d. X₁,...,Xₙ with finite mean μ and variance σ², show P(|X̄ₙ − μ| > ε) → 0 as n → ∞.

**Problem 2.** Entropy and compression: Prove that H(X) ≤ log₂|X|, with equality iff X is uniformly distributed. Interpret: an encryption scheme that produces uniform output reveals no information about the key length.

**Problem 3.** Markov chain security model: Model a network host as a 3-state Markov chain: Normal (N), Compromised (C), Detected (D). Define a plausible transition matrix P. Find the stationary distribution. What fraction of time does the model predict the host is in the Compromised state?

**Problem 4.** Prove: If X and Y are independent random variables, then Var(X + Y) = Var(X) + Var(Y). Then show that independence is not necessary — find the weakest condition required.

**Problem 5.** Differential privacy preview: The Laplace mechanism adds noise drawn from Laplace(0, Δf/ε) to a query result, where Δf is the sensitivity. Compute E[error²] as a function of ε and Δf. Explain the privacy-utility trade-off mathematically.

**Problem 6.** (Capstone) Information-theoretic security proof: Prove that the one-time pad achieves perfect secrecy: P(M = m | C = c) = P(M = m) for all m, c. Formally state and use the definition P(C = c | M = m) = 1/|K|. Then prove that any perfectly secret cipher must have |K| ≥ |M|.

---

### Milestone Assessment — Module 0.3
*Pass threshold: 75% (15/20 problems). Required before beginning Phase 1.*

**Assessment Problem 1.** State and prove Bayes' theorem from the definition of conditional probability.

**Assessment Problem 2.** A network intrusion detection system has P(alert|intrusion) = 0.95 and P(alert|normal) = 0.005. If 1 in 10,000 sessions is malicious, what is P(intrusion|alert)?

**Assessment Problem 3.** Let X ~ Binomial(n=20, p=0.3). Compute P(X = 6) and E[X].

**Assessment Problem 4.** Let X ~ Exponential(λ = 1). Compute P(1 < X < 3).

**Assessment Problem 5.** State the Central Limit Theorem. Apply it: 100 password attempts per hour, each independently succeeding with probability 0.001. Approximate P(at least 1 success per hour).

**Assessment Problem 6.** Compute the Shannon entropy (in bits) of a source with outcomes {a: 0.5, b: 0.25, c: 0.125, d: 0.125}.

**Assessment Problem 7.** Define mutual independence for events A, B, C. Give an example where A, B, C are pairwise independent but not mutually independent.

**Assessment Problem 8.** Use Chebyshev's inequality to find the minimum sample size n such that the sample mean of a distribution with σ² = 25 is within 1 unit of the true mean with probability at least 0.95.

**Assessment Problem 9.** Let X ~ Geometric(p = 0.4). Find P(X > 5) and E[X]. Verify the memoryless property: P(X > 8 | X > 3) = P(X > 5).

**Assessment Problem 10.** Prove the union bound: P(A ∪ B) ≤ P(A) + P(B). Generalize to n events.

---

# Phase 0 — Global Capstone Projects

Complete all three before beginning Phase 1. These projects integrate all three modules.

---

## Capstone Project 0-A: Cryptographic Math Library

**Objective:** Implement a self-contained Python library with the following:
- Euclidean and Extended GCD
- Modular exponentiation (fast exponentiation)
- Miller-Rabin primality test
- RSA key generation, encryption, and decryption (textbook — no padding)
- Chinese Remainder Theorem solver
- Baby-step Giant-step discrete logarithm solver (small instances)

**Requirements:**
- No cryptographic libraries (no `cryptography`, no `pycryptodome` for core math)
- Full unit test suite with ≥95% coverage
- Complexity analysis for each function
- A README explaining the mathematical basis for each implementation

**Evaluation criteria:** Correctness (passes test suite), mathematical documentation quality, complexity analysis accuracy.

---

## Capstone Project 0-B: Probability & Statistics Security Toolkit

**Objective:** Build a Python toolkit for security-relevant statistical analysis:
- Shannon entropy calculator for arbitrary files
- Birthday collision probability calculator (given hash output size, compute threshold)
- Bayesian anomaly detector: given a stream of binary events (normal/anomalous), maintain and update a posterior probability of attack using Bayes' theorem
- Chi-squared randomness test for byte sequences

**Requirements:**
- Demonstrate on real data: compute entropy of a text file, a JPEG, a ZIP file, and a random bytes file; interpret the results
- All mathematical derivations documented with LaTeX or Markdown math

---

## Capstone Project 0-C: Graph & Logic Proof Portfolio

**Objective:** A written portfolio of 10 original proofs, one for each of the following:
1. A proof by induction on a graph property
2. A proof using the pigeonhole principle
3. A proof by contradiction involving number theory
4. A proof using Bayes' theorem to update a security-relevant belief
5. A proof that a given language property implies another (preview of Module 1.5)
6. A proof involving equivalence classes
7. A proof that a specific matrix transformation is injective or surjective
8. A proof involving expected value and variance
9. A proof using the law of total probability
10. A combinatorial proof of a binomial identity (prove it two different ways: algebraically and combinatorially)

**Format:** Each proof must include: statement, proof strategy selected and justified, complete formal proof, and a one-paragraph explanation of why this result matters in CS or security.

---

*End of Phase 0 Complete Study Package*
*Next: Phase 1 — Core Computer Science*

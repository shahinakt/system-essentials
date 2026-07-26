# Master Curriculum: Computer Science, Computer Engineering, Systems Programming & Cybersecurity
### From First Principles to Expert — University-Grade + Advanced Security Specialization

---

> **How to read this document**
> The curriculum is organized into **5 Phases** → **Semesters** → **Modules**. Each module lists its learning objectives, prerequisites, estimated study time, difficulty, projects/labs, and authoritative references. Prerequisites flow strictly upward: no module assumes knowledge from a later module. The final phase is a graduate-level cybersecurity specialization mirroring CMU's MSIT-IS, MIT's 6.858, and ETH Zürich's System Security track.

---

## Curriculum Map (Overview)

```
PHASE 0 │ Mathematical & Logical Foundations           (3–4 months)
PHASE 1 │ Core Computer Science                        (10–12 months)
PHASE 2 │ Computer Engineering & Systems               (8–10 months)
PHASE 3 │ Systems Programming & Low-Level Mastery      (8–10 months)
PHASE 4 │ Advanced Cybersecurity Specialization        (12–14 months)
─────────────────────────────────────────────────────────────────────
TOTAL   │ ~42–50 months of structured, full-depth study
```

---

# PHASE 0 — Mathematical & Logical Foundations

> **Why first?** Every advanced topic in this curriculum — from algorithm analysis to exploit development — rests on mathematical reasoning. Cryptography requires number theory. Compilers require formal languages. Network security requires probability. Architecture requires Boolean algebra. These are not optional enrichment; they are load-bearing.

---

## Phase 0 · Semester 0-A

### Module 0.1 — Discrete Mathematics & Logic

| Field | Detail |
|---|---|
| **Difficulty** | Beginner |
| **Estimated Study Time** | 8–10 weeks (10–12 hrs/week) |
| **Prerequisites** | High-school algebra; no CS knowledge required |

**Why this comes first:** Logic and proof techniques underpin every rigorous argument in computer science. Before writing code or studying algorithms, you must be able to reason precisely about truth, structure, and correctness.

**Learning Objectives:**
- Construct and evaluate propositional and predicate logic statements
- Write formal proofs using direct proof, proof by contradiction, and mathematical induction
- Apply set theory, relations, and functions to model computational problems
- Analyze combinatorics and counting principles used in algorithm analysis and cryptography
- Understand graph theory fundamentals used throughout CS and networking
- Work with modular arithmetic and number theory as a foundation for cryptography

**Core Topics:**
- Propositional logic, truth tables, Boolean algebra
- Predicate logic, quantifiers, inference rules
- Proof techniques: direct, contradiction, induction, strong induction
- Set theory: sets, subsets, power sets, Cartesian products
- Functions: injective, surjective, bijective, composition
- Relations: equivalence relations, partial and total orders
- Counting: permutations, combinations, pigeonhole principle, inclusion-exclusion
- Graphs: paths, cycles, trees, planarity, graph coloring, Euler/Hamiltonian paths
- Modular arithmetic: congruences, GCD, Euclidean algorithm, prime numbers, Fermat's Little Theorem
- Introduction to formal languages and regular expressions

**Practical Projects:**
1. Build a propositional logic truth-table generator in Python
2. Implement the Euclidean Algorithm and Extended GCD from scratch
3. Solve 30 curated proof problems (induction, contradiction, graph theorems)
4. Graph traversal visualizer (BFS/DFS) as both proof exercise and programming warm-up

**Labs:**
- Lab 0.1.A: Logic puzzle sets (Knights and Knaves, Zebra Puzzle) modeled formally
- Lab 0.1.B: Modular arithmetic exercises leading into RSA intuition
- Lab 0.1.C: Graph theory problems on real-world networks (six degrees, coloring maps)

**Milestone:** Pass a proof-writing assessment covering all six proof techniques and a graph theory problem set at 80%+ accuracy.

**Authoritative References:**
- Rosen, *Discrete Mathematics and Its Applications* (McGraw-Hill)
- Lehman, Leighton & Meyer, *Mathematics for Computer Science* (MIT OpenCourseWare, free)
- Sipser, *Introduction to the Theory of Computation* (Ch. 0 only, for formal language preview)
- MIT 6.042J course materials (OCW)

---

### Module 0.2 — Linear Algebra

| Field | Detail |
|---|---|
| **Difficulty** | Beginner–Intermediate |
| **Estimated Study Time** | 6–8 weeks (8–10 hrs/week) |
| **Prerequisites** | Module 0.1 (proof literacy) |

**Why this comes before systems and security:** Linear algebra is essential for understanding computer graphics, machine learning components of modern security tools, error-correcting codes, and lattice-based cryptography.

**Learning Objectives:**
- Perform vector and matrix operations fluently
- Understand linear transformations geometrically and algebraically
- Apply eigenvalue decomposition to understand system behavior
- Understand vector spaces, basis, and rank as tools for reasoning about data
- Connect linear algebra to applications in systems and cryptography

**Core Topics:**
- Vectors and vector spaces, linear independence, span, basis, dimension
- Matrices: operations, transpose, inverse, determinant
- Systems of linear equations: Gaussian elimination, LU decomposition
- Linear transformations and their matrix representations
- Eigenvalues and eigenvectors, diagonalization
- Orthogonality, projections, Gram-Schmidt, QR decomposition
- Singular Value Decomposition (SVD) — conceptual understanding
- Applications: least-squares, error-correcting codes, PCA intuition

**Practical Projects:**
1. Implement Gaussian elimination and back-substitution without libraries
2. Build a 2D graphics transformation engine using matrix operations
3. Simple error-correcting code (Hamming Code) implemented from first principles

**Labs:**
- Lab 0.2.A: Visualizing linear transformations in 2D/3D with matplotlib
- Lab 0.2.B: Hamming code encoder/decoder implementation

**Authoritative References:**
- Strang, *Introduction to Linear Algebra* (Wellesley-Cambridge Press)
- Strang, *Linear Algebra and Its Applications* (Cengage)
- MIT 18.06SC Linear Algebra (OCW, includes video lectures)
- Axler, *Linear Algebra Done Right* (Springer, free PDF via Axler's site) — for the proof-oriented treatment

---

### Module 0.3 — Calculus & Probability for Computing

| Field | Detail |
|---|---|
| **Difficulty** | Beginner–Intermediate |
| **Estimated Study Time** | 8–10 weeks (10 hrs/week) |
| **Prerequisites** | Module 0.1 |

**Why before systems and security:** Probability theory is the mathematical language of cryptographic security proofs, network traffic analysis, intrusion detection (anomaly detection), and complexity theory. Calculus underpins performance modeling and continuous optimization.

**Learning Objectives:**
- Apply differential and integral calculus to performance and optimization problems
- Reason about probability spaces, random variables, and distributions
- Apply Bayes' Theorem — critical for intrusion detection and forensic reasoning
- Understand information theory basics (entropy, mutual information)
- Work with Markov chains as a model for protocol and system behavior

**Core Topics:**
- Limits, derivatives, integrals — focused on intuition and application
- Probability axioms, sample spaces, conditional probability
- Bayes' Theorem and its applications to decision-making under uncertainty
- Random variables: discrete and continuous, expectation, variance
- Common distributions: Binomial, Geometric, Poisson, Normal, Exponential
- Law of Large Numbers, Central Limit Theorem
- Information entropy (Shannon entropy), mutual information
- Markov chains and transition matrices

**Practical Projects:**
1. Birthday attack probability calculator (cryptographic relevance)
2. Bayesian spam filter from scratch
3. Entropy calculator for analyzing file randomness (malware/steganography preview)

**Labs:**
- Lab 0.3.A: Simulating and visualizing probability distributions in Python
- Lab 0.3.B: Shannon entropy analysis on different file types (text vs. binary vs. encrypted)

**Authoritative References:**
- Sheldon Ross, *A First Course in Probability* (Pearson)
- Cover & Thomas, *Elements of Information Theory* (Wiley) — Ch. 1–2 for entropy
- MIT 6.041 Probabilistic Systems Analysis (OCW)
- Mitzenmacher & Upfal, *Probability and Computing* (Cambridge) — algorithmically focused

---

# PHASE 1 — Core Computer Science

> **Why this phase?** Phases 0 laid the mathematical skeleton. Phase 1 builds the intellectual infrastructure of CS itself: how to think algorithmically, how programs are structured and executed, how data is organized, how computation is bounded, and how software is engineered at scale. Every systems and security topic assumes fluency here.

---

## Phase 1 · Semester 1-A

### Module 1.1 — Programming Foundations (Python)

| Field | Detail |
|---|---|
| **Difficulty** | Beginner |
| **Estimated Study Time** | 6–8 weeks (12–15 hrs/week) |
| **Prerequisites** | Module 0.1 (basic logic) |

**Why Python first:** Python's syntax is minimal enough that cognitive load lands on problem-solving, not language mechanics. It allows immediate focus on algorithmic thinking before introducing the complexity of type systems and memory management.

**Learning Objectives:**
- Write correct, well-structured Python programs
- Understand control flow, functions, recursion, and scope
- Apply basic data structures: lists, dictionaries, sets, tuples
- Read and write files; handle errors and exceptions
- Understand object-oriented basics: classes, inheritance, encapsulation
- Write automated tests for your code

**Core Topics:**
- Variables, types, expressions, statements
- Control flow: conditionals, loops, break/continue
- Functions: parameters, return values, scope, closures, higher-order functions
- Recursion and the call stack
- Built-in data structures and their complexity characteristics
- File I/O, exception handling, context managers
- Modules and packages
- OOP fundamentals: classes, `__init__`, inheritance, polymorphism, dunder methods
- List comprehensions, generators, iterators
- Unit testing with `unittest` or `pytest`

**Practical Projects:**
1. Text adventure game (control flow, state management)
2. CSV data analyzer (file I/O, data manipulation)
3. Recursive maze solver with visualization
4. Personal finance tracker with file persistence and OOP design

**Labs:**
- Lab 1.1.A: Debugging exercises — 10 deliberately broken programs to fix
- Lab 1.1.B: Write a test suite for a provided buggy module

**Authoritative References:**
- Downey, *Think Python* (O'Reilly, free online)
- Lutz, *Learning Python* (O'Reilly)
- MIT 6.0001 Introduction to Computer Science and Programming in Python (OCW)
- Python official documentation: docs.python.org

---

### Module 1.2 — Data Structures & Algorithm Design

| Field | Detail |
|---|---|
| **Difficulty** | Intermediate |
| **Estimated Study Time** | 12–14 weeks (12–15 hrs/week) |
| **Prerequisites** | Module 0.1 (proofs, induction), Module 0.3 (probability), Module 1.1 |

**Why this is the spine of the curriculum:** Every system — operating systems, compilers, databases, network stacks, and security tools — is built from algorithms and data structures. Understanding time/space complexity is what separates engineers who build systems that scale from those who don't.

**Learning Objectives:**
- Analyze algorithm correctness using invariants and formal reasoning
- Analyze time and space complexity using asymptotic notation
- Design algorithms using divide-and-conquer, greedy, dynamic programming, and backtracking
- Implement and analyze all fundamental data structures from first principles
- Reason about algorithmic trade-offs for real-world problem selection
- Apply graph algorithms to network and system problems

**Core Topics:**
- Asymptotic notation: O, Ω, Θ, o, ω; best/worst/average case
- Recurrence relations and the Master Theorem
- Arrays, linked lists, stacks, queues, deques — implementation and complexity
- Hash tables: hash functions, collision resolution (chaining, open addressing), load factors
- Trees: binary search trees, AVL trees, Red-Black trees, B-trees
- Heaps and priority queues; heapsort
- Sorting algorithms: insertion, merge, quicksort, counting, radix, bucket sort
- Graphs: representation (adjacency list/matrix), BFS, DFS, topological sort
- Shortest path: Dijkstra's, Bellman-Ford, Floyd-Warshall
- Minimum spanning trees: Kruskal's, Prim's
- Greedy algorithms: activity selection, Huffman coding
- Dynamic programming: memoization, tabulation, LCS, LIS, knapsack, edit distance
- Divide and conquer: binary search, merge sort, Strassen's matrix multiplication
- Backtracking: N-queens, constraint satisfaction
- String algorithms: KMP, Rabin-Karp, tries, suffix arrays
- Amortized analysis

**Practical Projects:**
1. Implement every data structure from scratch with full test suites (no library use)
2. Build a spell-checker using a trie and edit distance (DP)
3. Huffman compression tool — full encoder/decoder
4. Pathfinding visualizer (Dijkstra + A*) on a grid

**Labs:**
- Lab 1.2.A: Complexity analysis — instrument and benchmark 5 sorting algorithms, graph results
- Lab 1.2.B: Hash table collision analysis under different load factors
- Lab 1.2.C: Graph algorithm application — shortest path in a real city road network dataset

**Capstone (Module-level):** Design and implement a data structure of your choice to solve a non-trivial real-world problem. Write a full correctness proof and amortized complexity analysis.

**Authoritative References:**
- CLRS — Cormen, Leiserson, Rivest, Stein, *Introduction to Algorithms* (MIT Press) — the definitive reference
- Sedgewick & Wayne, *Algorithms* (Addison-Wesley)
- Skiena, *The Algorithm Design Manual* (Springer)
- MIT 6.006 Introduction to Algorithms (OCW)
- MIT 6.046 Design and Analysis of Algorithms (OCW)

---

### Module 1.3 — Systems Thinking: Unix/Linux Fundamentals

| Field | Detail |
|---|---|
| **Difficulty** | Beginner–Intermediate |
| **Estimated Study Time** | 4–6 weeks (10 hrs/week) |
| **Prerequisites** | Module 1.1 |

**Why now:** All systems and security work in this curriculum occurs on Unix/Linux. Building fluency early means every subsequent module can use the terminal naturally. This is practical infrastructure, not a detour.

**Learning Objectives:**
- Navigate and administer a Linux system confidently
- Understand the Unix philosophy and its architectural implications
- Write shell scripts that automate real tasks
- Understand file permissions, users, and process management
- Use standard tools (grep, sed, awk, find, curl, strace, lsof) effectively

**Core Topics:**
- Filesystem hierarchy, navigation, file manipulation
- File permissions: user/group/other, chmod, chown, SUID/SGID/sticky bit
- Processes: fork, exec, signals, ps, kill, job control, process trees
- Shell scripting: bash syntax, variables, loops, conditionals, functions, pipelines
- I/O redirection, pipes, heredocs
- Package management (apt/dnf/pacman)
- Networking basics: ifconfig/ip, ping, traceroute, netstat/ss, curl, wget
- Text processing: grep (regex), sed, awk, sort, uniq, cut, tr
- Archiving and compression: tar, gzip, zip
- SSH: key generation, config, tunneling basics
- Cron and task scheduling
- Introduction to systemd and service management

**Practical Projects:**
1. System hardening script that audits and locks down a fresh Linux install
2. Log analyzer: parse /var/log files to detect anomalies using bash
3. Automated backup script with scheduling and integrity verification

**Labs:**
- Lab 1.3.A: OverTheWire Bandit (levels 0–25) — gamified Linux proficiency
- Lab 1.3.B: Write 15 shell one-liners to solve common sysadmin tasks

**Authoritative References:**
- Barrett, *Linux Pocket Guide* (O'Reilly)
- Kerrisk, *The Linux Programming Interface* (No Starch Press) — Chapters 1–4 for this module
- Williams, *Learning the bash Shell* (O'Reilly)
- *The Linux Command Line* by Shotts (No Starch Press, free online)

---

## Phase 1 · Semester 1-B

### Module 1.4 — Object-Oriented Design & Software Engineering

| Field | Detail |
|---|---|
| **Difficulty** | Intermediate |
| **Estimated Study Time** | 8–10 weeks (10–12 hrs/week) |
| **Prerequisites** | Module 1.1, Module 1.2 |

**Why before systems:** Before studying how operating systems are designed, you need to understand how large software systems are designed at all — modularity, abstraction boundaries, interfaces, and testing. These principles apply directly to kernel code, compilers, and security tools.

**Learning Objectives:**
- Apply SOLID principles to software design
- Design and implement systems using classical design patterns
- Write software that is testable, maintainable, and well-documented
- Reason about software quality: cohesion, coupling, and code smell
- Use version control (Git) as a professional engineering discipline

**Core Topics:**
- OOP principles: encapsulation, inheritance, polymorphism, abstraction
- SOLID principles (Single Responsibility through Dependency Inversion)
- Design patterns: creational (Factory, Singleton, Builder), structural (Adapter, Decorator, Facade), behavioral (Observer, Strategy, Command, Iterator)
- UML class, sequence, and state diagrams
- Test-driven development (TDD) and behavior-driven development
- Code review practices
- Git: branches, merges, rebasing, pull requests, conflict resolution
- Refactoring techniques
- Documentation: docstrings, API documentation
- Introduction to CI/CD concepts

**Practical Projects:**
1. Refactor a messy 500-line script into a clean OOP system applying SOLID
2. Implement 10 design patterns with real-world motivating scenarios
3. Library management system — full design cycle from UML to tested implementation

**Labs:**
- Lab 1.4.A: Code smell identification and refactoring exercise set
- Lab 1.4.B: TDD cycle — write tests before every feature in a small project

**Authoritative References:**
- Gamma, Helm, Johnson, Vlissides, *Design Patterns: Elements of Reusable Object-Oriented Software* (Addison-Wesley) — the Gang of Four book
- Martin, *Clean Code* (Prentice Hall)
- McConnell, *Code Complete* (Microsoft Press)
- Fowler, *Refactoring* (Addison-Wesley)
- MIT 6.005 / 6.031 Software Construction (OCW)

---

### Module 1.5 — Theory of Computation

| Field | Detail |
|---|---|
| **Difficulty** | Intermediate–Advanced |
| **Estimated Study Time** | 8–10 weeks (10–12 hrs/week) |
| **Prerequisites** | Module 0.1 (proof techniques, formal logic), Module 1.2 |

**Why before compilers and security:** Theory of computation gives you the vocabulary to talk about what computers *can* and *cannot* do, and at what cost. Regular languages underpin lexers. Context-free grammars define programming language syntax. Decidability and complexity theory define the limits of security analysis and verification tools.

**Learning Objectives:**
- Define and recognize the Chomsky hierarchy of formal languages
- Build deterministic and nondeterministic finite automata
- Convert between NFAs, DFAs, and regular expressions
- Build pushdown automata and context-free grammars for programming language syntax
- Understand Turing machines as the universal model of computation
- Prove language properties using pumping lemmas
- Understand decidability, semi-decidability, and undecidability (halting problem)
- Understand complexity classes P, NP, NP-Complete, and their implications for cryptography and security

**Core Topics:**
- Finite automata: DFA, NFA, ε-NFA; equivalence and minimization
- Regular expressions and their equivalence to finite automata
- Closure properties of regular languages; pumping lemma for regular languages
- Context-free grammars, parse trees, ambiguity
- Pushdown automata; CFL pumping lemma
- Turing machines: definition, variants, Church-Turing thesis
- Decidable and recognizable languages
- Undecidability: Halting Problem, Rice's Theorem, reductions
- Time complexity: P, NP, polynomial reduction, NP-completeness, Cook-Levin theorem
- Space complexity: PSPACE, L, NL, coNP

**Practical Projects:**
1. DFA/NFA simulator and minimization tool
2. CFG parser for a subset of Python (preview of compilers)
3. Write formal reduction proofs showing NP-completeness for 3 problems

**Labs:**
- Lab 1.5.A: JFLAP exercises — automata construction and analysis
- Lab 1.5.B: Complexity argument construction for security-relevant problems (e.g., why graph coloring relates to register allocation)

**Authoritative References:**
- Sipser, *Introduction to the Theory of Computation* (Cengage) — the gold standard
- Hopcroft, Motwani & Ullman, *Introduction to Automata Theory, Languages, and Computation* (Addison-Wesley)
- Arora & Barak, *Computational Complexity: A Modern Approach* (Cambridge) — for depth on complexity
- MIT 18.404J Theory of Computation (OCW)

---

### Module 1.6 — Computer Networks

| Field | Detail |
|---|---|
| **Difficulty** | Intermediate |
| **Estimated Study Time** | 10–12 weeks (10–12 hrs/week) |
| **Prerequisites** | Module 0.3 (probability), Module 1.3 (Linux/Unix), Module 1.2 (algorithms) |

**Why before security:** Virtually every cybersecurity topic — from network intrusion detection to protocol exploitation to cloud security — requires deep understanding of how networks actually work at every layer. You cannot attack or defend what you don't understand.

**Learning Objectives:**
- Understand and apply the OSI and TCP/IP models at every layer
- Analyze packet-level behavior of protocols using Wireshark
- Implement simple TCP/IP socket programs
- Understand routing, switching, and the control/data plane distinction
- Understand how DNS, HTTP, TLS, and BGP work in depth
- Identify common network vulnerabilities at each layer

**Core Topics:**
- OSI 7-layer model vs. TCP/IP 4-layer model; protocol encapsulation
- Physical and data link layer: Ethernet, MAC addressing, ARP, VLANs, STP
- Network layer: IPv4, IPv6, ICMP, subnetting, CIDR, NAT, routing (RIP, OSPF, BGP)
- Transport layer: UDP, TCP (3-way handshake, congestion control, flow control, state machine), QUIC
- Application layer: DNS (full resolution chain), HTTP/1.1, HTTP/2, HTTP/3, TLS 1.3 handshake, SMTP, FTP, SSH
- Socket programming: TCP/UDP client-server in Python
- Network address translation (NAT) and firewalls
- Packet capture and analysis with Wireshark/tshark
- CDNs, load balancers, and proxies
- Quality of Service (QoS) and congestion

**Practical Projects:**
1. Implement an HTTP/1.1 server from raw TCP sockets (no frameworks)
2. Build a multi-threaded TCP port scanner with banner grabbing
3. Network traffic analyzer: parse a .pcap and produce a summary report
4. Implement a simple DNS resolver that walks the resolution chain

**Labs:**
- Lab 1.6.A: Wireshark capture and protocol dissection — analyze 5 real protocol exchanges
- Lab 1.6.B: TCP handshake and teardown observation with simultaneous packet capture and code execution
- Lab 1.6.C: Simulate a small network topology in GNS3 or EVE-NG

**Capstone (Module-level):** Build a working network monitoring agent that captures traffic, identifies protocols, detects port scans against it, and logs anomalies to a structured file.

**Authoritative References:**
- Kurose & Ross, *Computer Networking: A Top-Down Approach* (Pearson) — the standard text
- Stevens, Fenner & Rudoff, *Unix Network Programming, Vol. 1* (Addison-Wesley) — for socket depth
- Tanenbaum & Wetherall, *Computer Networks* (Pearson)
- RFC documents (IETF): RFC 791 (IPv4), RFC 793 (TCP), RFC 1035 (DNS), RFC 8446 (TLS 1.3)
- Stanford CS144 Computer Networking (course notes available online)

---

### Module 1.7 — Databases & Storage Systems

| Field | Detail |
|---|---|
| **Difficulty** | Intermediate |
| **Estimated Study Time** | 8–10 weeks (10 hrs/week) |
| **Prerequisites** | Module 1.2, Module 1.4 |

**Why here:** Databases are critical infrastructure whose security (SQL injection, data exfiltration, authentication bypass) is a major attack surface. Understanding storage internals also prepares you for operating system and filesystem work ahead.

**Learning Objectives:**
- Model data using relational and non-relational paradigms
- Write complex SQL queries including window functions and recursive CTEs
- Understand physical storage structures: B-trees, LSM trees, buffer pools
- Reason about ACID properties and transaction isolation levels
- Understand indexing, query planning, and optimization
- Identify and exploit common database vulnerabilities

**Core Topics:**
- Relational model: tables, keys, normalization (1NF–BCNF)
- SQL: DDL, DML, joins, aggregation, subqueries, window functions, recursive CTEs
- Storage: heap files, slotted pages, buffer pool management, disk I/O
- Indexing: B+ trees (primary and secondary), hash indexes, bitmap indexes
- Query execution: parsing, logical plan, physical plan, cost estimation
- Transactions: ACID, serializability, two-phase locking, MVCC
- Crash recovery: WAL, ARIES protocol
- NoSQL: document stores (MongoDB), key-value stores (Redis), column stores, graph databases
- Distributed databases: CAP theorem, eventual consistency, replication, sharding
- Database security: SQL injection, access control, encryption at rest and in transit

**Practical Projects:**
1. Implement a simple B+ tree from scratch with insert, delete, range scan
2. Build a mini relational database engine: parser → planner → executor → storage
3. Exploit a deliberately vulnerable web application's database via SQL injection (sandboxed environment)

**Labs:**
- Lab 1.7.A: Query optimization — explain plans and index tuning on a real dataset
- Lab 1.7.B: SQL injection lab (DVWA or SQLite target) — five different attack vectors

**Authoritative References:**
- Ramakrishnan & Gehrke, *Database Management Systems* (McGraw-Hill)
- Abiteboul, Hull & Vianu, *Foundations of Databases* (free online)
- CMU 15-445/645 Database Systems (course notes and labs available publicly)
- Andy Pavlo's lecture notes (CMU) — freely available
- Kleppmann, *Designing Data-Intensive Applications* (O'Reilly) — for distributed systems depth

---

# PHASE 2 — Computer Engineering & Computer Architecture

> **Why this phase?** Software runs on hardware. Without understanding how processors execute instructions, how memory is physically organized, how interrupts work, and how the hardware-software interface functions, you cannot understand operating systems, cannot interpret assembly during reverse engineering, cannot reason about hardware-level attacks (Spectre, Rowhammer, JTAG), and cannot write efficient systems code. Phase 2 builds the machine beneath the software.

---

## Phase 2 · Semester 2-A

### Module 2.1 — Digital Logic & Boolean Circuits

| Field | Detail |
|---|---|
| **Difficulty** | Beginner–Intermediate |
| **Estimated Study Time** | 6–8 weeks (10 hrs/week) |
| **Prerequisites** | Module 0.1 (Boolean algebra, logic) |

**Why this comes before architecture:** A processor is a physical Boolean circuit. Understanding gates, combinational logic, and sequential logic is the foundation upon which everything from ALUs to memory controllers is built.

**Learning Objectives:**
- Design and analyze combinational and sequential circuits
- Minimize Boolean expressions using Karnaugh maps and Quine-McCluskey
- Build and analyze key circuits: adders, multiplexers, decoders, flip-flops
- Understand finite state machines as the basis for control units
- Simulate digital circuits at the gate level

**Core Topics:**
- Binary, hexadecimal, octal number systems; two's complement arithmetic
- Boolean algebra; De Morgan's laws; logic minimization
- Combinational circuits: half-adder, full-adder, ripple-carry and carry-lookahead adders
- Multiplexers, demultiplexers, encoders, decoders, comparators
- Karnaugh maps (up to 6 variables) and sum-of-products minimization
- Sequential circuits: SR, D, JK, T flip-flops; latches
- Registers, counters, shift registers
- Finite state machines: Moore and Mealy models
- Memory: SRAM, DRAM basics; ROM, PLA, PAL

**Practical Projects:**
1. Design and simulate a 4-bit ALU in Logisim-Evolution
2. Build a traffic light controller FSM and simulate it
3. Implement a 4-bit CPU with register file and memory in a logic simulator

**Labs:**
- Lab 2.1.A: Logisim-Evolution — build all fundamental combinational circuits
- Lab 2.1.B: FSM design for a serial communication protocol (SPI or UART simplified)

**Authoritative References:**
- Mano & Ciletti, *Digital Design* (Pearson)
- Harris & Harris, *Digital Design and Computer Architecture* (Morgan Kaufmann)
- Wakerly, *Digital Design: Principles and Practices* (Pearson)
- MIT 6.004 Computation Structures (OCW)

---

### Module 2.2 — Computer Architecture I: Processor Design

| Field | Detail |
|---|---|
| **Difficulty** | Intermediate |
| **Estimated Study Time** | 10–12 weeks (12 hrs/week) |
| **Prerequisites** | Module 2.1, Module 1.2 (algorithms — performance reasoning) |

**Why before OS and systems programming:** The instruction set architecture (ISA) is the contract between hardware and software. You cannot understand assembly, calling conventions, stack frames, system calls, or hardware exploits without understanding how a processor executes instructions.

**Learning Objectives:**
- Understand the MIPS and x86-64 instruction set architectures
- Design a pipelined datapath in HDL (VHDL or Verilog)
- Analyze pipeline hazards (structural, data, control) and their solutions
- Understand the memory hierarchy and its performance implications
- Reason about superscalar execution, out-of-order execution, and branch prediction
- Connect architectural decisions to security (Spectre, Meltdown as case studies)

**Core Topics:**
- ISA design: RISC vs CISC, instruction formats, addressing modes
- MIPS ISA: R/I/J-type instructions, register conventions, MIPS assembly programming
- x86-64 ISA: registers (rax–r15, rsp, rbp, rip, rflags), instruction encoding, addressing
- Single-cycle datapath design
- Pipelining: IF/ID/EX/MEM/WB stages; CPI analysis
- Hazards: data hazards (RAW, WAW, WAR), forwarding, stalls; structural hazards; control hazards, branch prediction (static, dynamic: 2-bit counter, branch target buffer), speculative execution
- Memory hierarchy: registers → L1 → L2 → L3 → DRAM → disk; latency numbers
- Cache design: direct-mapped, set-associative, fully associative; replacement policies (LRU, FIFO, random); write policies (write-through, write-back)
- Virtual memory overview (detailed in Module 3.1)
- Modern processor features: out-of-order execution, register renaming, ROB, superscalar
- Case study: Spectre and Meltdown — understanding speculative execution side-channels

**Practical Projects:**
1. Implement a MIPS simulator in C or Python: fetch-decode-execute loop, register file, memory model
2. Write 10 non-trivial MIPS assembly programs (sorting, string operations, recursion)
3. Implement a 5-stage pipelined MIPS processor in Verilog/VHDL with hazard detection and forwarding

**Labs:**
- Lab 2.2.A: Cache simulation — measure hit rate on matrix multiplication with row-major vs column-major access
- Lab 2.2.B: Branch predictor accuracy measurement on real SPEC benchmarks
- Lab 2.2.C: Write and explain MIPS calling convention stack frame layouts

**Capstone (Module-level):** Design and simulate a small 16-bit processor in Verilog with an assembler written in Python — define your own ISA, implement it in HDL, write programs that run on it.

**Authoritative References:**
- Patterson & Hennessy, *Computer Organization and Design: The Hardware/Software Interface* (Morgan Kaufmann) — the definitive text
- Harris & Harris, *Digital Design and Computer Architecture* (Morgan Kaufmann)
- Bryant & O'Hallaron, *Computer Systems: A Programmer's Perspective* (Pearson) — Chapters 1–6
- MIT 6.004 Computation Structures (OCW)
- CMU 15-213 Introduction to Computer Systems (OCW)

---

### Module 2.3 — Computer Architecture II: Memory Systems & I/O

| Field | Detail |
|---|---|
| **Difficulty** | Intermediate–Advanced |
| **Estimated Study Time** | 6–8 weeks (10–12 hrs/week) |
| **Prerequisites** | Module 2.2 |

**Why a dedicated module for memory:** Memory systems are where performance is won and lost, and where many hardware-level security vulnerabilities live (Rowhammer, DRAM flip attacks, cache-timing attacks). Deep understanding of physical memory, virtual memory, and the TLB is essential.

**Learning Objectives:**
- Understand DRAM organization down to row/column addressing
- Design and analyze multi-level cache hierarchies
- Understand virtual memory: page tables, TLBs, page faults
- Understand I/O: programmed I/O, interrupt-driven I/O, DMA
- Analyze hardware security vulnerabilities arising from memory systems

**Core Topics:**
- DRAM: banks, rows, columns, refresh cycles, SDRAM, DDR SDRAM
- Cache coherence in multi-core systems: MESI protocol
- Virtual memory: page tables (single-level, multi-level, x86-64 4-level), TLB, TLB shootdown
- Page replacement: optimal, LRU, clock, working set
- Memory-mapped I/O vs port-mapped I/O
- Interrupts and interrupt controllers (APIC)
- DMA: bus mastering, scatter-gather
- PCI Express architecture and device enumeration
- NVMe and storage interfaces
- Rowhammer attack: DRAM refresh vulnerability and exploitation (conceptual and historical)

**Practical Projects:**
1. Virtual memory simulator: implement a page table walker for a defined virtual address space
2. TLB simulation with miss rate analysis
3. Memory profiler: use `perf` and `valgrind --tool=cachegrind` on real programs

**Labs:**
- Lab 2.3.A: Rowhammer reproduction (on own hardware or simulator) — understand DRAM vulnerability
- Lab 2.3.B: `perf` cache miss analysis — profile three programs and optimize them

**Authoritative References:**
- Patterson & Hennessy, *Computer Organization and Design* (Morgan Kaufmann)
- Jacob, Ng & Wang, *Memory Systems: Cache, DRAM, Disk* (Morgan Kaufmann)
- Intel® 64 and IA-32 Architectures Software Developer's Manual (Intel, free)
- Kim et al., "Flipping Bits in Memory Without Accessing Them" (ISCA 2014) — Rowhammer paper

---

## Phase 2 · Semester 2-B

### Module 2.4 — Embedded Systems & Microcontrollers

| Field | Detail |
|---|---|
| **Difficulty** | Intermediate |
| **Estimated Study Time** | 6–8 weeks (10 hrs/week) |
| **Prerequisites** | Module 2.2, Module 1.1 |

**Why embedded systems:** IoT and embedded device security is one of the fastest-growing attack surfaces. Embedded systems are pervasive in critical infrastructure, medical devices, and industrial control systems. Understanding them is essential for hardware security, firmware reverse engineering, and JTAG/SWD debugging.

**Learning Objectives:**
- Program ARM Cortex-M microcontrollers in C
- Interface with hardware peripherals via GPIO, SPI, I2C, UART
- Understand real-time constraints and RTOS fundamentals
- Understand bootloaders, firmware update mechanisms, and their security implications
- Perform basic firmware analysis

**Core Topics:**
- ARM Cortex-M architecture: registers, exception model, Thumb instruction set
- Memory map: Flash, SRAM, peripheral registers, vectors
- GPIO, timers, PWM, ADC/DAC
- Serial communication: UART, SPI, I2C protocols
- Interrupts and NVIC; real-time constraints
- RTOS concepts: tasks, scheduling, semaphores, message queues (FreeRTOS)
- Bootloaders: startup sequence, linker scripts, vector table
- Debugging: JTAG, SWD, GDB with OpenOCD
- Firmware update security: signature verification, anti-rollback

**Practical Projects:**
1. Build a digital oscilloscope on an ARM Cortex-M4 board
2. Implement a secure bootloader with firmware signature verification
3. RTOS-based sensor data logger with multiple tasks and semaphore coordination

**Labs:**
- Lab 2.4.A: JTAG debugging session — extract and analyze firmware from a development board
- Lab 2.4.B: Fault injection (clock glitching conceptual lab) — understand power analysis attacks

**Authoritative References:**
- Yiu, *The Definitive Guide to ARM Cortex-M3 and Cortex-M4 Processors* (Newnes)
- Barr & Massa, *Programming Embedded Systems in C and C++* (O'Reilly)
- FreeRTOS Reference Manual (freertos.org)
- ARM Architecture Reference Manual (free with registration from arm.com)

---

### Module 2.5 — Compilers & Language Implementation

| Field | Detail |
|---|---|
| **Difficulty** | Advanced |
| **Estimated Study Time** | 12–14 weeks (12–15 hrs/week) |
| **Prerequisites** | Module 1.5 (Theory of Computation), Module 1.2 (Data Structures), Module 2.2 (Architecture — for code generation) |

**Why compilers:** Compiler internals directly inform security. Understanding parsing enables you to find injection vulnerabilities systematically. Understanding intermediate representations and optimization passes helps you understand what binary code actually does when reverse engineering. Understanding code generation prepares you for writing shellcode and understanding compiler-level mitigations (stack canaries, PIE, RELRO).

**Learning Objectives:**
- Implement all phases of a compiler: lexing, parsing, semantic analysis, IR generation, optimization, and code generation
- Understand the relationship between high-level constructs and assembly output
- Understand how compiler optimizations can introduce or eliminate security properties
- Understand compiler security mitigations and how they work at the instruction level

**Core Topics:**
- Compiler overview: phases, passes, and the role of each
- Lexical analysis: regular expressions, finite automata, `lex`/`flex`
- Parsing: top-down (recursive descent, LL), bottom-up (LR, SLR, LALR, GLR); `yacc`/`bison`
- Abstract Syntax Trees (ASTs); symbol tables; scoping
- Type systems and type checking; type inference basics
- Intermediate representations: three-address code, SSA form, LLVM IR
- Data flow analysis: liveness, reaching definitions, dominators
- Optimizations: constant folding, dead code elimination, common subexpression elimination, loop optimizations, inlining
- Code generation: instruction selection, register allocation (graph coloring), instruction scheduling
- Runtime systems: call stack, calling conventions (System V AMD64 ABI), heap allocation, garbage collection basics
- Compiler security mitigations: stack canaries (how generated), ASLR interaction with PIE, CFI (control flow integrity)

**Practical Projects:**
1. Implement a full compiler for a statically-typed toy language (e.g., a Tiger or Decaf variant) that produces x86-64 assembly
2. Write a recursive-descent parser for a subset of C
3. Implement constant folding and dead-code elimination passes on your AST/IR

**Labs:**
- Lab 2.5.A: Disassemble and annotate compiler output for 5 C constructs (loops, recursion, structs, function pointers, varargs) using `gcc -O0` vs `-O2`
- Lab 2.5.B: LLVM IR inspection — write a C program, compile to IR, trace how an optimization pass transforms it

**Capstone (Module-level):** Build a complete compiler for a small statically-typed language, targeting LLVM IR or x86-64, with at least 3 optimization passes and a test suite covering 50+ programs.

**Authoritative References:**
- Aho, Lam, Sethi & Ullman, *Compilers: Principles, Techniques, and Tools* (Addison-Wesley) — the Dragon Book
- Appel, *Modern Compiler Implementation in C/Java/ML* (Cambridge)
- Cooper & Torczon, *Engineering a Compiler* (Morgan Kaufmann)
- LLVM Language Reference Manual (llvm.org) — free online
- Stanford CS143 Compilers (course materials available)

---

# PHASE 3 — Systems Programming & Low-Level Mastery

> **Why this phase?** This is where C, assembly, operating systems, and concurrency converge. The systems programmer writes code that runs at the boundary of hardware and software. This phase produces the deep technical foundation that distinguishes a security researcher from a script kiddie: you will understand memory layout, the kernel, system calls, concurrency bugs, and the full call stack from hardware interrupt to userspace application.

---

## Phase 3 · Semester 3-A

### Module 3.1 — C Programming & Memory Management

| Field | Detail |
|---|---|
| **Difficulty** | Intermediate–Advanced |
| **Estimated Study Time** | 8–10 weeks (12–15 hrs/week) |
| **Prerequisites** | Module 1.1, Module 2.2 (architecture, memory model), Module 2.3 (virtual memory) |

**Why C before the OS:** The Linux kernel and most system-level security-relevant code is written in C. You cannot read kernel source, understand buffer overflows at the instruction level, or write shellcode without deep C fluency. C is the language where security mistakes live at the lowest level.

**Learning Objectives:**
- Write correct, portable C code across the full language
- Understand and manage memory manually: malloc, free, valgrind-clean programs
- Reason about undefined behavior and its security implications
- Understand the C abstract machine, object model, and lifetime rules
- Use debugging tools (gdb, valgrind, AddressSanitizer) expertly
- Understand how C constructs map to x86-64 assembly

**Core Topics:**
- Data types, sizes, alignment; integer arithmetic and overflow
- Pointers: pointer arithmetic, pointer-to-pointer, function pointers, void pointers
- Arrays and their decay to pointers; multi-dimensional arrays
- Strings: null termination, buffer overflows, safe string handling
- Structs, unions, bit fields; alignment and padding
- Memory layout: stack, heap, BSS, data, text segments
- Dynamic memory: malloc, calloc, realloc, free; heap metadata; use-after-free, double-free
- Undefined behavior: signed overflow, uninitialized reads, out-of-bounds access — and why compilers exploit UB for optimization
- `const`, `volatile`, `restrict` — semantics and security relevance
- Preprocessor: macros, include guards, stringification, token pasting
- Linking: object files, symbols, relocation, static vs dynamic linking, GOT/PLT
- C11 standard: atomics, `_Generic`, `_Static_assert`

**Practical Projects:**
1. Implement a memory allocator (malloc/free) from scratch using `mmap` and `sbrk`
2. Write a string library that is safe against buffer overflows (with bounds-checking)
3. Build a simple garbage collector (mark-and-sweep) in C

**Labs:**
- Lab 3.1.A: Valgrind and AddressSanitizer — fix 10 progressively harder memory bugs
- Lab 3.1.B: Undefined behavior tour — 15 examples where UB causes surprising behavior; explain the compiler's optimization rationale
- Lab 3.1.C: GDB mastery — 5 debugging exercises requiring breakpoints, watchpoints, memory inspection, call stack walking

**Authoritative References:**
- Kernighan & Ritchie, *The C Programming Language* (Prentice Hall) — the original reference
- Seacord, *Effective C* (No Starch Press)
- Seacord, *Secure Coding in C and C++* (Addison-Wesley)
- Kerrisk, *The Linux Programming Interface* (No Starch Press) — the definitive Linux/C reference
- ISO/IEC 9899:2018 (C17 standard) — free draft available as N2176

---

### Module 3.2 — x86-64 Assembly Language

| Field | Detail |
|---|---|
| **Difficulty** | Advanced |
| **Estimated Study Time** | 8–10 weeks (12–15 hrs/week) |
| **Prerequisites** | Module 2.2 (architecture, ISA), Module 3.1 (C, memory layout) |

**Why dedicated assembly:** Every reverse engineering, exploit development, shellcode writing, and malware analysis task requires fluency in reading and writing x86-64 assembly. This is not optional for a serious security practitioner.

**Learning Objectives:**
- Read, write, and modify x86-64 assembly confidently
- Understand Intel vs AT&T syntax differences
- Map C constructs (loops, functions, structs, arrays, switch) to assembly exactly
- Understand the System V AMD64 calling convention in full detail
- Write position-independent shellcode by hand
- Understand SIMD (SSE/AVX) at a conceptual level

**Core Topics:**
- x86-64 register set: general purpose (rax, rbx, rcx, rdx, rsi, rdi, r8–r15), rsp, rbp, rip, rflags, segment registers
- Instruction classes: data movement, arithmetic, logical, shift/rotate, control flow, string operations
- Addressing modes: immediate, register, memory (base+index*scale+displacement)
- Stack frame layout: prologue, epilogue, local variables, saved registers, return address
- System V AMD64 ABI: integer arguments (rdi, rsi, rdx, rcx, r8, r9), floating point (xmm0–7), return values, red zone, callee-saved registers
- NASM/GAS syntax; assembling and linking
- System calls: `syscall` instruction, syscall table (Linux), argument passing
- SIMD: SSE2 and AVX basics — packed operations on vectors
- Control flow: jcc instructions, cmov, loop instructions
- Writing shellcode: constraints (null-byte avoidance), PC-relative addressing for PIC shellcode
- Anti-disassembly tricks (for reverse engineering context)

**Practical Projects:**
1. Implement 10 standard algorithms (bubble sort, binary search, strlen, memcpy, strcmp) in pure NASM assembly
2. Write a "Hello, World!" program using only Linux syscalls in raw assembly
3. Write a position-independent TCP reverse shell in x86-64 assembly (for shellcode technique — sandboxed environment)
4. Optimize a C inner loop using SSE2 intrinsics and compare with pure C

**Labs:**
- Lab 3.2.A: Reverse engineer 15 compiler-generated functions from binary only (no source) — annotate them
- Lab 3.2.B: Manually encode 5 x86-64 instructions from opcode tables — understand encoding

**Authoritative References:**
- Intel® 64 and IA-32 Architectures Software Developer's Manual (free from intel.com) — Vol. 2 for instruction reference
- AMD64 Architecture Programmer's Manual (free from amd.com)
- Doran, *Assembly Language Step-by-Step* (Wiley)
- System V AMD64 ABI specification (refspecs.linuxbase.org)
- *PC Assembly Language* by Paul Carter (free PDF)

---

### Module 3.3 — Operating Systems: Concepts & Design

| Field | Detail |
|---|---|
| **Difficulty** | Advanced |
| **Estimated Study Time** | 12–14 weeks (12–15 hrs/week) |
| **Prerequisites** | Module 2.2 (architecture), Module 2.3 (memory systems), Module 3.1 (C), Module 3.2 (assembly), Module 1.6 (networks — for sockets in OS context) |

**Why the most demanding non-security module:** The OS is the trust boundary between user applications and hardware. Every privilege escalation attack, kernel exploit, rootkit, and sandbox escape is fundamentally an OS security problem. You cannot understand those without implementing OS components yourself.

**Learning Objectives:**
- Understand and implement process, thread, and scheduler abstractions
- Implement virtual memory management including page table walking and TLB management
- Implement synchronization primitives from hardware atomics
- Understand file systems at the block level
- Implement system call interfaces
- Understand OS security mechanisms: capabilities, namespaces, seccomp, SELinux

**Core Topics:**
- OS structure: monolithic, microkernel, exokernel, hypervisor
- Processes: PCB, process creation (fork/exec on Linux), context switching
- Threads: kernel vs user threads, thread scheduling
- CPU scheduling: FCFS, SJF, round-robin, CFS (Linux Completely Fair Scheduler), real-time scheduling (EDF, RMS)
- Synchronization: race conditions, critical sections, Peterson's algorithm, hardware atomics (CAS, LL/SC), spinlocks, mutexes, semaphores, monitors, condition variables
- Deadlock: Coffman conditions, detection, prevention, avoidance (Banker's algorithm)
- Memory management: segmentation, paging, multi-level page tables, x86-64 4-level page tables, TLB, TLB shootdown
- Virtual memory: demand paging, page faults, copy-on-write, memory-mapped files (mmap)
- Page replacement: OPT, LRU, Clock, Working Set; thrashing
- File systems: VFS abstraction, ext4 internals (inodes, data blocks, journals), FAT, NTFS overview, copy-on-write FSes (ZFS, Btrfs)
- I/O and device drivers: interrupt handling, DMA, block I/O scheduler
- Inter-process communication: pipes, FIFOs, message queues, shared memory, sockets
- Security mechanisms: privilege rings, system call filtering (seccomp-BPF), Linux namespaces (pid/net/mnt/user), cgroups, capabilities, mandatory access control (SELinux/AppArmor)

**Practical Projects:**
1. **xv6 deep-dive:** Read, annotate, and extend the MIT xv6 OS (add system calls, improve scheduler, add a file system feature)
2. Implement a user-space threading library (M:N threads with preemption via SIGALRM)
3. Write a FUSE filesystem (user-space filesystem) — implement a simple encrypted filesystem
4. Implement a shell (fork, exec, pipes, redirection, job control, signals)

**Labs:**
- Lab 3.3.A: Linux kernel module — write a kernel module that implements a character device driver
- Lab 3.3.B: Strace analysis — trace system calls of 5 programs and explain each OS interaction
- Lab 3.3.C: Container internals — manually create a container using Linux namespaces and cgroups without Docker

**Capstone (Module-level):** Implement a minimal operating system kernel from scratch that boots on x86-64 (via GRUB/Multiboot), sets up GDT/IDT, implements virtual memory, preemptive multitasking, and a simple round-robin scheduler.

**Authoritative References:**
- Silberschatz, Galvin & Gagne, *Operating System Concepts* (Wiley) — the dinosaur book
- Arpaci-Dusseau & Arpaci-Dusseau, *Operating Systems: Three Easy Pieces* (free online — OSTEP)
- Tanenbaum, *Modern Operating Systems* (Pearson)
- Kerrisk, *The Linux Programming Interface* (No Starch Press) — Linux-specific system calls in depth
- Love, *Linux Kernel Development* (Addison-Wesley)
- MIT 6.828 Operating System Engineering (OCW) — uses xv6; labs are essential

---

## Phase 3 · Semester 3-B

### Module 3.4 — Concurrent & Parallel Programming

| Field | Detail |
|---|---|
| **Difficulty** | Advanced |
| **Estimated Study Time** | 8–10 weeks (12 hrs/week) |
| **Prerequisites** | Module 3.3 (OS — synchronization primitives), Module 3.1 (C) |

**Why a dedicated concurrency module:** Race conditions and concurrency bugs are a major class of security vulnerability (TOCTOU attacks, kernel data races, use-after-free in concurrent code). Understanding concurrency at the memory model level is essential for auditing multi-threaded systems code.

**Learning Objectives:**
- Write correct concurrent programs using POSIX threads, mutexes, and condition variables
- Reason about programs using memory model guarantees (C11 atomics)
- Detect and fix concurrency bugs: data races, deadlocks, livelocks, starvation
- Understand lock-free and wait-free data structures
- Reason about TOCTOU (time-of-check to time-of-use) vulnerabilities
- Apply concurrency patterns (thread pool, pipeline, producer-consumer)

**Core Topics:**
- POSIX Threads (pthreads): creation, joining, detaching, thread-local storage
- Mutex types, recursive mutexes, rwlocks
- Condition variables and monitors
- Semaphores and their relationship to mutexes
- C11 memory model: atomic types, memory orders (relaxed, acquire, release, seq_cst), happens-before relation
- Lock-free data structures: compare-and-swap based stack and queue
- ABA problem and solutions (tagged pointers, hazard pointers)
- Parallel patterns: map-reduce, pipeline, work-stealing, fork-join
- OpenMP for shared-memory parallel programming
- MPI overview for distributed-memory parallel programming
- TOCTOU vulnerabilities: file system races, /tmp races, and their exploitation
- ThreadSanitizer for dynamic race detection

**Practical Projects:**
1. Implement a thread-safe, lock-free concurrent hash map
2. Build a work-stealing thread pool
3. Exploit a TOCTOU race condition vulnerability in a sandboxed file operation program

**Labs:**
- Lab 3.4.A: ThreadSanitizer — detect races in 5 provided buggy programs
- Lab 3.4.B: Benchmark lock-based vs lock-free data structures at varying thread counts

**Authoritative References:**
- Williams, *C++ Concurrency in Action* (Manning) — best modern treatment (concepts apply to C)
- Herlihy & Shavit, *The Art of Multiprocessor Programming* (Morgan Kaufmann)
- Kerrisk, *The Linux Programming Interface* (No Starch Press) — pthreads chapters
- POSIX Threads standard documentation
- CMU 15-418/618 Parallel Computer Architecture and Programming (course notes available)

---

### Module 3.5 — Systems Programming: Advanced Topics

| Field | Detail |
|---|---|
| **Difficulty** | Advanced |
| **Estimated Study Time** | 8–10 weeks (12 hrs/week) |
| **Prerequisites** | Module 3.1, Module 3.3, Module 3.4, Module 1.6 (networks) |

**Why this module:** This covers the production-level systems programming skills used in network servers, high-performance applications, and security tools: epoll-based I/O, zero-copy techniques, memory-mapped I/O, profiling, and the complete lifecycle of a syscall from userspace to kernel and back.

**Learning Objectives:**
- Write high-performance network servers using asynchronous I/O
- Understand the full syscall path from userspace to kernel
- Write and analyze eBPF programs for observability and security
- Profile and optimize systems programs with `perf`
- Understand Linux security namespaces, cgroups, and seccomp from a programming perspective

**Core Topics:**
- Advanced file descriptors: epoll, io_uring, signalfd, timerfd, eventfd
- Asynchronous I/O patterns: reactor, proactor, event loop design
- Zero-copy I/O: sendfile, splice, vmsplice, mmap
- Advanced memory management: mmap, mprotect, madvise, huge pages, NUMA awareness
- The Linux syscall path: vDSO, syscall entry, kernel entry code, return path
- eBPF: programs, maps, helpers, bpftrace, libbpf; safety guarantees
- Linux tracing: ftrace, perf events, uprobe/kprobe, USDT
- Profiling: `perf record`, `perf report`, flame graphs, CPU profiling vs off-CPU profiling
- Seccomp-BPF: writing syscall filters for application sandboxing
- AF_UNIX sockets, abstract namespace, credential passing (SCM_CREDENTIALS)

**Practical Projects:**
1. Build a high-performance HTTP/1.1 server using epoll with 10,000+ concurrent connections
2. Write an eBPF-based network monitor that logs all outbound connections without modifying applications
3. Write a seccomp-BPF sandbox for an untrusted subprocess

**Labs:**
- Lab 3.5.A: io_uring — implement a file copy utility using io_uring and benchmark against read/write
- Lab 3.5.B: Flame graph analysis — profile a slow server, identify bottleneck, fix, re-profile

**Authoritative References:**
- Kerrisk, *The Linux Programming Interface* (No Starch Press) — advanced chapters
- Gregg, *Systems Performance* (Addison-Wesley) — the performance bible
- Gregg, *BPF Performance Tools* (Addison-Wesley)
- eBPF.io documentation and kernel documentation
- io_uring documentation: liburing GitHub repository

---

### Module 3.6 — C++ for Systems Programming

| Field | Detail |
|---|---|
| **Difficulty** | Advanced |
| **Estimated Study Time** | 8–10 weeks (12 hrs/week) |
| **Prerequisites** | Module 3.1 (C), Module 1.4 (OOP) |

**Why C++ in a systems/security track:** Many security tools (LLVM, Clang, Frida, many vulnerability research tools), operating system components (Chrome OS, macOS kernel extensions), and performance-critical security infrastructure are written in C++. Understanding move semantics, RAII, and template metaprogramming is essential for reading and contributing to this ecosystem.

**Learning Objectives:**
- Write modern C++ (C++17/20) that is safe, efficient, and idiomatic
- Understand RAII and smart pointers as the solution to C memory bugs
- Apply template metaprogramming and concepts
- Understand C++ object model: vtables, construction/destruction order, alignment
- Reason about C++ undefined behavior and its security implications

**Core Topics:**
- Value semantics: copy, move, forwarding; rule of 0/3/5
- Smart pointers: `unique_ptr`, `shared_ptr`, `weak_ptr` — implementation and performance
- RAII: resource acquisition and guaranteed release
- Templates: function templates, class templates, variadic templates, SFINAE, concepts (C++20)
- Standard library: STL containers (with complexity guarantees), algorithms, `string_view`, `span`, `optional`, `variant`, `expected`
- Lambda expressions, `std::function`, closures, captures
- C++ memory model and atomics
- vtable layout, virtual dispatch, RTTI
- `constexpr`, `consteval`, compile-time computation
- Ranges (C++20)
- Common C++ security pitfalls: iterator invalidation, dangling references, integer overflow

**Practical Projects:**
1. Rewrite your Module 3.1 memory allocator in C++ using RAII and smart pointers
2. Build a type-safe event system using templates and `std::variant`
3. Implement a policy-based design (e.g., an allocator-aware container) using templates

**Authoritative References:**
- Stroustrup, *The C++ Programming Language* (Addison-Wesley)
- Meyers, *Effective Modern C++* (O'Reilly)
- Meyers, *Effective C++* and *More Effective C++* (Addison-Wesley)
- Josuttis, *The C++ Standard Library* (Addison-Wesley)
- ISO/IEC 14882:2020 (C++20 standard) — draft freely available as N4868

---

# PHASE 4 — Advanced Cybersecurity Specialization

> **Why this phase comes last:** Every module here requires deep, fluent integration of the preceding three phases. Exploit development requires x86-64 assembly, C, virtual memory, and compiler mitigations. Malware analysis requires OS internals, compilers, and reverse engineering. Cryptography requires number theory, probability, and algorithm analysis. Cloud security requires networking, OS security, and systems programming. The expert security researcher is a generalist in Phases 0–3 and a specialist in Phase 4.

---

## Phase 4 · Semester 4-A: Foundations of Security

### Module 4.1 — Cryptography: Theory & Practice

| Field | Detail |
|---|---|
| **Difficulty** | Advanced |
| **Estimated Study Time** | 12–14 weeks (12–15 hrs/week) |
| **Prerequisites** | Module 0.1 (number theory, modular arithmetic), Module 0.3 (probability, information theory), Module 1.5 (complexity theory — for security reductions) |

**Why cryptography is the first security module:** Cryptography is the mathematical backbone of all secure systems. Every subsequent module — network security, web security, cloud security, malware C2 analysis — involves cryptographic protocols. Breaking cryptographic implementations is one of the most reliable attack paths. You must understand cryptography deeply before studying attacks against it.

**Learning Objectives:**
- Prove security of cryptographic schemes using formal security definitions and reductions
- Understand and implement all classical and modern symmetric/asymmetric primitives
- Understand how TLS 1.3, SSH, and Signal work at the protocol level
- Identify and exploit common cryptographic implementation mistakes
- Understand post-quantum cryptography at a conceptual level
- Implement and break classical ciphers and side-channel-vulnerable implementations

**Core Topics:**
- Information-theoretic security: perfect secrecy, one-time pad, Shannon's theorem
- Computational security: negligible functions, security parameters, polynomial reduction
- Symmetric cryptography:
  - Block ciphers: DES (historical), AES (full construction: SubBytes, ShiftRows, MixColumns, AddRoundKey), modes of operation (ECB weakness, CBC, CTR, GCM), authenticated encryption
  - Stream ciphers: ChaCha20, LFSR-based (historical weaknesses)
  - Hash functions: SHA-2, SHA-3 (Keccak), hash security properties (preimage, second preimage, collision resistance), Merkle-Damgård construction, length extension attacks
  - MACs: HMAC construction and security proof, CMAC, Poly1305
- Asymmetric cryptography:
  - Number theory: groups, rings, fields, Euler's theorem, Chinese Remainder Theorem
  - RSA: key generation, OAEP padding, PSS signatures; textbook RSA attacks (CRT fault attacks, small exponent, timing side-channel)
  - Diffie-Hellman: discrete logarithm problem, CDH/DDH assumptions; ECDH
  - Elliptic Curve Cryptography: group law, point multiplication, secp256k1/P-256/Curve25519; ECDSA, EdDSA
  - ElGamal encryption
- Key exchange and public key infrastructure: X.509 certificates, certificate chains, CT logs, OCSP, CRL
- Protocol analysis: TLS 1.3 handshake (full key schedule), SSH protocol, Signal Protocol (Double Ratchet, X3DH)
- Cryptographic attacks: padding oracle (CBC), bleichenbacher attack (RSA PKCS#1 v1.5), CRIME/BEAST/POODLE, nonce reuse on AES-GCM, timing side-channels
- Zero-knowledge proofs: conceptual overview, Schnorr protocol
- Post-quantum cryptography: lattice problems (LWE, RLWE), NIST PQC selections (CRYSTALS-Kyber, CRYSTALS-Dilithium)

**Practical Projects:**
1. Implement AES-128 from scratch (no libraries) — all four transformations, key schedule, GCM mode
2. Implement RSA and ECDH key exchange, then exploit textbook RSA (no padding)
3. Exploit a padding oracle vulnerability against a CBC-mode encryption oracle
4. Implement the Signal Protocol's X3DH key agreement from scratch

**Labs:**
- Lab 4.1.A: Cryptopals Challenges (Sets 1–8) — this is mandatory; it is the best applied cryptography curriculum in existence
- Lab 4.1.B: Timing side-channel measurement — demonstrate that a non-constant-time string comparison leaks key information
- Lab 4.1.C: Certificate chain analysis — parse and validate an X.509 certificate chain using Python's `cryptography` library

**Capstone (Module-level):** Audit an open-source implementation of a cryptographic protocol (e.g., a small TLS library), find at least one implementation flaw, document it formally, and propose a fix.

**Authoritative References:**
- Boneh & Shoup, *A Graduate Course in Applied Cryptography* (free at crypto.stanford.edu) — the most current graduate-level text
- Katz & Lindell, *Introduction to Modern Cryptography* (CRC Press)
- Ferguson, Schneier & Kohno, *Cryptography Engineering* (Wiley) — for implementation focus
- Bernstein et al., *Post-Quantum Cryptography* (Springer)
- Cryptopals Matasano Crypto Challenges (cryptopals.com) — required lab resource
- MIT 6.875 Cryptography and Cryptanalysis (OCW)

---

### Module 4.2 — Network Security & Protocol Attacks

| Field | Detail |
|---|---|
| **Difficulty** | Advanced |
| **Estimated Study Time** | 10–12 weeks (12 hrs/week) |
| **Prerequisites** | Module 1.6 (networks — deep), Module 4.1 (cryptography — for TLS analysis), Module 3.5 (systems programming — for tool building) |

**Learning Objectives:**
- Perform packet-level network attacks: ARP spoofing, DHCP starvation, DNS cache poisoning
- Analyze and attack TLS configurations and implementations
- Understand and deploy network intrusion detection systems
- Implement network security tools: port scanners, protocol fuzzers, packet injectors
- Understand BGP hijacking, DNSSEC, and internet routing security

**Core Topics:**
- Network threat model: active vs passive attacker, on-path vs off-path
- Layer 2 attacks: ARP cache poisoning (Ettercap, scapy), MAC flooding, VLAN hopping
- Layer 3 attacks: IP spoofing, ICMP redirect, smurf, fragmentation attacks
- Layer 4 attacks: TCP SYN flood, RST injection, session hijacking
- DNS attacks: cache poisoning (Kaminsky attack), DNS amplification DDoS, DNS rebinding
- TLS attacks: weak cipher negotiation, certificate validation failures, HSTS bypass, certificate pinning bypass
- Wireless attacks: WPA2 4-way handshake capture and offline crack, PMKID attack, evil twin AP, WPA3 dragonblood
- VPN protocols: WireGuard, IPSec, OpenVPN — architecture and security analysis
- Firewall evasion: fragmentation, tunneling (DNS tunneling, ICMP tunneling), protocol obfuscation
- Intrusion detection: Snort/Suricata rule writing, anomaly detection, network baseline
- BGP security: route hijacking, RPKI, BGP communities; historical incidents

**Practical Projects:**
1. Build a full ARP poisoning MitM tool in Python using raw sockets and scapy
2. Implement a Snort-compatible rule engine that detects common attack patterns
3. Demonstrate DNS cache poisoning against a lab resolver
4. Build a DNS tunneling tool (for command & control understanding)

**Labs:**
- Lab 4.2.A: Wireshark capture and analysis of TLS 1.3 handshake — decode key schedule
- Lab 4.2.B: WPA2 handshake capture and hashcat crack in a dedicated lab environment
- Lab 4.2.C: Set up a complete network monitoring pipeline: packet capture → Suricata → Elasticsearch → Kibana

**Authoritative References:**
- Stallings, *Network Security Essentials* (Pearson)
- Kaufman, Perlman & Speciner, *Network Security: Private Communication in a Public World* (Prentice Hall)
- Bellovin & Cheswick, *Firewalls and Internet Security* (Addison-Wesley)
- Forshaw, *Attacking Network Protocols* (No Starch Press)
- RFC 4301 (IPSec), RFC 8446 (TLS 1.3)

---

### Module 4.3 — Web Security & Application Exploitation

| Field | Detail |
|---|---|
| **Difficulty** | Advanced |
| **Estimated Study Time** | 10–12 weeks (12 hrs/week) |
| **Prerequisites** | Module 1.6 (HTTP/network), Module 4.1 (cryptography — cookies, tokens), Module 1.7 (databases — SQL injection) |

**Learning Objectives:**
- Understand and exploit all OWASP Top 10 vulnerability classes
- Perform manual web application penetration testing
- Write custom exploits for injection, authentication, and authorization flaws
- Understand browser security model: SOP, CORS, CSP, CSRF tokens
- Perform server-side template injection, XXE, SSRF, and deserialization attacks
- Write Burp Suite extensions in Python/Java

**Core Topics:**
- HTTP security: cookies (SameSite, HttpOnly, Secure, partitioned), HSTS, security headers
- Authentication attacks: credential stuffing, brute force, password reset flaws, MFA bypass
- Session management: JWT attacks (alg:none, RS→HS confusion, weak secrets), session fixation, sidejacking
- Injection attacks: SQLi (blind, time-based, out-of-band), command injection, LDAP injection, XPath injection
- XSS: reflected, stored, DOM-based; CSP bypass techniques; exfiltration payloads
- CSRF: SameSite bypass, preflight bypass, JSON CSRF
- SSRF: internal service access, cloud metadata (169.254.169.254), protocol-based (file://, gopher://)
- XXE: OOB exfiltration, billion laughs, SSRF via XXE
- Insecure deserialization: Java (ysoserial), PHP object injection, Python pickle
- Server-side template injection: Jinja2, Twig, Freemarker
- Path traversal and file inclusion: LFI → RCE via log poisoning, PHP wrappers
- OAuth 2.0 and OIDC attack surface: redirect_uri hijacking, state parameter bypass, implicit flow attacks
- Browser security model: SOP, CORS misconfiguration, postMessage issues
- GraphQL-specific vulnerabilities: introspection, IDOR, batching attacks

**Practical Projects:**
1. Exploit all 10 OWASP Top 10 categories in DVWA (Damn Vulnerable Web Application) and document each
2. Build a custom Burp Suite extension that automates blind SQL injection detection
3. Complete all PortSwigger Web Security Academy labs (this is the mandatory hands-on track)
4. Build a simple WAF bypass toolkit

**Labs:**
- Lab 4.3.A: PortSwigger Web Security Academy — all labs across all categories (required)
- Lab 4.3.B: HackTheBox/TryHackMe web challenges — minimum 20 boxes
- Lab 4.3.C: SSRF → cloud metadata → credential exfiltration chain on a lab environment

**Authoritative References:**
- Stuttard & Pinto, *The Web Application Hacker's Handbook* (Wiley)
- Samy Kamkar, Michal Zalewski — research papers on web security
- PortSwigger Web Security Academy (portswigger.net) — the authoritative web security lab platform
- OWASP Testing Guide (owasp.org) — the pentesting methodology reference
- RFC 6749 (OAuth 2.0), RFC 9068 (JWT for OAuth 2.0)

---

## Phase 4 · Semester 4-B: Offensive Security

### Module 4.4 — Reverse Engineering

| Field | Detail |
|---|---|
| **Difficulty** | Expert |
| **Estimated Study Time** | 12–14 weeks (15+ hrs/week) |
| **Prerequisites** | Module 3.2 (x86-64 assembly), Module 3.1 (C), Module 2.5 (compilers — understanding optimization), Module 3.3 (OS — understanding process layout) |

**Learning Objectives:**
- Reverse engineer stripped x86-64 ELF and PE binaries using IDA Pro/Ghidra/Binary Ninja
- Dynamically analyze binaries with GDB, WinDbg, x64dbg
- Understand and defeat common anti-analysis techniques
- Reverse engineer network protocols from binary implementations
- Analyze ARM binaries (mobile and embedded)
- Reverse engineer packed/protected binaries

**Core Topics:**
- ELF binary format: sections, segments, symbols, dynamic linking, PLT/GOT, DWARF debug info
- PE binary format: DOS header, PE header, sections, imports, exports, relocations, TLS callbacks
- Static analysis workflow: entry point, main identification, cross-reference analysis, data structure reconstruction
- Ghidra: decompiler, scripting (Java/Python), custom analyzers, structure definition
- IDA Pro: graph view, pseudocode decompiler, IDAPython scripting, FLIRT signatures
- Dynamic analysis: GDB with PEDA/pwndbg/GEF, conditional breakpoints, function hooking
- Reconstructing data structures from binary: struct recovery, C++ vtable recovery
- Anti-analysis techniques: anti-debugging (ptrace check, timing checks, IsDebuggerPresent), anti-disassembly (opaque predicates, overlapping instructions, indirect branches), packing/encryption
- Unpacking: manual unpacking with OEP detection, dump and fix imports (PE)
- Protocol reverse engineering: correlate binary operations with network traffic to reconstruct protocol state machine
- ARM reverse engineering: Thumb/Thumb-2, AArch64; iOS/Android binary analysis
- .NET and Java reverse engineering: IL/bytecode, dnSpy, jadx

**Practical Projects:**
1. Reverse 10 crackmes of increasing difficulty (crackmes.one) and write detailed analysis reports
2. Reverse engineer a custom network protocol binary — document the protocol specification from binary analysis alone
3. Manually unpack a UPX-packed binary and restore its original import table
4. Write a Ghidra script that automatically identifies and labels all format string vulnerabilities in a binary

**Labs:**
- Lab 4.4.A: Flare-ON challenge (past years) — minimum 5 challenges solved
- Lab 4.4.B: Anti-debugging bypass — defeat 5 different anti-debugging techniques
- Lab 4.4.C: Reconstruct a C++ class hierarchy from a binary with no debug symbols

**Capstone (Module-level):** Perform a complete reverse engineering analysis of a real-world open-source binary with intentionally stripped symbols. Produce a professional-grade analysis report documenting all discovered functionality, data structures, and any identified vulnerabilities.

**Authoritative References:**
- Sikorski & Honig, *Practical Malware Analysis* (No Starch Press)
- Eilam, *Reversing: Secrets of Reverse Engineering* (Wiley)
- Dang, Gazet & Bachaalany, *The IDA Pro Book* (No Starch Press)
- Eagle, *The Ghidra Book* (No Starch Press)
- Intel® 64 and IA-32 Architectures Software Developer's Manual (instruction reference)

---

### Module 4.5 — Exploit Development & Vulnerability Research

| Field | Detail |
|---|---|
| **Difficulty** | Expert |
| **Estimated Study Time** | 14–16 weeks (15+ hrs/week) |
| **Prerequisites** | Module 3.2 (assembly), Module 3.3 (OS — virtual memory, kernel), Module 4.4 (reverse engineering), Module 3.1 (C — memory layout) |

**Learning Objectives:**
- Understand and exploit all major classes of memory corruption vulnerabilities
- Bypass modern exploit mitigations: ASLR, DEP/NX, stack canaries, RELRO, CFI, KASLR
- Write reliable, portable exploits in Python (pwntools)
- Exploit kernel vulnerabilities to achieve local privilege escalation
- Understand and perform heap exploitation against modern allocators (ptmalloc, tcmalloc, jemalloc)
- Analyze and exploit web browsers and complex applications

**Core Topics:**
- Exploit development fundamentals: vulnerability classes, attacker capabilities, exploit reliability
- Stack buffer overflows: basic overflow, return address overwrite, NOP sled
- Shellcode: writing null-free position-independent shellcode; encoding schemes
- Protection mechanisms and bypasses:
  - Stack canaries: bypass via information leak, brute force (fork servers), format string overwrite
  - NX/DEP: return-to-libc, ret2plt
  - ASLR: information leak to defeat, brute force (32-bit), heap spray
  - PIE: leaked base address exploitation
  - RELRO: partial vs full; GOT overwrite under partial RELRO
- Return-Oriented Programming (ROP): gadget finding (ROPgadget, ropper), ROP chains, ret2libc with ROP, SROP (Sigreturn-Oriented Programming)
- Format string vulnerabilities: read and write primitives, arbitrary write using %n
- Use-After-Free: understanding heap metadata, basic UAF exploitation
- Heap exploitation (ptmalloc):
  - Chunk layout, heap metadata (prev_size, size, fd, bk)
  - Fastbin attacks, tcache poisoning, unsorted bin attack, house of series
  - Safe-linking bypass
- Integer overflow vulnerabilities: signed/unsigned conversion, wrap-around, truncation
- Kernel exploitation:
  - Kernel attack surface: system calls, ioctl, /proc, /sys, kernel modules
  - SMEP, SMAP, KPTI, KASLR — bypass techniques
  - ret2usr, ROP in kernel context, modprobe_path overwrite
  - Kernel heap: SLUB allocator exploitation
  - Privilege escalation via commit_creds/prepare_kernel_cred
- Browser exploitation overview: V8 JIT compiler bugs, type confusion, sandbox escape
- Fuzzing: coverage-guided fuzzing (AFL++, libFuzzer), grammar-based fuzzing, corpus management; triage with ASan/UBSan
- CVE analysis: reading patches to reconstruct vulnerabilities, N-day exploit development

**Practical Projects:**
1. Solve all pwn challenges in the Nightmare binary exploitation course (coursework-style)
2. Develop a working exploit for a real CVE (kernel or application, from the last 3 years) — full chain
3. Build a coverage-guided fuzzer for a target and find at least one real bug
4. Exploit a heap corruption vulnerability in a custom allocator — implement three different exploitation techniques

**Labs:**
- Lab 4.5.A: pwn.college (dojo) — complete all relevant modules through advanced heap exploitation
- Lab 4.5.B: Kernel exploitation lab — exploit a known CTF kernel challenge (via QEMU)
- Lab 4.5.C: Format string exploitation — write to arbitrary address, leak stack canary, gain shell; 5 escalating targets

**Capstone (Module-level):** Discover (via fuzzing or manual analysis) a previously unknown or N-day vulnerability in an open-source program, develop a working end-to-end exploit with ASLR bypass, write a full technical advisory in the style of a professional CVE disclosure, and responsibly disclose.

**Authoritative References:**
- Hacking: The Art of Exploitation — Erickson (No Starch Press)
- Seacord, *Secure Coding in C and C++* (Addison-Wesley)
- Angelini, *Buffer Overflow Attacks* (Syngress)
- pwn.college (pwn.college) — the best structured exploit development curriculum
- Nightmare Binary Exploitation course (guyinatuxedo.github.io) — free, comprehensive
- Linux kernel source (kernel.org) and exploit-db.com
- Phrack Magazine (phrack.org) — historical and cutting-edge exploitation technique papers

---

## Phase 4 · Semester 4-C: Defensive Security & Analysis

### Module 4.6 — Malware Analysis

| Field | Detail |
|---|---|
| **Difficulty** | Expert |
| **Estimated Study Time** | 10–12 weeks (12–15 hrs/week) |
| **Prerequisites** | Module 4.4 (reverse engineering), Module 3.3 (OS — rootkit techniques, kernel), Module 4.2 (network — C2 protocols) |

**Learning Objectives:**
- Perform complete static and dynamic malware analysis
- Analyze all major malware families: RATs, ransomware, rootkits, bootkits, worms, cryptominers
- Analyze malware evasion techniques and defeat them
- Extract, decode, and analyze malware configuration and C2 protocols
- Write YARA rules and Snort/Suricata signatures from analysis
- Understand and analyze Android malware

**Core Topics:**
- Malware analysis environment setup: isolated VM, network simulation (INetSim), snapshot workflows
- Static analysis: hashing (MD5, SHA-256, imphash, ssdeep), strings, packer detection (PEiD, Detect-It-Easy), import analysis, code section entropy
- Dynamic analysis: process monitoring (Process Monitor, Process Hacker), API call tracing, network traffic analysis, registry and filesystem changes
- Malware categories and techniques:
  - Droppers, loaders, stagers, shellcode runners
  - Keyloggers: kernel-level vs user-level (SetWindowsHookEx, DirectInput)
  - RATs: remote access, screenshot, keylogging, file exfil, command dispatch
  - Ransomware: encryption workflow, key management, ransom note delivery; recovery forensics
  - Rootkits: user-mode (DLL injection, API hooking via IAT/EAT/inline), kernel-mode (DKOM, filter drivers), bootkits
  - Worms: propagation mechanisms, exploit payload, network scanning behavior
  - Fileless malware: living-off-the-land (LOLBins), PowerShell cradles, reflective DLL injection, process hollowing
  - Banking trojans: web injection, MitB (man-in-the-browser), certificate theft
  - Cryptominers: stratum protocol analysis, CPU/GPU fingerprinting evasion
- Evasion techniques: timing checks, environment fingerprinting (VM detection), obfuscation (string XOR, custom base64), anti-sandbox, sleep-based evasion
- Unpacking and deobfuscation: memory dump at OEP, automatic unpackers (unpacme), script deobfuscation
- C2 analysis: HTTP/HTTPS beaconing patterns, DNS-based C2, domain generation algorithms (DGA), protocol reconstruction
- Malware families in depth: Emotet, TrickBot, Cobalt Strike beacon analysis, Mimikatz
- YARA rules: writing effective signatures from malware analysis findings
- Android malware: APK structure, smali analysis, dynamic analysis with Frida

**Practical Projects:**
1. Analyze 5 real-world malware samples from MalwareBazaar — produce professional-grade analysis reports for each
2. Write 10 YARA rules that correctly classify your analyzed samples (tune for false positive rate)
3. Reverse engineer a DGA algorithm from a malware sample and predict its domains
4. Detect and analyze process hollowing live using Volatility memory forensics

**Labs:**
- Lab 4.6.A: ANY.RUN / Cuckoo sandbox — analyze 10 samples, compare automated vs manual findings
- Lab 4.6.B: Kernel rootkit detection — use Volatility3 to detect DKOM rootkit artifacts
- Lab 4.6.C: Cobalt Strike beacon analysis — extract C2 configuration from a beacon sample

**Authoritative References:**
- Sikorski & Honig, *Practical Malware Analysis* (No Starch Press) — the definitive reference
- Szor, *The Art of Computer Virus Research and Defense* (Addison-Wesley)
- MITRE ATT&CK Framework (attack.mitre.org) — technique taxonomy
- MalwareBazaar (bazaar.abuse.ch) — sample repository for analysis practice
- Cobalt Strike analysis resources: Didier Stevens' blog, FortiGuard, Mandiant publications

---

### Module 4.7 — Digital Forensics & Incident Response

| Field | Detail |
|---|---|
| **Difficulty** | Advanced–Expert |
| **Estimated Study Time** | 10–12 weeks (12 hrs/week) |
| **Prerequisites** | Module 3.3 (OS — filesystems, kernel), Module 4.6 (malware — for artifact understanding), Module 1.6 (networks — for PCAP analysis) |

**Learning Objectives:**
- Perform forensically sound evidence acquisition for disk, memory, and network
- Analyze Windows and Linux filesystem artifacts for evidence of compromise
- Perform complete memory forensics on both Windows and Linux memory images
- Reconstruct timelines of compromise from multiple artifact sources
- Perform network forensics from full-packet capture
- Conduct structured incident response investigations

**Core Topics:**
- Forensic methodology: chain of custody, write blocking, hashing for integrity, legal considerations
- Disk forensics:
  - Disk imaging: dd, dc3dd, FTK Imager; acquiring raw, E01, AFF4 formats
  - Filesystem forensics:
    - NTFS: MFT records, $LogFile, $UsnJrnl, $I30 directory index, ADS, timestamps (MACE)
    - ext4: inode structure, journal (journal.dat), superblock, deleted file recovery
    - FAT32: cluster chains, deleted entries, slack space
  - Windows artifact analysis: registry hives (SAM, SYSTEM, SOFTWARE, NTUSER.DAT), prefetch files, LNK files, jump lists, shellbags, event logs, browser artifacts, $Recycle.Bin, Volume Shadow Copies
  - Linux artifact analysis: bash history, /var/log/auth.log, /var/log/syslog, cron artifacts, ~/.bash_history, SSDT hooks
  - File carving: Photorec, foremost — recovering deleted files by file signature
  - Autopsy and Sleuth Kit workflow
- Memory forensics:
  - Memory acquisition: winpmem, lime (Linux Memory Extractor), VMware vmem
  - Volatility3 framework: process listing, DLLs, handles, network connections, registry, malfind, dumpfiles
  - DKOM detection: EPROCESS list vs pool scanning
  - Injected code detection: VAD inspection, code injection indicators
  - Cryptographic key extraction from memory: AES keys, TLS session keys
- Network forensics: Wireshark / Zeek / Arkime; correlation of IPs to events; extracting files from PCAP; protocol anomaly detection
- Log analysis and SIEM: Splunk/ELK stack queries, log correlation rules, alert tuning
- Timeline analysis: Plaso log2timeline, super timeline creation, event correlation
- Incident response process: preparation, identification, containment, eradication, recovery, lessons learned (NIST SP 800-61)
- Threat intelligence integration: IOC extraction, STIX/TAXII, VirusTotal, MISP

**Practical Projects:**
1. Analyze a complete forensic challenge image (from NIST or a CTF) — produce an incident report covering full compromise timeline
2. Build a memory forensics pipeline that automatically extracts network connections and injected processes from a memory image
3. Reconstruct a ransomware attack timeline from Windows event logs, filesystem artifacts, and memory dump

**Labs:**
- Lab 4.7.A: NIST CFReDS Project disk images — full analysis
- Lab 4.7.B: Memory forensics CTF challenges (MemLabs) — all 6 challenges
- Lab 4.7.C: Network forensics — analyze a provided PCAP of a multi-stage intrusion; identify all attacker actions

**Authoritative References:**
- Carvey, *Windows Forensic Analysis Toolkit* (Elsevier)
- Ligh, Case, Levy & Walters, *The Art of Memory Forensics* (Wiley)
- Casey, *Digital Evidence and Computer Crime* (Academic Press)
- NIST SP 800-86, *Guide to Integrating Forensic Techniques into Incident Response*
- Volatility3 documentation (volatilityfoundation.org)

---

## Phase 4 · Semester 4-D: Advanced Offensive & Defensive

### Module 4.8 — Penetration Testing & Red Team Operations

| Field | Detail |
|---|---|
| **Difficulty** | Expert |
| **Estimated Study Time** | 10–12 weeks (15+ hrs/week) |
| **Prerequisites** | Modules 4.2, 4.3, 4.5 (network, web, exploit development), Module 4.4 (reverse engineering) |

**Learning Objectives:**
- Conduct end-to-end penetration tests using a structured methodology (PTES, OWASP, NIST)
- Perform Active Directory attacks: Kerberoasting, Pass-the-Hash, DCSync, Golden Ticket
- Operate post-exploitation frameworks (Metasploit, Cobalt Strike, Sliver)
- Write custom C2 implants and evasion tooling
- Perform physical security assessments (RFID cloning, lock bypass)
- Document and communicate findings in professional reports

**Core Topics:**
- Penetration testing methodology: PTES, OWASP Testing Guide, rules of engagement, scoping
- Reconnaissance: OSINT (Maltego, theHarvester, Shodan, LinkedIn, Certificate Transparency), passive DNS, WHOIS, GitHub dorking
- Scanning and enumeration: nmap, masscan, service fingerprinting, vulnerability scanning (Nessus, OpenVAS)
- Active Directory attacks:
  - Enumeration: BloodHound/SharpHound, ldapsearch, PowerView
  - Kerberoasting and AS-REP roasting
  - Pass-the-Hash, Pass-the-Ticket, Over-Pass-the-Hash
  - DCSync: replication privilege abuse
  - Golden and Silver Ticket attacks
  - ACL abuse: WriteDACL, GenericAll, etc.
  - ADCS (Active Directory Certificate Services) attacks: ESC1–ESC8
  - Lateral movement: PsExec, WMI, DCOM, WinRM
- Credential harvesting: Mimikatz, secretsdump, LSASS dumping, SAM/SYSTEM/SECURITY offline cracking
- Persistence mechanisms: registry run keys, scheduled tasks, WMI subscriptions, DLL hijacking, COM hijacking, service installation, BITS jobs
- Defense evasion: AMSI bypass, ETW unhooking, process injection (shellcode injection, DLL injection, process hollowing, early bird injection), timestomping, log clearing
- C2 architecture: HTTP/HTTPS beaconing, domain fronting, C2 over DNS/ICMP, malleable C2 profiles
- Cobalt Strike and open-source alternatives (Sliver, Havoc, Brute Ratel)
- Reporting: executive summary, technical findings, CVSS scoring, remediation guidance, evidence appendix

**Practical Projects:**
1. Complete a full Active Directory lab attack chain (BloodHound → Kerberoasting → lateral movement → DCSync → domain dominance) in a personal lab
2. Write a custom C2 implant in C with HTTPS communication, sleep jitter, and a basic command interface
3. Complete 30 HackTheBox machines (mix of Linux and Windows, including Active Directory machines)
4. Write a professional penetration test report from one of your HackTheBox campaigns

**Labs:**
- Lab 4.8.A: HackTheBox Pro Labs (Offshore, RastaLabs) — mandatory
- Lab 4.8.B: CRTE (Certified Red Team Expert) lab environment
- Lab 4.8.C: Build a personal Active Directory lab using free evaluation Windows Server licenses

**Authoritative References:**
- Seitz, *Gray Hat Python* (No Starch Press)
- Weidman, *Penetration Testing* (No Starch Press)
- Metasploit: *The Penetration Tester's Guide* (No Starch Press)
- SpecterOps research blog (posts.specterops.io) — leading AD security research
- Harmj0y's blog (harmj0y.net) — Active Directory attack techniques
- MITRE ATT&CK for Enterprise (attack.mitre.org)

---

### Module 4.9 — Cloud Security

| Field | Detail |
|---|---|
| **Difficulty** | Advanced–Expert |
| **Estimated Study Time** | 10–12 weeks (12 hrs/week) |
| **Prerequisites** | Module 1.6 (networks), Module 3.3 (OS — containers/namespaces), Module 4.3 (web security), Module 4.2 (network security) |

**Learning Objectives:**
- Understand AWS, Azure, and GCP security architecture from first principles
- Perform cloud penetration testing: IAM privilege escalation, metadata exploitation, S3/storage misconfigurations
- Understand Kubernetes architecture and perform cluster security assessments
- Design and audit cloud security architectures for compliance and defense
- Understand serverless and container security models

**Core Topics:**
- Cloud shared responsibility model; threat model differences from on-premise
- AWS Security Architecture:
  - IAM: users, roles, policies (identity vs resource-based), permission boundaries, SCPs, trust relationships
  - EC2: instance metadata service (IMDSv1 vs IMDSv2), user data, security groups, VPC
  - S3: bucket policies, ACLs, block public access, presigned URLs, S3 notifications
  - Secrets: Secrets Manager, SSM Parameter Store, KMS CMKs, CloudHSM
  - Logging: CloudTrail, CloudWatch Logs, VPC Flow Logs, Config
  - IAM privilege escalation paths: CreatePolicyVersion, PassRole, sts:AssumeRole abuse
  - CloudTrail evasion; GuardDuty bypass techniques
- Azure Security: AAD, Managed Identity, RBAC, Key Vault, Defender for Cloud, Sentinel
- GCP Security: service accounts, Workload Identity, Cloud Armor, Security Command Center
- Container security:
  - Docker internals: namespaces, cgroups, overlay filesystem, capabilities
  - Docker security: privileged containers, volume mount escapes, socket exposure
  - Container escape techniques and detection
- Kubernetes security:
  - Architecture: API server, etcd, kubelet, scheduler, controller-manager
  - RBAC: ClusterRole, RoleBinding, ServiceAccount token misuse
  - Network policies, pod security admission, OPA/Gatekeeper
  - K8s attack paths: anonymous access, SSRF to API server, etcd access, token theft
  - Falco for runtime threat detection
- Serverless security: Lambda/Functions cold start attacks, event injection, over-privileged execution roles
- Supply chain security: SBOM, container image signing (Sigstore/Cosign), SLSA framework

**Practical Projects:**
1. Complete all flaws.cloud (CloudGoat by Rhino Security) scenarios — end-to-end cloud attack chains
2. Enumerate and exploit IAM privilege escalation paths in a personal AWS account
3. Perform a Kubernetes cluster security assessment on a misconfigured lab cluster
4. Design a full AWS security architecture for a three-tier web application using defense-in-depth

**Labs:**
- Lab 4.9.A: CloudGoat (Rhino Security Labs) — all scenarios
- Lab 4.9.B: KubeGoat (Kubernetes vulnerable-by-design cluster) — all scenarios
- Lab 4.9.C: Build a CSPM (cloud security posture management) tool using Boto3 that checks 20 security controls

**Authoritative References:**
- Amazon Web Services Security documentation (docs.aws.amazon.com/security)
- Prabhu & Shah, *Hacking the Cloud* (practical attack techniques, various publications)
- Rhino Security Labs blog (rhinosecuritylabs.com) — leading cloud attack research
- Trail of Bits, *Building Secure and Reliable Systems* (Google SRE Security book, free)
- CIS Benchmarks for AWS/Azure/GCP (cisecurity.org)
- Kubernetes security documentation (kubernetes.io/docs/concepts/security)

---

### Module 4.10 — Security Engineering & Secure Systems Design

| Field | Detail |
|---|---|
| **Difficulty** | Advanced–Expert |
| **Estimated Study Time** | 8–10 weeks (12 hrs/week) |
| **Prerequisites** | All Phase 4 modules; Modules 3.3, 3.4, 3.5 (systems programming) |

**Learning Objectives:**
- Apply threat modeling systematically to real systems (STRIDE, PASTA, attack trees)
- Design cryptographic protocols with formal security proofs
- Understand and apply formal verification to security-critical code
- Design reference monitor architectures and access control systems
- Write security engineering documentation: threat models, security requirements, design reviews
- Understand hardware security: TPM, Secure Enclave, HSM

**Core Topics:**
- Security engineering principles: least privilege, defense in depth, fail-safe defaults, separation of privilege, complete mediation, open design (Saltzer & Schroeder)
- Threat modeling: STRIDE (per-element analysis), PASTA (risk-centric), attack trees, data flow diagrams, threat libraries, MITRE ATT&CK integration
- Security design patterns: secure proxy, security kernel, reference monitor, credential manager, secure logger
- Access control models: DAC, MAC, RBAC, ABAC, IBAC; Bell-LaPadula, Biba, Clark-Wilson models
- Cryptographic protocol design: authentication protocols (challenge-response, PAKE), key agreement (SIGMA, Noise Protocol Framework), secure messaging (Signal protocol)
- Protocol formal verification: ProVerif and Tamarin Prover — model and verify TLS, SSH, or custom protocols
- Secure software development lifecycle (S-SDLC): security requirements, design review, code review, penetration testing, security regression testing, bug bounty
- Formal methods basics: model checking (TLA+, Alloy), program verification (Coq for security properties, Frama-C for C code), separation logic
- Hardware security:
  - TPM 2.0: PCRs, sealing/unsealing, remote attestation, measured boot
  - Secure Enclave/TEE: Intel SGX, ARM TrustZone — trust model, attack surface, side-channels
  - HSM: FIPS 140-2/3 requirements, key ceremony
- Zero Trust Architecture: NIST SP 800-207 principles, BeyondCorp implementation model
- Secure supply chain: reproducible builds, code signing, dependency auditing (SCA), SBOM standards (CycloneDX, SPDX)

**Practical Projects:**
1. Produce a complete threat model for a real application (can be open source) using STRIDE — minimum 20 threats identified, all with mitigations
2. Design and formally verify a simple key agreement protocol using ProVerif
3. Implement a reference monitor in C for a simple file access control system
4. Design a zero-trust architecture for a 3-tier application; document all security controls

**Labs:**
- Lab 4.10.A: TLA+ specification of a distributed consensus protocol — verify safety properties
- Lab 4.10.B: ProVerif — model the Diffie-Hellman key exchange; verify secrecy and authentication
- Lab 4.10.C: TPM 2.0 attestation — implement remote attestation using a software TPM (swtpm)

**Authoritative References:**
- Anderson, *Security Engineering* (Wiley, 3rd ed.) — the most comprehensive security engineering textbook
- Shostack, *Threat Modeling: Designing for Security* (Wiley)
- Saltzer & Schroeder, "The Protection of Information in Computer Systems" (CACM 1975) — foundational paper
- Kaufman, Perlman & Speciner, *Network Security* (Prentice Hall)
- NIST SP 800-207 (Zero Trust Architecture) — free from nist.gov
- ProVerif manual and Tamarin Prover documentation

---

## Phase 4 · Semester 4-E: Final Capstone

### Module 4.11 — Capstone: Comprehensive Security Research Project

| Field | Detail |
|---|---|
| **Difficulty** | Expert |
| **Estimated Study Time** | 12–16 weeks (20+ hrs/week) |
| **Prerequisites** | All modules in Phases 0–4 |

**Purpose:** This capstone integrates all curriculum knowledge into an original, publishable-quality security research project. It should approximate the quality of a USENIX Security, CCS, or S&P conference paper, or a professional security advisory.

**Learning Objectives:**
- Conduct original security research from hypothesis to publication
- Select, scope, and execute a research project with real-world impact
- Write a technical research paper at conference quality
- Present findings clearly to both technical and non-technical audiences

**Project Options (choose one):**

**Track A — Vulnerability Research:**
Discover a previously unknown vulnerability in a widely deployed system (OS, browser, library, protocol). Develop a working proof-of-concept exploit. Write a full CVE-format advisory and responsible disclosure. Produce an analysis paper.

**Track B — Defensive Tool:**
Design, implement, evaluate, and open-source a novel security defensive tool (IDS, fuzzer, static analyzer, memory safe allocator). Evaluate against baselines. Publish with reproducible evaluation.

**Track C — Cryptographic Research:**
Design and formally verify a new cryptographic protocol or prove a new attack on an existing protocol. Implement in a production-ready library. Write the security proof in the style of a cryptography paper.

**Track D — Forensics & Threat Intelligence:**
Conduct an in-depth analysis of a malware campaign or threat actor. Produce a threat intelligence report with ATT&CK mapping, IOC set, detection rules, and original technical findings not previously published.

**Deliverables:**
- Written technical report (minimum 15 pages, conference style)
- Working code repository (GitHub) with README, build instructions, and reproducible evaluation
- 30-minute technical presentation
- Responsible disclosure (if vulnerabilities found) or public release

**Authoritative References:**
- IEEE S&P, USENIX Security, ACM CCS, NDSS proceedings — study the format and bar
- Shostack, *Threat Modeling: Designing for Security* (Wiley)
- Writing resources: Dreyfus, *The Elements of Style*; IEEE Style Manual

---

# Cross-Curriculum Resources

## Hands-On Practice Platforms (Required Throughout)

| Platform | Primary Use | Phase |
|---|---|---|
| OverTheWire (Bandit/Narnia/Protostar) | Linux + binary basics | 1–3 |
| pwn.college | Exploit development (structured) | 3–4 |
| HackTheBox | Penetration testing, CTF | 4 |
| TryHackMe | Guided defensive + offensive | 3–4 |
| Cryptopals | Applied cryptography | 4 |
| PortSwigger Web Security Academy | Web security | 4 |
| CTFtime.org | Competitive CTF (weekly) | 2–4 |
| VulnHub | Local VM-based targets | 4 |
| CloudGoat / flaws.cloud | Cloud security | 4 |
| Hack The Box Pro Labs | Advanced AD + enterprise | 4 |

## Essential Professional Certifications (Aligned to Curriculum)

Pursue after the relevant phase is complete:

| Certification | Phase Alignment | Body |
|---|---|---|
| Linux+ or LPIC-1 | After Phase 1 | CompTIA / LPI |
| eJPT | After Phase 4.2–4.3 | eLearnSecurity |
| OSCP (PEN-200) | After Module 4.8 | Offensive Security |
| CRTE / CRTP | After Module 4.8 | Altered Security |
| GREM | After Module 4.6 | GIAC |
| GCFE / GCFA | After Module 4.7 | GIAC |
| AWS Security Specialty | After Module 4.9 | AWS |
| OSED (EXP-301) | After Module 4.5 | Offensive Security |

---

# Master Prerequisites Graph

```
Phase 0: Mathematical Foundations
├── 0.1 Discrete Math & Logic
│   └──→ 0.2 Linear Algebra
│   └──→ 0.3 Calculus & Probability
│
Phase 1: Core Computer Science
├── 1.1 Programming (Python)          ← 0.1
├── 1.2 Data Structures & Algorithms  ← 0.1, 0.3, 1.1
├── 1.3 Unix/Linux Fundamentals       ← 1.1
├── 1.4 OOP & Software Engineering    ← 1.1, 1.2
├── 1.5 Theory of Computation         ← 0.1, 1.2
├── 1.6 Computer Networks             ← 0.3, 1.2, 1.3
└── 1.7 Databases                     ← 1.2, 1.4
│
Phase 2: Computer Engineering
├── 2.1 Digital Logic                 ← 0.1
├── 2.2 Computer Architecture I       ← 2.1, 1.2
├── 2.3 Memory Systems & I/O          ← 2.2
├── 2.4 Embedded Systems              ← 2.2, 1.1
└── 2.5 Compilers                     ← 1.5, 1.2, 2.2
│
Phase 3: Systems Programming
├── 3.1 C Programming                 ← 1.1, 2.2, 2.3
├── 3.2 x86-64 Assembly               ← 2.2, 3.1
├── 3.3 Operating Systems             ← 2.2, 2.3, 3.1, 3.2, 1.6
├── 3.4 Concurrent Programming        ← 3.3, 3.1
├── 3.5 Advanced Systems Programming  ← 3.1, 3.3, 3.4, 1.6
└── 3.6 C++                           ← 3.1, 1.4
│
Phase 4: Cybersecurity Specialization
├── 4.1 Cryptography                  ← 0.1, 0.3, 1.5
├── 4.2 Network Security              ← 1.6, 4.1, 3.5
├── 4.3 Web Security                  ← 1.6, 4.1, 1.7
├── 4.4 Reverse Engineering           ← 3.2, 3.1, 2.5, 3.3
├── 4.5 Exploit Development           ← 3.2, 3.3, 4.4, 3.1
├── 4.6 Malware Analysis              ← 4.4, 3.3, 4.2
├── 4.7 Digital Forensics & IR        ← 3.3, 4.6, 1.6
├── 4.8 Penetration Testing & Red Team← 4.2, 4.3, 4.5, 4.4
├── 4.9 Cloud Security                ← 1.6, 3.3, 4.3, 4.2
├── 4.10 Security Engineering         ← All Phase 4 modules
└── 4.11 Capstone                     ← All modules
```

---

# Study Time Summary

| Phase | Modules | Estimated Duration |
|---|---|---|
| Phase 0: Mathematical Foundations | 3 modules | 3–4 months |
| Phase 1: Core Computer Science | 7 modules | 10–12 months |
| Phase 2: Computer Engineering | 5 modules | 8–10 months |
| Phase 3: Systems Programming | 6 modules | 8–10 months |
| Phase 4: Cybersecurity Specialization | 11 modules | 14–16 months |
| **Total** | **32 modules** | **~43–52 months** |

> **Suggested pace:** 10–15 hours per week = approximately 4.5 years of part-time study. Full-time immersive study (30–40 hrs/week) can compress this to 18–24 months without sacrificing depth. Do not skip phases. The prerequisites are not suggestions.

---

*Curriculum version 1.0 — Detailed chapter-by-chapter reading lists, weekly study schedules, and graded problem sets available on request.*

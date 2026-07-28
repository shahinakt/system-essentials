# Phase 2 — Complete Study Package
## Computer Engineering & Computer Architecture
### Chapter Reading Lists · Weekly Schedules · Graded Problem Sets

---

> **Prerequisites before starting Phase 2:** All Phase 1 milestone assessments passed. You must be comfortable with: formal proof (Phase 0), algorithm analysis and data structures (Module 1.2), Python and C-adjacent thinking (Module 1.1), and basic Linux fluency (Module 1.3). Phase 2 descends from software into hardware — from algorithms into circuits, from programs into instruction sets, from files into physical memory cells. This is the machine beneath everything you've written so far.

---

# MODULE 2.1 — Digital Logic & Boolean Circuits

**Duration:** 6–8 weeks | **Hours/week:** 10 | **Total hours:** ~70

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Mano & Ciletti — *Digital Design*, 5th ed.

---

### Chapter 1 — Digital Systems and Binary Numbers

**Read:** Entire chapter.

**Section 1.1 — Digital and Analog Systems**
Focus on: why digital (discrete) representations dominate over analog in modern computing — noise immunity and reproducibility. The bit as the fundamental unit of information (connect to Shannon entropy from Module 0.3).

**Section 1.2 — Binary Numbers**
Focus on: positional notation in base 2; converting between binary, octal, and hexadecimal by grouping. Hex is how you read memory dumps, binary patches, network captures, and disassembly — it is a fundamental skill. Practice until conversion is automatic (target: convert any 8-bit hex value to binary and decimal in under 5 seconds mentally).

**Section 1.3 — Number-Base Conversions**
Focus on: integer conversion (repeated division); fractional conversion (repeated multiplication). Understand: most fractional decimal values cannot be represented exactly in binary — this is the source of floating-point rounding errors.

**Section 1.4 — Octal and Hexadecimal Numbers**
Read for completeness. Focus on the grouped-bit shorthand that makes hex the standard for representing binary data.

**Section 1.5 — Complements**
Focus on: one's complement and two's complement representations. Two's complement is how all modern processors represent signed integers. Understand: negation = invert all bits and add 1; the range of n-bit two's complement is [−2^{n−1}, 2^{n−1}−1]; overflow detection. **This section directly connects to integer overflow vulnerabilities in Modules 3.1 and 4.5.**

**Section 1.6 — Signed Binary Numbers**
Focus on: sign-magnitude vs two's complement; sign extension (critical for understanding how C handles type conversions — a source of security bugs).

**Section 1.7 — Binary Codes**
Focus on: BCD (Binary-Coded Decimal) and its use in legacy systems; Gray code; ASCII and Unicode basics; parity bits as the simplest error-detection code (connects to error-correcting codes in Module 0.2).

**Section 1.8 — Binary Storage and Registers**
Focus on: a register as a collection of flip-flops storing bits; transfer operations; the register as the hardware counterpart to a variable.

---

### Chapter 2 — Boolean Algebra and Logic Gates

**Read:** Entire chapter — the algebraic foundation of all digital design.

**Section 2.1 — Basic Definitions**
Focus on: Boolean algebra as an algebraic system (not just true/false tables) with closure, associativity, commutativity, distributivity, identity elements, and complement. Huntington's postulates — know all six.

**Section 2.2 — Axiomatic Definition of Boolean Algebra**
Focus on: the duality principle — every Boolean theorem has a dual obtained by swapping AND↔OR and 0↔1. This halves the number of theorems you need to prove.

**Section 2.3 — Basic Theorems and Properties**
Memorize and prove: idempotency (A·A = A), involution (A'' = A), De Morgan's laws (both forms), absorption laws (A + AB = A; A(A+B) = A), consensus theorem. **De Morgan's laws are the single most-used identity in digital design, compiler optimization, and network firewall rule analysis.**

**Section 2.4 — Boolean Functions**
Focus on: the canonical forms — sum of minterms (SOM) and product of maxterms (POM). Every Boolean function has a unique canonical SOM and POM representation. Understand: a truth table IS a canonical SOM representation.

**Section 2.5 — Canonical and Standard Forms**
Focus on: minterms, maxterms, minterm numbering; converting between truth table and canonical forms; sum of products (SOP) and product of sums (POS) standard forms (these need not be canonical).

**Section 2.6 — Other Logic Operations**
Focus on: NAND, NOR, XOR, XNOR. NAND and NOR are functionally complete (any Boolean function can be built from NAND alone, or from NOR alone). XOR is the fundamental operation of addition and cryptographic mixing — it appears in AES, DES, SHA, stream ciphers, and CRC computation.

**Section 2.7 — Digital Logic Gates**
Focus on: gate symbols, timing diagrams, propagation delay, fan-in, fan-out. CMOS implementation conceptually — understand why CMOS gates naturally implement NAND/NOR, which is why these are universal.

**Section 2.8 — Integrated Circuits**
Skim — historical context on SSI/MSI/LSI/VLSI. Understand: a modern CPU contains billions of CMOS transistors; the basic NAND gate uses 4.

---

### Chapter 3 — Gate-Level Minimization

**Read:** Entire chapter.

**Section 3.1 — The Map Method (Karnaugh Maps)**
Focus on: Karnaugh maps for 2, 3, 4, and 5 variables; grouping 1s in powers of 2 (1, 2, 4, 8, 16); the rule for valid groupings (must be rectangular, must wrap around edges); don't-care conditions. K-maps are the primary minimization tool in hardware design. For 6 variables, use two 5-variable maps.

**Section 3.2 — Four-Variable Maps**
Work every example by hand. The ability to read a K-map quickly is a practical skill.

**Section 3.3 — Product of Sums Simplification**
Focus on: grouping 0s for POS; the dual procedure to SOP minimization.

**Section 3.4 — Don't-Care Conditions**
Focus on: using don't-cares to achieve further minimization; the risk of incorrectly assuming a don't-care (in hardware design, a don't-care that actually occurs produces undefined behavior — a source of security issues in some embedded contexts).

**Section 3.5 — NAND and NOR Implementation**
Focus on: converting a SOP expression to an all-NAND implementation (double negation and De Morgan); converting a POS expression to all-NOR. **Every digital circuit can be implemented with only NAND gates — this is what FPGAs and ASICs do internally.**

**Section 3.6 — Exclusive-OR Function**
Focus on: XOR properties (self-inverse: A ⊕ A = 0; A ⊕ 0 = A; A ⊕ 1 = A'); odd-parity function; XOR as controlled inverter; applications in error detection and cryptography.

**Section 3.7 — Hardware Description Languages**
Read as an introduction — HDL implementation is the focus of Module 2.2.

---

### Chapter 4 — Combinational Logic

**Read:** Entire chapter.

**Section 4.1 — Combinational Circuits**
Focus on: the definition (output depends only on current input, no memory); functional specification + timing specification; the difference from sequential logic (which has memory). Design methodology: truth table → Boolean expression → minimized expression → gate implementation.

**Section 4.2 — Analysis Procedure**
Focus on: deriving the Boolean function from a gate-level circuit; propagation delay analysis (longest path = critical path). **The critical path determines the maximum clock frequency — critical for processor design in Module 2.2.**

**Section 4.3 — Design Procedure**
Focus on: the systematic 7-step design procedure. Apply it in full to every design problem.

**Section 4.4 — Binary Adder-Subtractor**
Focus on: the half adder (sum = A ⊕ B, carry = AB); the full adder (sum = A ⊕ B ⊕ C_in, carry = majority function); the ripple-carry adder (chain of full adders); critical path of the ripple-carry adder is O(n). The full adder is the building block of the ALU — it appears in every processor. **Understand carry propagation: it is why hardware integer arithmetic is faster than software bignum arithmetic.**

**Section 4.5 — Carry Lookahead Adder**
Focus on: generate (G = AB) and propagate (P = A ⊕ B) signals; the carry lookahead equations; how the CLA reduces critical path from O(n) to O(log n) at the cost of more gates. This is the first example of the time-space tradeoff in hardware.

**Section 4.6 — Other Arithmetic Functions**
Focus on: binary multiplication as repeated addition and shift; BCD adder; magnitude comparator.

**Section 4.7 — Decoders**
Focus on: n-to-2^n decoder; the decoder as a minterm generator; implementing any Boolean function using a decoder and OR gate.

**Section 4.8 — Encoders**
Focus on: the priority encoder and its applications.

**Section 4.9 — Multiplexers**
Focus on: the 2-to-1, 4-to-1, and 8-to-1 mux; implementing any Boolean function with a mux (the data selector approach); the relationship between muxes and if-else constructs in hardware.

**Section 4.10 — HDL Models of Combinational Circuits**
Read the Verilog examples — you will write Verilog in Module 2.2.

---

### Chapter 5 — Synchronous Sequential Logic

**Read:** Entire chapter.

**Section 5.1 — Sequential Circuits**
Focus on: the distinction between combinational (memoryless) and sequential (has state) logic; the Mealy vs Moore machine models; the state register as the circuit's memory; the clock as the synchronization mechanism.

**Section 5.2 — Storage Elements: Latches**
Focus on: SR latch (NOR-based and NAND-based); the forbidden state (S=R=1 for NOR latch); the D latch (eliminates forbidden state); level-triggered vs edge-triggered operation. Understanding the SR latch is essential for understanding DRAM cells and cache vulnerabilities.

**Section 5.3 — Storage Elements: Flip-Flops**
Focus on: the master-slave construction; the D flip-flop (positive edge-triggered: samples D on rising clock edge); the JK flip-flop; the T flip-flop. **Every bit of processor state — every register bit, every cache valid bit, every pipeline register — is a D flip-flop.**

**Section 5.4 — Analysis of Clocked Sequential Circuits**
Focus on: state table; state diagram; next-state and output equations; the analysis procedure. Trace through the analysis of a 3-bit counter.

**Section 5.5 — Synthesizable HDL Models of Sequential Circuits**
Focus on: the `always @(posedge clk)` block in Verilog; the difference between blocking (=) and non-blocking (<=) assignments — **this distinction causes the most common HDL bugs**.

**Section 5.6 — State Reduction and Assignment**
Focus on: finding equivalent states (same output and same next-state behavior); the table-filling algorithm for state minimization; state encoding choices (binary, Gray, one-hot).

**Section 5.7 — Design Procedure**
Focus on: the complete design flow from word problem to implemented circuit. Apply to: a sequence detector, a vending machine controller, a traffic light controller.

---

### Chapter 6 — Registers and Counters

**Read:** Sections 6.1–6.6.

**Section 6.1 — Registers**
Focus on: the parallel load register; the shift register; SIPO, PISO, SISO, PIPO configurations. Shift registers are used in CRC computation (connect to Module 1.6 networking) and in cryptographic LFSRs.

**Section 6.2 — Shift Registers**
Focus on: the Linear Feedback Shift Register (LFSR) as a hardware pseudo-random number generator. **LFSRs are used in stream ciphers (broken ones, like A5/1 in GSM) — understanding them at the hardware level is prerequisite to attacking them in Module 4.1.**

**Section 6.3 — Ripple Counters**
Focus on: the asynchronous ripple counter; the propagation delay problem; why synchronous counters are preferred.

**Section 6.4 — Synchronous Counters**
Focus on: the synchronous binary counter; carry lookahead in counters; modulo-N counter design.

**Section 6.5 — Other Counters**
Focus on: the Johnson counter; ring counter; up-down counter.

**Section 6.6 — HDL for Registers and Counters**
Read and implement all HDL examples.

---

### Chapter 7 — Memory and Programmable Logic

**Read:** Sections 7.1–7.5.

**Section 7.1 — Introduction**
Focus on: RAM vs ROM distinction; volatile vs non-volatile; the address/data bus model — this is the physical model of the memory hierarchy in Module 2.3.

**Section 7.2 — Random-Access Memory**
Focus on: SRAM cell (6-transistor cross-coupled inverters); DRAM cell (1-transistor capacitor); the read-destructive nature of DRAM reads; the refresh cycle; why DRAM requires periodic refresh — **this is the physical basis of the Rowhammer vulnerability in Module 2.3**.

**Section 7.3 — Memory Decoding**
Focus on: address decoding; memory expansion (word-width expansion and address-space expansion using multiple chips); the memory map concept.

**Section 7.4 — Error Detection and Correction**
Focus on: parity bits (detect 1-bit errors, cannot correct); Hamming codes (detect and correct 1-bit errors); SEC-DED (Single Error Correct, Double Error Detect) codes used in ECC RAM. **ECC memory exists precisely because DRAM bit flips occur — connecting hardware to the Rowhammer exploit.**

**Section 7.5 — Read-Only Memory**
Focus on: ROM, PROM, EPROM, EEPROM, Flash — understand the write mechanism for Flash (Fowler-Nordheim tunneling) and why Flash has limited write cycles (relevant to SSD forensics in Module 4.7).

---

### Supplementary: Harris & Harris — *Digital Design and Computer Architecture*, 2nd ed.

**Read in parallel with Mano:**
- **Chapter 1:** Number systems (alternative treatment, clearer on two's complement).
- **Chapter 2:** Combinational logic design (stronger on hardware description language coverage).
- **Chapter 3:** Sequential logic design (best treatment of timing analysis).
- **Chapter 4:** Hardware Description Languages — the primary HDL reference; read all Verilog sections.

---

### Supplementary: MIT 6.004 Computation Structures (OCW)
Watch: Labs 1–6 (combinational logic through sequential circuits). These labs use a browser-based circuit simulator — complete all exercises before attempting the Logisim-Evolution projects.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Number Systems and Boolean Algebra
- **Day 1:** Mano Ch. 1.1–1.6. Convert 30 numbers between binary, hex, and decimal without a calculator. Practice two's complement negation on 10 signed values.
- **Day 2:** Mano Ch. 1.7–1.8. ASCII encoding, parity. Compute the even parity bit for 5 byte values.
- **Day 3:** Mano Ch. 2.1–2.4. Boolean axioms. Prove 8 Boolean identities algebraically (no truth tables).
- **Day 4:** Mano Ch. 2.5–2.8. Write canonical SOM for 5 truth tables. Implement NAND-only versions.
- **Day 5:** Problem Set 2.1 Tier 1, problems 1–8.
- **Day 6:** Logisim-Evolution Lab — build and test all basic gates, verify De Morgan's laws experimentally.
- **Day 7:** Rest.

### Week 2 — Minimization and Combinational Design
- **Day 1:** Mano Ch. 3.1–3.4. K-map minimization of 10 functions (3 and 4 variable). Include don't-cares.
- **Day 2:** Mano Ch. 3.5–3.6. Convert SOP to all-NAND; verify equivalence. XOR properties and applications.
- **Day 3:** Mano Ch. 4.1–4.5. Half adder, full adder, ripple-carry adder, CLA. Design and simulate.
- **Day 4:** Mano Ch. 4.7–4.9. Decoder, encoder, MUX. Implement a 4-bit function using a MUX.
- **Day 5:** Problem Set 2.1 Tier 1, problems 9–16.
- **Day 6:** Logisim-Evolution Lab — build a 4-bit ripple-carry adder and a 4-bit CLA; compare gate count and critical paths.
- **Day 7:** Rest.

### Week 3 — Sequential Logic: Latches and Flip-Flops
- **Day 1:** Mano Ch. 5.1–5.3. SR latch, D latch, D flip-flop. Trace the master-slave operation on 3 clock cycles.
- **Day 2:** Mano Ch. 5.4. Analyze a given clocked sequential circuit: derive state table and state diagram.
- **Day 3:** Mano Ch. 5.5 + Harris Ch. 4 (HDL). Write Verilog for a D flip-flop and a register. Simulate in ModelSim or Icarus Verilog.
- **Day 4:** Mano Ch. 5.6–5.7. Design a sequence detector FSM (detects "1011" in a serial bitstream). Full design procedure.
- **Day 5:** Problem Set 2.1 Tier 1, problems 17–20, Tier 2 problems 1–4.
- **Day 6:** Logisim-Evolution Lab — build the sequence detector. Test with all 16 possible 4-bit inputs.
- **Day 7:** Rest.

### Week 4 — Registers, Counters, Memory
- **Day 1:** Mano Ch. 6.1–6.4. Shift register, LFSR, synchronous counter. Trace LFSR output for 5 clock cycles.
- **Day 2:** Mano Ch. 7.1–7.5. SRAM cell analysis, DRAM refresh, Hamming code construction.
- **Day 3:** Harris Ch. 4 (complete HDL chapter). Verilog for: synchronous counter, shift register, memory model.
- **Day 4:** Problem Set 2.1 Tier 2, problems 5–10.
- **Day 5:** Capstone project: 4-bit CPU in Logisim-Evolution — begin design (register file + ALU).
- **Day 6:** Continue capstone: instruction memory + control unit skeleton.
- **Day 7:** Rest.

### Week 5 — Capstone: 4-bit CPU and HDL Project
- **Days 1–4:** Complete the 4-bit CPU in Logisim-Evolution. It must execute: ADD, SUB, AND, OR, LOAD, STORE, JMP, BEQ.
- **Day 5:** Write Verilog for the same design. Simulate with a test bench.
- **Day 6:** Problem Set 2.1 Tier 3, problems 1–6.
- **Day 7:** Rest.

### Week 6 — Review, FSM Lab, and Milestone
- **Days 1–2:** Traffic light controller FSM — design, implement in Logisim, implement in Verilog.
- **Day 3:** UART simplified FSM — design a serial receiver state machine.
- **Day 4:** Problem Set 2.1 Tier 3, problems 7–10.
- **Day 5:** Milestone assessment attempt.
- **Day 6:** Remediation.
- **Day 7:** Rest.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Convert without a calculator:
(a) 0xDEAD to binary and decimal.
(b) 0b10110111 to hex and decimal.
(c) −53 (decimal) to 8-bit two's complement binary and hex.
(d) 0xFF in 8-bit two's complement — what decimal value does this represent?

**Problem 2.** Using only Boolean algebra (no truth tables), prove each identity and state which axiom or theorem justifies each step:
(a) A + AB = A (absorption)
(b) (A + B)(A + C) = A + BC (distributivity)
(c) AB + A'C + BC = AB + A'C (consensus theorem)

**Problem 3.** Write the canonical sum of minterms (SOM) for the function f(A,B,C,D) defined by the truth table: f = 1 when the 4-bit input represents a prime number (1–15). Minimize using a K-map. Draw the minimized gate-level circuit.

**Problem 4.** Design a full adder using only NAND gates. Show the transformation from the SOP expression to an all-NAND circuit using De Morgan's laws. Count the total gates and compare to the standard XOR-based implementation.

**Problem 5.** A 4-bit ripple-carry adder has a full adder propagation delay of t_FA = 10ns. (a) What is the worst-case addition delay? (b) A 4-bit carry-lookahead adder has individual gate delays of 2ns. What is the CLA's critical path? (c) At what bit width does the CLA become faster than the ripple-carry?

**Problem 6.** Design a 3-bit Gray code counter (cycles through Gray code sequence) using D flip-flops. Give the state table, next-state equations (minimized via K-map), and the circuit schematic.

**Problem 7.** Design an FSM (Moore model) that detects the sequence "101" (overlapping) in a serial input stream. (a) Draw the state diagram with all transitions labeled. (b) Write the state table. (c) Minimize using state equivalence. (d) Implement with D flip-flops — give next-state and output equations.

**Problem 8.** A 16×8 RAM chip has 16 memory locations, each 8 bits wide. (a) How many address lines are needed? (b) How many data lines? (c) Show how to connect four such chips to form a 64×8 memory. (d) Show how to connect four such chips to form a 16×32 memory.

**Problem 9.** Compute the Hamming code for the 4-bit data word 1011. Show the positions of all parity bits and data bits. Then introduce a single-bit error in bit position 5 and show how the parity check identifies and corrects the error.

**Problem 10.** Explain why DRAM requires periodic refresh but SRAM does not. Relate this to the physical storage mechanism of each. Then explain how Rowhammer exploits the physics of DRAM — what physical phenomenon causes bit flips in adjacent rows?

**Problem 11.** Write synthesizable Verilog for a parameterized N-bit register with synchronous reset, enable, and parallel load. Write a testbench that verifies all four control cases.

**Problem 12.** Design a priority encoder with 8 inputs (I7–I0) and 3-bit output indicating the highest active input. Include a valid output signal. Minimize using K-maps. Implement in Verilog.

**Problem 13.** An LFSR has taps at positions 4 and 1 (polynomial x⁴ + x + 1). Starting from seed 0001, trace the LFSR output for 15 clock cycles. How many cycles before it returns to 0001? Is this the maximum-length sequence for a 4-bit LFSR?

**Problem 14.** Using a 4-to-1 multiplexer and one additional gate, implement the function f(A,B,C) = A'B + AB'C + AC. Show which signals connect to which MUX inputs and select lines.

**Problem 15.** Design a BCD-to-7-segment display decoder. The inputs are a 4-bit BCD digit (0–9); the seven outputs drive segments a–g of a 7-segment display. Use K-maps (with don't-cares for inputs 10–15) to minimize each output. Write the Verilog implementation.

**Problem 16.** Analyze the following Verilog snippet. What is the functional difference between using blocking (=) and non-blocking (<=) assignments in this context? What is the correct choice for a sequential circuit and why?
```verilog
always @(posedge clk) begin
    a = b;
    b = a;  // blocking version
end
// vs
always @(posedge clk) begin
    a <= b;
    b <= a;  // non-blocking version
end
```

**Problem 17.** A traffic light controller manages a 4-way intersection. Design a Moore FSM with states: NS_GREEN, NS_YELLOW, EW_GREEN, EW_YELLOW. Inputs: timer expiry signal. Draw the complete state diagram. Implement in Verilog with a 2-bit state register.

**Problem 18.** Prove that NAND is functionally complete by showing how to implement NOT, AND, and OR using only NAND gates. Then prove NOR is also functionally complete.

**Problem 19.** A 1024-word × 32-bit memory is built from 256×8 chips. (a) How many chips are required? (b) Draw the connection diagram showing address, data, and chip-select signals. (c) How many address bits select the word, and how are they distributed?

**Problem 20.** Sign-extend the following values from 8-bit to 16-bit two's complement. Then explain how a C compiler uses sign extension when converting `int8_t` to `int16_t` and why an incorrect unsigned extension would produce a wrong result:
(a) 0x7F, (b) 0x80, (c) 0xFF, (d) 0x01.

---

### Tier 2 — Intermediate

**Problem 1.** Design a 4-bit magnitude comparator that outputs three signals: A>B, A=B, A<B. Use K-maps to minimize each output. Compare your minimized design to the standard iterative comparator approach.

**Problem 2.** Implement a 4-bit ALU in Verilog that performs: ADD, SUB (two's complement), AND, OR, XOR, NOT (of A), SHL (shift left by 1), SHR (arithmetic shift right by 1). Include carry-out, zero flag, negative flag, and overflow flag. Write a comprehensive testbench covering all 8 operations and all corner cases (overflow, zero result, carry out).

**Problem 3.** Design a synchronous 4-bit up/down counter with: synchronous reset, load (parallel load from 4-bit input), and count direction control. Use D flip-flops. Minimize next-state equations. Write Verilog and a complete testbench.

**Problem 4.** A UART transmitter sends 8-bit data with 1 start bit (low), 1 stop bit (high), and even parity at 9600 baud. Design the FSM controlling the transmission. Define all states, transitions, and output signals. Write the Verilog implementation.

**Problem 5.** Design a hardware divider for unsigned 8-bit numbers using the shift-and-subtract algorithm. (a) Describe the algorithm step by step. (b) Design the datapath (shifter, subtractor, register). (c) Design the control FSM. (d) Analyze the worst-case number of cycles.

**Problem 6.** Explain the concept of metastability in flip-flops. When does it occur? Why can it never be completely eliminated (connect to the fundamental physics of bistable elements)? What engineering practices (synchronizer circuits) mitigate it? Why is metastability relevant to security (glitching attacks on secure microcontrollers)?

**Problem 7.** A memory system uses 30-bit physical addresses and 4KB pages. (a) How many bits are the page number and page offset? (b) How many entries are in a flat page table? (c) If each page table entry is 4 bytes, how large is the page table? (d) Why does this motivate multi-level page tables? (This problem bridges to Module 2.3.)

**Problem 8.** Implement a 4-bit multiplier using an array of full adders (the standard shift-and-add hardware implementation). Draw the complete circuit. Count the total number of full adders and half adders. Analyze the critical path.

---

### Tier 3 — Advanced

**Problem 1.** Design a hardware implementation of CRC-32 (the polynomial used in Ethernet, ZIP, and PNG). The generator polynomial is x³² + x²⁶ + x²³ + x²² + x¹⁶ + x¹² + x¹¹ + x¹⁰ + x⁸ + x⁷ + x⁵ + x⁴ + x² + x + 1. (a) Implement a bit-serial CRC calculator using an LFSR in Verilog. (b) Test against a known CRC-32 value. (c) Explain how CRC can detect all burst errors up to 32 bits and most longer burst errors.

**Problem 2.** Power analysis attacks on hardware: A smart card performs AES-128 encryption. The Hamming weight of the intermediate values (number of 1-bits) correlates with the card's instantaneous power consumption. Explain: (a) how an attacker with power traces can recover the key using correlation power analysis (CPA); (b) what hardware countermeasures (masking, dual-rail logic) resist this; (c) implement a Hamming-weight power model in Python and demonstrate the correlation between input data and simulated power.

**Problem 3.** Formally verify the correctness of a 1-bit full adder: (a) write the truth table; (b) derive the SOP expressions; (c) prove algebraically that the carry-out is the majority function (AB + BC + AC); (d) prove using structural induction on n that a chain of n full adders correctly computes the (n+1)-bit sum of two n-bit integers.

**Problem 4.** (Capstone Hardware Project) Design a complete 8-bit processor in Verilog with: 8-bit data path, 256-byte instruction memory, 256-byte data memory, 8 general-purpose registers, a 4-instruction ISA of your design (at minimum: LOAD, STORE, ADD, BEQ), a 3-stage pipeline (Fetch, Decode/Execute, Write-back), and data hazard detection via stalling. Write an assembler in Python. Demonstrate running: a counting loop, a Fibonacci computation to the 8th term, and a bubble sort on 8 values.

---

### Milestone Assessment — Module 2.1
*Pass threshold: 80%. Time: 3 hours. Paper and pencil. No simulator.*

1. Convert 0xC0DE to binary (16-bit) and to signed decimal (two's complement).
2. Minimize f(A,B,C,D) = Σm(1,3,5,7,9,11,13,15) + Σd(0,2) using a K-map. Draw the minimized gate diagram.
3. Design a full adder using only NOR gates. Show all derivation steps using De Morgan's laws.
4. Design an FSM that detects the sequence "110" (overlapping) in a serial input. Give the state diagram, state table, and minimized D flip-flop next-state equations.
5. A DRAM cell stores a bit as a charge on a 30fF capacitor. The leakage current is 1fA. How long before the charge drops below the refresh threshold (assume 50% threshold)? Why must refresh happen in milliseconds rather than minutes?

---

---

# MODULE 2.2 — Computer Architecture I: Processor Design

**Duration:** 10–12 weeks | **Hours/week:** 12 | **Total hours:** ~140

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Patterson & Hennessy — *Computer Organization and Design: The Hardware/Software Interface* (RISC-V Edition), 5th ed.

*Note: The RISC-V edition is preferred for its clean ISA. x86-64 details are covered via the Bryant & O'Hallaron supplementary.*

---

### Chapter 1 — Computer Abstractions and Technology

**Read:** Entire chapter.

**Section 1.1 — Introduction**
Focus on: the abstraction hierarchy (transistor → logic gate → circuit → microarchitecture → ISA → OS → application); why each layer hides complexity from the layer above; the "great idea" of abstraction.

**Section 1.2 — Eight Great Ideas in Computer Architecture**
Memorize and understand: Moore's Law, abstraction, make the common case fast, parallelism, pipelining, prediction, memory hierarchy, dependability via redundancy. These recur throughout the curriculum.

**Section 1.5 — Technologies for Building Processors and Memory**
Focus on: VLSI technology; transistor density trends; power consumption (dynamic and static); the "power wall" that ended frequency scaling — why modern processors scale through cores rather than clock speed.

**Section 1.6 — Performance**
Focus on: response time vs throughput; the CPU performance equation: CPU time = IC × CPI × Clock period. This equation is the fundamental tool for performance analysis. Understand: to improve performance, you reduce IC (better algorithms), CPI (better microarchitecture), or clock period (better technology/pipeline).

**Section 1.7 — The Power Wall**
Focus on: dynamic power = capacitance × voltage² × frequency; why reducing voltage is the primary technique for reducing power; the reliability limit that prevents unlimited voltage reduction.

---

### Chapter 2 — Instructions: Language of the Computer

**Read:** Entire chapter — the ISA chapter is the bridge between hardware and software.

**Section 2.1 — Introduction**
Focus on: the stored-program concept; the instruction set as the contract between hardware and software; why RISC (Reduced Instruction Set Computer) simplifies implementation while enabling high clock rates.

**Section 2.2 — Operations of the Computer Hardware**
Focus on: arithmetic instructions; the three-address format (destination, source1, source2); the regularity principle (why uniform 3-register format simplifies hardware).

**Section 2.3 — Operands of the Computer Hardware**
Focus on: the register file (32 registers in RISC-V); why registers are faster than memory; the register conventions (x0 always zero, x1 return address, x2 stack pointer, etc.); word, halfword, byte; memory alignment and its hardware implications.

**Section 2.4 — Signed and Unsigned Numbers**
Focus on: two's complement revisited; sign extension in load instructions (LB vs LBU); overflow in signed vs unsigned arithmetic. **Sign extension bugs are a common source of security vulnerabilities — connect to Module 3.1.**

**Section 2.5 — Representing Instructions in the Computer**
Focus on: the RISC-V R-type, I-type, S-type, B-type, U-type, J-type instruction formats; how opcode, funct3, funct7, and register fields are encoded; the instruction encoding as bit fields. You must be able to encode and decode any RISC-V instruction by hand.

**Section 2.6 — Logical Operations**
Focus on: AND, OR, XOR, shifts (SLL, SRL, SRA — the difference between logical and arithmetic right shift matters for sign preservation). SRA is the hardware equivalent of integer division by powers of 2.

**Section 2.7 — Instructions for Making Decisions**
Focus on: branch instructions (BEQ, BNE, BLT, BGE, BLTU, BGEU); the PC-relative branch target encoding; why RISC-V uses a signed offset rather than an absolute address.

**Section 2.8 — Supporting Procedures in Computer Hardware**
Focus on (extremely carefully): the procedure call convention; the stack frame layout; callee-saved vs caller-saved registers; the full call/return sequence (JAL stores return address in rd; JALR returns to address in rs1+offset). **The stack frame is the foundation of buffer overflow exploits — this section is foundational to Module 4.5.**

**Section 2.9 — Communicating with People**
Skim — ASCII and string operations.

**Section 2.10 — RISC-V Addressing for Wide Immediates and Addresses**
Focus on: LUI + ADDI for 32-bit constants; AUIPC for PC-relative addressing; JAL encoding (why the 20-bit offset is sufficient for most programs).

**Section 2.11 — Parallelism and Instructions: Synchronization**
Focus on: the load-reserved/store-conditional (LR/SC) pair as the hardware primitive for atomic operations; why you cannot implement a mutex with two separate loads and stores (the atomicity gap). **This connects to synchronization primitives in Module 3.3 and 3.4.**

**Section 2.12 — Translating and Starting a Program**
Focus on: compilation → assembly → object file → linking → loading; relocatable vs absolute addresses; the role of the linker in resolving symbols; the GOT and PLT (preview of Module 4.5's exploit techniques).

**Section 2.13 — A C Sort Example**
Read entirely. Trace through the translation of a C bubble sort to RISC-V assembly instruction by instruction. This is the most important applied example in the chapter.

---

### Chapter 3 — Arithmetic for Computers

**Read:** Sections 3.1–3.6.

**Section 3.1 — Introduction**
Skim.

**Section 3.2 — Addition and Subtraction**
Focus on: overflow detection for signed addition (overflow iff operands have same sign but result has different sign); carry-out vs overflow (they are different things for signed arithmetic). **Integer overflow exploitation requires understanding exactly when and how the processor sets the overflow flag.**

**Section 3.3 — Multiplication**
Focus on: the hardware multiply algorithm (shift-and-add); the MUL and MULH instructions; why 32×32 produces a 64-bit result; why this matters for overflow (multiplying two 32-bit values can overflow even if each is individually representable).

**Section 3.4 — Division**
Focus on: the hardware division algorithm; the DIV and REM instructions; signed vs unsigned division; division by zero and overflow (INT_MIN / -1 overflows in two's complement).

**Section 3.5 — Floating Point**
Focus on: IEEE 754 single precision: sign (1 bit), exponent (8 bits, biased by 127), significand (23 bits, implicit leading 1); special values (±0, ±∞, NaN); denormalized numbers. Understand: floating-point arithmetic is not associative, which affects security (timing channels based on floating-point branch behavior). Know how to convert between decimal and IEEE 754 by hand.

**Section 3.6 — Parallelism and Computer Arithmetic: Subword Parallelism**
Skim — SIMD preview.

---

### Chapter 4 — The Processor

**Read:** Entire chapter — the core of this module.

**Section 4.1 — Introduction**
Focus on: the implementation determines performance; the datapath and control as two separable concerns.

**Section 4.2 — Logic Design Conventions**
Focus on: combinational vs clocked state elements in the context of processor design; setup time, hold time, and the clock period constraint: t_{clk} ≥ t_{pcq} + t_{comb} + t_{setup}.

**Section 4.3 — Building a Datapath**
Focus on: the datapath elements for each instruction class: register file, ALU, data memory, instruction memory, PC; how the data flows through the datapath for each instruction type (R-type, load, store, branch, jump). Draw the complete single-cycle datapath from memory.

**Section 4.4 — A Simple Implementation Scheme**
Focus on: the control unit as a combinational circuit; the main control decoder; the ALU control; how the two-level control reduces implementation complexity.

**Section 4.5 — An Overview of Pipelining**
Focus on: the pipeline analogy; throughput vs latency; the ideal speedup = number of stages; why the pipelined CPI approaches 1. **Pipelining is the most important performance technique in processor design.**

**Section 4.6 — Pipelined Datapath and Control**
Focus on: the five stages IF/ID/EX/MEM/WB; the pipeline registers (IF/ID, ID/EX, EX/MEM, MEM/WB) and what values they hold; how control signals are generated and propagated through pipeline registers.

**Section 4.7 — Data Hazards: Forwarding versus Stalling**
Focus on (extremely carefully):
- **RAW (Read After Write) hazard:** the next instruction reads a register that the previous instruction is still computing.
- **Forwarding (bypassing):** route ALU result directly to ALU input without waiting for WB stage. Know the four forwarding conditions and their priority.
- **Load-use hazard:** cannot be resolved by forwarding alone (data isn't ready until end of MEM stage); requires a one-cycle stall (bubble insertion). The hazard detection unit identifies this case.
- **Performance impact:** one stall per load-use hazard reduces CPI from 1.0 to approximately 1.05–1.15 in real programs.

**Section 4.8 — Control Hazards**
Focus on:
- **Branch hazard:** branch outcome and target not known until end of EX stage; two instructions after the branch have been fetched by then.
- **Assume-not-taken prediction:** always fetch PC+4; flush incorrectly fetched instructions if branch taken.
- **Branch prediction:** 1-bit predictor, 2-bit saturating counter, local/global branch history; branch target buffer (BTB); the return address stack (RAS). Know how each improves prediction accuracy.
- **Speculative execution:** the processor executes past a branch before knowing the outcome — **this is the physical basis of Spectre.**

**Section 4.9 — Exceptions**
Focus on: precise vs imprecise exceptions; the exception handler; the role of the pipeline in making exceptions precise (the EPC and Cause registers); the difference between exceptions (synchronous, caused by instruction) and interrupts (asynchronous, caused by external events). **Exception handling is how system calls work, which is how user-to-kernel transitions happen — central to OS security.**

**Section 4.10 — Parallelism via Instructions**
Focus on: ILP (Instruction-Level Parallelism); the dependency graph of a program; true dependencies (RAW) limit ILP; multiple issue (superscalar); dynamic scheduling (out-of-order execution); register renaming. These concepts explain why modern out-of-order CPUs are vulnerable to Spectre-class attacks.

---

### Chapter 5 — Large and Fast: Exploiting Memory Hierarchy

**Read:** Entire chapter — foundational for cache timing attacks.

**Section 5.1 — Introduction**
Focus on: the principle of locality (temporal: recently used data will be used again; spatial: data near recently used data will be used); why the memory hierarchy works; the cost-performance triangle (registers → L1 → L2 → L3 → DRAM → SSD → disk).

**Section 5.2 — Memory Technologies**
Focus on: SRAM (fast, expensive, 6 transistors/bit); DRAM (slow, cheap, 1 transistor/bit); the latency numbers every programmer should know: L1 ~4 cycles, L2 ~12 cycles, L3 ~40 cycles, DRAM ~200 cycles. **These latency differences are the physical basis of cache timing side-channel attacks.**

**Section 5.3 — The Basics of Caches**
Focus on: direct-mapped cache (index, tag, valid bit); address decomposition into tag, index, and offset; hit vs miss; cold miss, capacity miss, conflict miss; the three Cs model.

**Section 5.4 — Measuring and Improving Cache Performance**
Focus on: AMAT (Average Memory Access Time) = hit time + miss rate × miss penalty; the miss rate vs cache size trade-off; ways to reduce miss rate (larger cache, higher associativity, larger blocks); the three types of misses.

**Section 5.5 — Dependable Memory Hierarchy**
Focus on: set-associative caches (N-way set associative); fully associative cache; replacement policies (LRU, random, FIFO); the trade-off between associativity and hit time.

**Section 5.6 — Virtual Machines**
Skim for this module — covered in Module 3.3.

**Section 5.7 — Using FSMs to Control Simple Caches**
Focus on: the cache controller FSM for a write-back, write-allocate cache. Know the states and transitions.

**Section 5.8 — Parallelism and Memory Hierarchy: Cache Coherence**
Focus on: the coherence problem in multiprocessors; the MESI protocol (Modified, Exclusive, Shared, Invalid); coherence transactions (read, write, invalidate). **Cache coherence is relevant to cache-coherence attacks (Prime+Probe, Flush+Reload).**

**Section 5.9 — Advanced Material**
Focus on: write-through vs write-back; write-allocate vs no-write-allocate; write buffers; multilevel caches. Know: modern CPUs use write-back, write-allocate L1/L2/L3 caches.

---

### Chapter 6 — Parallel Processors from Client to Cloud

**Read:** Sections 6.1–6.4 for context on multicore and GPU architectures.

---

### Supplementary: Bryant & O'Hallaron — *Computer Systems: A Programmer's Perspective*, 3rd ed.

**Read the following chapters in parallel with Patterson & Hennessy:**

**Chapter 1 — A Tour of Computer Systems**
Read entirely as orientation. It presents the same content as P&H from the programmer's perspective rather than the hardware designer's perspective.

**Chapter 2 — Representing and Manipulating Information**
Read entirely. Focus on: integer representations (unsigned, two's complement); arithmetic in C; signed vs unsigned conversions and the surprising results; truncation; bit manipulation tricks. **This chapter is required reading for Module 3.1 (C programming) and Module 4.5 (integer overflow exploitation).**

**Chapter 3 — Machine-Level Representation of Programs**
Read Sections 3.1–3.10 in full. This is the x86-64 architecture chapter and is foundational for Modules 3.2 and 4.4–4.5.
- §3.4: Data formats; the x86-64 register set; operand specifiers.
- §3.5: Arithmetic and logic operations.
- §3.6: Control flow — conditional codes, conditional moves.
- §3.7: Procedures — the stack frame, call/return, callee-saved registers, caller-saved registers. **The stack frame diagram in §3.7 is the single most important figure for understanding buffer overflows.**
- §3.8: Arrays and structures.
- §3.9: Heterogeneous data structures.
- §3.10: Combining control and data — vulnerable code patterns.

**Chapter 5 — Optimizing Program Performance**
Read §5.1–5.7. Focus on: understanding the processor's out-of-order execution model from the programmer's perspective; critical path analysis; loop unrolling; the throughput/latency distinction for functional units.

**Chapter 6 — The Memory Hierarchy**
Read entirely — this complements P&H Ch. 5 with programmer-focused perspective and explicit cache-friendly programming examples.

---

### Supplementary: Spectre and Meltdown Papers
After completing P&H Ch. 4–5:
- Read: Kocher et al., "Spectre Attacks: Exploiting Speculative Execution" (IEEE S&P 2019)
- Read: Lipp et al., "Meltdown: Reading Kernel Memory from User Space" (USENIX Security 2018)
Focus on: understanding the attack at the microarchitectural level (speculative execution + cache timing side-channel). You should now have all the prerequisite knowledge.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — ISA and Assembly Fundamentals
- **Day 1:** P&H Ch. 1. CPU performance equation — compute and compare 5 processor configurations.
- **Day 2:** P&H Ch. 2.1–2.5. Instruction formats. Encode 10 RISC-V instructions by hand from the ISA specification.
- **Day 3:** P&H Ch. 2.6–2.8. Assembly programming. Implement 5 functions in RISC-V assembly (abs, max, GCD, factorial, Fibonacci).
- **Day 4:** P&H Ch. 2.12–2.13. C sort example — trace each C statement to its RISC-V instructions.
- **Day 5:** B&O Ch. 2. Integer representations and C. Do all exercises.
- **Day 6:** Problem Set 2.2 Tier 1, problems 1–6.
- **Day 7:** Rest.

### Week 2 — Arithmetic and Floating Point
- **Day 1:** P&H Ch. 3.1–3.4. Overflow conditions. Multiply/divide corner cases.
- **Day 2:** P&H Ch. 3.5. IEEE 754. Convert 10 values to/from single-precision binary.
- **Day 3:** B&O Ch. 2 (continued) + B&O Ch. 3.1–3.5. x86-64 register set; data movement; arithmetic.
- **Day 4:** B&O Ch. 3.6–3.7. Conditionals and procedures. Trace C function calls through x86-64 assembly.
- **Day 5:** Problem Set 2.2 Tier 1, problems 7–14.
- **Day 6:** MIPS/RISC-V simulator — implement in Python: register file, memory model, fetch-decode-execute cycle.
- **Day 7:** Rest.

### Week 3 — Single-Cycle Datapath
- **Day 1:** P&H Ch. 4.1–4.3. Datapath elements. Draw the complete single-cycle datapath for R-type, Load, and Branch.
- **Day 2:** P&H Ch. 4.4. Control unit. Truth table for main control and ALU control. Build the control logic.
- **Day 3:** Implement the single-cycle RISC-V processor in Verilog. R-type instructions only first.
- **Day 4:** Extend to Load/Store, Branch, Jump instructions. Test with assembly programs.
- **Day 5:** Problem Set 2.2 Tier 1, problems 15–20.
- **Day 6:** Lab — run a simple Fibonacci program on your RISC-V simulator and your Verilog implementation; verify identical results.
- **Day 7:** Rest.

### Week 4 — Pipelined Datapath
- **Day 1:** P&H Ch. 4.5–4.6. Pipeline stages. Pipeline registers. Draw the complete 5-stage pipeline datapath.
- **Day 2:** P&H Ch. 4.7. Data hazards. Identify all RAW hazards in a 10-instruction sequence. Determine which are resolved by forwarding and which require a stall.
- **Day 3:** Forwarding unit implementation in Verilog. Hazard detection unit for load-use hazards.
- **Day 4:** P&H Ch. 4.8. Control hazards. Implement branch prediction (assume not taken). Measure misprediction penalty.
- **Day 5:** Problem Set 2.2 Tier 2, problems 1–5.
- **Day 6:** Pipelined processor Verilog project — add forwarding and hazard detection to single-cycle design.
- **Day 7:** Rest.

### Week 5 — Exceptions and Advanced Microarchitecture
- **Day 1:** P&H Ch. 4.9. Exceptions. Implement exception handling in your pipelined processor (at minimum: invalid instruction, memory alignment error).
- **Day 2:** P&H Ch. 4.10. Superscalar and out-of-order execution — conceptual only. Read the Tomasulo algorithm description.
- **Day 3:** Branch prediction deep-dive: 2-bit saturating counter. Implement a branch predictor simulation and measure accuracy on a real instruction trace.
- **Day 4:** Spectre paper (Kocher et al.). Understand the attack: speculative execution → cache state change → timing side-channel.
- **Day 5:** Problem Set 2.2 Tier 2, problems 6–10.
- **Day 6:** Meltdown paper (Lipp et al.). Understand how kernel memory is read from user space.
- **Day 7:** Rest.

### Weeks 6–8 — Memory Hierarchy: Caches
- **Week 6:** P&H Ch. 5.1–5.5. Direct-mapped and set-associative caches. AMAT calculations. Implement a cache simulator.
- **Week 7:** P&H Ch. 5.8–5.9. Cache coherence (MESI). Write-back policies. B&O Ch. 6 (programmer's view).
- **Week 8:** Cache timing side-channel lab — implement FLUSH+RELOAD in C. Measure L1/L2/DRAM latency on your machine using RDTSC. Demonstrate the measurable latency difference that enables side-channel attacks.

### Weeks 9–10 — Module Capstone: Complete Processor
- **Week 9:** Complete the pipelined RISC-V processor in Verilog with: full forwarding, hazard detection, branch prediction (2-bit counter), exception handling, and a memory hierarchy simulator.
- **Week 10:** Write the Python assembler for your ISA. Run 5 complete programs. Write performance analysis: CPI measurements, branch prediction accuracy, cache miss rates.

### Weeks 11–12 — Review and Milestone
- B&O Ch. 3 complete (x86-64 assembly) — this is required before Module 3.2.
- Problem Set 2.2 Tier 3.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Using the CPU performance equation, compare two processors:
- Processor A: 3 GHz clock, CPI = 1.5 for a benchmark with 10⁹ instructions.
- Processor B: 2 GHz clock, CPI = 1.0 for the same benchmark.
Which is faster? By what factor?

**Problem 2.** Encode the following RISC-V instructions as 32-bit binary, then convert to hex. Show all fields (opcode, funct3, funct7, rs1, rs2, rd, immediate):
(a) `add x5, x6, x7`
(b) `addi x5, x6, -10`
(c) `lw x5, 8(x6)`
(d) `beq x5, x6, 16` (PC-relative offset in bytes)
(e) `jal x1, -40`

**Problem 3.** Trace the execution of the following RISC-V assembly through a pipelined processor (5 stages). Mark all RAW hazards, indicate which are resolved by forwarding, and which require a stall. Draw the pipeline diagram (cycle-by-cycle).
```
lw   x1, 0(x2)
add  x3, x1, x4
sub  x5, x3, x6
and  x7, x5, x8
```

**Problem 4.** Convert the following to IEEE 754 single precision (32-bit). Show sign, biased exponent, and significand fields in binary and hex:
(a) +0.625
(b) −37.0
(c) +∞
(d) What decimal value does 0xC0A00000 represent?

**Problem 5.** A direct-mapped cache has 16 cache lines, each holding 4 words (16 bytes). Physical addresses are 16 bits. For each address below, determine the byte offset, index, and tag. Then, given the access sequence [0x0004, 0x0024, 0x0044, 0x0004, 0x0024], determine hit or miss for each access:
Addresses: 0x0004, 0x0024, 0x0044, 0x0004, 0x0024.

**Problem 6.** Explain with a concrete example why a RAW data hazard cannot be resolved by forwarding when the hazardous instruction is a load followed immediately by a dependent instruction. Draw the pipeline diagram showing why the data isn't available in time.

**Problem 7.** The following C code is vulnerable to an integer overflow. Identify the vulnerability, explain at what value of `n` it triggers, and describe the attacker's exploitation scenario:
```c
void *allocate_buffer(size_t n) {
    size_t size = n * sizeof(uint32_t);  // potential overflow
    return malloc(size);
}
```
Connect your analysis to the CPU performance equation: how does the hardware perform multiplication, and what happens to the high bits of the result in a 64-bit processor?

**Problem 8.** A branch predictor uses a 2-bit saturating counter (states: Strongly Not Taken, Weakly Not Taken, Weakly Taken, Strongly Taken). Starting from Strongly Not Taken, trace the state transitions and predictions for the branch outcome sequence: T T N T T T N N T. Compute the prediction accuracy.

**Problem 9.** The AMAT of a memory system is: AMAT = L1 hit time + L1 miss rate × (L2 hit time + L2 miss rate × memory access time). Given: L1 hit time = 2 cycles, L1 miss rate = 5%, L2 hit time = 10 cycles, L2 miss rate = 20%, memory access time = 100 cycles. Compute AMAT. What L1 miss rate would be needed to reduce AMAT to 3 cycles (keeping all other parameters fixed)?

**Problem 10.** Explain the x86-64 System V AMD64 calling convention precisely:
(a) Which registers pass the first 6 integer arguments?
(b) Which registers are callee-saved vs caller-saved?
(c) What is the "red zone" and why does it exist?
(d) Draw the stack frame layout for a function `int foo(int a, int b, int c)` that allocates 16 bytes of local variables and calls another function.

**Problem 11.** Design a hazard detection unit for a 5-stage pipeline. Write the Boolean logic (Verilog-style) for detecting a load-use hazard and generating a stall signal (PC write disable, IF/ID register write disable, insert a NOP in ID/EX).

**Problem 12.** Explain the Spectre attack at the microarchitectural level. Your explanation must reference: speculative execution, the branch predictor, the cache as a covert channel, and the RDTSC instruction. Which CPU design feature enables the attack? Why does flushing the branch predictor not fully mitigate it?

---

### Tier 2 — Intermediate

**Problem 1.** Implement a complete 5-stage RISC-V pipeline simulator in Python. It must handle: all R-type instructions, LW/SW, BEQ/BNE, JAL. Include: forwarding unit, hazard detection (load-use stall), assume-not-taken branch prediction. Run a bubble sort program and report: total cycles, CPI, number of stalls, number of branch mispredictions.

**Problem 2.** Design a direct-mapped cache simulator in Python. Parameters: cache size (bytes), block size (bytes), address width (bits). Simulate an access trace and report: total accesses, hit count, miss count, miss rate, AMAT (given hit and miss penalties). Test with: (a) matrix multiplication row-major, (b) column-major. Explain the difference.

**Problem 3.** Given the RISC-V instruction `add x3, x1, x2`, trace all 5 pipeline stages cycle by cycle. For each cycle, state: the instruction in each stage, the values in each pipeline register, and the forwarding paths (if any) that are active.

**Problem 4.** Explain why out-of-order execution creates the Spectre vulnerability. What is the precise sequence of events from: (a) processor fetches a branch instruction, (b) speculative execution occurs, (c) branch is resolved as not-taken, (d) register state is rolled back, (e) cache state is NOT rolled back — to attacker reading the cache state via timing.

**Problem 5.** Implement a cache timing side-channel demo in C: using `rdtsc` (or `clock_gettime`), measure the access time for an array element that is (a) in L1 cache and (b) not in cache (use `clflush` to evict). Demonstrate a consistent, measurable timing difference. Discuss the implications for Flush+Reload attacks.

---

### Tier 3 — Advanced

**Problem 1.** Implement a Tomasulo algorithm simulator for a 2-issue out-of-order processor. Support: ADD (3-cycle latency), MUL (5-cycle latency), LOAD (4-cycle latency). Simulate the issue, execution, and commit of 8 instructions with RAW and WAW dependencies. Show the reservation station state and register status at each cycle.

**Problem 2.** Implement a FLUSH+RELOAD cache covert channel in C between two processes sharing a page (via shared memory). Channel: sender flushes or accesses a cache line; receiver measures access time. Achieve at least 100 bits/second of covert bandwidth. Discuss KASLR bypass implications.

**Problem 3.** (Capstone) Implement a complete pipelined RISC-V processor in Verilog with: 5-stage pipeline, forwarding, load-use hazard stall, 2-bit branch predictor with BTB (16-entry Branch Target Buffer), exception handling for illegal instruction and misaligned memory. Write a Python assembler. Demonstrate with 5 programs including one with loops and one with function calls. Measure and report CPI, branch prediction accuracy, and instruction-class breakdown.

---

---

# MODULE 2.3 — Computer Architecture II: Memory Systems & I/O

**Duration:** 6–8 weeks | **Hours/week:** 10–12 | **Total hours:** ~85

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Patterson & Hennessy — *Computer Organization and Design*, Ch. 5 (continued) + Appendices

### Supplementary: Jacob, Ng & Wang — *Memory Systems: Cache, DRAM, Disk* (Morgan Kaufmann)

---

**P&H Chapter 5 (Advanced Cache Topics) — Complete**

Revisit §5.3–5.9 with focus on:
- **Virtual memory integration with caches:** virtually indexed physically tagged (VIPT) caches; why VIPT is the standard for L1 caches; aliasing in virtually indexed caches.
- **TLB (Translation Lookaside Buffer):** a small, fully associative cache for page table entries; TLB hit path vs miss path; hardware vs software TLB miss handling; TLB shootdown in multiprocessor systems.
- **Large page support:** 4KB vs 2MB vs 1GB pages; why huge pages reduce TLB pressure; transparent huge pages in Linux.

---

**Jacob et al. — Memory Systems**

**Chapter 2 — DRAM: The Main Memory Substrate**
Focus on:
- DRAM array organization: banks, rows, columns; the row buffer as a cache row.
- The DRAM access protocol: activate (open row) → read/write (access column) → precharge (close row).
- tRAS, tRCD, tCL, tRP timing parameters and their physical meaning.
- SDRAM and DDR SDRAM: how double-data-rate works (data transferred on both clock edges); DDR4/DDR5 specifications.
- **Rowhammer:** repeated activation of the same row (before auto-refresh) induces charge leakage in adjacent rows. The physics: capacitive coupling between adjacent row transistors. The attack: by rapidly reading two rows alternately (hammer them), bits flip in the row between them. **This is the physical mechanism behind the Rowhammer privilege escalation exploits in Module 4.5.**

**Chapter 3 — The Memory Controller**
Focus on:
- The memory controller's role in translating CPU memory requests to DRAM commands.
- Command scheduling: FR-FCFS (First Ready, First Come First Serve); how the scheduler affects timing fairness.
- Refresh scheduling: tREFI and tRFC timing.
- ECC (Error-Correcting Code) memory: SECDED codes; how the memory controller detects and corrects single-bit errors.

**Chapter 4 — Storage Interfaces**
Focus on (selectively):
- ATA/SATA interface basics.
- NVMe over PCIe: the queue model; multiple queues and their security implications (queue exhaustion attacks).
- Storage latency hierarchy and its effect on OS design.

---

**Intel® 64 and IA-32 Architectures Software Developer's Manual — Volume 3A (System Programming Guide)**

**Chapter 2 — System Architecture Overview**
Read §2.1–2.3. Focus on: privilege levels (rings 0–3); the segmentation model (mostly legacy in 64-bit mode, but segment descriptors still relevant for security — the GDT/LDT).

**Chapter 3 — Protected-Mode Memory Management**
Read §3.1–3.4. Focus on: the x86-64 4-level paging structure (PML4 → PDPT → PD → PT → physical page); the page table entry fields (present, R/W, U/S, NX/XD, physical page number); how a virtual address is split into four 9-bit indices and a 12-bit offset; the role of CR3 (page table base register). **Understanding x86-64 paging is essential for kernel exploitation, sandbox escapes, and KASLR bypasses in Module 4.5.**

**Chapter 4 — Paging**
Read §4.1–4.6. Focus on: page-level protection (read/write/execute per page — the NX bit); supervisor vs user mode pages; the WP (write protect) bit in CR0; SMEP (Supervisor Mode Execution Prevention) and SMAP (Supervisor Mode Access Prevention) — the hardware mechanism that makes ret2usr attacks harder.

**Chapter 11 — Memory Cache Control**
Read §11.1–11.5. Focus on: the cache hierarchy control bits (WB, WT, UC, WC) in page table entries; the CLFLUSH instruction; MTRR (Memory Type Range Registers); WBINVD. These are used in firmware attacks and cache-side-channel exploits.

---

### Supplementary: Rowhammer Research Papers

Read the following in order:
1. Kim et al., "Flipping Bits in Memory Without Accessing Them: An Experimental Study of DRAM Disturbance Errors" (ISCA 2014) — the original paper.
2. Seaborn & Dullien, "Exploiting the DRAM Rowhammer Bug to Gain Kernel Privileges" (Google Project Zero, 2015) — the first exploit.
3. van der Veen et al., "Drammer: Deterministic Rowhammer Attacks on Mobile Platforms" (CCS 2016) — ARM exploitation.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Virtual Memory Deep Dive
- Intel SDM Vol. 3A Ch. 2–3. Draw the x86-64 4-level page table walk for an address. Calculate the physical address from a virtual address given page table entries.
- TLB simulation — implement a TLB with LRU replacement. Measure hit rate on a real program's memory access trace.

### Week 2 — DRAM Architecture
- Jacob et al. Ch. 2. DRAM timing parameters. Calculate the latency of an activate-read-precharge cycle given real DDR4 parameters.
- DRAM refresh: calculate the minimum refresh rate to prevent charge loss given tRET (retention time).

### Week 3 — Rowhammer
- Read all three Rowhammer papers.
- Implement a Rowhammer hammer loop in C (on your own hardware — not a production system). Measure the access time for two rows using RDTSC. Verify you are hitting DRAM and not cache (use CLFLUSH).
- Lab: If on vulnerable hardware, attempt to induce a bit flip (expected to take minutes to hours). If not available, use the rowhammer-test tool.

### Week 4 — Memory Controller and I/O
- Jacob et al. Ch. 3. Memory controller scheduling.
- Intel SDM Vol. 3A Ch. 11. Cache control bits. Understand the implications of UC (uncacheable) mappings for device memory.
- NVMe architecture — queue model, multiple queues, interrupt affinity.

### Week 5 — System Integration: TLB, Paging, and Protection
- Intel SDM Vol. 3A Ch. 4. SMEP/SMAP. Understand how each is enabled and what each prevents.
- Implement a virtual-to-physical address translator in Python: given a page table (modeled as a dictionary), translate a virtual address through 4 levels.
- Problem Set 2.3 Tier 1 and Tier 2.

### Weeks 6–7 — Performance Lab and Milestone
- `perf` and `valgrind --tool=cachegrind` profiling lab: profile 3 programs; identify cache bottlenecks; optimize.
- Rowhammer mitigation lab: implement Target Row Refresh (TRR) simulation.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** A system uses 48-bit virtual addresses and 4KB pages with 4-level paging (9+9+9+9+12 bit split). For virtual address 0x0000_7FFF_FFC0_1234:
(a) Extract the PML4, PDPT, PD, PT indices, and page offset.
(b) If PML4[index] = 0x0000_0000_0020_0067 (present, R/W, User), what is the physical address of the PDPT?
(c) What do the lower 12 bits (flags) of a page table entry represent? List at least 6 flags and their meaning.

**Problem 2.** Explain why SMEP prevents ret2usr attacks. What does SMEP check, when is it checked, and how does it prevent a kernel exploit from jumping to user-space shellcode? How does SMAP complement SMEP?

**Problem 3.** A DRAM module has these timing parameters: tRCD = 14ns, tCL = 14ns, tRP = 14ns. The memory bus runs at 3200 MT/s (DDR4-3200). Calculate:
(a) The latency for a read to a closed row (worst case).
(b) The latency for a read to an open row (best case).
(c) How many CPU cycles (at 3.2 GHz) elapse during a worst-case DRAM read?

**Problem 4.** Explain the Rowhammer attack mechanism at the physical level. Your answer must include: the physics of charge leakage, the role of the refresh cycle, how the hammer loop bypasses the refresh, and why ECC memory mitigates but does not fully prevent Rowhammer.

**Problem 5.** A TLB has 64 entries, 4-way set associative, with LRU replacement. A program accesses memory in a pattern that cycles through 65 unique pages. Compute the TLB hit rate for this access pattern. What change to the access pattern would increase the TLB hit rate to 100%?

---

### Tier 2 — Intermediate

**Problem 1.** Implement a multi-level page table walker in Python. Support: 2-level paging (10+10+12 for 32-bit), 4-level paging (9+9+9+9+12 for 64-bit). Given a dictionary representing physical memory (address → value), implement `translate(virtual_addr, cr3)` that walks the page table and returns the physical address, raising a page fault if any entry is not present.

**Problem 2.** The NX (No-eXecute) bit in page table entries prevents execution of data pages. Describe how the following attacks are defeated by NX, and how each circumvents it:
(a) Classic stack buffer overflow with shellcode on the stack — defeated by NX; circumvented by ROP.
(b) Heap spray with shellcode — defeated by NX on heap; circumvented by JIT spraying.
(c) Why can't NX prevent all code execution attacks?

**Problem 3.** Profile the following two matrix multiplication implementations using `perf stat` and `valgrind --tool=cachegrind`. Explain the cache performance difference in terms of spatial locality and the cache line size (64 bytes on modern x86-64):
```c
// Version A: row-major access
for (i = 0; i < N; i++)
    for (j = 0; j < N; j++)
        for (k = 0; k < N; k++)
            C[i][j] += A[i][k] * B[k][j];  // B accessed column-major

// Version B: tiled/blocked access
// (implement a cache-oblivious or cache-aware blocked version)
```

---

---

# MODULE 2.4 — Embedded Systems & Microcontrollers

**Duration:** 6–8 weeks | **Hours/week:** 10 | **Total hours:** ~70

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Yiu — *The Definitive Guide to ARM Cortex-M3 and Cortex-M4 Processors*, 3rd ed.

---

**Chapter 1 — Introduction to the Cortex-M Processors**
Focus on: the Cortex-M family (M0, M0+, M3, M4, M7, M33); the Thumb-2 instruction set as a blend of 16-bit and 32-bit instructions; the architectural registers (R0–R12 general purpose, R13=SP, R14=LR, R15=PC, xPSR).

**Chapter 2 — Overview**
Focus on: the Harvard vs von Neumann architecture distinction; memory-mapped peripherals (everything is in the address space); the bus matrix; the NVIC (Nested Vectored Interrupt Controller).

**Chapter 3 — The Cortex-M3/M4 Instruction Sets**
Read §3.1–3.8. Focus on: data processing instructions (add, subtract, logical, shift); memory access instructions (LDR, STR with various addressing modes); branch instructions; the `BL` and `BX` for function calls and returns (connect to stack frame from Module 2.2).

**Chapter 4 — Cortex-M3/M4 Architecture**
Focus on: the exception model (16 system exceptions + up to 240 external interrupts); the vector table at address 0x00000000 (or relocated via VTOR); exception priority levels; the PSP (Process Stack Pointer) vs MSP (Main Stack Pointer) for OS/RTOS support.

**Chapter 8 — Using Embedded Operating Systems**
Focus on: the Cortex-M hardware support for RTOS: PSP for task stacks, MSP for kernel stack; PendSV for context switching; SysTick for periodic interrupt; privilege levels (Thread/Handler mode × Privileged/Unprivileged).

**Chapter 13 — Fault Exceptions and Fault Handling**
Focus on: HardFault, UsageFault, BusFault, MemManage fault — what causes each; the fault status registers; using fault handlers to catch and diagnose embedded software bugs. **This is the embedded system equivalent of segmentation faults — understanding fault handlers is prerequisite to embedded exploitation.**

**Chapter 18 — Custom Instructions and DSP Features (Cortex-M4)**
Skim — understand the SIMD/DSP instructions conceptually; the FPU (Floating-Point Unit) registers.

---

### Supplementary: Barr & Massa — *Programming Embedded Systems in C and C++*, 2nd ed. (O'Reilly)

**Chapter 1 — Introduction**
Read for context on real-time constraints and the embedded development environment.

**Chapter 2 — Your First Embedded Program**
Focus on: the toolchain (arm-none-eabi-gcc, objcopy, objdump); the linker script; the startup code (`Reset_Handler`, initializing .data and .bss sections, calling main). **Understanding the linker script and startup code is required for firmware analysis in Module 4.6.**

**Chapter 3 — Compiling, Linking, and Locating**
Focus on: memory sections (.text, .data, .bss, .rodata, .stack, .heap); the linker script defining each section's address; how the startup code copies .data from Flash to RAM. Draw the memory map of a typical embedded application.

**Chapter 4 — Downloading and Debugging**
Focus on: JTAG/SWD debugging interface; OpenOCD + GDB workflow; hardware breakpoints (limited number on Cortex-M); memory read/write via JTAG. **JTAG is how firmware is extracted for reverse engineering in Module 4.4.**

**Chapter 6 — Memory**
Focus on: Flash programming; write latency; execute-in-place vs copy-and-execute; the MPU (Memory Protection Unit) — the embedded equivalent of a MMU; using the MPU to enforce read/write/execute permissions per memory region (the embedded equivalent of NX).

**Chapter 8 — Operating Systems**
Focus on: the RTOS task model; preemptive scheduling; inter-task communication (queues, semaphores, mutexes); priority inversion; the Mars Pathfinder incident as a case study.

---

### Supplementary: FreeRTOS Reference Manual (freertos.org)

Read: Task management (vTaskCreate, vTaskDelete, vTaskSuspend, vTaskResume), queue management (xQueueCreate, xQueueSend, xQueueReceive), semaphore management, and the scheduler internals section.

---

### Supplementary: ARM Architecture Reference Manual (ARMv7-M)

**Read selectively:**
- B1: System Level Architecture — registers, exception model.
- B3: Memory Model — memory types (Normal, Device, Strongly-Ordered); memory ordering.
- A7: The Thumb-2 instruction set reference — for any instruction you need to understand precisely.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — ARM Cortex-M Architecture
- Yiu Ch. 1–3. Register file, instruction set, addressing modes.
- Set up: STM32 (Discovery or Nucleo board), arm-none-eabi-gcc toolchain, OpenOCD, GDB.
- Write: "Hello World" via UART (polling, no HAL).
- Blink an LED using register-level GPIO manipulation (no HAL).

### Week 2 — Interrupts and NVIC
- Yiu Ch. 4, 8. Exception model. Vector table. SysTick.
- Write: SysTick-based millisecond timer. Button interrupt (EXTI) with debouncing.
- Analyze: the startup code and linker script for your BSP.

### Week 3 — FreeRTOS
- FreeRTOS Reference Manual (tasks, queues, semaphores).
- Implement: 3-task FreeRTOS application — producer, consumer, and monitor — communicating via a queue with mutex-protected shared state.
- Understand: how the context switch works at the hardware level (PendSV + PSP).

### Week 4 — Secure Bootloader
- Barr & Massa Ch. 2–3, 6.
- Design: a bootloader that: (1) resides in the first 32KB of Flash; (2) verifies the application firmware's SHA-256 hash against a stored value; (3) jumps to application only if valid; (4) has an update mechanism that writes new firmware to Flash and updates the stored hash.
- Implement in C for your target board.

### Week 5 — JTAG and Firmware Analysis
- Barr & Massa Ch. 4.
- Lab: Use OpenOCD + GDB to: (a) halt execution at an arbitrary address; (b) read and dump the entire Flash contents to a file; (c) disassemble the startup code; (d) set a hardware breakpoint and inspect registers at the breakpoint.

### Weeks 6–7 — Projects and Milestone
- Digital oscilloscope project.
- RTOS sensor logger project.
- Problem Set 2.4 + milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** A Cortex-M4 has the vector table at address 0x08000000 (remapped Flash). What is at address 0x08000000? What is at 0x08000004? What is at 0x08000008? Explain how the processor uses these values on reset.

**Problem 2.** The MPU on a Cortex-M4 has 8 regions. Design an MPU configuration for a FreeRTOS application with: kernel code (read-only, executable), task stacks (read-write, non-executable), peripheral registers (device type, non-executable), and shared data (read-write, non-executable). Specify the base address, size, permissions, and attributes for each region.

**Problem 3.** Explain priority inversion. A classic example: low-priority task L holds a mutex; high-priority task H tries to acquire the mutex; medium-priority task M preempts L, preventing L from releasing the mutex. H is blocked indefinitely. Describe two OS mechanisms that solve priority inversion.

**Problem 4.** Write the linker script sections for a Cortex-M4 application with Flash at 0x08000000 (256KB) and SRAM at 0x20000000 (64KB). Define: .text, .rodata, .data (load address in Flash, VMA in SRAM), .bss, .stack. Include the vector table at the start of .text.

**Problem 5.** Explain how an attacker with JTAG access to an embedded device can: (a) extract all Flash contents; (b) read the value of a hardware security key stored in OTP (One-Time Programmable) memory; (c) bypass a firmware signature check by patching the branch instruction in Flash. What countermeasures prevent each?

---

### Tier 2 — Intermediate

**Problem 1.** Implement a power analysis simulation: model an AES-128 SubBytes operation in software on Cortex-M4. Simulate power consumption as the Hamming weight of the output byte XOR'd with the previous value. Show that for 1000 random plaintexts, the correlation between simulated power and the hypothesis `HW(SubBytes(plaintext_byte XOR key_byte_guess))` peaks at the correct key byte.

**Problem 2.** Implement a fault injection simulation: write a C program that performs a firmware signature check using a loop that verifies each byte. Introduce a deliberate race condition where the check result is stored in a variable that can be modified after the check but before the branch. Explain how a real glitching attack (voltage or clock glitch) would exploit this — and how to redesign the check to resist it.

---

---

# MODULE 2.5 — Compilers & Language Implementation

**Duration:** 12–14 weeks | **Hours/week:** 12–15 | **Total hours:** ~175

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Aho, Lam, Sethi & Ullman — *Compilers: Principles, Techniques, and Tools*, 2nd ed. (Dragon Book)

---

**Chapter 1 — Introduction to Compiling**
Read entirely. Focus on: the compiler phases (lexical analysis → syntax analysis → semantic analysis → IR generation → optimization → code generation); the symbol table as a cross-phase data structure; the difference between a compiler, interpreter, and JIT (just-in-time compiler).

**Chapter 2 — A Simple Syntax-Directed Translator**
Read §2.1–2.6. This chapter walks through building a simple expression translator end-to-end. Read it before studying the individual phases — it gives you the big picture before the details.

**Chapter 3 — Lexical Analysis**
Read §3.1–3.7.
- §3.1: The role of the lexer; token, lexeme, pattern.
- §3.3: Regular expressions for token specification.
- §3.4–3.6: From regex to NFA (Thompson's construction) to DFA (subset construction) to minimized DFA — this directly applies Module 1.5 theory to practice.
- §3.7: Lex/Flex specification language. Write a complete lexer for a C-like language using Flex.

**Chapter 4 — Syntax Analysis**
Read §4.1–4.9 — the longest chapter and the heart of the book.
- §4.1: Context-free grammars for programming languages (connect to Module 1.5).
- §4.2: Writing grammars — eliminating ambiguity, left recursion elimination, left factoring.
- §4.3: Top-down parsing: recursive descent (most readable and practical); LL(1) grammars; FIRST and FOLLOW sets.
- §4.4–4.5: Bottom-up parsing: shift-reduce; handle identification.
- §4.6: Introduction to LR parsing: LR(0), SLR(1), LALR(1), LR(1). Focus on: the items as states, the action and goto tables, the parsing algorithm.
- §4.7: More powerful LR parsers. Understand LALR(1) specifically — it's what Yacc/Bison generates.
- §4.8: Using Yacc/Bison — write a complete parser for a C-like expression language.
- §4.9: Ambiguity and error recovery.

**Chapter 5 — Syntax-Directed Translation**
Read §5.1–5.4.
- §5.1: Syntax-directed definitions (SDDs): attributes, semantic rules.
- §5.2: Evaluation orders: S-attributed definitions (all synthesized attributes — bottom-up evaluation); L-attributed definitions (synthesized + some inherited — top-down evaluation).
- §5.4: Syntax-directed translation schemes: embedding semantic actions into grammar productions. This is how you compute types, generate code, and build ASTs during parsing.

**Chapter 6 — Intermediate Code Generation**
Read §6.1–6.7.
- §6.1: Variants of syntax trees: abstract syntax trees (ASTs) vs concrete parse trees; DAGs for common subexpression elimination.
- §6.2: Three-address code (TAC): the standard IR form; quadruples and triples representation.
- §6.3: Types and declarations: symbol table structure, type equivalence.
- §6.4: Translation of expressions to TAC.
- §6.5: Type checking: structural vs name equivalence; coercions.
- §6.6: Control flow: boolean expressions and their short-circuit evaluation; translation of if/while/for to TAC with labels and gotos.
- §6.7: Backpatching: defer filling in jump targets until the target is known.

**Chapter 7 — Run-Time Environments**
Read §7.1–7.4 — directly relevant to security.
- §7.1: Storage organization: the static area (global variables, constants), the stack (activation records), the heap (dynamic allocation).
- §7.2: Stack allocation of space: the activation record (also called stack frame); static link and dynamic link for nested procedures; the access link.
- §7.3: Access to nonlocal data on the stack: the display; the static chain.
- §7.4: Heap management: manual allocation/deallocation; automatic garbage collection (mark-and-sweep, reference counting, copying). **The activation record layout in §7.2 is the hardware-level explanation of what you'll see in Assembly (Module 3.2) and exploit (Module 4.5).**

**Chapter 8 — Code Generation**
Read §8.1–8.4, §8.6.
- §8.1: Issues in code generation: instruction selection, register allocation, instruction ordering.
- §8.2: The target machine: a simple RISC model; addressing modes for code generation.
- §8.3: Addresses in the target code: names, computed addresses, run-time addresses.
- §8.4: Basic blocks and flow graphs: identifying basic blocks; the control flow graph (CFG) as the unit of analysis for optimization.
- §8.6: Peephole optimization: replacing instruction sequences with equivalent, shorter sequences. Understanding peephole optimization explains many of the optimization patterns you'll see when reverse engineering compiled code.

**Chapter 9 — Machine-Independent Optimizations**
Read §9.1–9.6.
- §9.1: The principal sources of optimization: local (within a basic block), intraprocedural (within a function), interprocedural (across functions).
- §9.2: Introduction to data-flow analysis: reaching definitions, live variable analysis, available expressions. The gen/kill framework.
- §9.3: Foundations of data-flow analysis: the meet operator; monotone data-flow frameworks; convergence.
- §9.4: Constant propagation: replacing variable references with constant values.
- §9.5: Dead code elimination: removing computations whose results are never used.
- §9.6: Loop optimizations: induction variable analysis, strength reduction, loop invariant code motion. **Understanding loop optimizations explains why reverse engineering optimized code is harder than `-O0` code.**

**Chapter 10 — Instruction-Level Parallelism**
Read §10.1–10.2. Focus on: the concepts of instruction scheduling and its interaction with the pipelined processor from Module 2.2; the dependency graph as the constraint on instruction reordering.

**Chapter 12 — Interprocedural Analysis**
Read §12.1–12.2. Focus on: call graphs; context-sensitivity; points-to analysis. These are the foundations of static analysis tools used in security (Module 4.10).

---

### Supplementary: Cooper & Torczon — *Engineering a Compiler*, 3rd ed.

Use for alternative explanations of:
- **Ch. 8 (Code Shape):** Code generation patterns for arrays, structs, function calls — extremely useful for reverse engineering.
- **Ch. 9 (Register Allocation):** Graph-coloring register allocation — the algorithm used by GCC and LLVM.
- **Ch. 10 (Scalar Optimizations):** Alternative treatment of data-flow analysis.

---

### Supplementary: LLVM Language Reference Manual (llvm.org)

Read: Introduction, Type System, Instruction Reference (at least: arithmetic, memory access, terminator instructions). LLVM IR is the intermediate representation used by Clang, Rust, Swift, and many security tools (including KLEE, angr, and many fuzzers).

---

### Supplementary: Stanford CS143 Compilers
Watch: Lectures 1–10 (Alex Aiken). These are clearer than the Dragon Book on parsing.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Overview and Lexical Analysis
- Dragon Book Ch. 1–2. End-to-end overview. Build a simple expression compiler mentally.
- Dragon Book Ch. 3. Regex → NFA → DFA → minimized DFA by hand for 2 examples.
- Implement a lexer for a C-like language using Python (without Flex first), then port to Flex.

### Week 2 — Parsing I: LL and Recursive Descent
- Dragon Book §4.1–4.3. Grammar transformations. FIRST and FOLLOW sets for 3 grammars.
- Implement a recursive-descent parser for arithmetic expressions with precedence.
- Extend to: variables, assignment, if-else, while loops.

### Week 3 — Parsing II: LR Parsing
- Dragon Book §4.4–4.8. LR(0) items, SLR(1) tables for a small grammar by hand.
- Write a LALR(1) grammar for your toy language and generate a parser using Bison.
- Test the parser on 20 programs; verify correct rejection of invalid programs.

### Week 4 — Semantic Analysis and Type Checking
- Dragon Book Ch. 5–6 (§6.1–6.3). Build an AST from your parser. Symbol table with scoping (hash table + scope stack).
- Implement type checking for: integers, booleans, arrays, and function calls.

### Week 5 — Intermediate Representation
- Dragon Book §6.4–6.7. Generate three-address code from your AST.
- Implement short-circuit evaluation for boolean expressions.
- Implement backpatching for if/while jump targets.

### Week 6 — Runtime Environments
- Dragon Book Ch. 7. Activation record layout. Implement runtime stack simulation.
- Lab: Compile a C function with GCC at -O0 and -O2. Compare the generated stack frames and activation records using GDB. Connect to the Dragon Book diagrams.

### Week 7 — Code Generation
- Dragon Book Ch. 8. Implement a code generator targeting x86-64 assembly (subset).
- At minimum: generate code for: arithmetic expressions, variable reads/writes, if/else, while, function call/return using the System V AMD64 ABI.

### Week 8 — Optimizations
- Dragon Book §9.1–9.5. Implement on your IR: constant folding, dead code elimination, common subexpression elimination.
- Lab: Compile a program with GCC -O0 vs -O2. Use objdump to identify which optimizations the compiler applied. Match each transformation to a named optimization.

### Weeks 9–10 — LLVM IR and Clang
- LLVM Language Reference. Write 5 programs directly in LLVM IR (using `llvm-as` to assemble).
- Clang: compile C to LLVM IR (`clang -S -emit-llvm`). Read and annotate the IR output for 5 functions.
- Write an LLVM pass (opt plugin) that counts the number of each instruction type in a function.

### Weeks 11–12 — Security-Relevant Compiler Topics
- Stack canaries: trace through the GCC-generated prologue/epilogue code that inserts and checks the canary. Understand the value stored and the check mechanism.
- PIE: understand how position-independent code is generated; how the GOT and PLT work; how ASLR interacts with PIE.
- CFI (Control Flow Integrity): read the CFI paper (Abadi et al.); understand how Clang's CFI implementation works.
- UBSan and ASan: what undefined behaviors do they detect; how do they instrument code.

### Weeks 13–14 — Capstone Compiler and Milestone
- **Capstone:** Complete compiler for your toy language producing x86-64 assembly. Must include: lexer, parser, type checker, IR generator, optimizer (3 passes), and code generator. Compile and run 50 test programs.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Construct the NFA for the regular expression `(a|b)*abb` using Thompson's construction. Convert to a DFA using the subset construction. Minimize the DFA using the table-filling algorithm. Draw each stage.

**Problem 2.** Given the grammar: E → E + T | T; T → T * F | F; F → (E) | id. (a) Show this grammar is unambiguous for `id + id * id`. (b) Eliminate left recursion. (c) Compute FIRST and FOLLOW for each non-terminal in the modified grammar.

**Problem 3.** Construct the SLR(1) parsing table for the grammar: S → if E then S | if E then S else S | a; E → b. Demonstrate the shift-reduce conflict that arises and explain how it corresponds to the dangling else ambiguity.

**Problem 4.** Translate the following C code to three-address code. Show the complete set of temporaries and labels:
```c
int x = 5, y = 3, z;
if (x > y) {
    z = x * 2;
} else {
    z = y + 1;
}
while (z > 0) {
    z = z - x;
}
```

**Problem 5.** Draw the activation record (stack frame) for the following function according to the System V AMD64 ABI. Label every slot: saved registers, local variables, spilled temporaries, and return address. What is the frame size (in bytes)?
```c
int compute(int a, int b, int c, int d, int e, int f, int g) {
    int local1 = a + b;
    int local2 = c * d;
    return local1 + local2 + e + f + g;
}
```

**Problem 6.** Compile the following C to x86-64 assembly by hand (System V ABI). Your output should be valid assembly that could be assembled with `nasm` or `as`:
```c
int add(int x, int y) {
    return x + y;
}
```

**Problem 7.** Apply constant folding, dead code elimination, and common subexpression elimination to the following three-address code. Show each optimization step and the intermediate state after each pass:
```
t1 = 3 + 5
t2 = t1 * 2
t3 = 3 + 5
t4 = t3 + x
t5 = t2 + 0
t6 = t4 * 1
return t5
```

**Problem 8.** Explain how GCC implements stack canaries. Where is the canary value stored? When is it read? When is it checked? What happens if the check fails? How can an attacker bypass a stack canary if they have an information leak?

**Problem 9.** Explain position-independent code (PIC) and how it enables ASLR. What is the GOT (Global Offset Table)? What is the PLT (Procedure Linkage Table)? Trace through the resolution of the first call to `printf` in a dynamically linked PIE binary: from the call site, through the PLT stub, to the GOT entry, to the dynamic linker, back to `printf`.

**Problem 10.** What is Control Flow Integrity (CFI)? Describe two classes of control flow attacks that CFI prevents (forward-edge: indirect calls; backward-edge: return address hijacking). What is the performance overhead of CFI, and why is it sometimes acceptable in security-critical software?

---

### Tier 2 — Intermediate

**Problem 1.** Implement a recursive-descent parser for the following grammar that produces an AST (as Python objects):
```
Program → Statement*
Statement → Assignment | If | While | Return
Assignment → ID '=' Expr ';'
If → 'if' '(' Expr ')' Block ('else' Block)?
While → 'while' '(' Expr ')' Block
Block → '{' Statement* '}'
Expr → (standard arithmetic with precedence)
```
Test on 10 programs covering all constructs.

**Problem 2.** Implement a complete data-flow analysis framework. Implement reaching definitions analysis as an instance: define the gen/kill sets for each basic block, implement the iterative fixed-point algorithm, and verify convergence. Test on a CFG with a loop.

**Problem 3.** Write an LLVM pass (C++) that performs the following transformation: replace every multiplication by a constant power of 2 with a left shift. Verify correctness on 5 test cases using the LLVM test infrastructure.

**Problem 4.** Analyze the following GCC-compiled x86-64 function (from a `-O2` binary). Identify which optimizations were applied (loop unrolling, strength reduction, induction variable elimination, etc.) and reconstruct the original C source:
```asm
<function>:
  xor    eax, eax
  test   edi, edi
  jle    .L2
  lea    edx, [rdi-1]
  lea    eax, [rdi-2]
  imul   eax, edx
  shr    eax
  add    eax, edi
.L2:
  ret
```

---

### Tier 3 — Advanced

**Problem 1.** Implement graph-coloring register allocation for your toy language compiler. (a) Build the interference graph from liveness information. (b) Implement the Chaitin-Briggs algorithm: simplify (remove low-degree nodes), spill (remove high-degree nodes), select (assign colors), and spill code generation. Test on a function with more live variables than registers (force at least one spill).

**Problem 2.** Implement a simple pointer analysis (Andersen's algorithm) for a C-like IR. Track the points-to set of each pointer variable. Use it to detect potential null pointer dereferences statically.

**Problem 3.** (Capstone Compiler) Implement a complete, working compiler for a statically-typed language of your design. Requirements: (a) Lexer (from scratch or using Flex), (b) Parser (recursive descent or LALR(1) with Bison), (c) Type checker with static type inference for at least one feature (e.g., let-polymorphism), (d) IR generation (three-address code or LLVM IR), (e) At least 3 optimization passes, (f) Code generation for x86-64 or LLVM backend, (g) A test suite of ≥50 programs, (h) A 5-page writeup documenting the design decisions, especially for the type system and optimization passes.

---

## Phase 2 — Global Capstone Projects

Complete all three before beginning Phase 3.

---

### Capstone 2-A: Complete Processor in Verilog

Extend the Module 2.2 pipelined processor to:
- **Full RISC-V RV32I ISA** (all 47 instructions)
- **Cache hierarchy**: 4-way set-associative L1 I-cache and D-cache (1KB each); direct-mapped L2 (8KB)
- **Memory interface**: simple DRAM model with configurable latency
- **Branch predictor**: gshare or tournament predictor with a 16-entry BTB
- **Exception handling**: all required RISC-V machine-mode exceptions
- **Python assembler + linker** supporting labels, pseudo-instructions, and basic directives
- **Benchmark suite**: run five programs including matrix multiply, bubble sort, recursive Fibonacci, and a string search; report IPC, cache miss rate, and branch prediction accuracy for each

Deliverables: Verilog source, testbenches with 100% statement coverage, assembler, benchmarks, and a 5-page design report.

---

### Capstone 2-B: Complete Compiler

The full compiler described in Module 2.5 Tier 3 Problem 3, cross-compiled to produce RISC-V assembly runnable on your Capstone 2-A processor. Demonstrate: a sorting algorithm compiled by your compiler, assembled by your assembler, and executing correctly on your Verilog processor — end to end.

---

### Capstone 2-C: Firmware Security Analysis

Given a real-world open-source embedded firmware image (e.g., an IoT router firmware, a hobbyist RTOS project, or a provided binary):
1. Extract and identify all binary sections using `binwalk`, `objdump`, and your own tools.
2. Reverse the bootloader: identify the integrity check mechanism, the jump-to-application sequence, and the firmware update handler.
3. Identify at least 3 potential security vulnerabilities: missing input validation, unsafe string functions, lack of UART authentication, exposed debug interfaces.
4. Propose mitigations for each vulnerability.
5. Write a 6-page technical report in the style of a firmware security assessment.

---

*End of Phase 2 Complete Study Package*
*Next: Phase 3 — Systems Programming & Low-Level Mastery*

# Phase 3 — Complete Study Package
## Systems Programming & Low-Level Mastery
### Chapter Reading Lists · Weekly Schedules · Graded Problem Sets

---

> **Prerequisites before starting Phase 3:** All Phase 2 milestone assessments passed. You must be fluent in: digital logic and sequential circuits (Module 2.1), processor architecture and pipelining (Module 2.2), virtual memory and the x86-64 paging model (Module 2.3), and compiler internals including stack frame layout, GOT/PLT, and calling conventions (Module 2.5). Phase 3 is where hardware knowledge meets software — you will write C that touches raw memory, read and write x86-64 assembly by hand, implement an operating system kernel, and reason about programs at the level of clock cycles and bytes. This is the phase that makes the difference between a developer and a systems engineer.

---

# MODULE 3.1 — C Programming & Memory Management

**Duration:** 8–10 weeks | **Hours/week:** 12–15 | **Total hours:** ~130

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Kernighan & Ritchie — *The C Programming Language*, 2nd ed.

The K&R book is short and dense. Every sentence is deliberate. Read slowly. Do every exercise.

---

**Chapter 1 — A Tutorial Introduction**
Read entirely. Focus on: the compilation model (source → preprocessor → compiler → assembler → linker → executable); the distinction between declaration and definition; why C requires explicit type specification (no inference). The "Hello, World" example is the entry point — trace it through the entire toolchain manually.

**Chapter 2 — Types, Operators, and Expressions**
Read entirely. Focus on:
- Data type sizes: `char` (1 byte), `short` (2), `int` (4 on most platforms), `long` (8 on Linux x86-64, 4 on Windows x86-64), `long long` (8), `size_t` (pointer-width). **Type size confusion is a primary source of integer overflow vulnerabilities — memorize these and know when they differ.**
- Integer arithmetic: overflow wraps around for unsigned (defined behavior); signed overflow is undefined behavior — compilers assume it does not happen and optimize accordingly.
- Bitwise operators: `&`, `|`, `^`, `~`, `<<`, `>>`. Know: arithmetic vs logical right shift; masking and setting/clearing bits. **Bitwise operations are the language of hardware registers, network packet headers, cryptographic primitives, and shellcode.**
- Implicit conversions: integer promotion (all arithmetic is done at `int` width or wider); the usual arithmetic conversions. The rules for signed/unsigned mixing produce results that surprise nearly everyone.

**Chapter 3 — Control Flow**
Read entirely. Focus on: `switch` fall-through (absence of `break` is intentional in some patterns); the interaction of `break` and `continue` with labeled loops; `goto` as legitimate for error-path cleanup in C (the Linux kernel uses it heavily).

**Chapter 4 — Functions and Program Structure**
Read entirely. Focus on:
- Scope: block scope, file scope (static), external linkage. The `static` keyword has two meanings (local persistence + file scope) — both matter.
- Recursion: the stack frame model from Module 2.5 is now concrete in C.
- The preprocessor: `#define`, `#include`, conditional compilation (`#ifdef`, `#ifndef`, `#endif`), `#pragma`, stringification (`#`), token pasting (`##`). **Understanding macros is essential for reading kernel source code.**

**Chapter 5 — Pointers and Arrays**
Read entirely — the most important chapter in the book for systems programming and security.
- Pointers: address-of (`&`), dereference (`*`); pointer arithmetic; the relationship between pointer arithmetic and array indexing.
- The crucial identity: `a[i]` is exactly equivalent to `*(a + i)` — this identity is architectural, not syntactic sugar.
- Pointer to pointer (`char **argv`): drawing the memory layout is essential.
- Strings as `char *`: null termination; the absence of bounds checking; why `strcpy` and `gets` are dangerous; why `strncpy` is subtly wrong (may not null-terminate).
- Function pointers: declaration syntax; calling via function pointer; tables of function pointers as dispatch mechanisms (vtables in C++ are this, implemented in C). **Function pointer corruption is an exploitation technique — you need to understand function pointers thoroughly.**
- `void *`: the generic pointer type; casting to/from void *; alignment requirements.

**Chapter 6 — Structures**
Read entirely. Focus on:
- Struct layout: member ordering; padding inserted by the compiler for alignment; `sizeof(struct)` is not always the sum of `sizeof(member)`. **Struct padding is a source of information leakage in kernel data structures (uninitialized padding bytes).**
- Pointers to structures and the `->` operator.
- Self-referential structures (linked list node).
- Unions: all members share the same memory location; union size is the size of the largest member; type punning with unions; endianness analysis with unions.
- Bit fields: packing boolean flags; hardware register modeling.

**Chapter 7 — Input and Output**
Read entirely. Focus on: formatted I/O (`printf`/`scanf` format string interpretation — this is where format string vulnerabilities originate); file I/O with `fopen`/`fclose`/`fread`/`fwrite`; the `FILE *` abstraction as a buffered wrapper around a file descriptor.

**Chapter 8 — The UNIX System Interface**
Read entirely. This chapter is essential — it covers the POSIX interface directly:
- `open`, `read`, `write`, `close`: the unbuffered I/O system calls.
- The file descriptor as a kernel-managed integer — file descriptor table, global file table, inode table.
- `lseek`: seeking within files; the `SEEK_SET`/`SEEK_CUR`/`SEEK_END` constants.
- `stat` and the file metadata structure.
- Directory operations: `opendir`, `readdir`.
- Dynamic storage allocation: the `sbrk` system call as the traditional heap expansion mechanism.

---

### Primary Text: Seacord — *Effective C*, 1st ed. (No Starch Press)

Read this after K&R to fill in C11/C17 features and security-focused practices.

**Chapter 1 — Getting Started with C**
Skim — overlap with K&R. Focus on the C standard compliance discussion and the difference between implementation-defined, unspecified, and undefined behavior.

**Chapter 2 — Objects, Functions, and Types**
Read entirely. Focus on: object lifetime (static, automatic, allocated, temporary); type qualifiers (`const`, `volatile`, `restrict`, `_Atomic`). `volatile` is not a synchronization primitive — it prevents compiler optimization of reads/writes but provides no memory ordering guarantees. `restrict` tells the compiler that pointer arguments do not alias — enabling aggressive optimization, with undefined behavior if violated.

**Chapter 3 — Arithmetic Types**
Read entirely. Focus on: the full integer type hierarchy; `<stdint.h>` fixed-width types (`uint8_t`, `int32_t`, etc.) — **always use these in security-sensitive code**; `size_t` and `ptrdiff_t`; integer overflow, truncation, and sign conversion — the three integer bugs most commonly exploited.

**Chapter 4 — Expressions and Statements**
Read entirely. Focus on: sequence points (now sequence-before relation in C11); undefined behavior from unsequenced modifications; short-circuit evaluation of `&&` and `||`.

**Chapter 5 — Control Flow**
Skim — overlap with K&R.

**Chapter 6 — Dynamically Allocated Memory**
Read entirely — the most security-relevant chapter in this book. Focus on:
- `malloc`/`calloc`/`realloc`/`free`: the contract for each; what `calloc` guarantees that `malloc` does not (zero-initialization — important for preventing information disclosure).
- Common errors: use-after-free, double-free, heap buffer overflow, use of uninitialized memory, failing to check `malloc` return value for NULL. **Each of these is an exploitable vulnerability class in Module 4.5.**
- Memory layout: how `malloc` implementations (ptmalloc, jemalloc, tcmalloc) maintain metadata; the heap metadata as an attack target.
- The `aligned_alloc` function for over-aligned types.

**Chapter 7 — Characters and Strings**
Read entirely. Focus on: the string model (null-terminated `char` array); the family of standard string functions and their safety properties; C11 Annex K bounds-checking functions (`strcpy_s`, `strcat_s`, `memcpy_s`); why string operations are the most common source of buffer overflows.

**Chapter 8 — Input/Output**
Read entirely. Focus on: format string vulnerabilities — how `printf(user_input)` with a `%n` specifier allows arbitrary writes; why the compiler warns about this; how to write safe formatted I/O. **Format string vulnerabilities are an exploitation class in Module 4.5.**

**Chapter 9 — Preprocessing**
Read entirely. Function-like macros vs inline functions: macros have no type checking and can have surprising evaluation order issues (always parenthesize macro arguments and bodies). Understand `_Static_assert` for compile-time invariant checking.

**Chapter 10 — Program Structure**
Read entirely. Translation units; header guards; `extern` declarations vs definitions; the one definition rule.

**Chapter 11 — Concurrency**
Read §11.1–11.3 (C11 atomics preview — detailed coverage in Module 3.4).

---

### Primary Text: Seacord — *Secure Coding in C and C++*, 2nd ed. (Addison-Wesley)

**Chapter 2 — Strings**
Read entirely. Focus on: the anatomy of a string vulnerability; buffer overflow via `strcpy`, `strcat`, `gets`, `scanf %s`; format string attacks; the `strlcpy`/`strlcat` safe alternatives; POSIX string functions.

**Chapter 3 — Pointer Subterfuge**
Read entirely. Focus on: function pointer overwrite; GOT overwrite; the `setjmp`/`longjmp` exploitation angle; vtable pointer overwrite.

**Chapter 5 — Integer Security**
Read entirely. Focus on: signed integer overflow; unsigned integer wrapping; integer truncation (assignment to a narrower type); sign conversion (signed to unsigned and vice versa). **This chapter is directly prerequisite to Module 4.5's integer overflow exploitation section.**

**Chapter 7 — File I/O**
Read §7.1–7.4. Focus on: TOCTOU (time-of-check to time-of-use) vulnerabilities — the race between checking a file's properties and using the file; symlink attacks; `/tmp` race conditions. **TOCTOU exploitation is covered in Module 3.4.**

---

### Primary Text: Kerrisk — *The Linux Programming Interface* (TLPI)

This is the definitive reference for Linux system programming. For Module 3.1, read:

**Chapter 1 — History and Standards**
Read entirely. The POSIX and SUS standards; GNU/Linux vs other Unices; the C standard library.

**Chapter 2 — Fundamental Concepts**
Read entirely. Focus on: the kernel/user space distinction; system calls (the `syscall` instruction); the C library as a thin wrapper; file descriptors; processes and threads; virtual memory concepts (revisiting from Module 2.3 now from the programmer's perspective).

**Chapter 3 — System Programming Concepts**
Read entirely. Focus on: error handling with `errno`; the error-checking wrapper function pattern; the `perror` and `strerror` functions; function design for error propagation.

**Chapter 4 — File I/O: The Universal I/O Model**
Read entirely. Focus on: `open`, `read`, `write`, `close`; file offset and `lseek`; `ioctl` as the escape hatch for device-specific operations; the file descriptor table, open file table, and inode table — three levels of kernel file data structures. **Understanding these three tables is essential for understanding how container file system isolation works.**

**Chapter 6 — Processes**
Read entirely. Focus on: process layout in virtual memory (text, initialized data, BSS, heap, stack, kernel virtual addresses); `getpid`, `getppid`; the `/proc/PID/maps` file as a window into a process's virtual address space. **Reading `/proc/PID/maps` is a fundamental reverse engineering and exploitation technique.**

**Chapter 7 — Memory Allocation**
Read entirely. Focus on: `brk`/`sbrk` (heap expansion system calls); `malloc` as a library on top of `brk`/`mmap`; the memory allocation debugging tools (mtrace, mcheck).

---

## Part B: Week-by-Week Study Schedule

### Week 1 — C Fundamentals: Types, Pointers, Memory Layout
- **Day 1:** K&R Ch. 1–2. Compile and trace 10 small programs. Inspect generated assembly with `gcc -S -O0`.
- **Day 2:** K&R Ch. 5.1–5.5. Pointer arithmetic. Draw memory layouts for: `int a[5]`, `char *s = "hello"`, `char **argv`. Verify with `printf("%p")`.
- **Day 3:** K&R Ch. 5.6–5.12. Function pointers. Implement a dispatch table (array of function pointers) for a simple command interpreter.
- **Day 4:** Seacord *Effective C* Ch. 2–3. Fixed-width types. Integer overflow examples — verify with `-fsanitize=undefined`.
- **Day 5:** Problem Set 3.1 Tier 1, problems 1–8.
- **Day 6:** GDB lab — set breakpoints in 5 programs; inspect stack, heap, global, and code segments using `info proc mappings` and `/proc/PID/maps`.
- **Day 7:** Rest.

### Week 2 — Structs, Unions, and the C Object Model
- **Day 1:** K&R Ch. 6. Struct layout and padding. Verify `sizeof` for 5 structs with different orderings. Use `__attribute__((packed))` and observe the difference.
- **Day 2:** Unions and type punning. Implement an endianness detector using a union. Explain IEEE 754 bit patterns via union access.
- **Day 3:** K&R Ch. 4. Preprocessor. Implement 5 safe macros. Implement `container_of` (the Linux kernel macro for embedding structs).
- **Day 4:** Seacord *Effective C* Ch. 6. Dynamic allocation. Implement a safe `xmalloc` that aborts on NULL and a `safe_strdup`.
- **Day 5:** Problem Set 3.1 Tier 1, problems 9–16.
- **Day 6:** Valgrind lab — fix 10 memory bugs (provided programs with deliberate use-after-free, double-free, heap overflow, uninitialized read).
- **Day 7:** Rest.

### Week 3 — System Calls and POSIX I/O
- **Day 1:** K&R Ch. 8 + TLPI Ch. 4. `open`/`read`/`write`/`close`. Implement a file copy program using only system calls (no `fopen`).
- **Day 2:** TLPI Ch. 6. Process memory layout. Read `/proc/self/maps` and annotate each region (stack, heap, libraries, vDSO, vsyscall).
- **Day 3:** TLPI Ch. 7. `brk`/`sbrk`. Implement a bump allocator using `sbrk`.
- **Day 4:** Seacord *Secure Coding* Ch. 2. String vulnerability analysis. Find 5 CVEs from NVD involving `strcpy`/`gets`; read the patch.
- **Day 5:** Problem Set 3.1 Tier 1, problems 17–20 + Tier 2, problems 1–4.
- **Day 6:** Project start — memory allocator (malloc/free from scratch using `mmap`).
- **Day 7:** Rest.

### Week 4 — Memory Allocator Project
- **Days 1–4:** Implement a memory allocator: free list management (first-fit, then best-fit), block splitting, coalescing adjacent free blocks, `realloc`. Use `mmap` for large allocations, `sbrk` for small ones.
- **Day 5:** Test your allocator: replace `malloc` with `LD_PRELOAD` and run real programs. Fix crashes.
- **Day 6:** AddressSanitizer lab — enable ASan on 5 programs; understand each error report.
- **Day 7:** Rest.

### Week 5 — Undefined Behavior, Integer Security, and Format Strings
- **Day 1:** Seacord *Effective C* Ch. 3–4. UB tour — compile 10 UB examples at `-O0` and `-O2`; observe how the optimizer exploits UB.
- **Day 2:** Seacord *Secure Coding* Ch. 5. Integer overflow exploitation theory. Write C programs demonstrating: signed overflow wrapping to negative (at -O0), unsigned wrapping, truncation in `size_t` to `int` conversion.
- **Day 3:** Seacord *Secure Coding* Ch. 3 + Ch. 8. Format string bugs. Write a program vulnerable to format string read (`%x`) and explain `%n`. Use `printf` with `%n` to write a value to a stack variable (in a sandboxed program).
- **Day 4:** TOCTOU preview — Seacord *Secure Coding* Ch. 7. Demonstrate a `/tmp` symlink race.
- **Day 5:** Problem Set 3.1 Tier 2, problems 5–12.
- **Day 6:** Safe string library project — implement `safe_strcpy`, `safe_strcat`, `safe_snprintf` with bounds checking.
- **Day 7:** Rest.

### Week 6 — GDB Mastery and Debugging Tools
- **Day 1:** GDB deep-dive: conditional breakpoints, watchpoints, `commands`, `define`, hardware breakpoints vs software breakpoints, reverse debugging (`record`).
- **Day 2:** Debugging exercise set — 5 programs with bugs only findable via watchpoints or memory inspection.
- **Day 3:** `ltrace` and `strace` — trace system calls and library calls of 5 programs. Annotate every call.
- **Day 4:** Compile with `-g -fsanitize=address,undefined,leak` — fix all issues in your allocator project.
- **Day 5:** Problem Set 3.1 Tier 2, problems 13–20.
- **Day 6:** Mark-and-sweep garbage collector project — begin implementation.
- **Day 7:** Rest.

### Weeks 7–8 — Projects, Integration, and Milestone
- **Week 7:** Complete all three projects: memory allocator, safe string library, mark-and-sweep GC.
- **Week 8:** Problem Set 3.1 Tier 3 + milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Write a C function `void *safe_memcpy(void *dst, size_t dst_size, const void *src, size_t n)` that copies at most `min(dst_size, n)` bytes, always null-terminates if dst is a string buffer, and returns NULL if `dst` or `src` is NULL. Explain why `memcpy` itself is not sufficient and what vulnerability it enables.

**Problem 2.** For each struct below, state its `sizeof` on a 64-bit Linux system (x86-64, System V ABI). Explain every padding byte inserted and why. Then reorder fields to minimize padding:
```c
struct A { char a; int b; char c; double d; };
struct B { char a; char b; short c; int d; long e; };
struct C { int a; char b[3]; short c; double d; char e; };
```

**Problem 3.** Explain the difference between `char *p = "hello"` and `char p[] = "hello"`. Where is each stored in memory? What happens if you attempt to write through `p` in the first case? Why does this matter for security?

**Problem 4.** Write a function `int parse_int(const char *s, int *result)` that safely converts a string to an integer. It must: detect overflow (return -1), detect non-numeric input (return -1), handle leading whitespace and optional sign, and store the result in `*result` only on success. Write 15 unit tests covering all edge cases.

**Problem 5.** The following function has a use-after-free vulnerability. Identify it, explain under what conditions it is exploitable, and fix it:
```c
typedef struct Node { int val; struct Node *next; } Node;
void delete_list(Node *head) {
    Node *cur = head;
    while (cur) {
        free(cur);
        cur = cur->next;  // use-after-free
    }
}
```

**Problem 6.** Implement a generic doubly-linked list in C using `void *` data pointers and function pointers for comparison and printing. Include: `list_append`, `list_prepend`, `list_remove`, `list_find`, `list_sort` (merge sort on the list), `list_free`. Write unit tests for all operations.

**Problem 7.** The following integer arithmetic is intended to allocate a buffer for `n` elements of `size` bytes each:
```c
void *alloc_array(size_t n, size_t size) {
    return malloc(n * size);
}
```
(a) Demonstrate the integer overflow: for what values of `n` and `size` does `n * size` overflow `size_t` on a 64-bit system? (b) Write a safe version that detects overflow before calling `malloc`.

**Problem 8.** Explain what each of the following does to `/proc/PID/maps` output, and what security significance each has: `PROT_READ`, `PROT_WRITE`, `PROT_EXEC`, `MAP_ANONYMOUS`, `MAP_SHARED`. Then explain: what does it mean for a memory region to be `r-xp` vs `rw-p` vs `rwxp`? Why is `rwxp` suspicious?

**Problem 9.** Write a C program that: (a) allocates a 64-byte buffer on the stack; (b) fills it with the return address of the current function (read from the stack); (c) prints the return address in hex; (d) explains what information an attacker gains from knowing this value. Compile with `-fno-stack-protector -no-pie` to disable mitigations.

**Problem 10.** Explain how a format string vulnerability in `printf(user_input)` allows an attacker to: (a) read arbitrary stack values using `%x` or `%p`; (b) read an arbitrary memory address using `%s` with a crafted address on the stack; (c) write an arbitrary value to an arbitrary address using `%n`. Write a demonstration for (a) in a sandboxed program.

**Problem 11.** Implement `strtol` from scratch (no standard library). Handle: decimal, hexadecimal (`0x` prefix), octal (`0` prefix), leading whitespace, optional sign, overflow detection, endptr. Write 20 unit tests.

**Problem 12.** The following code is vulnerable to a TOCTOU attack. Identify the window of vulnerability and describe the exploit:
```c
if (access(path, W_OK) == 0) {
    fd = open(path, O_WRONLY | O_TRUNC);
    write(fd, data, len);
}
```
Write the fixed version using `O_NOFOLLOW` and explain why it closes the window.

**Problem 13.** Implement a memory pool allocator: a fixed-size allocator for objects of a single size. Support `pool_create(obj_size, capacity)`, `pool_alloc(pool)` (O(1)), `pool_free(pool, ptr)` (O(1)), `pool_destroy(pool)`. Use a free list of pre-allocated slots. Write a benchmark comparing pool allocation vs `malloc` for 1,000,000 allocations.

**Problem 14.** Write a C implementation of a hash table that handles collisions via separate chaining. Support: `ht_create(capacity)`, `ht_insert(ht, key, value)`, `ht_lookup(ht, key)`, `ht_delete(ht, key)`, `ht_resize(ht)` (double size when load factor exceeds 0.75). Use a djb2 hash function. Write 15 unit tests.

**Problem 15.** Explain the difference between `static int x` at file scope and `static int x` at function scope. What are the implications for: (a) lifetime, (b) linkage, (c) thread safety? Give an example where the function-scope `static` creates a security issue in a multi-threaded program.

**Problem 16.** Write a `printf`-like function `safe_printf(const char *fmt, ...)` that accepts only `%d`, `%s`, `%p`, and `%%` format specifiers and ignores or rejects `%n` and `%x`. Use `<stdarg.h>`. Explain why rejecting `%n` prevents the write primitive in format string exploits.

**Problem 17.** The `realloc` function has two failure modes that are often confused. Describe both, and explain the memory leak that results from this common pattern:
```c
ptr = realloc(ptr, new_size);  // BUG: if realloc fails, original ptr is lost
```
Write the correct idiom and explain each step.

**Problem 18.** Implement a mark-and-sweep garbage collector skeleton: an object graph where each node has a `mark` bit and a list of pointers to other nodes. Implement `gc_mark(root)` (recursive DFS to set mark bits) and `gc_sweep(heap)` (free all unmarked nodes). Demonstrate on a graph with a cycle.

**Problem 19.** Write a C program that uses `mmap` to create an anonymous mapping, writes data to it, then uses `mprotect` to make it read-only, and verifies that a write attempt generates a `SIGSEGV`. Catch the signal using `sigaction` and print a diagnostic message before re-raising it.

**Problem 20.** Describe in precise detail what happens when a C program dereferences a NULL pointer on Linux x86-64: from the faulting instruction through the hardware exception, the kernel's fault handler, the signal delivery to the process, the default signal disposition (`SIGSEGV` → core dump), and what information is in the core dump.

---

### Tier 2 — Intermediate

**Problem 1.** Implement a complete memory allocator (`malloc`, `free`, `realloc`, `calloc`) using `mmap` for large allocations and `sbrk` for small ones. Your allocator must: use a segregated free list (size classes: 8, 16, 32, 64, 128, 256, 512, 1024, 4096, and large), coalesce adjacent free blocks, split blocks when the remainder is large enough, and handle alignment correctly for all standard types. Validate with `LD_PRELOAD` on real programs.

**Problem 2.** Implement `setjmp`/`longjmp` semantics from scratch in C using `<ucontext.h>` or inline assembly to save and restore registers. Explain: which registers must be saved (callee-saved), what happens to the stack between `setjmp` and `longjmp`, and why `longjmp` past a `free()` call is dangerous.

**Problem 3.** Write a C program that demonstrates three distinct integer security vulnerabilities each triggering with a different input. For each: (a) identify the CWE (CWE-190 signed overflow, CWE-191 unsigned overflow, CWE-197 truncation, CWE-195 sign conversion); (b) show the input that triggers it; (c) explain the worst-case exploitation scenario; (d) write the fixed version.

**Problem 4.** Implement the `container_of` macro used throughout the Linux kernel:
```c
#define container_of(ptr, type, member) \
    ((type *)((char *)(ptr) - offsetof(type, member)))
```
Prove its correctness by drawing the memory layout for a struct with three members, showing how subtracting the member offset recovers the struct base address. Write a test that verifies it for 3 different struct/member combinations.

**Problem 5.** Implement a safe string library providing: `sstr_t` (a struct containing `char *buf`, `size_t len`, `size_t cap`), `sstr_new(cap)`, `sstr_append(s, data, len)`, `sstr_append_cstr(s, cstr)`, `sstr_resize(s, new_cap)`, `sstr_free(s)`. All operations must be bounds-safe. Write 20 unit tests including overflow attempts.

---

### Tier 3 — Advanced

**Problem 1.** Implement a complete, production-quality memory allocator with: (a) thread safety using per-thread caches (tcmalloc-style) with a global arena protected by a spinlock; (b) heap metadata integrity validation on every `free` (detect double-free and wild pointer free); (c) canary values in chunk headers to detect heap overflow; (d) `malloc_stats()` reporting total allocated, peak allocated, and current live allocations. Test with a multi-threaded benchmark.

**Problem 2.** Write a C program that performs a heap spray: allocate many fixed-size objects with predictable content; demonstrate that after spraying, a use-after-free of a freed object likely returns a controlled buffer. Explain how heap spraying is used in Module 4.5 exploitation to increase reliability.

**Problem 3.** Implement a shadow stack in C: before each function call, push the return address to a shadow stack (allocated with `mmap(PROT_READ|PROT_WRITE)`); on return, compare the hardware return address to the shadow stack top and abort if they differ. Implement as a Clang instrumentation pass (or as a source-level wrapper using `__builtin_return_address`). Test against a stack buffer overflow exploit.

---

### Milestone Assessment — Module 3.1
*Pass threshold: 80%. Time: 4 hours. Open book (no code execution).*

1. Write a complete, safe `read_line(char *buf, size_t buf_size, FILE *fp)` function that reads one line, truncates at `buf_size-1`, always null-terminates, handles EOF and error, and returns the number of bytes read.
2. Given a `struct` definition, compute its size, draw its memory layout with padding, and reorder fields to minimize size.
3. Write a function that safely computes `a * b` for `size_t a, b` without integer overflow, returning 0 on overflow.
4. Explain the three-table model of file descriptors in the Linux kernel. What happens at each level when `dup2(oldfd, newfd)` is called?
5. Write and annotate a C program that demonstrates use-after-free, double-free, and heap overflow in three separate functions. Explain how ASan detects each.

---

---

# MODULE 3.2 — x86-64 Assembly Language

**Duration:** 8–10 weeks | **Hours/week:** 12–15 | **Total hours:** ~120

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Bryant & O'Hallaron — *Computer Systems: A Programmer's Perspective*, 3rd ed., Chapter 3 (complete)

You began this chapter in Module 2.2. Now read it in full depth as an assembly practitioner, not as a computer architecture student.

---

**Section 3.1 — A Historical Perspective**
Skim — the 8086 → 286 → 386 → x86-64 evolution. Understand: x86-64 is a 64-bit extension of a 32-bit ISA (IA-32) which was itself an extension of 16-bit x86. The legacy baggage (segment registers, real mode, 16-bit encodings) explains many of the ISA's quirks.

**Section 3.2 — Program Encodings**
Focus on: the relationship between C source, GCC output, object files, and the final binary; `objdump -d` to disassemble; the machine instruction as a variable-length byte string (1–15 bytes on x86-64); the instruction pointer `rip` as the program counter.

**Section 3.3 — Data Formats**
Focus on: the Intel size suffixes (byte=8b, word=16b, double word=32b, quad word=64b); the AT&T suffixes (`b`, `w`, `l`, `q`); moving data between registers and memory.

**Section 3.4 — Accessing Information**
Focus on (memorize completely):
- **16 general-purpose registers:** `rax`/`eax`/`ax`/`al` (return value, accumulator), `rbx`/`ebx`/`bx`/`bl` (callee-saved), `rcx`/`ecx`/`cx`/`cl` (4th arg, shift count), `rdx`/`edx`/`dx`/`dl` (3rd arg), `rsi`/`esi`/`si`/`sil` (2nd arg), `rdi`/`edi`/`di`/`dil` (1st arg), `rbp`/`ebp`/`bp`/`bpl` (callee-saved, optional frame pointer), `rsp`/`esp`/`sp`/`spl` (stack pointer), `r8`–`r15` (5th–6th args in `r8`/`r9`, then callee-saved or caller-saved per the ABI).
- Addressing modes: immediate `$imm`, register `%reg`, memory absolute `addr`, register indirect `(%reg)`, base+displacement `disp(%reg)`, indexed `(%base,%index,scale)`, general `disp(%base,%index,scale)`.
- Data movement: `mov`, `movsx` (sign extend), `movzx` (zero extend), `lea` (load effective address — used for arithmetic, not just address computation).

**Section 3.5 — Arithmetic and Logical Operations**
Focus on: `add`, `sub`, `imul`, `idiv`, `inc`, `dec`, `neg`, `not`, `and`, `or`, `xor`, `sal`/`shl`, `sar` (arithmetic right shift — sign-preserving), `shr` (logical right shift). The `xor %reg, %reg` idiom for zeroing a register (smaller encoding than `mov $0, %reg`). `lea` for multi-operand arithmetic without affecting flags.

**Section 3.6 — Control**
Focus on: condition codes (`CF`, `ZF`, `SF`, `OF`) and what sets them; `cmp` and `test` (they set flags without storing results); conditional set instructions (`sete`, `setne`, `setl`, `setg`, etc.); conditional jumps (`je`/`jne`/`jl`/`jg`/`jle`/`jge`/`ja`/`jb` and their signed/unsigned distinctions — **this distinction matters for exploit code**); conditional move `cmov` for branch-free code.

**Section 3.7 — Procedures**
Focus on (with extreme care — this is the foundation of stack exploitation):
- `call` instruction: pushes `rip+instruction_length` (the return address) onto the stack, then jumps to the target.
- `ret` instruction: pops the top of the stack into `rip` (jumps to the return address). **This is the instruction hijacked by stack buffer overflow exploits.**
- The complete System V AMD64 ABI stack frame:
  - Arguments 1–6: `rdi`, `rsi`, `rdx`, `rcx`, `r8`, `r9`.
  - Arguments 7+: pushed on stack in reverse order (right to left).
  - Callee-saved: `rbx`, `rbp`, `r12`, `r13`, `r14`, `r15` — the callee must preserve these.
  - Caller-saved: `rax`, `rcx`, `rdx`, `rsi`, `rdi`, `r8`, `r9`, `r10`, `r11` — the caller must save these if it needs them across a call.
  - Return value: `rax` (integer/pointer), `rax`+`rdx` (128-bit), `xmm0` (float/double).
  - Red zone: 128 bytes below `rsp` that a leaf function may use without adjusting `rsp` (signal handlers and interrupt handlers must not touch this region).
  - Stack alignment: `rsp` must be 16-byte aligned at the point of a `call` instruction.

**Section 3.8 — Array Allocation and Access**
Focus on: how `a[i]` compiles to `(%rdi,%rsi,8)` (for a 64-bit element array); multidimensional array row-major layout; the compiler's use of `lea` for index computation.

**Section 3.9 — Heterogeneous Data Structures**
Focus on: struct field access as a fixed displacement from the base pointer; union memory layout (all fields at offset 0); the assembly patterns for struct/union access — recognizing these is essential for reverse engineering.

**Section 3.10 — Combining Control and Data in Machine-Level Programs**
Focus on: understanding pointers to code (function pointers); out-of-bounds array access and memory corruption at the assembly level; buffer overflow in assembly — trace the exact bytes that overwrite the return address.

**Section 3.11 — Floating-Point Code**
Focus on: `xmm0`–`xmm15` registers (128-bit each, used for scalar and SIMD float); `movss`/`movsd` for single/double float moves; `addss`/`addsd`/`mulss`/`mulsd` for arithmetic; how floating-point arguments and return values use `xmm` registers in the ABI.

**Section 3.12 — Aside: Machine-Level Representations of Programs**
Focus on: `nop` sleds (a sequence of `nop` instructions that slides execution to shellcode — relevant to Module 4.5); obfuscated code patterns; pointer-based control flow.

---

### Primary Text: Intel® 64 and IA-32 Architectures Software Developer's Manual

**Volume 1 — Basic Architecture**
Read: Chapter 3 (Basic Execution Environment — registers and flags), Chapter 4 (Data Types).

**Volume 2 — Instruction Set Reference**
Use as a reference. For every instruction you encounter, look up: encoding, operand forms, flags affected, and any exceptions. Key instructions to look up precisely: `syscall`, `sysret`, `cpuid`, `rdtsc`, `rdtscp`, `xchg`, `cmpxchg`, `cmpxchg8b`, `lock` prefix, `rep`/`repe`/`repne` string prefixes, `clflush`, `lfence`/`mfence`/`sfence`, `int3`, `ud2`, `hlt`, `in`/`out` (I/O port access — relevant for VM escape techniques).

**Volume 3 — System Programming Guide**
Read: Chapter 5 (Protection — privilege levels, segment descriptors, call gates), Chapter 6 (Interrupt and Exception Handling — IDT, gate descriptors, interrupt stack), Chapter 7 (Task Management).

---

### Supplementary: System V AMD64 ABI Specification
Read: §3.1 (Registers and the Stack Frame), §3.2 (The Stack Frame), §3.2.3 (Parameter Passing), §3.4 (Process Initialization).

---

### Supplementary: *PC Assembly Language* by Paul Carter (free PDF)
Use for NASM-syntax examples and exercises if you prefer Intel syntax over AT&T.

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Register Set and Data Movement
- **Day 1:** B&O §3.4. Memorize all 16 registers, their sub-register names, and their ABI roles. Write a table from memory.
- **Day 2:** B&O §3.3–3.4. Addressing modes. Write 20 `mov` instructions using all addressing modes in GAS syntax. Assemble and disassemble with `objdump`.
- **Day 3:** B&O §3.5. Arithmetic. Implement in pure NASM/GAS assembly: abs, min, max, integer square root (Newton's method), GCD.
- **Day 4:** Intel SDM Vol. 2 — look up `movsx`, `movzx`, `movsxd`, `cdqe`. Understand sign/zero extension and when each is generated by the compiler.
- **Day 5:** Problem Set 3.2 Tier 1, problems 1–6.
- **Day 6:** Disassembly lab — compile 5 C functions at `-O0` and `-O2`; annotate every instruction in the output.
- **Day 7:** Rest.

### Week 2 — Control Flow and Conditionals
- **Day 1:** B&O §3.6. Condition codes. Fill out the condition code table: what `cmp a,b` sets; what each `jcc` condition tests (signed vs unsigned).
- **Day 2:** Implement in assembly: bubble sort, selection sort. Verify against C reference.
- **Day 3:** Conditional moves: rewrite an if-else in assembly using `cmov` (branch-free). Measure performance difference.
- **Day 4:** Switch tables: compile a C `switch` with 10 cases; analyze the jump table generated by GCC `-O2`.
- **Day 5:** Problem Set 3.2 Tier 1, problems 7–12.
- **Day 6:** Reverse engineering lab — 15 stripped functions to identify and annotate.
- **Day 7:** Rest.

### Week 3 — Procedures and the Stack Frame
- **Day 1:** B&O §3.7. The full ABI. Draw the stack frame for a function with 8 arguments (2 on stack), 3 local variables, calling another function. Label every slot with its offset from `rsp` and `rbp`.
- **Day 2:** Implement in assembly (full ABI compliance): recursive Fibonacci, recursive binary tree traversal, a function taking 8 arguments.
- **Day 3:** Implement all 10 standard algorithms from Module 3.2's project list: `strlen`, `strcpy`, `memcpy`, `memset`, `strcmp`, `memmove`, bubble sort, binary search, GCD, power.
- **Day 4:** Trace a function call chain 4 levels deep in GDB — inspect `rsp`, `rbp`, and the stack frame contents at each level.
- **Day 5:** Problem Set 3.2 Tier 1, problems 13–18.
- **Day 6:** Project — "Hello World" from raw syscalls only (no libc, no startup code — just `_start` and `syscall`).
- **Day 7:** Rest.

### Week 4 — System Calls and Shellcode Fundamentals
- **Day 1:** `syscall` instruction — Linux x86-64 syscall calling convention: `rax`=syscall number, `rdi`/`rsi`/`rdx`/`r10`/`r8`/`r9` = args. Write assembly programs using: `read`, `write`, `open`, `close`, `exit`, `mmap`, `execve`.
- **Day 2:** Shellcode constraints: null-byte avoidance (many injection contexts are null-terminated strings); encoding tricks to eliminate null bytes; position-independent code (no absolute addresses — use RIP-relative addressing).
- **Day 3:** Write a minimal `execve("/bin/sh", NULL, NULL)` shellcode in NASM. Verify it is null-free. Test by injecting into a C program via a global char array.
- **Day 4:** PIC shellcode: write a function that calls another without knowing its absolute address (using `call/pop` or `lea rax, [rip+offset]`).
- **Day 5:** Problem Set 3.2 Tier 2, problems 1–5.
- **Day 6:** TCP reverse shell shellcode — implement (for shellcode technique understanding in sandboxed lab environment).
- **Day 7:** Rest.

### Week 5 — SSE/AVX SIMD and Advanced Instructions
- **Day 1:** B&O §3.11. `xmm` registers. Scalar float operations. Write: float dot product, vector norm.
- **Day 2:** SSE2 packed operations: `paddb`, `paddw`, `paddq`, `pcmpeqb`, `pmovmskb`. Implement `strlen` using SSE2 (compare 16 bytes at once for null byte).
- **Day 3:** Intel SDM Vol. 2 — `rdtsc`, `rdtscp`, `cpuid`, `lfence`. Understand the memory ordering guarantees and why `lfence` is needed for timing measurements.
- **Day 4:** `lock` prefix and atomic instructions: `lock xadd`, `lock cmpxchg`. Implement a spinlock in assembly.
- **Day 5:** Problem Set 3.2 Tier 2, problems 6–10.
- **Day 6:** Optimize an inner loop (e.g., XOR of two 64-byte buffers) using SSE2; benchmark against C.
- **Day 7:** Rest.

### Weeks 6–8 — Reverse Engineering Labs and Milestone
- **Week 6:** Reverse engineering lab — annotate 20 stripped binary functions. Write analysis report for each.
- **Week 7:** Manual instruction encoding lab — encode 5 instructions from the Intel opcode tables by hand (without a compiler); verify with `ndisasm`.
- **Week 8:** Problem Set 3.2 Tier 3 + milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Write in x86-64 AT&T assembly (GAS syntax): a function `long sum_array(long *a, long n)` that sums `n` elements of array `a`. Use a loop with a counter in a register. Comply fully with the System V ABI (handle callee-saved registers, return in `rax`).

**Problem 2.** Trace the following assembly line by line. State the value of `rax`, `rbx`, `rcx`, `rsp`, and the value at `[rsp]` after each instruction:
```asm
mov    $0x10, %rax
mov    $0x20, %rbx
push   %rbx
push   %rax
pop    %rcx
add    (%rsp), %rcx
pop    %rbx
```

**Problem 3.** The following C function is compiled to the assembly below. Reconstruct the C source from the assembly. Explain each instruction's purpose:
```asm
mystery:
  xor    %eax, %eax
  test   %edi, %edi
  jle    .done
.loop:
  add    (%rsi), %eax
  add    $4, %rsi
  dec    %edi
  jnz    .loop
.done:
  cltq
  ret
```

**Problem 4.** Encode the following x86-64 instructions manually using the Intel opcode tables (Vol. 2). State each byte of the encoding in hex:
(a) `nop` (b) `ret` (c) `xor %eax, %eax` (d) `push %rbp` (e) `mov %rsp, %rbp`

**Problem 5.** Write a position-independent `execve("/bin/sh", NULL, NULL)` shellcode in NASM. Requirements: (a) no null bytes in the shellcode; (b) no absolute addresses; (c) ≤60 bytes. Show the shellcode bytes, verify null-byte absence, and demonstrate execution in a test harness.

**Problem 6.** The System V AMD64 ABI requires `rsp` to be 16-byte aligned before a `call` instruction. Explain why this requirement exists (hint: consider SSE instructions and their alignment requirements). Write an assembly function that demonstrates the misalignment that occurs when a function is called and show how the prologue restores alignment.

**Problem 7.** Implement in x86-64 NASM: `void *mymemset(void *ptr, int value, size_t n)` using the `stosb` string instruction with the `rep` prefix. Then implement a faster version using 8-byte stores (`stosq` with `rep`) for aligned regions. Benchmark both.

**Problem 8.** Disassemble the following byte sequence as x86-64 (using `ndisasm -b 64` or manually). Identify any anti-disassembly tricks and explain their effect on a linear-sweep disassembler:
```
55 48 89 E5 EB 01 CC 48 83 EC 10 48 C7 45 F8 00 00 00 00 5D C3
```

**Problem 9.** Write an assembly program that uses `sigaction` (via `syscall`) to install a signal handler for `SIGSEGV`. The handler should print "Caught SIGSEGV at address 0x{fault_address}" using `write` and then call `exit(1)`. Test by dereferencing a NULL pointer.

**Problem 10.** Explain precisely what happens during a Linux x86-64 system call: from the `syscall` instruction through the kernel entry point, the handling of the syscall number, the argument marshalling, kernel execution, and `sysret` back to user space. What is the vDSO and why does `gettimeofday` not require a full kernel entry on modern Linux?

---

### Tier 2 — Intermediate

**Problem 1.** Implement a hand-optimized `strcmp` in x86-64 assembly using SSE4.2's `pcmpistri` (packed compare implicit-length strings). Compare performance against the glibc implementation on strings of length 1, 16, 64, and 256 bytes.

**Problem 2.** Write a position-independent shellcode that: (a) locates the base address of `libc` in memory by parsing the ELF dynamic loader structures accessible via the `_r_debug` struct; (b) finds the address of `system()` using the ELF symbol table. Write this entirely in assembly. This is the technique used before GOT/PLT overwrites became standard — understand why it was necessary.

**Problem 3.** Implement a spinlock in x86-64 assembly using `lock cmpxchg`. The lock must be fair (FIFO order of acquisition using a ticket lock). Demonstrate: (a) lock acquisition when free; (b) lock acquisition when contended (busy-wait); (c) unlock. Write a multi-threaded C test harness that verifies mutual exclusion.

**Problem 4.** Perform the following reverse engineering task: given the stripped binary for a program that encrypts a string with a custom XOR cipher, recover the key and decrypt a sample ciphertext. Use only GDB and objdump — no decompiler. Document your analysis methodology.

**Problem 5.** Write an x86-64 assembly implementation of AES-128 SubBytes using a precomputed S-box table. Then implement a bitsliced version (where 8 bytes are processed in parallel using bitwise operations on 8 registers). Benchmark both implementations.

---

### Tier 3 — Advanced

**Problem 1.** Write a complete x86-64 ELF binary by hand: (a) lay out the ELF header, program header, and section header manually; (b) write a minimal x86-64 program in raw bytes (a program that writes "HELLO" to stdout and exits); (c) verify it executes with `chmod +x && ./binary`. No assembler — only a hex editor and your knowledge of the ELF format.

**Problem 2.** Implement a JIT compiler for a simple stack-based bytecode VM: (a) define a bytecode with 8 instructions (PUSH, POP, ADD, SUB, MUL, DUP, JZ, RET); (b) implement a JIT compiler that translates bytecode to x86-64 machine code at runtime; (c) allocate executable memory with `mmap(PROT_READ|PROT_WRITE|PROT_EXEC)`; (d) emit machine code for each instruction; (e) jump to the compiled code and execute it. Benchmark JIT vs interpreted execution.

**Problem 3.** Implement a hardware performance counter profiler using the `perf_event_open` system call. Measure for a provided program: (a) retired instructions, (b) CPU cycles, (c) L1-dcache misses, (d) branch mispredictions. Display IPC, L1 miss rate, and branch misprediction rate.

---

---

# MODULE 3.3 — Operating Systems: Concepts & Design

**Duration:** 12–14 weeks | **Hours/week:** 12–15 | **Total hours:** ~175

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Arpaci-Dusseau & Arpaci-Dusseau — *Operating Systems: Three Easy Pieces* (OSTEP, free at ostep.org)

OSTEP is the clearest OS textbook ever written. Every chapter ends with questions — do them all.

---

#### Part I — Virtualization

**Chapter 2 — Introduction to Operating Systems**
Read entirely. Focus on: the OS as a resource manager; the three pieces (virtualization, concurrency, persistence); the system call as the API of the OS; the principle of limited direct execution.

**Chapter 4 — The Abstraction: The Process**
Focus on: the process as a running program; the Process Control Block (PCB); process states (running, ready, blocked); the OS process list; what `fork()` does (create a nearly-identical copy); what `exec()` does (replace the current process image with a new program — understand why these are two separate calls). **The `fork`/`exec` model is the basis of all process creation on Unix and is central to understanding privilege escalation via SUID executables.**

**Chapter 5 — Interlude: Process API**
Focus on: `fork()`, `wait()`, `waitpid()`, `exec()` family; the `exit()` and the zombie process; the `orphan` process (init adoption). The `system()` function as a security anti-pattern: it invokes `/bin/sh -c` and is vulnerable to environment variable injection.

**Chapter 6 — Mechanism: Limited Direct Execution**
Focus on: the trap instruction (system call entry); the trap table (kernel's syscall dispatch table); timer interrupt for preemption; the two modes of execution (user mode and kernel mode); context switch. **The trap table is what the IDT (Interrupt Descriptor Table) implements on x86 — connect to the Intel SDM Vol. 3 coverage in Module 3.2.**

**Chapter 7 — Scheduling: Introduction**
Focus on: scheduling metrics (turnaround time, response time); FIFO, SJF, STCF scheduling policies; the convoy effect.

**Chapter 8 — Scheduling: The Multi-Level Feedback Queue**
Focus on: the MLFQ rules; how it approximates SJF without knowing burst time; gaming the scheduler; the Completely Fair Scheduler (CFS) as Linux's current scheduler.

**Chapter 9 — Scheduling: Proportional Share**
Focus on: lottery scheduling; stride scheduling; the CFS's red-black tree runqueue.

**Chapter 13 — The Abstraction: Address Spaces**
Focus on: the address space as the OS's illusion of private memory; code, stack, heap in the address space; the goal of transparency (process doesn't know it's sharing physical memory).

**Chapters 14–15 — Interlude: Memory API / Mechanism: Address Translation**
Focus on: `malloc`/`free` as library calls above `sbrk`/`mmap`; base-and-bounds (historical) hardware address translation; hardware support required for protection.

**Chapter 16 — Segmentation**
Focus on: segmentation as a generalization of base-and-bounds; segments for code, stack, and heap; external fragmentation; why segmentation is largely replaced by paging.

**Chapters 18–22 — Paging**
This section is the most important in the Virtualization part.
- **Ch. 18 — Introduction to Paging:** The page table as an array; virtual-to-physical translation; the page table entry (PTE) structure; valid bit, protection bits, present bit, dirty bit, reference bit.
- **Ch. 19 — Paging: Faster Translations (TLBs):** TLB hit path; TLB miss (hardware vs software walk); TLB management on context switch (ASID vs full flush); TLB reach.
- **Ch. 20 — Paging: Smaller Tables:** Multi-level page tables; the x86-64 4-level page table revisited from the OS perspective; inverted page tables.
- **Ch. 21 — Beyond Physical Memory: Mechanisms:** Swap space; page fault handler; present bit in the PTE; the swap daemon; page replacement policy.
- **Ch. 22 — Beyond Physical Memory: Policies:** OPT, FIFO, LRU, Clock, working set; Belady's anomaly; thrashing.

---

#### Part II — Concurrency

**Chapter 25 — Concurrency: An Introduction**
Focus on: the thread as a lightweight process; thread stack vs process stack; shared address space; why concurrency is hard (non-deterministic interleaving).

**Chapter 26 — Concurrency: Locks**
Focus on: the critical section; the lock as a mutual exclusion primitive; correctness properties (mutual exclusion, progress, bounded waiting); the hardware primitives: test-and-set, compare-and-swap, fetch-and-add. Implement each lock type from its hardware primitive. **The `lock` prefix on x86 provides the atomicity guarantee — connect to Module 3.2.**

**Chapter 28 — Locks: Real Implementations**
Focus on: the problem with spin locks (wasteful on uniprocessors); the two-phase lock (spin briefly, then yield); the futex (Linux's userspace fast mutex) — `FUTEX_WAIT` and `FUTEX_WAKE`. The `pthread_mutex_t` is built on futexes.

**Chapter 29 — Lock-based Concurrent Data Structures**
Focus on: concurrent counter, linked list, queue, and hash table with locks; the granularity of locking (coarse vs fine); lock-free data structures preview.

**Chapter 30 — Condition Variables**
Focus on: the condition variable as a thread synchronization primitive; `wait(cv, lock)` releases the lock and sleeps; `signal(cv)` wakes one waiter; `broadcast(cv)` wakes all; the consumer-producer problem; the Mesa vs Hoare semantics distinction; always use `while` not `if` to check the condition after waking.

**Chapter 31 — Semaphores**
Focus on: the semaphore as a generalized synchronization primitive (counter + wait + post); binary semaphore as a mutex; counting semaphore for resource pools; the reader-writer problem; the dining philosophers problem.

**Chapter 32 — Concurrency Bugs**
Focus on: atomicity bugs (non-atomic operations on shared data); order bugs (wrong assumed ordering between threads); deadlock (Coffman conditions: mutual exclusion, hold-and-wait, no preemption, circular wait); deadlock prevention strategies (lock ordering, trylock with backoff).

**Chapter 33 — Event-Based Concurrency**
Focus on: the event loop model (select, poll, epoll); the blocking call problem; async I/O; why event-driven servers (nginx) outperform thread-per-connection servers (Apache) at high concurrency. **This directly connects to Module 3.5's epoll coverage.**

---

#### Part III — Persistence

**Chapter 36 — I/O Devices**
Focus on: the canonical device interface (status, command, data registers); polling vs interrupt-driven I/O; DMA; the device driver as the OS software layer above hardware.

**Chapter 37 — Hard Disk Drives**
Focus on: disk geometry (platter, track, sector); seek time, rotational latency, transfer time; disk scheduling (SSTF, SCAN, C-SCAN); how these latencies affect file system design.

**Chapter 38 — Redundant Arrays of Inexpensive Disks (RAID)**
Focus on: RAID 0 (striping), RAID 1 (mirroring), RAID 4 (parity), RAID 5 (distributed parity); performance and fault tolerance trade-offs. **RAID levels matter for digital forensics — understanding which drives contain which data.**

**Chapter 39 — Files and Directories**
Focus on: the file as a named sequence of bytes; the directory as a mapping from names to inode numbers; the inode as the file's metadata; hard links vs symbolic links; the pathname resolution algorithm (connect to TOCTOU vulnerabilities from Module 3.1).

**Chapter 40 — File System Implementation**
Focus on: the disk layout of a simple file system (superblock, inode bitmap, data bitmap, inodes, data blocks); the inode structure (type, size, direct/indirect block pointers); path traversal from the root inode; reading and writing files at the block level. **Understanding inode structure is essential for filesystem forensics in Module 4.7.**

**Chapter 41 — Fast File System (FFS)**
Focus on: the cylinder group locality optimization; block groups in ext2/ext3/ext4.

**Chapter 42 — Crash Consistency: FSCK and Journaling**
Focus on: the consistency problem (crash between write operations); fsck (slow, post-hoc repair); journaling (write-ahead log for atomicity); journal modes (writeback, ordered, data). **ext4 journaling is directly relevant to forensic timeline reconstruction.**

**Chapter 43 — Log-Structured File Systems**
Focus on: the LFS design (always append to a log); garbage collection; the imap; why SSDs use LFS-like designs.

**Chapter 44 — Flash-Based SSDs**
Focus on: NAND Flash write granularity (must erase before write); write amplification; the FTL (Flash Translation Layer) as a software layer that presents a block device abstraction; wear leveling; SSD forensics implications (writes may not be overwritten in place). **SSD write behavior complicates forensic data recovery in Module 4.7.**

---

### Supplementary: Silberschatz, Galvin & Gagne — *Operating System Concepts*, 10th ed.
Use for alternative explanations of: Chapter 3 (Processes), Chapter 5 (CPU Scheduling), Chapter 6–7 (Synchronization), Chapter 9 (Virtual Memory). The Silberschatz book has more diagrams and worked examples.

### Supplementary: Tanenbaum — *Modern Operating Systems*, 4th ed.
Use for: Chapter 4 (File Systems — the most thorough treatment), Chapter 5 (I/O), Chapter 9 (Security — an OS-perspective preview of Phase 4).

### Supplementary: Love — *Linux Kernel Development*, 3rd ed.
**Read:** Chapter 1 (Linux Kernel Introduction), Chapter 3 (Process Management — `task_struct`, the process scheduler), Chapter 4 (Process Scheduling — CFS), Chapter 12 (Memory Management — zones, pages, slab allocator), Chapter 13 (Virtual File System), Chapter 15 (The Block I/O Layer), Chapter 16 (Page Cache). This bridges conceptual OS to the actual Linux implementation.

### Supplementary: Kerrisk — *The Linux Programming Interface*
**Read (new chapters for this module):**
- Ch. 20–22: Signals (signal dispositions, `sigaction`, signal masks, `sigsuspend`, real-time signals).
- Ch. 24–26: Process creation and program execution in depth.
- Ch. 30: Threads (POSIX threads introduction).
- Ch. 43–44: Pipes and FIFOs.
- Ch. 49–50: Virtual memory operations (`mmap`, `mprotect`, `mlock`, `msync`).
- Ch. 59–60: Sockets (Unix domain sockets for IPC).

### Supplementary: MIT 6.828 xv6 Book
Read entirely. xv6 is a teaching OS modeled on Unix V6, implemented in ~10,000 lines of C. Every line of code is readable. **You must read and deeply understand xv6 source code for the capstone project.** Focus on: `proc.c` (process management), `vm.c` (virtual memory), `fs.c` (file system), `trap.c` (interrupts and system calls), `spinlock.c` (synchronization).

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Processes and System Calls
- **Day 1:** OSTEP Ch. 2, 4–5. `fork`/`exec`/`wait` API. Write 10 programs using the process API.
- **Day 2:** OSTEP Ch. 6. Limited direct execution. xv6 `trap.c` — trace a system call from userspace to kernel and back.
- **Day 3:** TLPI Ch. 24–26. Process creation deep dive. Trace `execve` from libc through the kernel using `strace`.
- **Day 4:** Write a shell: `fork` + `exec` + `wait`; pipes (`|`); I/O redirection (`<`, `>`, `>>`); background jobs (`&`); signal handling (`SIGINT`, `SIGTSTP`).
- **Day 5:** Problem Set 3.3 Tier 1, problems 1–6.
- **Day 6:** Linux kernel module — write a "Hello, World" character device driver.
- **Day 7:** Rest.

### Week 2 — CPU Scheduling
- **Day 1:** OSTEP Ch. 7–9. Implement: FIFO, SJF, STCF, Round Robin, MLFQ schedulers as simulations.
- **Day 2:** Linux CFS: Love Ch. 4. Read `kernel/sched/fair.c` (key functions only: `enqueue_task_fair`, `dequeue_task_fair`, `pick_next_task_fair`).
- **Day 3:** Scheduler simulation: compare MLFQ vs CFS on a mixed workload of CPU-bound and I/O-bound processes.
- **Day 4:** Problem Set 3.3 Tier 1, problems 7–12.
- **Day 5:** xv6 lab — add a simple lottery scheduler to xv6.
- **Day 6:** Rest.
- **Day 7:** Rest.

### Week 3 — Virtual Memory: Paging and TLB
- **Day 1:** OSTEP Ch. 18–20. Multi-level page tables. Implement a page table walker for x86-64.
- **Day 2:** OSTEP Ch. 21–22. Swap, page fault handler, page replacement. Implement LRU simulation.
- **Day 3:** xv6 `vm.c` — read and annotate every function. Trace a page fault from the trap handler through the page allocator.
- **Day 4:** `mmap` and `mprotect` programming. Implement a user-space page fault handler using `userfaultfd`.
- **Day 5:** Problem Set 3.3 Tier 1, problems 13–18.
- **Day 6:** Linux `proc/PID/maps` and `proc/PID/smaps` analysis — read and interpret for 5 processes.
- **Day 7:** Rest.

### Week 4 — Concurrency: Locks and Condition Variables
- **Day 1:** OSTEP Ch. 25–26. Implement a spinlock from `test-and-set` in C with inline assembly (`__sync_lock_test_and_set`). Verify mutual exclusion with 4 threads.
- **Day 2:** OSTEP Ch. 28. Mutex from futex. Read the `futex(2)` man page. Implement a mutex using `FUTEX_WAIT`/`FUTEX_WAKE`.
- **Day 3:** OSTEP Ch. 30. Condition variables. Implement the producer-consumer bounded buffer. Verify with `helgrind`.
- **Day 4:** OSTEP Ch. 31. Semaphores. Implement the reader-writer problem with semaphores. Implement the dining philosophers with deadlock prevention.
- **Day 5:** Problem Set 3.3 Tier 2, problems 1–5.
- **Day 6:** xv6 lab — read `spinlock.c` and `proc.c` scheduler locking. Add a second processor to the xv6 simulation.
- **Day 7:** Rest.

### Week 5 — Concurrency Bugs and Detection
- **Day 1:** OSTEP Ch. 32. Deadlock analysis. Add ThreadSanitizer (`-fsanitize=thread`) to 5 programs with intentional races.
- **Day 2:** Implement a lock-free stack using `__sync_bool_compare_and_swap`. Verify with ThreadSanitizer.
- **Day 3:** TOCTOU exploitation lab — write a race condition exploit for the `/tmp` symlink pattern from Module 3.1.
- **Day 4:** Problem Set 3.3 Tier 2, problems 6–10.
- **Day 5:** Helgrind deep-dive — run on 3 real concurrent programs; analyze and fix all reported issues.
- **Day 6:** Rest.
- **Day 7:** Rest.

### Week 6 — File Systems
- **Day 1:** OSTEP Ch. 39–40. Inode structure. Trace path resolution for `/usr/bin/ls` from the root inode.
- **Day 2:** OSTEP Ch. 42. Journaling. Trace an ext4 journal commit using `debugfs` and `dmesg`.
- **Day 3:** xv6 `fs.c` — read and annotate. Trace a file creation from the system call through inode allocation to directory entry.
- **Day 4:** FUSE filesystem project — implement an encrypted filesystem using FUSE.
- **Day 5:** Problem Set 3.3 Tier 2, problems 11–15.
- **Day 6:** Forensic lab — use `debugfs` to recover a deleted file from an ext4 image without `fsck`.
- **Day 7:** Rest.

### Weeks 7–9 — OS Security Mechanisms
- **Week 7:** Linux namespaces — implement a container from scratch: `clone(CLONE_NEWPID|CLONE_NEWNET|CLONE_NEWMNT|CLONE_NEWUSER)`, `pivot_root`, `unshare`. No Docker.
- **Week 8:** seccomp-BPF — write a seccomp filter using `libseccomp` that restricts a process to 5 system calls. Verify that blocked calls produce `SIGSYS`.
- **Week 9:** SELinux/AppArmor — write an AppArmor profile for a network service. Verify it blocks file access outside the profile.

### Weeks 10–12 — Kernel Module, xv6 Capstone, and Milestone
- **Week 10:** Kernel module: character device driver with `ioctl` for configuration, `read`/`write` for data transfer, `mmap` to map a kernel buffer into userspace.
- **Weeks 11–12:** xv6 capstone: (a) add a new system call; (b) implement demand paging with copy-on-write fork; (c) add a basic memory-mapped file implementation.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Write a C program that: (a) forks a child; (b) the child executes `/usr/bin/ls -la /etc`; (c) the parent waits for the child; (d) the parent prints the child's exit status; (e) handles the case where `fork()` or `execve()` fail. Trace the system calls using `strace -f`.

**Problem 2.** Explain precisely what happens during a context switch between two processes on Linux x86-64. Your answer must include: the timer interrupt, saving the current process's registers (where?), the scheduler's decision, restoring the next process's registers, and the `iretq` instruction.

**Problem 3.** Implement a bounded-buffer (producer-consumer) using POSIX threads and condition variables. Buffer capacity: 10 items. 3 producer threads, 2 consumer threads. Producers sleep 100ms between productions; consumers process items and sleep 200ms. Verify with ThreadSanitizer that there are no data races.

**Problem 4.** Explain the Coffman conditions for deadlock with a concrete example involving 2 threads and 2 mutexes. Then demonstrate the deadlock in C using pthreads. Fix it using lock ordering.

**Problem 5.** The following code has a TOCTOU vulnerability. Write an exploit program that races the check and the use to create `/etc/passwd` as a symlink target:
```c
if (access(filename, W_OK) == 0)
    fd = open(filename, O_WRONLY);
```
Describe the conditions required for the exploit to succeed and the probability given a single exploit attempt.

**Problem 6.** An ext4 inode has 12 direct block pointers, 1 singly-indirect, 1 doubly-indirect, and 1 triply-indirect pointer. Block size is 4096 bytes; block pointer size is 8 bytes. Calculate: (a) the maximum file size; (b) the number of disk reads required to access byte offset 100,000,000 of a file starting from a cold cache; (c) the number of disk reads for offset 1,000 from a cold cache.

**Problem 7.** Implement a user-space thread library using `clone()` (or `ucontext`) with preemptive scheduling via `SIGALRM`. Support: `thread_create`, `thread_yield`, `thread_exit`, `thread_join`. Demonstrate 3 threads running concurrently.

**Problem 8.** Explain the difference between a hard link and a symbolic link at the inode level. Can you hard-link a directory? Can you hard-link across filesystems? What happens to each type of link when the original file is deleted?

**Problem 9.** Write a seccomp-BPF filter in C (using `prctl(PR_SET_SECCOMP, SECCOMP_MODE_FILTER, ...)`) that allows only: `read`, `write`, `exit`, `exit_group`, and `sigreturn`. Test it by attempting a `fork()` and verifying it produces `SIGSYS`.

**Problem 10.** Implement a mark-and-sweep garbage collector integrated with a simple memory allocator. The GC must: maintain a list of all allocated objects; support registering root pointers; implement `gc_mark(root)` (recursive traversal); implement `gc_sweep()` (free all unmarked objects); demonstrate collection of a cycle that traditional reference counting would not collect.

---

### Tier 2 — Intermediate

**Problem 1.** Implement a complete shell in C supporting: command execution (`fork`/`exec`), pipes (`cmd1 | cmd2 | cmd3`), I/O redirection (`< infile`, `> outfile`, `>> outfile`, `2> errfile`), background execution (`cmd &`), `SIGINT` handling (kill foreground job, not shell), `SIGCHLD` handling (reap zombie children), and built-ins: `cd`, `exit`, `jobs`, `fg`, `bg`.

**Problem 2.** Implement copy-on-write (COW) `fork` in xv6: when a page is marked COW (shared between parent and child), a write to it should trigger a page fault, the fault handler should allocate a new physical page, copy the content, update the PTE, and retry the write.

**Problem 3.** Write a Linux container from scratch using namespaces: (a) create new PID, network, mount, and user namespaces; (b) set up a minimal root filesystem using `pivot_root`; (c) mount `/proc` in the new namespace; (d) exec a shell inside the container. Verify isolation: the container's PID 1 should be the shell; the host network should be invisible.

**Problem 4.** Implement a memory-mapped file (`mmap`-backed) B+ tree that persists to disk. The tree must: use `mmap` to map a file as its storage; support insert, search, and range scan; flush dirty pages using `msync`; survive a crash (reload the file and continue operating correctly).

**Problem 5.** Implement a simple page cache in user space: a hash table mapping (file_id, page_number) → page buffer. Support: `page_get(file, page_num)` (load from file if not cached), `page_put(file, page_num, data)` (write to cache, mark dirty), `page_evict()` (evict the LRU clean page, or flush-and-evict a dirty page). Implement the clock algorithm for eviction.

---

### Tier 3 — Advanced

**Problem 1.** Implement a complete kernel-space character device driver for a virtual "crypto device" that: (a) accepts arbitrary-length data via `write()` and encrypts it with AES-128-ECB using a key set via `ioctl`; (b) returns ciphertext via `read()`; (c) maps a shared memory buffer into userspace via `mmap` (so a userspace client can pass data without copying); (d) is race-condition free under concurrent access from multiple processes.

**Problem 2.** Write a complete `strace`-like tool using `ptrace(PTRACE_SYSCALL)`. It must: attach to a target process, intercept every system call entry and exit, decode the syscall number to a name, print the arguments (for the 10 most common syscalls), and print the return value.

**Problem 3.** (OS Kernel Capstone) Implement a minimal x86-64 kernel that: boots via Multiboot2 (GRUB-compatible), sets up the GDT and IDT, initializes the physical memory map from the Multiboot info structure, implements a simple physical page allocator (buddy or bitmap), enables paging (identity-map the first 1GB and higher-half map the kernel), implements preemptive multitasking (multiple kernel threads scheduled by a round-robin scheduler on timer interrupt), and implements 3 system calls: `write(fd, buf, len)`, `getpid()`, `exit(status)`. Test with a userspace program that creates 3 threads, each printing its PID in a loop.

---

---

# MODULE 3.4 — Concurrent & Parallel Programming

**Duration:** 8–10 weeks | **Hours/week:** 12 | **Total hours:** ~105

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Williams — *C++ Concurrency in Action*, 2nd ed.

The concepts are universal; C++ is the language but the principles map directly to C with pthreads and to the C11 memory model.

---

**Chapter 1 — Hello, World of Concurrency**
Read entirely. Focus on: what concurrency is (multiple activities happening at once); why C++ has concurrency support in the standard (portability); the difference between task switching and genuine parallelism.

**Chapter 2 — Managing Threads**
Focus on: `std::thread` creation; joining vs detaching; passing arguments; transferring thread ownership; thread scope. Equivalent POSIX: `pthread_create`, `pthread_join`, `pthread_detach`.

**Chapter 3 — Sharing Data Between Threads**
Focus on: the data race as undefined behavior (not just a bug — the compiler is allowed to assume no races exist); mutex as the primary protection; lock guard (RAII); unique lock (deferred locking, try-lock); avoiding deadlock (consistent lock ordering, `std::lock` for multiple mutexes simultaneously); avoiding data races on member functions; thread-safe lazy initialization with `std::once_flag`.

**Chapter 4 — Synchronizing Concurrent Operations**
Focus on: condition variables (wait, notify_one, notify_all); spurious wakeup (always use a predicate); futures and promises; `std::async`; packaged tasks. The mental model: condition variable = "notify when condition becomes true"; the mutex protects the condition itself.

**Chapter 5 — The C++ Memory Model and Atomic Operations**
Focus on (critically):
- The memory model: every object has a modification order; all threads observe the same modification order for a single object; the question is what order different threads observe operations on different objects.
- `std::atomic<T>`: operations are atomic (indivisible); each operation has a memory order parameter.
- Memory orders: `memory_order_relaxed` (only atomicity, no ordering guarantees), `memory_order_acquire` (no reads/writes in this thread can be reordered before this load), `memory_order_release` (no reads/writes in this thread can be reordered after this store), `memory_order_acq_rel` (both), `memory_order_seq_cst` (total sequential order — the default and safest).
- The happens-before relation: if A synchronizes-with B, then A happens-before B.
- Acquire-release synchronization: a release store "synchronizes with" an acquire load that reads the stored value — this is how mutexes work.
- **This chapter is prerequisite to writing any correct lock-free code.**

**Chapter 6 — Designing Lock-Based Concurrent Data Structures**
Focus on: thread-safe queue (fine-grained locking: head lock + tail lock); thread-safe map (bucket-level locking vs reader-writer lock).

**Chapter 7 — Designing Lock-Free Concurrent Data Structures**
Focus on: lock-free stack using compare-exchange; the ABA problem (a value changes from A to B back to A — the CAS sees A and incorrectly succeeds); hazard pointers; lock-free queue (Michael-Scott queue). **The ABA problem is subtle and important — understand it deeply.**

**Chapter 8 — Designing Concurrent Code**
Focus on: data parallelism vs task parallelism; parallel accumulate; parallel find; work-stealing thread pools; cache effects on concurrent code (false sharing: two threads accessing different variables on the same cache line cause cache coherence traffic).

---

### Supplementary: Herlihy & Shavit — *The Art of Multiprocessor Programming*, 2nd ed.

**Chapter 1 — Introduction**
Read entirely. Focus on: the correctness properties (safety, liveness); the mutual exclusion problem formalization; the formal definition of a lock.

**Chapter 2 — Mutual Exclusion**
Focus on: Dijkstra's mutual exclusion (uses shared read-write registers); Peterson's algorithm (2-thread mutual exclusion); the Filter lock (n-thread generalization); Bakery algorithm (deadlock-free, fair). **These algorithms work under sequential consistency — modern hardware requires memory barriers to enforce SC.**

**Chapter 3 — Concurrent Objects**
Focus on: linearizability as the correctness condition for concurrent objects; the linearization point of an operation; proving a data structure linearizable.

**Chapter 7 — Spin Locks and Contention**
Focus on: TAS lock, TTAS lock (test-and-test-and-set — reduce cache coherence traffic by reading before writing); backoff (exponential backoff reduces contention); CLH queue lock; MCS queue lock (NUMA-aware).

**Chapter 9 — Linked Lists**
Focus on: the coarse-grained synchronized list; the fine-grained hand-over-hand locking; the optimistic list; the lazy list (logical deletion before physical removal); the lock-free list.

**Chapter 10 — Queues, Stacks, and Deques**
Focus on: the Michael-Scott queue (lock-free FIFO); the elimination-backoff stack.

---

### Supplementary: POSIX Threads API Documentation
Read the man pages for: `pthread_create`, `pthread_join`, `pthread_detach`, `pthread_mutex_init`, `pthread_mutex_lock`, `pthread_mutex_unlock`, `pthread_mutex_trylock`, `pthread_rwlock_*`, `pthread_cond_*`, `pthread_barrier_*`, `pthread_key_*` (thread-local storage).

---

### Supplementary: OpenMP Specification (openmp.org)
Read: Ch. 2 (Directives — `#pragma omp parallel`, `#pragma omp for`, `#pragma omp critical`, `#pragma omp atomic`, `#pragma omp task`).

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Thread Fundamentals and Mutual Exclusion
- Williams Ch. 1–3. Implement: mutex from a spinlock; RAII lock guard in C; Peterson's lock (requires memory barriers — add `__asm__ volatile("mfence")` between the two register writes).
- Verify Peterson's mutual exclusion with 100,000 iterations of a counter increment. Confirm no races with ThreadSanitizer.

### Week 2 — Condition Variables and Synchronization Patterns
- Williams Ch. 4. Producer-consumer, readers-writers (prefer-readers and prefer-writers variants), barrier synchronization.
- Implement: a thread pool using a work queue protected by mutex + condition variable.

### Week 3 — The C Memory Model and Atomics
- Williams Ch. 5. For each memory order, write a minimal example where using a weaker order is correct vs incorrect.
- Implement a lock-free counter with `memory_order_relaxed` and prove it is correct for counting (no ordering required).
- Implement a spinlock using `memory_order_acquire`/`memory_order_release`. Verify equivalent to `seq_cst` spinlock.

### Week 4 — Lock-Free Data Structures
- Williams Ch. 7. Implement: lock-free Treiber stack. Demonstrate the ABA problem with a concrete sequence of operations. Implement hazard pointer protection for safe memory reclamation.
- Implement: Michael-Scott queue (lock-free FIFO). Linearizability argument.

### Week 5 — Parallel Patterns and Work Stealing
- Williams Ch. 8. Implement: parallel reduce, parallel map-filter.
- Work-stealing thread pool: each worker has a local deque; when empty, it steals from the back of a random other worker's deque. Compare throughput to a shared-queue pool.

### Week 6 — OpenMP and MPI Survey
- OpenMP: parallelize matrix multiplication, merge sort, BFS. Measure speedup vs sequential.
- MPI: ring-allreduce on a single machine (multiple processes). Understand distributed memory programming model.

### Week 7 — TOCTOU Exploitation and Concurrent Bugs
- Problem Set 3.4 Tier 2 + TOCTOU exploitation lab.
- Lock-free vs locked data structure benchmark (compare under 1, 2, 4, 8, 16 threads).

### Weeks 8–9 — Projects and Milestone
- Lock-free concurrent hash map project.
- Work-stealing thread pool project.
- TOCTOU exploit project.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Implement a `RWLock` (reader-writer lock) in C using pthreads primitives only (mutex + condition variable + counter). Support: multiple concurrent readers OR one exclusive writer. Demonstrate that: (a) multiple readers can hold the lock simultaneously; (b) a writer blocks until all readers release; (c) readers block when a writer holds the lock.

**Problem 2.** Explain the ABA problem with a concrete 3-step example involving a lock-free stack and `compare_exchange`. Then explain how tagged pointers (using unused high bits of a 64-bit pointer for a version counter) prevent it.

**Problem 3.** The following concurrent counter is incorrect. Identify the race, explain why `counter++` is not atomic on x86-64 (even though it compiles to a single `inc` instruction without the `lock` prefix), and provide three correct implementations: (a) mutex-protected, (b) `__atomic_fetch_add` with `__ATOMIC_SEQ_CST`, (c) `__atomic_fetch_add` with `__ATOMIC_RELAXED` — and justify when (c) is correct.
```c
static int counter = 0;
void *increment(void *arg) {
    for (int i = 0; i < 1000000; i++) counter++;
    return NULL;
}
```

**Problem 4.** Implement Dijkstra's dining philosophers solution using semaphores (one semaphore per chopstick). Demonstrate the deadlock scenario (all philosophers pick up their left chopstick simultaneously). Implement three deadlock-free solutions: (a) asymmetric (one philosopher picks right first), (b) global ordering (always acquire lower-numbered chopstick first), (c) Chandy/Misra (clean/dirty fork protocol).

**Problem 5.** Explain false sharing. Write a benchmark demonstrating it: (a) an array where each thread updates `array[thread_id]`; (b) a padded version where each thread's element is on a separate cache line. Measure the speedup from padding on a multi-core machine.

---

### Tier 2 — Intermediate

**Problem 1.** Implement a lock-free single-producer single-consumer (SPSC) queue using `memory_order_acquire`/`memory_order_release` on the head and tail indices. Prove it is correct using the happens-before relation: show that every item written by the producer is visible to the consumer when the consumer reads the item.

**Problem 2.** Implement a concurrent skip list with `memory_order` annotations that make it linearizable. Your implementation must pass ThreadSanitizer with 8 threads performing concurrent inserts and lookups.

**Problem 3.** Implement a work-stealing thread pool with a per-worker deque (push/pop from back; steal from front). The deque must be lock-free for the owning thread; the steal operation requires a CAS. Benchmark with: (a) a balanced workload; (b) an imbalanced workload where one worker generates all tasks. Measure steal rate and efficiency.

**Problem 4.** Write a TOCTOU exploit for the following setuid program. The program checks if a file is owned by the invoking user before writing to it. Exploit the race between `stat()` and `open()` to write to `/etc/passwd`:
```c
struct stat st;
stat(filename, &st);
if (st.st_uid == getuid())
    open(filename, O_WRONLY | O_TRUNC);
```
Describe the exploit mechanism, implement the race as a concurrent C program, and state the required conditions for success.

---

---

# MODULE 3.5 — Systems Programming: Advanced Topics

**Duration:** 8–10 weeks | **Hours/week:** 12 | **Total hours:** ~105

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Kerrisk — *The Linux Programming Interface* (TLPI)

For this module, read the following chapters for the first time (or in depth):

**Chapter 5 — File I/O: Further Details**
Focus on: `pread`/`pwrite` (atomic seek+read for concurrent file access); `readv`/`writev` (scatter-gather I/O — reading/writing non-contiguous buffers in a single syscall, avoiding multiple copies); `truncate`/`ftruncate`; file holes (sparse files — important for forensics).

**Chapter 17 — ACLs**
Focus on: POSIX ACLs as an extension of the traditional permission model; `getfacl`/`setfacl`; the security implications of ACL misconfiguration.

**Chapter 44 — Pipes and FIFOs**
Focus on: the pipe as a kernel buffer with a read end and write end; `pipe()` and `pipe2()`; `dup2()` for I/O redirection; FIFO (named pipe) as a file in the filesystem; the `PIPE_BUF` atomic write guarantee.

**Chapter 59 — Sockets: Introduction**
Focus on: the socket as a communication endpoint; AF_UNIX (local) vs AF_INET (IPv4) vs AF_INET6 (IPv6); SOCK_STREAM (TCP) vs SOCK_DGRAM (UDP); the socket API: `socket`, `bind`, `listen`, `accept`, `connect`, `send`, `recv`.

**Chapter 60 — Sockets: Server Design**
Focus on: iterative vs concurrent server designs; the `select`/`poll`/`epoll` I/O multiplexing APIs; the `SO_REUSEADDR` and `SO_REUSEPORT` socket options.

**Chapter 62 — Terminals and Pseudoterminals**
Focus on: the pty (pseudo-terminal) architecture — used by SSH, terminal emulators, and container implementations.

**Chapter 63 — Alternative I/O Models**
Focus on (very carefully):
- `select()`: the original I/O multiplexing call; `fd_set` bitmask; O(n) scaling with the number of FDs — **broken for large server workloads**.
- `poll()`: array of `pollfd` structs instead of bitmask; still O(n) for readiness scanning.
- `epoll()`: the Linux-specific, O(1) I/O event notification API: `epoll_create`, `epoll_ctl`, `epoll_wait`; edge-triggered (EPOLLET) vs level-triggered; `epoll_wait` returns only the ready FDs. **This is the API underlying every high-performance network server (nginx, Redis, Node.js, etc.).**
- `io_uring`: the modern Linux async I/O interface: submission queue (SQ) and completion queue (CQ); `io_uring_setup`, `io_uring_enter`; zero-copy via registered buffers; `io_uring_prep_read`, `io_uring_prep_write`, `io_uring_prep_accept`.

**Chapter 49 — Memory Mappings**
Focus on: `mmap()` in full: file-backed mapping vs anonymous mapping; `MAP_SHARED` vs `MAP_PRIVATE`; `mprotect()` for changing permissions; `madvise()` for performance hints (MADV_SEQUENTIAL, MADV_RANDOM, MADV_DONTNEED); `mlock()`/`mlockall()` for preventing swap (used in security-sensitive code that must not swap secrets to disk); `MAP_POPULATE` for pre-faulting; `msync()` for flushing dirty pages.

**Chapter 51 — POSIX Shared Memory**
Focus on: `shm_open`/`shm_unlink` as the POSIX interface; combining with `mmap` for IPC; the shared memory region as a race condition surface.

---

### Primary Text: Gregg — *Systems Performance*, 2nd ed.

**Chapter 1 — Introduction**
Read entirely. Focus on: the systems performance methodology; USE (Utilization, Saturation, Errors) method; the observer effect.

**Chapter 2 — Methodologies**
Read §2.1–2.5. Focus on: workload characterization; latency analysis; the 60-second Linux performance checklist (`uptime`, `dmesg`, `vmstat`, `mpstat`, `pidstat`, `iostat`, `free`, `sar`, `top`).

**Chapter 6 — CPUs**
Read §6.1–6.4. Focus on: CPU profiling methodology; the `perf` tool for sampling; on-CPU vs off-CPU time; profiling with `perf record -g`; flame graphs.

**Chapter 7 — Memory**
Read §7.1–7.4. Focus on: page faults (minor vs major); swap-in rate as a saturation signal; the `/proc/meminfo` fields; memory profiling with Valgrind and heaptrack.

**Chapter 10 — Network**
Read §10.1–10.4. Focus on: socket buffer utilization; TCP retransmits; network stack saturation; `ss -s` statistics.

---

### Primary Text: Gregg — *BPF Performance Tools* (Addison-Wesley)

**Chapter 1 — Introduction**
Read entirely. Focus on: eBPF as a kernel-safe virtual machine; the BPF verifier; map types (hash, array, perf event, ring buffer); helper functions; tracing vs networking eBPF.

**Chapter 2 — Technology Background**
Focus on: kprobe/kretprobe (kernel function entry/exit tracing); uprobe/uretprobe (user-space function entry/exit); USDT (User Statically Defined Tracing — `bpf_usdt_enabled`); tracepoints (stable kernel trace events); perf events.

**Chapter 3 — Performance Analysis**
Focus on: the `bpftrace` scripting language for one-liners; `libbpf` for C eBPF programs.

---

### Supplementary: io_uring Documentation
Read: `liburing` README and examples (github.com/axboe/liburing); the io_uring.pdf by Jens Axboe; the io_uring man pages (`io_uring_setup(2)`, `io_uring_enter(2)`, `io_uring_register(2)`).

---

## Part B: Week-by-Week Study Schedule

### Week 1 — Advanced File I/O and Scatter-Gather
- TLPI Ch. 5, 44. Implement `sendfile`-based file server; `readv`/`writev` for multi-buffer I/O.
- Benchmark: single `write()` vs `writev()` vs `sendfile()` for serving a 10MB file. Plot throughput.

### Week 2 — Epoll and High-Performance I/O
- TLPI Ch. 63 (epoll). Implement an echo server using epoll. Benchmark with `wrk` or `ab` at 1000, 5000, 10000 concurrent connections.
- Edge-triggered vs level-triggered epoll: implement both and demonstrate the behavior difference.

### Week 3 — io_uring
- io_uring documentation. Implement: file copy using io_uring; echo server using io_uring; zero-copy read using registered buffers.
- Benchmark io_uring vs epoll for: small packets (latency) and large file transfers (throughput).

### Week 4 — Memory Mapping and IPC
- TLPI Ch. 49–51. Implement: a shared memory ring buffer for IPC between two processes; a memory-mapped log file that survives process crash.
- `mlock` — lock sensitive key material in memory to prevent swapping. Verify with `/proc/PID/smaps` that the region is locked.

### Week 5 — eBPF: Observability and Security
- Gregg BPF Ch. 1–3. Write bpftrace one-liners for: syscall frequency, network connection tracking, file open tracing.
- Write a libbpf program that: attaches to `sys_enter_openat`; logs every file opened by a target process; generates an alert if `/etc/shadow` is opened.
- Write a seccomp-BPF program using raw BPF instructions (not libseccomp): allow `read`, `write`, `exit`; kill the process on any other syscall.

### Week 6 — Performance Profiling
- Gregg Systems Performance Ch. 6. Profile 3 programs with `perf record -g -F 99` and generate flame graphs.
- Identify and fix a performance bottleneck in your Module 1.2 sorting library.

### Week 7 — Network Server Project
- Build a production-quality HTTP/1.1 server using epoll: concurrent connections, keep-alive, chunked transfer encoding, partial content (Range requests), and proper connection timeouts. Load test with `wrk`.

### Weeks 8–9 — eBPF Security Project and Milestone
- Build an eBPF network monitor that logs all outbound connections (syscalls: `connect`, `sendto`) with source PID, destination IP/port, and process name. Output in JSON.
- Build a seccomp-BPF sandbox for an untrusted subprocess.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Explain the difference between `read()` + `write()`, `mmap()` + `memcpy()`, and `sendfile()` for transferring file data over a socket. How many times does the data cross the kernel/userspace boundary in each case? Which is fastest for large files and why?

**Problem 2.** Implement an echo server that supports 10,000 concurrent connections using `epoll`. Measure: (a) maximum throughput (messages/second) at 1000, 5000, 10000 clients; (b) 99th percentile latency; (c) CPU utilization. Compare to a `select()`-based implementation.

**Problem 3.** Write a bpftrace script that, for every `execve()` system call, prints: the PID, the command name, the arguments (up to 4), and the parent PID. Test by running `ls`, `find /tmp`, and a shell script.

**Problem 4.** Explain why `mlock()` is used in cryptographic libraries (e.g., libsodium, OpenSSL). What attack does it prevent? What is the limitation of `mlock()` on most Linux systems (ulimit)? How does a security-critical daemon (e.g., a password manager) use `mlock()` and `madvise(MADV_DONTDUMP)` together to protect secret material?

**Problem 5.** Implement an io_uring-based file copier that: reads from source using `io_uring_prep_read` into a registered buffer; writes to destination using `io_uring_prep_write` from the same buffer; pipelines reads and writes (while writing block N, reads block N+1). Compare throughput to `sendfile()` for a 1GB file.

---

---

# MODULE 3.6 — C++ for Systems Programming

**Duration:** 8–10 weeks | **Hours/week:** 12 | **Total hours:** ~100

---

## Part A: Chapter-by-Chapter Reading List

### Primary Text: Meyers — *Effective Modern C++* (O'Reilly)

---

**Item 1 — Understand Template Type Deduction**
Focus on: the three cases (pointer/reference, universal reference, pass by value); array and function argument special cases. Template type deduction is the foundation of `auto` and generic programming.

**Item 2 — Understand `auto` Type Deduction**
Focus on: `auto` follows template type deduction rules with one exception (`std::initializer_list`); why `auto` is safer than explicit type declarations (eliminates implicit conversion bugs).

**Item 5 — Prefer `auto` to Explicit Type Declarations**
Focus on: type portability; avoiding silent truncation (declaring `int` where `size_t` is returned).

**Item 7 — Distinguish Between `()` and `{}` When Creating Objects**
Focus on: uniform initialization; narrowing conversions are ill-formed with `{}`; the most vexing parse.

**Item 8 — Prefer `nullptr` to `0` and `NULL`**
Focus on: the type of `nullptr` (`std::nullptr_t`); why `NULL` causes overload resolution ambiguity.

**Item 11 — Prefer Deleted Functions to Private Undefined Ones**
Focus on: preventing unintended copying by deleting copy constructor and copy assignment.

**Items 12–15 — Override, `const`, and `constexpr`**
Focus on: `override` keyword (catches silent virtual function hiding); `const` member functions and the bitwise vs logical constness distinction; `constexpr` for compile-time computation; `consteval` (C++20) for functions that must be evaluated at compile time.

**Items 16–17 — `const` Member Functions and Special Member Functions**
Focus on: the rule of 0/3/5; when the compiler synthesizes vs suppresses special member functions.

**Items 18–22 — Smart Pointers**
Focus on (most important section in the book for systems programming):
- `unique_ptr`: exclusive ownership; zero overhead; custom deleters; `make_unique`.
- `shared_ptr`: reference-counted shared ownership; the control block; `make_shared` vs `new`; the weak_ptr to break cycles; performance overhead of atomic reference count.
- `weak_ptr`: non-owning reference to `shared_ptr`-managed object; `lock()` to upgrade to `shared_ptr`.
- **Never use raw `new`/`delete` in new C++ code.** The smart pointer is the RAII wrapper that eliminates the double-free and use-after-free bugs endemic to C.

**Items 23–30 — Move Semantics and Perfect Forwarding**
Focus on:
- lvalue vs rvalue distinction; rvalue references (`&&`); `std::move` as an unconditional cast to rvalue; `std::forward` as a conditional cast.
- Move semantics: moving (transferring ownership) vs copying (duplicating content); the move constructor and move assignment operator; how `std::vector` uses move semantics when reallocating.
- Perfect forwarding: forwarding references; `std::forward`; variadic templates.
- **Move semantics eliminate unnecessary copies in security-critical code (e.g., moving a key buffer rather than copying it).**

**Items 31–34 — Lambda Expressions**
Focus on: capture by value vs by reference; the dangers of capturing a reference to a local variable that outlives the lambda; `mutable` lambdas; generic lambdas (C++14); `std::function` overhead vs template + lambda; IIFE (immediately invoked function expression) pattern.

**Items 35–40 — Concurrency**
Focus on: `std::thread`, `std::async`; the C++ memory model (equivalent to Williams Ch. 5); `std::atomic` with all memory orders; the difference between `std::mutex` and `std::shared_mutex`; `std::condition_variable`.

**Items 41–42 — Performance**
Focus on: when to use `reserve()` on `std::vector`; pass by value vs pass by const ref for small types; `emplace_back` vs `push_back`; avoiding unnecessary copying in return values (NRVO — Named Return Value Optimization).

---

### Primary Text: Meyers — *Effective C++*, 3rd ed.

**Item 1 — View C++ as a Federation of Languages**
Read to understand the C++/C interop model — essential for writing kernel modules and FFI.

**Item 13–17 — Resource Management**
Focus on: RAII; use objects to manage resources (the fundamental C++ safety principle); the copy constructor and copy assignment operator; the prohibition on copying resource-managing objects unless you implement them correctly.

**Item 25 — Consider Support for a Non-Throwing Swap**
Focus on: the swap idiom; specializing `std::swap` for performance.

**Items 26–30 — Templates and Generic Programming**
Focus on: implicit interfaces vs explicit interfaces; the cost of code bloat from templates; type traits; `enable_if` (SFINAE).

---

### Primary Text: Stroustrup — *The C++ Programming Language*, 4th ed. (selected chapters)

**Chapter 13 — Exception Handling**
Focus on: the exception safety guarantees (basic, strong, nothrow); exception-safe programming; RAII as the mechanism that makes exception safety tractable; `noexcept`.

**Chapter 34 — Memory and Resources**
Focus on: custom allocators; placement new; aligned storage; memory pools in C++; operator new/delete overloading.

**Chapter 35 — Utilities**
Focus on: `std::variant` for type-safe unions; `std::optional` for nullable values (eliminates null pointer bugs); `std::span` (C++20) for non-owning contiguous range views; `std::string_view` for non-owning string references.

---

### Supplementary: ISO C++20 Standard (draft)
Read: Concepts (§13), Ranges (§25), Coroutines (§9). Understand the concepts feature — it replaces `enable_if` with human-readable constraints.

---

## Part B: Week-by-Week Study Schedule

### Weeks 1–2 — Type System, RAII, and Smart Pointers
- Effective Modern C++ Items 1–22. Rewrite your Module 3.1 memory allocator project in C++ using RAII and `unique_ptr`.
- Rule of 5 exercise: implement a `Buffer` class that owns a heap-allocated array; implement all 5 special member functions correctly.

### Weeks 3–4 — Move Semantics and Templates
- Effective Modern C++ Items 23–34. Implement: a move-only `File` wrapper, a perfect-forwarding `make_unique` implementation, a generic `ThreadSafeQueue<T>`.
- Template metaprogramming: implement `TypeList`, `IndexOf`, `TypeAt` using recursive templates.

### Weeks 5–6 — Concurrency in C++
- Effective Modern C++ Items 35–40. Port Module 3.4 projects to C++: `std::atomic` lock-free counter, `std::shared_mutex` reader-writer lock, `std::condition_variable` producer-consumer.
- Implement an `Executor` class: a thread pool with `submit(Callable)` that returns a `std::future`.

### Weeks 7–8 — Advanced Topics and Security Pitfalls
- C++ security pitfalls: iterator invalidation (dangling iterators after `push_back`); dangling references (returning a reference to a local variable); object slicing; exception safety failures.
- Implement: a policy-based `SecureBuffer<Policy>` where policies control: erasure-on-destruction (`ErasePolicy`), bounds-checking (`CheckedPolicy`), and alignment (`AlignedPolicy`).

### Weeks 9–10 — Projects and Milestone
- Rewrite your Module 3.5 epoll HTTP server in C++ using RAII, `unique_ptr`, `std::variant` for request state, and `std::optional` for nullable results.
- Milestone assessment.

---

## Part C: Graded Problem Sets

### Tier 1 — Foundational

**Problem 1.** Implement a `UniquePtr<T>` class template (a simplified `std::unique_ptr`) with: constructor from raw pointer, destructor (calls `delete`), move constructor and move assignment, deleted copy constructor and copy assignment, `get()`, `release()`, `reset()`, and `operator*`/`operator->`. Write 15 unit tests.

**Problem 2.** The following C++ code has a resource leak. Identify it and rewrite using RAII:
```cpp
void process(const std::string &path) {
    FILE *f = fopen(path.c_str(), "r");
    auto data = parse_file(f);  // may throw
    fclose(f);
    use(data);
}
```

**Problem 3.** Explain the difference between a strong exception guarantee and a basic exception guarantee. Implement `Container::push_back(T val)` with the strong exception guarantee.

**Problem 4.** Implement a `variant<int, std::string, double>` using a union and a tag (without `std::variant`). Support: construction from each type, type-safe access (throw on wrong type), `visit(f)` with a visitor. Write 10 unit tests.

**Problem 5.** Explain why the following code is undefined behavior and how to fix it:
```cpp
std::string &get_greeting() {
    std::string s = "Hello, World!";
    return s;  // dangling reference
}
```

**Problem 6.** Implement a `ThreadPool` class using C++17: `std::thread`, `std::mutex`, `std::condition_variable`, and `std::function<void()>`. Support `submit(f)` returning `std::future<decltype(f())>`. Submit 100 tasks and verify all complete.

**Problem 7.** Explain iterator invalidation rules for `std::vector`, `std::list`, `std::unordered_map`, and `std::map`. Write a program that demonstrates iterator invalidation for `std::vector` after `push_back`. Explain the security implication if an attacker can trigger a vector reallocation between obtaining an iterator and using it.

---

## Phase 3 — Global Capstone Projects

Complete all three before beginning Phase 4.

---

### Capstone 3-A: Complete Shell

Implement a full POSIX-compliant shell in C:
- Command execution: `fork`/`exec`/`wait`, `$PATH` search
- Pipes: `cmd1 | cmd2 | cmd3` (arbitrary depth)
- I/O redirection: `<`, `>`, `>>`, `2>`, `2>&1`, `&>`
- Here-documents: `cmd << EOF`
- Background jobs: `cmd &`, `jobs`, `fg`, `bg`
- Signal handling: `SIGINT` (kill foreground), `SIGTSTP` (stop foreground), `SIGCHLD` (reap zombies)
- Builtins: `cd`, `pwd`, `exit`, `export`, `unset`, `echo`, `type`, `source`, `alias`
- Job control: process groups, terminal control (`tcsetpgrp`)
- History: 500-entry command history, `!!`, `!n`, `!prefix`
- Tab completion: file and command name completion using `readline` or your own implementation
- Security: prevent shell injection in argument handling; safe `PATH` handling

Deliverables: source code, man page, 50-test automated test suite.

---

### Capstone 3-B: Systems Monitoring Agent

Build a production-quality Linux system monitoring agent in C/C++ using eBPF:
- **Process monitor:** track all process creation/exit events with PID, PPID, command, arguments, and user. Detect processes spawned from unusual parents (shell spawned from web server = potential RCE).
- **Network monitor:** track all outbound TCP connections with source PID, destination IP/port. Flag connections to unusual destinations.
- **File monitor:** track all `open()` calls on sensitive files (`/etc/shadow`, `/etc/sudoers`, `/root/*`, `~/.ssh/*`). Alert on access from unexpected processes.
- **System call anomaly detector:** build a per-process syscall frequency baseline; alert when a process's syscall pattern deviates significantly from its baseline (potential shellcode detection).
- **Output:** structured JSON log with timestamps; configurable alert thresholds; a summary dashboard printed to stdout every 30 seconds.

Technology: libbpf (C), ring buffer maps for event streaming, perf_event maps for counters.

---

### Capstone 3-C: Mini OS Kernel

Implement a minimal but functional x86-64 OS kernel (extending the Module 3.3 Tier 3 Problem 3 or the xv6 codebase):
- **Boot:** Multiboot2 or UEFI stub; x86-64 long mode; higher-half kernel mapping
- **Memory:** physical allocator (buddy system); virtual memory with 4-level paging; `mmap`/`munmap` system calls; copy-on-write `fork`
- **Processes:** `fork`, `exec` (loading a flat binary), `wait`, `exit`; preemptive round-robin scheduler on PIT or LAPIC timer
- **System calls:** at minimum: `read`, `write`, `open`, `close`, `fork`, `exec`, `wait`, `exit`, `getpid`, `mmap`
- **File system:** read-only ext2 driver sufficient; or implement a simple in-memory filesystem
- **Shell:** a minimal shell binary that runs in user space and exercises all system calls
- **Security:** proper privilege separation (ring 0 kernel / ring 3 user); SMEP enforcement; non-executable user stack (NX bit in page tables)

Deliverables: kernel source (C + NASM), build system (Makefile), QEMU-bootable disk image, automated test suite, 5-page design document.

---

*End of Phase 3 Complete Study Package*
*Next: Phase 4 — Advanced Cybersecurity Specialization*

# Synchronization_Lock

This repository contains a collection of educational projects and simulators for exploring thread synchronization, locking mechanisms, condition variables, and deadlock avoidance in concurrent programming. The code is organized into several subdirectories, each focusing on a different aspect of synchronization and threading.

## Contents

### 1. Thread_Lock

Simulates thread interleaving and lock mechanisms using a custom x86-like assembly interpreter (`x86.py`). Includes example assembly files for various locking algorithms:

- `flag.s`, `peterson.s`, `test-and-set.s`, `test-and-test-and-set.s`, `ticket.s`, `yield.s`: Assembly examples for different synchronization algorithms.
- `x86.py`: Python simulator for running and visualizing thread interleaving and lock behavior.
- `README-locks`: Documentation for the simulator and assembly syntax.

#### Usage Example

```bash
python x86.py -p flag.s -t 2 -M flag -R ax,bx -c
```

### 2. Condition_Variable

Explore real C code using locks and condition variables to solve the producer/consumer problem. Multiple variants demonstrate correct and incorrect approaches:

- `main-one-cv-while.c`: Single condition variable.
- `main-two-cvs-if.c`: Two condition variables, using `if`.
- `main-two-cvs-while.c`: Two condition variables, using `while` (correct version).
- `main-two-cvs-while-extra-unlock.c`: Extra unlock/relock around fill/get routines.
- `main-common.c`, `main-header.h`, `pc-header.h`, `mythreads.h`: Shared code and headers.
- `Makefile`: Build all variants.

#### Usage Example

```bash
make
./main-two-cvs-while -p 2 -c 2 -m 5 -l 10 -v
```

### 3. Thread_bugs

Demonstrates deadlock scenarios and solutions in vector operations:

- `vector-deadlock.c`: Shows how deadlock can occur.
- `vector-global-order.c`: Avoids deadlock by enforcing a global lock order.
- `vector-avoid-hold-and-wait.c`, `vector-try-wait.c`, `vector-nolock.c`: Other concurrency strategies.
- `main-common.c`, `main-header.h`, `vector-header.h`, `mythreads.h`: Shared code and headers.
- `Makefile`: Build all variants.

#### Usage Example

```bash
make
./vector-global-order -t -n 4 -l 100000 -d -p
```

## Building

Each subproject contains a `Makefile` for building the C programs. Navigate to the desired subdirectory and run:

```bash
make
```

## Running

Refer to the individual README files in each subdirectory for specific usage instructions and command-line options. Most programs support flags for thread count, buffer size, loop count, and verbose/timing output.

## Educational Goals

- Visualize and understand thread interleaving and synchronization.
- Experiment with lock algorithms and condition variables.
- Observe and resolve deadlock scenarios.
- Learn best practices for concurrent programming.

## License

This repository is for educational use.
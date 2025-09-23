# Divide-and-Conquer Algorithms in Java

This repository implements and evaluates several classical divide-and-conquer algorithms with extra metrics collection.

## Implemented algorithms
- **MergeSort**: standard recursive mergesort, uses one reusable buffer and switches to insertion sort for very small arrays.
- **QuickSort**: randomized pivot, always recurse into the smaller partition and iterate over the larger one to keep stack depth small.
- **Deterministic Select**: median-of-medians with groups of 5, in-place partitioning, only one recursive side.
- **Closest Pair of Points (2D)**: sort by x, recursive split, merge step checks at most 7 neighbours in the strip.

## Metrics collected
- Number of comparisons
- Number of moves (assignments/swaps)
- Number of allocations
- Maximum recursion depth

## Recurrence analysis
- MergeSort: `T(n) = 2T(n/2) + Θ(n)` → `Θ(n log n)` (Master theorem, case 2).
- QuickSort: expected `Θ(n log n)` with random pivots, depth bounded by `O(log n)` with smaller-first recursion.
- Select (median-of-medians): `T(n) ≤ T(n/5) + T(7n/10) + Θ(n)` → `Θ(n)` by Akra–Bazzi intuition.
- Closest Pair: `T(n) = 2T(n/2) + Θ(n)` → `Θ(n log n)`.

## How to run
```bash
mvn test             # run all tests
mvn package
java -jar target/dnc-algos-java-1.0-SNAPSHOT.jar all 100000 10000

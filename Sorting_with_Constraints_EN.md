---
title: Choosing Sorting Algorithms with Constraints
weight: 3
authors:
- [Dmitriy Popovich]
created: 2024
---

When solving algorithmic problems, we often face situations where simply sorting data is not enough - we need to consider additional constraints on execution time, memory, or other resources. In such cases, the key skill becomes choosing the optimal sorting algorithm that accounts for all given constraints.

## Trade-offs of Sorting Algorithms

Major sorting algorithms can be classified by their time and space complexity:

| Algorithm | Time (comparisons) | Memory | Key Characteristics |
|-----------|-------------------|---------|---------------------|
| **QuickSort** | $O(n \log n)$ | $O(\log n)$ | Fast on average, but $O(n^2)$ worst-case |
| **MergeSort** | $O(n \log n)$ | $O(n)$ | Stable, predictable time |
| **HeapSort** | $O(n \log n)$ | $O(1)$ | In-place, guaranteed complexity |
| **Counting Sort** | $O(n + k)$ | $O(k)$ | Linear time when $k$ is small |
| **Radix Sort** | $O(d \cdot (n + b))$ | $O(n + b)$ | Linear time for integers |
| **Insertion Sort** | $O(n^2)$ | $O(1)$ | Efficient for small $n$ |

where:
- $n$ — number of elements
- $k$ — value range (max - min + 1)
- $d$ — number of digits
- $b$ — base of the numeral system

## Algorithm Selection Criteria

### When to Use Counting Sort
**Conditions:**
- Value range $k$ is small: $k \leq \text{maxMemory} / 2$
- Strict constraints on comparisons
- Sufficient memory available: $n + k \leq \text{maxMemory}$

**Advantage:** Minimal comparison count - practically zero.

### When to Use Radix Sort
**Conditions:**
- Data consists of integers or strings
- Moderate memory constraints: $2n \leq \text{maxMemory}$
- Predictable execution time desired

**Characteristic:** Number of passes depends on digit count.

### When to Use HeapSort
**Conditions:**
- Strict memory constraints: $\text{maxMemory} \leq 50$
- Large data volumes
- Guaranteed $O(n \log n)$ time needed

**Advantage:** Works in-place, requires no additional memory.

### When to Use Insertion Sort
**Conditions:**
- Very strict memory constraints: $\text{maxMemory} \leq 10$
- Small number of elements: $n \leq 1000$
- Relaxed constraints on comparisons

**Application:** Edge cases with minimal available memory.

## Constraint Analysis

Given three parameters:
- $\text{maxValue}$ — maximum element value
- $\text{maxCount}$ — maximum comparison count
- $\text{maxMemory}$ — maximum additional memory

### Selection Algorithm

1. **Check Counting Sort:**
   $$
   k = \text{maxValue} - \min(\text{nums}) + 1
   $$
   If $k \leq \text{maxMemory}/2$ and $k \leq 200000$ → use Counting Sort

2. **Check Radix Sort:**
   If $2n \leq \text{maxMemory}$ → use Radix Sort

3. **Check Merge Sort:**
   If $\text{maxMemory} \geq n$ → use Merge Sort

4. **Choose between HeapSort and Insertion Sort:**
   - If $n \leq 1000$ or $\text{maxCount} \geq n^2$ → Insertion Sort
   - Otherwise → HeapSort

## Practical Rule of Thumb

For safe sorting with unknown data characteristics:

- With $O(n)$ memory available — **MergeSort** (stable, predictable)
- With limited memory — **HeapSort** (guaranteed complexity)
- With known small value range — **Counting Sort** (linear time)
- Working with integers — **Radix Sort** (linear time)

## Bonus: "Adaptive Sorting"

In practice, you can implement a hybrid approach that analyzes input data and constraints at runtime, automatically selecting the optimal algorithm. This approach is particularly useful in systems where input characteristics may vary significantly.

# Accelerating Computation with Multi-Threading

This project is a hands-on exploration of speeding up programs by using multiple CPU cores. Two basic applications (computing a mean and computing a volume) are implemented in both serial and multi-threaded versions. The goal is to compare performance and show how “throwing more hardware at it” can dramatically improve computation times when workloads are parallelizable.

---

## Speedup Analysis

To evaluate the performance gains from multi-threading, we calculate the speedup achieved at each thread count using the formula:

### $\text{speedup} = \frac{\text{single-thread running time}}{\text{multi-threaded running time}}$

---

## Computing a Mean

![Speedup Graph (Mean)](/mean.png)

### Shape of the curve

-	The speedup increases quickly at first as you add more threads.
-	Around 40 threads, the curve starts to flatten, meaning adding more threads gives diminishing returns.
-	Beyond 50 threads, the speedup essentially converges around 20x.

### Maximum speedup

- Maximum recorded speedup is approcimately 21.18x at 52 threads.

### Effect of using more cores than available

- Less than linear performance
- Speedup times may slightly decrease



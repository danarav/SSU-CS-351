**1. Which program is fastest? Is it always the fastest?**

The results show that malloc.out had the fastest overall runtime in this test, performing slightly better than alloca.out, while list.out and new.out were noticeably slower. The faster performance of malloc.out is due to its use of efficient, low-level heap memory allocation with minimal overhead. In contrast, list.out relies on the C++ Standard Library’s std::list, which adds additional management overhead, and new.out includes constructor handling that also slows performance.

**2. Which program is slowest? Is it always the slowest?**

From the test results, list.out was the slowest program, taking about 0.027 seconds to complete the task with 10,000 nodes. This slower performance is expected because list.out uses the C++ Standard Library’s std::list container, which adds extra overhead for managing nodes, iterators, and dynamic memory allocation behind the scenes. Each node allocation in std::list involves additional bookkeeping compared to the direct use of malloc or alloca.

**3. Was there a trend in program execution time based on the size of data in each Node? If so, what, and why?**

As Node data size increases, execution time increases across all programs.
The effect is most pronounced in heap-based allocations (malloc, new, std::list) due to memory fragmentation and cache inefficiency.
Stack-based allocation (alloca) remains fast for small Nodes but fails for large ones due to limited stack space.
Overall, smaller Node sizes yield faster performance because they reduce memory allocation overhead and improve cache locality.

**4. Was there a trend in program execution time based on the length of the block chain?**

Execution time increases roughly linearly with the length of the blockchain. malloc.cpp is fastest due to low-overhead heap allocation, new.cpp and list.cpp are slightly slower, and alloca.cpp is limited by stack size and recursion overhead, crashing for very large lists. Choice of memory allocation strongly impacts performance.

**5. Consider heap breaks, what's noticeable? Does increasing the stack size affect the heap? Speculate on any similarities and differences in programs?**

Heap usage grows noticeably in programs that allocate nodes on the heap (malloc.cpp, new.cpp, list.cpp), roughly proportional to the number of nodes, while alloca.cpp uses almost no heap. Increasing stack size doesn’t affect heap directly but allows stack-based programs to handle larger lists without crashing. Overall, heap-based programs grow linearly with list size, whereas stack-based allocation is limited by recursion depth.

**6. Considering either the malloc.cpp or alloca.cpp versions of the program, generate a diagram showing two Nodes. Include in the diagram
the relationship of the head, tail, and Node next pointers.
show the size (in bytes) and structure of a Node that allocated six bytes of data
include the bytes pointer, and indicate using an arrow which byte in the allocated memory it points to**.

<img width="1024" height="1024" alt="97F8738C-7F62-478C-8FB1-0E0D1FF46BB9" src="https://github.com/user-attachments/assets/49a26d41-195a-45c2-bfa3-e8c064839af3" />

**7. There's an overhead to allocating memory, initializing it, and eventually processing (in our case, hashing it). For each program, were any of these tasks the same? Which one(s) were different?**

All programs perform the same hashing on node data, so the processing step is consistent. The differences lie in memory allocation and initialization: malloc.out is fastest with low-overhead heap allocation, new.out adds constructor overhead, list.out has extra std::list bookkeeping, and alloca.out is fast for small nodes but limited by stack space.

**8. As the size of data in a Node increases, does the significance of allocating the node increase or decrease?**

The significance of allocation increases as Node size grows. Larger Nodes require more memory, which amplifies allocation overhead, memory fragmentation, and cache inefficiency—especially for heap-based allocations—making allocation a more dominant factor in execution time.



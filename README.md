# caching
*CPU caching*

Understanding how the hardware works is a critical component to understanding how to write the most performant code you can. Knowing the basics of processor caching can help you make better decisions within the scope of writing idiomatic code.

# CPU Cache Notes
- CPU caches works by caching main memory on cache lines.

- Cache lines today are either 32 or 64 bytes wide depending on the hardware.

- Cores do not access main memory directly. They tend to only have access their local caches.

- Both data and instructions are stored in the caches.

- Cache lines are shuffled down L1->L2->L3 as new cache lines need to be stored in the caches.

- Hardware likes to traverse data and instructions linearly along cache lines.

- Main memory is built on relatively fast cheap memory. Caches are built on very fast expensive memory.

- Access to main memory is incredibly slow, we need the cache.
    - Accessing one byte from main memory will cause an entire cache line to be read and cached.
    - Writes to one byte in a cache line requires the entire cache line to be written.
    
- Small = Fast
    - Compact, well localized code that fits in cache is fastest.
    - Compact data structures that fit in cache are fastest.
    - Traversals touching only cached data is the fastest.

- Predictable access patterns matter.
    - Whenever it is practical, you want to employ a linear array traversal.
    - Provide regular patterns of memory access.
    - Hardware can make better predictions about required memory.

- Cache misses can result in TLB cache misses as well.
    - Cache of translations of a virtual address to a physical address.
    - Waiting on the OS to tell us where the memory is.

All material is licensed under the Apache License Version 2.0, January 2004
http://www.apache.org/licenses/LICENSE-2.0
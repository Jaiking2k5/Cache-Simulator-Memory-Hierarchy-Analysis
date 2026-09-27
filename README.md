# Cache Simulator & Memory Hierarchy Analysis

A C++ based cache simulator designed to model fundamental cache-memory
behavior and study the effect of cache organization on memory-access
performance.

## Overview

Cache memory is a small and fast memory placed between the processor
and main memory. Its performance depends on parameters such as cache
capacity, cache-line size, associativity, and the pattern of memory
accesses.

This project implements a lightweight cache simulator to demonstrate
these concepts through configurable memory-access traces.

## Features

- Configurable cache capacity
- Configurable cache-line/block size
- Direct-mapped and set-associative cache organization
- Memory address decomposition into:
  - Tag
  - Set index
  - Block offset
- Cache hit/miss detection
- LRU (Least Recently Used) replacement
- Hit-rate and miss-rate calculation
- Support for custom memory-access traces
- Comparison of different cache configurations

## Cache Organization

For a byte-addressed memory system, a memory address can be divided
into three fields:

```text
+----------------------+----------------+----------------+
|         Tag          |   Set Index    | Block Offset   |
+----------------------+----------------+----------------+

Block Offset

Identifies the byte within a cache line.

Set Index

Identifies the cache set in which the corresponding memory block
may be stored.

Tag

Identifies which memory block is currently stored in the selected set.

Cache Parameters

The simulator allows the following parameters to be configured:

Total cache size
Cache-line size
Associativity

For example:

Cache Size   : 1024 bytes
Line Size    : 16 bytes
Associativity: 2-way

The number of cache lines is:

Number of Lines = Cache Size / Line Size

and the number of sets is:

Number of Sets = Number of Lines / Associativity
Cache Access

For every memory address:

The address is divided into tag, set index, and block offset.
The corresponding cache set is selected.
The tag is compared with valid cache entries.
If a matching tag is found, the access is a cache hit.
Otherwise, the access is a cache miss.
On a miss, an available cache line is used.
If the set is full, the least recently used entry is replaced.
Replacement Policy

For set-associative caches, the simulator uses:

LRU — Least Recently Used

Each cache entry records its most recent access. When a replacement
is required, the least recently accessed valid entry is selected.

Input

The simulator accepts a memory-access trace containing hexadecimal
memory addresses.

Example:

0x00000000
0x00000004
0x00000008
0x00000040
0x00000000
0x00000080

The trace can be modified to study different access patterns.

Example Experiments

The simulator can be used to investigate:

1. Associativity

Compare:

Direct-mapped
2-way set associative
4-way set associative

and observe the resulting hit and miss rates.

2. Cache Size

Compare different cache capacities and observe how increasing
capacity affects the miss rate.

3. Cache-Line Size

Study the effect of different cache-line sizes on sequential
memory accesses.

4. Access Patterns

Compare:

Sequential accesses
Repeated accesses
Strided accesses
Conflict-heavy accesses
Example Output
Cache Configuration
-------------------
Cache Size : 1024 bytes
Line Size  : 16 bytes
Ways       : 2
Sets       : 32

Simulation Results
------------------
Accesses  : 100
Hits      : 72
Misses    : 28
Hit Rate  : 72.00%
Miss Rate : 28.00%
Project Structure
cache-simulator/
│
├── cache_simulator.cpp
├── trace.txt
└── README.md
Technologies
C++
Object-Oriented Programming
Computer Architecture
Cache Memory
Memory Hierarchy
Learning Outcomes

This project provides practical understanding of:

Cache organization
Address decomposition
Cache hits and misses
Associativity
LRU replacement
Memory-access patterns
Cache performance analysis
Possible Extensions

The simulator can be extended to include:

Multi-level caches (L1/L2)
Write-through and write-back policies
Write-allocate policies
FIFO replacement
Random replacement
Average Memory Access Time (AMAT)
Separate instruction and data caches
Cache miss classification

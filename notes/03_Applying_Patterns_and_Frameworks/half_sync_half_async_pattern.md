# Half-Sync/Half-Async Pattern

## Context
Web servers that run in settings with large number of bursty request patterns

## Problem
Allocating an OS thread per connected client doesn't scale without devoting enormous processing capability and memory to the server(s)

## Solution
Apply the _Half-Sync/Half-Async_ pattern to scale server performance by processing HTTP request concurrently in multiple threads

## Details
The _Half-Sync/Half-Async_ pattern decouples async and sync service processing in concurrent systems, to simplify programming without unduly reducing performance

http://www.cs.wustl.edu/~schmidt/PDF/PLoP-95.pdf
http://www.dre.vanderbilt.edu/~schmidt/PDF/PLoP-95.pdf

## Benefits
#### Simplification and performance
The programming of higher-level synchronous processing services are simplified without degrading the performance of lower-level systems

#### Separation of concerns
Synchronization policies in each layer are decoupled so that each layer need not use the same concurrency strategies

#### Centralization of inter-layer communication
Inter-layer communication is centralized at a single access point, because all interaction is mediated by the queuing layer

## Limitations
#### May incur a boundary-crossing penalty
Arising from context switching, synchronization, and data copying overhead when data transferred between sync and async service layers

#### Higher-level app services may not benefit from async I/O
Depending on design of OS or application framework interfaces, higher-level services may not use low-level async I/O devices effectively

#### Increased complexity of debugging and testing
Apps can be hard to debug due to concurrent execution

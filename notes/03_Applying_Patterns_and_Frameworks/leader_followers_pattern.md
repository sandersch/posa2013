# Leader/Followers Pattern

## Context
Web servers that run on multi-core and CPU platforms

## Problem
_Half-Sync/Half-Async_ can incur excessive memory management, synchronization, context switching, and data movement overhead in some settings

## Solution
Apply the _**Leader/Followers**_ pattern to reduce thread pool overhead and jitter

## Details
_**Leader/Followers**_ provides an efficient and predictable concurrency model where multiple threads take turns sharing event sources to process service requests that occur on the event sources

http://www.dre.vanderbilt.edu/~schmidt/PDF/LF.pdf

#### Performance enhancement using the Leader/Follower Pattern
Improves CPU cache affinity by putting recently finished processing threads at the head of the queue to become leaders again

#### Comparison with Half-Sync/Half-Async Pattern
Half-Sync/Half-Async Pattern may still be more appropriate for certain types of servers, however, because:

  * It can reorder and prioritize client requests more flexibly via its request queue
  * It may be more scalable since it queues requests in virtual memory

## Benefits

#### Performance enhancements

  * Improves CPU cache affinity and removes need for dynamic memory allocation and data buffer sharing between threads
  * Minimizes locking overhead by not exchanging data between threads, thus reducing thread synchronization
  * Minimizes priority inversion because no extra queueing is used in the server
  * Doesn't require a context switch to handle each event

#### Programming simplicity
Simplifies programming of concurrency models where multiple threads receive requests, process responses, and demultiplex connections using a shared handle set

## Limitations

#### Implementation complexity
The advanced variants of the pattern are hard to implement

#### Lack of flexibility
It is hard to discard or reorder events because there is not explicit queue

#### Network I/O bottlenecks

  * Serializes processing by allowing only a single thread at a time to wait on the handle set
  * Could become a bottleneck because only one thread at a time (de)muxes I/O events

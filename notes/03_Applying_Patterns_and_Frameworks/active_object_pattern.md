# Active Object Pattern

## Context
High-performance web servers that need to leverage advances in hardware and software

## Problem
To improve quality-of-service (QoS) for all connected clients, a web server must not block while waiting for connection flow control to abate and must fully leverage parallelism

## Solution
Apply the _Active Object_ pattern to scale up server performance by processing each HTTP request concurrently in its own thread

## Details
_Active Object_ defines units of concurrency as service requests on components and runs service requests on a component in a different thread from the requesting client thread

https://www.dre.vanderbilt.edu/~schmidt/PDF/Active-Objects.pdf

## Benefits
#### Enhances concurrency and simplifies synchronized complexity
  * Client threads and asynchronous method executions can run concurrently
  * A scheduler can evaluate synchronization constaints to serialize access to servants

#### Transparent leveraging of available parallelism
Multiple active object methods can execute in parallel if supported by the OS/hardware

#### Method execution order can differ from method invocation order
Methods invoked asynchronously can be executed according to synchronization constraint defined by guards and scheduling policies

## Limitations
#### Higher overhead
Depending on how an active object is implemented, context switching, synchronization, and data movement/copying overhead may occur when invoking, scheduling, and executing active object method calls

#### Complicated Debugging
It is harder to debug programs that use concurrency due to non-determinism of the various schedulers

#### Increased complexity

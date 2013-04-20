# Monitor Object Pattern

## Context
A system with a boundary between synchronous and asynchronous processing components

## Problem
Naive request queues incur race conditions of "busy waiting" when multiple threads put/get requests

  * Concurrent threads can corrupt the queue's internal state if is not synchronized properly
  * These threads will "busy wait" when the queue is empty or full, which wastes CPU cycles unnecessarily

## Solution
Apply the _Monitor Object_ pattern to synchronize the request queue efficiently and conveniently

## Details
_Monitor Object_ synchronizes concurrent method execution to ensure only one method at a time runs within an object and allows an objects methods to cooperatively schedule their execution sequences

http://www.cs.wustl.edu/~schmidt/PDF/monitor.pdf

## Benefits
#### Simplification of concurrency control
This pattern presents a concise programming model for sharing an objet among cooperating threads where object synchronization corresponds to method invocations

#### Simplification of scheduling method execution
Synchronized methods use their monitor conditions to determine the circumstances under which they should suspend or resume their execution and that of collaborating monitor objects

## Limitations
#### Limited Scalability
A single monitor lock can limit scalability due to increased contention when multiple threads serialize on a monitor object

#### Complicated extensibility semantics
These result from the coupling between a monitor object's functionality and its synchronization mechanisms

#### Nested monitor lockout
This problem can occur when a monitor object is nested within another monitor object

See also: https://www.dre.vanderbilt.edu/~schmidt/C++2java.html

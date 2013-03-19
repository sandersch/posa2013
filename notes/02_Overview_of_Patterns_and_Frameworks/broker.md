# The Broker Pattern

## Motivating Example: Android App (same as Proxy)
  * [More Android programming info](https://www.dre.vanderbilt.edu/~schmidt/cs282)
  * The app Activity directs a Service to download images from a web server
  * The Service caches the images locally in external memory files managed by a Content Provider
  * Image URI is returned to Activity and displayed
  * Activity and Service interact via the Android Binder IPC mechanism
  * _Showcase use of the **Broker** pattern_

## Challenge: Isolating Communication Concerns

### Context
A system that consists of multiple (potentially) remote objects that interact synchronously or asynchronously

### Problems
App developers shouldn't need to handle:

  * Low-level message passing, which is fraught with accidental complexity
  * Networked computing diversity (e.g. heterogeneous languages, OSes, protocols, hardware, etc.)
  * Inherent networking complexities (e.g. partial failures, security mechanisms, latency, etc.)

### Solution: Use a Broker to Handle Communication Concerns
  * Separate system communication functionality from app functionality by providing a broker that isolates communication-related concerns
  * e.g. one way to implement this in Android
    * A Service implements a Binder object that a client can't access directly since it may reside in a different process
    * Clients call a method on the proxy, which uses the Android Binder IPC mechanism (broker) to communicate with the object across process boundaries
    * The Binder IPC mechanism use a stub to upcall a method to the object
  * Android Binder used the _Proxy_ pattern and support sync and async communication

## Broker

#### Intent

Connect clients with remote objects by mediating invocations from clients to remote objects, while encapsulating the details of IPC or network communication

#### Applicability

Apps need capabilities to support (potentially) remote communication, provide location transparency, handle faults, manage end-to-end QoS, and encapsulate low-level system details

#### Consequences

  * **Positives:**
    * Location independence
    * Separation of concerns
    * Portability, modularity, reusability, etc.
  * **Negatives:**
    * Additional time and space overhead
    * May complicate debugging and testing

#### Implementation

  * Co-location optimizations
  * Synchrony and asynchrony
  * Pluggable protocols
  * Strategizing concurrenency, synchronization, demuxing, connection management, fault tolerance, and security mechanisms, etc.

#### Some Known Uses

  * Distributed object computing middleware
    * e.g. Common Object Request Broker Architecture (CORBA) and Sun Java Remote Method Invocation (RMI)
  * Local RPC systems on smartphones
    * e.g. Android Binder

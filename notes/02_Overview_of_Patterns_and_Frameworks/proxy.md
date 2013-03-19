# The Proxy Pattern

## Motivating Example: Android App
  * [More Android programming info](https://www.dre.vanderbilt.edu/~schmidt/cs282)
  * The app Activity directs a Service to download images from a web server
  * The Service caches the images locally in external memory files managed by a Content Provider
  * Image URI is returned to Activity and displayed
  * Activity and Service interact via the Android Binder IPC mechanism
  * _Showcase use of the Proxy pattern_

## Proxy Pattern Overview
  * **Intent** &ndash; provide a surrogate or place holder for another object to control access to it
  * **Applicability** &ndash; Proxies are useful wherever there is a need for a more sohpisticated reference to an object than a simple pointer or simple reference can provide
  * **Structure** &ndash; http://upload.wikimedia.org/wikipedia/commons/7/75/Proxy_pattern_diagram.svg
  * **[More Info](https://en.wikipedia.org/wiki/Proxy_pattern)**

## Challenge: Simplifying Access to Remote Objects
### Context
  * It is often infeasible&mdash;or impossible&mdash;to access an object directly
    * e.g. may reside in server process
  * Partitioning of objects in a system may change as requirements evolve

### Problems
  * Manually (de)marshaling messages can be tedious, error-prone, and ineffcient
  * Ensuring remote objects look/act as much like local components as possible from a client app perspective

## Provide a Proxy so Remote Objects Appear Local
### Solution
  * Define a Proxy that provides a surrogate thru which clients can access remote objects
  * e.g. one way to implement this in Android
    * A service implements a Binder object that a client can't access directly since it may be in a different process
    * Proxy represents the Binder object via a common AIDL interface and ensures correct access to it
    * Client calls a method on the proxy to access Binder object
    * Whether the object is in-process or out-of-process can be controlled via the AndroidManifest.xml config file

## Proxy Pattern
### Consequences
  * **Positives**
    * Decoupling client from object location
    * Simplify tedious and error-prone details
  * **Negatives**
    * Additional overhead from indirection
    * May impose overly restrictive type system
    * It's not possible to entirely shield clients from implications of networking (leaky abstraction)

### Implementation
  * Auto-generated vs. hand-crafted
  * A proxy can cache stable information about the subject to postpone accessing it
  * Overloading operation -> in C++

### Some Known Uses
  * Remote Procedure Call (RPC) middleware
    * e.g. ONC RPC and OSF Distrubted Computing Environment (DCE)
  * Distributed object computing middleware
    * e.g. Sun Java Remote Method Invocation (RMI) & OMC Common Object Request Broker Architecture (CORBA)
  * Local RPC systems on smartphones
    * e.g. Android Binder

### Summary
  * The proxy pattern illustrates a recuring theme throughout the history of computing: _useful patterns evolve into programming language features_

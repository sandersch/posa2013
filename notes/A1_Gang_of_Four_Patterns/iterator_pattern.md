# The Iterator Pattern

## Problem: Extensible Expression Tree Operations

#### Goals
Create a framework for performing operations that affect nodes in a tree

#### Constraints/forces

  * Support multiple operations on the expression tree without tightly coupling operations with the tree structure
  * i.e. don't have `print()` and `evaluate()` methods in the node classes

#### Solution (Part A): Encapsulate Traversal

## Iterator
Encapsulates a traversal algorithm without exposing representation details to callers

#### Structure
http://en.wikipedia.org/wiki/Iterator_pattern

#### Intent
Access elements of an aggregate without exposing its representation

#### Applicability

  * Require multiple traversal algorithms over an aggregate
  * Require a uniform traversal interface over different aggregates
  * When aggregate classes and traversal algorithm must vary independently

#### Consequences

  * **Positives**
    * _Flexibility_: Aggregate and traversal are independent
    * _Multiplicity_: Multiple iterators and multiple traversal algorithms
  * **Negatives**
    * _Overhead_: Additional communication between iterator and aggregate
    * Particularly problematic for iterators in concurrent or distributed systems

#### Implementation

  * Internal vs. external iterators
  * Violating the object structure's encapsulation
  * Robust iterators
  * Synchronization overhead in multi-threaded programs
  * Batching in distributed and concurrent programs

#### Known Uses

  * C++ STL iterators
  * JDK Enumeration, Iterator
  * Unidraw Iterator
  * C++11 range-based for loops and Java for-each loops

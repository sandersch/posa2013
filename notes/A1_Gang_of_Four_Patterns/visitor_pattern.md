# The Visitor Pattern

## Problem: Extensible Expression Tree Operations

#### Goals
Create a framework for performing operations that affect nodes in a tree

#### Constraints/forces

  * Support multiple operations on the expression tree without tightly coupling operations with the tree structure
  * i.e. don't have `print()` and `evaluate()` methods in the node classes

#### Solution (Part A): Encapsulate Traversal
#### Solution (Part B): Decouple Operations from Expression Tree Structure

## Visitor
Defines action(s) at each step of traversal and avoids hard-coding action(s) into nodes

  * Iterator calls `accept(ET_Visitor&)` method on each node in expression tree

```c++
for (auto iter = expr_tree.begin(); 
     iter != expr_tree.end(); 
     ++iter)
  (*iter).accept(print_visitor);
```

  * `accept()` calls back to visitor, e.g.:

```c++
void Leaf_Node::accept(ET_Visitor &v) {
  v.visit(*this);
}
```

#### Structure
http://en.wikipedia.org/wiki/Visitor_pattern

#### Intent
Centralize operations on an object structure so that they can vary independently, but still behave polymorphically

#### Applicability

  * When classes define many unrelated operations
  * Class relationships in structure rarely change, but operations on them change
  * Algorithms keep state that's updated during traversal

#### Benefits

  * _Flexibility_: Visitor algorithm(s) and object structure are independent
  * _Separation of Concerns_: Localized functionality in the visitor subclass instance

#### Drawbacks

  * _Tight Coupling_: Circular dependency between Visitor and Element interfaces
  * Complicated to explain

#### Implementation

  * Double dispatch
  * General interface to elements of object structure

#### Known Uses

  * ProgramNodeEnumerator in Smalltalk-80 compiler
  * IRIS Inventor scene rendering
  * TAO IDL compiler to handle different backends

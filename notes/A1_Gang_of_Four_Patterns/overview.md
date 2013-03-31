# Overview of Pattern Case Study

### Description of Case Study

**How to Design an Expression Tree Processing App**

  * Apply an _Object-Oriented_ (OO) design based on model classes and objects in the application domain
  * Employ _hierarchical data abstraction_ where design components are based on stable _class_ and _object_ role and relationships
  * Associate actions with specific object and/or classes of objects
  * Group classes and objects in accordance to **patterns** and combine them to form **frameworks**

### An OO Expression Tree Design Method

  * Start with object-oriented (OO) modeling of the _expression tree_ application domain
    * Model a _tree_ as a collection of _nodes_
    * Represent _nodes_ as a hierarchy, capturing properties of each node (e.g. arities)
    * Conduct _Scope, Commonality, and Variability_ analysis to determine stable interfaces and extension points
    * Apply **"Gang of Four" (GoF)** patterns to guide efficient and extensible development of framework components
    * Integrate pattern-oriented language/library features with frameworks

### C++ Pattern-Oriented Language/Library Features

Over time, common patterns become institutionalized as programming language features, e.g.

```c++
Expression_Tree expr_tree = ...;
Print_Visitor print_visitor;

// Traditional STL iterator loop
for (Expression_Tree::iterator iter = expr_tree.begin(); iter != expr_tree.end(); ++iter)
  (*iter).accept(print_visitor);

// C++11 lambda expression
std::for_each (expr_tree.begin(), expr_tree.end(), 
  [&print_visitor]
  (const Expression_Tree &t)
  { t.accept (print_visitor); }
);

// C++11 range-based for loop
for (auto &iter : expr_tree)
  iter.accept(print_visitor);
```

### Java Pattern-Oriented Language/Library Features

Over time, common patterns become institutionalized as programming language features, e.g.

```java
ExpressionTree exprTree = ...;
ETVisitor printVisitor = new PrintVisitor();

// Java for-each loop (assumes tree implements Iterable)
for (ComponentNode node : exprTree)
  node.accept(printVisitor);

// Java iterator style
for (Iterator<ExpressionTree> itr = exprTree.iterator(); itr.hasNext(); )
  iter.next().accept(printVisitor);
```

### Outline of Design Space of GoF Patterns

  * **Creational Patterns** &ndash; Abstract the process of instantiating objects
  * **Structural Patterns** &ndash; Describe how classes and objects can be combined to form larger structures
  * **Behavioral Patterns** &ndash; Concerned with communication between objects

||Creational|Structural|Behavioral|
|---|---|---|---|
|**Class**|Factory Method|Adapter (class)|Interpreter|
||||Template Method|
|**Object**|Abstract Factory|Adapter (object)|Chain of Responsibility|
||Builder|Bridge|Iterator|
||Prototype|Composite|Mediator|
||Singleton|Decorator|Memento|
|||Flyweight|Observer|
|||Façade|State|
|||Proxy|Strategy|
||||Visitor|

### Design Problems and Pattern-Oriented Solutions

|Design Problem|Pattern(s)|
|---|---|
|Extensible expression tree structure|Composite|
|Encapsulating variability & simplifying memory management|Bridge|
|Parsing expressions & creating expression tree|Interpreter & Builder|
|Extensible expression tree operations|Iterator & Visitor|
|Implementing STL iterator semantics|Prototype|
|Consolidating user operations|Command|
|Consolidating creation of variabilities for commands, iterators, etc.|Abstract Factory & Factory Method|
|Ensuring correct protocol for commands|State|
|Structuring application event flow|Reactor|
|Supporting multiple operation modes|Template Method & Strategy|
|Centralizing access to global resources|Singleton|
|Eliminating loops via the STL `std::for_each()` algorithm|Adapter|

# The Bridge Pattern

## Problem: Encapsulating Variability and Simplifying Memory Management

#### Goals

  * Help encapsulate sources of variability in expression tree construction and use


```c++
Expression_Tree expr_tree (new Composite_Add_Node
  (new Leaf_Node (3), new Leaf_Node(4))));

Print_Visitor print_visitor;

for (auto iter = expr_tree.begin(); iter != expr_tree.end(); ++iter)
  (*iter).accept(print_visitor)

// Iterate through all the elements in the expression tree without concern for 
// how tree is structured or what traversal has been designated

```

  * Simplify memory management, e.g. minimize use of "naked pointers" in C++ app code to avoid memory leaks stemming from exceptions

```c++
Component_Node *l1 = new Leaf_Node(5);
Component_Node *l2 = new Leaf_Node(4);
Component_Node *l3 = new Leaf_Node(3);
Component_Node *u1 = new Composite_Negate_Node(l1);
Component_Node *b1 = new Composite_Add_Node(l2, l3);
Component_Node *b2 = new Composite_Multiply_Node(u1, b1);
...
delete b2; // This is just asking for trouble in C++!
```

#### Constraints/Forces
Account for the fact that STL algorithms and iterators have "value semantics"

## Solution: Decouple Interface & Implementation(s)

  * Create an interface class (`Expression_Tree`) used by clients and an implementor hierarchy (`Component_Node` et al) that encapsulates variability

#### Expression_Tree Class Interface

Interface for composite structure that ocntains all nodes in expression tree

```c++
        typedef ET_Iterator iterator
                ...
                Expression_Tree(Component_Node *root)
                Expression_Tree(const Expression_Tree &t)
           void operator=(const Expression_Tree &t)
                ~Expression_Tree()
           bool is_null() const
      const int item() const
Expression_Tree left()
Expression_Tree right()
           void accept(ET_Visitor &visitor)
       iterator begin(const std::string &order = "")
       iterator end(const std::string &order = "")
 const_iterator begin(const std::string order = "") const 
 const_iterator end(const std::string &order = "") const
```

  * **Commonality** &ndash; Provides a common interfaces for expression tree operations
  * **Variability** &ndash; The contents of the composite nodes in the expression tree will vary depending on the user input expression

## Bridge

#### Intent
Separate an interface from its implementation(s)

#### Applicability

  * When interface and implementation should vary independently
  * Require a uniform interface to interchangeable implementor hierarchies

#### Structure
http://en.wikipedia.org/wiki/Bridge_pattern

#### Bridge Example in C++
Separate expression tree interface from the composite node implementations

```c++
class Expression_Tree { 
public:
  // root_ manages lifecycle of pointer parameter
  Expression_Tree(Component_Node *root): root_(root) {}

  ...

  // Interface forwards to implementor via shared_ptr
  void accept(ET_Visitor &v) { root_->accept(v); } 

private:
  // C++11/Boost Smart Pointer that handles reference counting
  std::shared_ptr <Component_Node> root_;

...

// expr_tree manages lifecycle of composite via _Bridge_ pattern
Expression_Tree expr_tree (new Composite_Multiply_Node(u1, b1));
```

#### Consequences

  * **Positives**
    * Abstraction interface and implementor hierarchy are decoupled
    * Implementors can vary dynamically
    * Enables efficient use of value-based STL algorithms and containers
  * **Negatives**
    * One-size-fits-all abstraction and implementor interfaces

#### Implemention

  * Sharing implementors and reference counting
  * e.g. C++11/Boost `shared_ptr`
  * Crearing the right implementor
  * Often addressed by using factories
  * Not as widely used in Java as in C++

#### Known Uses

  * ET++ Window/WindowPort
  * libg++ Set/{LinkedList,HashTable}
  * AWT Component/ComponentPeer
  * Java Socket/SocketImpl
  * ACE Reactor framework

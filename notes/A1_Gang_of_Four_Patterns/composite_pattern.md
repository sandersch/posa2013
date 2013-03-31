# The Composite Pattern

## Problem: Extensible Expression Tree Structure

#### Goals

  * Support "physical" structure of expression tree
  * e.g. binary/unary operators and operands
  * Provide "hook methods" that enable arbitrary operations on tree nodes

#### Constraints/forces

  * Treat operators and operands uniformly
  * No distinction between one vs. many to avoid special cases

## Solution: Recursive Structure

  * Model an expression as a recursive collection of nodes
  * Nodes are represented in a hierarchy that captures properties of each node, e.g.:
    * Leaf nodes contain no children (5, 3, 4)
    * Unary nodes recursively contain one other child node (-)
    * Binary nodes recursively contain two other child nodes (\*, +)

```
    *
   / \
  /   \
 -     +
  \   / \
   5 3   4
```

## Component_Node Class Interface

Abstract base class for composable expression tree node objects

  * **Interface**

```
               virtual ~Component_Node()=0
           virtual int item() const
virtual Component_Node *left() const
virtual Component_Node *right() const
          virtual void accept(ET_Visitor &visitor) const
```

  * **Subclasses**
    * `Leaf_Node`, `Composite_Unary_Node`, `Composite_Binary_Node`, etc.
  * **Commonality**: Base class interface used by all nodes in an expression tree
  * **Variability**: Each subclass defines state and method implementations that are specific for the various types of nodes

## Composite

#### Intent
Treat individual object and multiple, recursively-composed objects uniformly

#### Applicability

  * Objects must be composed recursively
  * _and_ no distinction between individual and composed elements
  * _and_ objects in structure can be treated uniformly

#### Structure
http://en.wikipedia.org/wiki/Composite_pattern

#### Composite example in C++
Build an expression tree based on recursively-composed objects

```
    *            b2
   / \          /  \
  /   \        /    \
 -     +     u1      b1
  \   / \     \     / \
   5 3   4     l1  l2  l3
```

```c++
Component_Node *l1 = new Leaf_Node(5);
Component_Node *l2 = new Leaf_Node(4);
Component_Node *l3 = new Leaf_Node(3);
Component_Node *u1 = new Composite_Negate_Node(l1);
Component_Node *b1 = new Composite_Add_Node(l2, l3);
Component_Node *b2 = new Composite_Multiply_Node(u1, b1);
```

In C++ we need to consider how to manage dynamically allocated memory

#### Composite example in Java
Build an expression tree based on recursively-composed objects

```java
ComponentNode l1 = new LeafNode(5);
ComponentNode l2 = new LeafNode(4);
ComponentNode l3 = new LeafNode(3);
ComponentNode u1 = new CompositeNegateNode(l1);
ComponentNode b1 = new CompositeAddNode(l2, l3);
ComponentNode b2 = new CompositeMultiplyNode(u1, b1);
```

Java's garbage collection handles dynamically allocated memory automatically

#### Consequences

  * **Positives**
    * _Uniformity_ &ndash; Treat components the same regardless of complexity and behavior
    * _Extensibility_ &ndash; New component subclasses work wherever existing ones do
    * _Parsimony_ &ndash; Classes only include fields they need
  * **Negatives**
    * _Perceived complexity_ &ndash; May need what seems like a prohibitive number of classes/objects
    * _Awkward designs_ &ndash; May need to treat leaves as lobotomized composites in some cases

#### Implementation

  * Do components know their parents?
  * Uniform interface for both leaves and composites?
  * Don't allocate storage for children in component base class (big problem with algorithmic decomposition solution)
  * Who is responsible for deleting children?

#### Known Uses

  * ET++ Vobjects
  * InterViews Glyphs, Styles
  * Unidraw Components, MacroCommands
  * Directory structures on UNIX and Windows
  * Naming Contexts in CORBA
  * Internal representations of MIME types

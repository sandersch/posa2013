# The Interpreter Pattern

## Problem: Parsing Expressions and Creating an Expression Tree

#### Goals

  * Simplify and centralize the creation of all nodes in the composite expression tree
  * Be extensible for future types of expression formats and optimizations

#### Constraints/Forces

  * Don't recode existing clients when new types of expression formats are added
  * Add new user input expressions without recompiling existing code

## Solution: Build an Expression Tree Using Interpreter

  * Use an interpreter to create a _parse tree_ corresponding to user input expression
  * This parse tree is then traversed to build the appropriate type of nodes in the corresponding _expression tree_
  * We create the entire parse tree to enable optimizations (as a future extension)

## Interpreter

#### Intent
Given a language, define a representation for its grammar, along with an interpreter that uses the representation to interpret sentences in the language

#### Applicability

  * When the grammar is simple and relatively stable
  * When time/space efficiency is not a critical concern

#### Structure
http://en.wikipedia.org/wiki/Interpreter_pattern

#### Consequences

  * **Positives**
    * Simple grammars are easy to change and extend
    * e.g. All rules represented by distinct classes in a consistent and orderly manner
    * Adding another rule adds another class
  * **Negatives**
    * Complex grammars hard to create and maintain
    * e.g. More inter-dependent rules yield more inter-dependent classes

#### Implementation

  * Express language rules, one per class
  * Literal translations expression as _terminal expressions_
  * Alternations, repetitions, or sequences expressed as _nonterminal expressions_

#### Known Uses

  * Text editors and web browsers use _Interpreter_ to lay out documents and check spells
  * e.g. an equation in TeX is represented as a tree where internal nodes are operators and leaves are variables
  * Smalltalk compilers
  * The QOCA constraint-solving toolkit

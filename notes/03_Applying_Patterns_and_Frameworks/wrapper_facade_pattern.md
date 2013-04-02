# Wrapper Facade Pattern

## Context
Web servers must manage various OS services, e.g. 

  * processes
  * threads
  * connections
  * memory
  * etc.

## Problem
Programming directly to low-level OS APIs is tedious, error-prone, and non-portable due to accidental complexities

## Solution
Apply the _Wrapper Facade_ pattern to avoid accessing low-level operating system APIs directly

## Dynamics
http://en.wikipedia.org/wiki/Facade_pattern

## Benefits
#### Concise and robust higher-level OO programming interfaces
Reduce the tedium and increase the type-safety of developing apps, which decreases certain types of accidental complexities

#### Portability and Maintainability
Shield app developers from non-portable aspects of lower-level APIs

#### Modularity, Reusability, and Configurability
Creates cohesive and reusable class components that can be 'plugged' into other components in a wholesale fashion. For example, using OO language features like inheritance and parameterized types

## Limitations
#### Loss of Functionality
Whenever a portable abstraction is layered on top of an existing API it's possible to lose functionality

#### Performance Degradation
Performance can degrade if many forwarding function call and/or indirections are made per wrapper facade method

#### Programming Language and Compiler Limitations
May be hard to define wrapper facades for certain languages due to a lack of language support or limitations with compilers

# The Prototype Pattern

#### Structure
http://en.wikipedia.org/wiki/Prototype_pattern

#### Intent
Specify the kinds of objects to create using a prototypical instance and create new objects by copying this prototype

#### Applicability

  * When the classes to instantiate are specified at run-time
  * There's a need to avoid the creation of a factory hierarchy
  * It is more convenient to copy an existing instance than to create a new one

#### Benefits

  * Can add and remove classes at runetime by cloning them as needed
  * Reduced subclassing minimizes need for lexical dependencies at run-time

#### Drawbacks

  * Every class that used as a prototype must itself be instantiated
  * Classes that have circular references to other classes cannot really be cloned

#### Implementation

  * Use prototype manager
  * Shallow vs. deep copies
  * Initializing clone internal state within a uniform interface

#### Known Uses

  * The first widely known application of the Prototype pattern in an object-oriented language was in ThingLab
  * Jim Coplien describes idioms related to that Prototype pattern for C++ and gives many examples and variations
  * Etgdb debugger for ET++
  * The music editor example is based on the Unidraw drawing framework

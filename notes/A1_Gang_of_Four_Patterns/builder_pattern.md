# The Builder Pattern

#### Intent
Separate the construction of a complex object from its representation so that the same construction process can create different representations

#### Applicability

  * Need to isolate knowledge of the creation of a complex object from its parts
  * Need to allow different implementations/interfaces of an object's parts

#### Structure
http://en.wikipedia.org/wiki/Builder_pattern

#### Consequences

  * **Positives**
    * Can vary a product's internal representation
    * Isolates code for construction and representation
    * Finer control over the construction process
  * **Negatives**
    * May involve a lot of classes

#### Implementation

  * The Builder pattern is a "factory pattern with a mission"
  * A Builder pattern implementation exposes itself as a factory
  * It goes beyond conventional factory patterns by connecting various implementations together

#### Known Uses

  * ET++ RTF converter application
  * Smalltalk-80
  * ACE Service Configurator framework

# Activator Pattern

## Context
Resource constrained and highly dynamic environments

## Problem
It may not be feasible to have all application server implementations running all the time since this ties up end-system resources unnecessarily

## Solution
Apply the **Activator** pattern to activate and deactivate JAWS web server automatically


## Structure
**Activator** automates scalable on-demand activation and deactivation of service execution contexts to run services accessed by many clients without consuming excessive resources

  * http://www.eaipatterns.com/MessagingAdapter.html
  * http://www.dre.vanderbilt.edu/~schmidt/PDF/Activator.pdf
  * http://www.corej2eepatterns.com/Patterns2ndEd/ServiceActivator.htm

## Benefits
#### More effective resource utilization
Servers can be spawned "on-demand" thereby minimizing resource utilization until clients actually require them

#### Coarse-grained concurrency
By spawning server processes to run on multi-core/CPU computers

#### Modularity, testability, and reusability
Application modularity and reusability is improved by decoupling server implementations from the manner in which the servers are activated

## Limitations

#### Lack of determinism and ordering dependencies
Hard to determine or analyze the behavior of an app until its components are activated at runtime

#### Reduced security or reliability
An application that uses **Activator** may be less secure or reliable than an equivalent statically-configured application

#### Increased run-time overhead and infrastructure complexity
By adding levels of abstraction and indirection when activating and executing components

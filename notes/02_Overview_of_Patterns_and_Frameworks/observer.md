# The Observer Pattern
Uses same Android example as previous patterns.

## Challenge
#### Efficiently Maintain Consistency Between Related Objects with Tight Coupling

### Context
Smartphone platforms keep track of system-related status info that is of interest to apps. 

  * e.g., Android and iPhone track and report low battery status

### Problems
Multiple apps/services may be interested in system status info.

  * Coupling status info w/app presentation violated modularity
  * Apps polling for changes to status information is inefficient

### Solutions

  * Automatically notify all apps that depend on system status info when it changes
  * [Observer Pattern](http://en.wikipedia.org/wiki/Observer_pattern)
  * e.g. how this is done in Android:
    * Define a `BroadcastReceiver` whose `onReceive()` hook method is called when a change occurs to system status info
    * Use `registerReciever()` in an activity to attach `BroadcastReceiver` that's called back when intent is broadcast, e.g. _Action Battery Low_
    * `BatteryService` calls `sendBroadcast()` to tell `BroadcastReceivers` battery's low
    * _Note: Android also uses Proxy and Broker patterns in this scenario_

## Observer
### Intent
Define a one-to-many dependecy between objects so that when one object changes state, all dependents are notified and updated
### Applicability

  * An abstraction has two aspects, one dependent on the other
  * A change to one object requires changing untold others
  * An object should notify unkown other objects

### Consequences

  * **Positives:**
    * Modularity: subject and observers may very independently
    * Extensibility: can define/add any number of observers
    * Customizability: different observers offer different views of subject
  * **Negatives:**
    * Unexpected updates: observers don't know about each other
    * Update overhead: too many irrelevant updates

### Implementation

  * Subject-observer mapping
  * Dangling references
  * Update protocols: the push and pull methods
  * Adding filters to narrow interests efficiently

### Known Uses

  * Many GUI toolkits, e.g. Smalltalk, MFC, InterViews, etc.
  * Smartphone event notification. e.g. Android Intents framework and Content Providers
  * Java Observer and Observable

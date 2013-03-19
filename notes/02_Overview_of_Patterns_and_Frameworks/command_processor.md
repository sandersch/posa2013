# The Command Processor Pattern

Uses same Android example as Proxy and Broker pattern notes.

## Challenge: Avoiding Blocking Calls in UI Thread
### Context
Synchronous method calls in the Broker pattern can block client for extended periods. For example, the `downloadImage()` call with block while the Service downloads the image.
### Problems
  * Android generates an "Applicant Not Responding" (ANR) dialog if an app doesn't respond to user input with a short time (~3-5 seconds)
  * Calling a potentially lengthly operation like `downloadImage()` in the main thread can therefore be problematic
  * [More Info on ANRs](https://developer.android.com/training/articles/perf-anr.html)

## Solution: Execute Long-running Calls as Commands
  * _Create a command process processor that separates a request to download an image from service executing request._
  * [Wiki on Command Processor](http://en.wikipedia.org/wiki/Command_pattern)

For example, one way to implement in Android:

  * Implement a `DownloadService` that inherits from Android's `IntentService`
  * Activity creates `Intent` command designating `DownloadService` as target
    * Add URL and callback `Messenger` as "extras"
  * Activity calls `startService()` with `Intent`
  * Activity Manger Service starts `IntentService()`, which spawns internal thread
  * `IntentService` calls `onHandleIntent()` to download image in separate thread
  * [More Info](https://developer.android.com/reference/android/app/IntentService.html)

## Command Processor
### Intent
Encapsulate the request for a service as a command object
### Applicability

  * Specify, queue, and execute service request at different times
  * Ensure service enhancements don't break existing code
  * Implement additional capabilities (such as undo/redo and persistence) consistently for all requests to a service

### Consequences

  * **Positives:**
    * Allow different users to work with service in different ways via commands
    * Client isn't blocked for duration of command processing
  * **Negatives:**
    * Additional programming to handle info passed with commands (cf. Broker)
    * Supporting two-way operations requires additional patterns

### Implementation

  * Statically-typed vs. dynamically-typed commands
  * Concurrency and queuing model(s)
  * Support for persistence and transactions

### Some Known Uses

  * Android `IntentService`
  * Many UI toolkits:
    * InterViews, ET++, MacApp
  * Interpreters for command-line shells

## Summary

  * **Command Processor** provides a relatively straightforward architecture for passing messages containing commands asynchronously between threads and/or processes in concurrent and networked software
  * In contrast, many implementations of _Broker_ use synchronous method invocations
    * Some brokers also support asynchronous method invocations
    * e.g. Android Binder and CORBA both support asynchronous method invocations
  * It's the responsibility of software architects to understand the trade-offs between these patterns
  * **Command Processer** and **Broker** are _pattern complements_

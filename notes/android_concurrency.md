## Android Concurrency Support

  * An overview of Android mechanisms to implement _concurrent_ apps that:
    * Process requests simultaneously via multithreading
    * Synchronize their interactions

### Overview of Java Threads in Android

  * Android implements Java thread and concurrency classes
  * **Conceptual View**
    * Concurrent computation running in a process
  * **Implementation View**
    * Each Java thread has a program counter and a stack (**unique**)
    * The hap and static areas are shared across threads (**common**)

### Using Java Threads in Android

  * All threads must be given some code to run
  * You specify the code that should be run by extending `Thread` or implementing the `Runnable` interface
  * Threads/Runnables have a `run()` method that is called by the new thread after it starts up
  * The thread stays active until `run()` returns

### Synchronizing Java Threads in Android

  * Java provides the `synchronized` keyword to specify sections of code in an object that cannot be accessed concurrently by two threads
  * Only a single synchronized method can be active in any given object

  ```java
  public synchronized void onLocationChanged(Location location)
  {
    if (null == mBestReading
        || mBestReading.getTime() - System.currentTimeMillis()
           > TWO_MIN
        || location.getAccuracy() < mBestReading.getAccuracy())
      {
        mBestReading = location;
        mTextView.setText(getDisplayString(location));
      }
  }
  ```

  * Java objects with synchronized methods use the [Monitor Object](https://www.dre.vanderbilt.edu/~schmidt/PDF/monitor.pdf) pattern
  * A broader ranger of Java synchronizers are available in `java.util.concurrent`
    * e.g. Lock, `Semaphore`, `Condition`, `ReadWriteLock`, etc.
    * [Android Concurrency Reference](https://developer.android.com/reference/java/util/concurrent/package-summary.html)

### Motivating Android Concurrency Idioms

  * Android's UI has several design constraints:
    * An _Application Not Responding_ (ANR) dialog is generated if an app's UI Thread doesn't respond to user input with a short time
    * Also, non-UI thread can't access UI toolkit since it's not thread-safe
    * [More Info on ANRs](https://developer.android.com/training/articles/perf-anr.html)
  * Android thus support various concurrency idioms for processing long-running operations in background thread(s) and communicating with UI Thread
    * AsyncTask
    * Handlers, Messages, and Runnable

### Android AsyncTask

  * `AsyncTask` provides a structured way to manage work involving background and UI threads
  * Simplifies creation of long-running  tasks that need to communcate with the UI
  * Must be subclasses and hook methods overridden
  * [More AsyncTask Info](https://developer.android.com/reference/android/os/AsyncTask.html)

### Handlers, Messages, and Runnables

  * Threads in Android also communicate by exchanging `Messages` and `Runnables`
  * **UI Thread**
    * UI Thread performs user interaction, system callbacks, and Activity lifecycle methods
    * Connects to looper to manage and dispatch `MessageQueue` entries
  * [UI Thread Communication](https://developer.android.com/training/multiple-threads/communicate-ui.html)
  * **Handler**
    * Sends `Messages` and `Runnables` to UI Thread from other threads
    * Schedules `Messages` and `Runnables` for future execution
    * Enqueues actions to perform on a different thread

### Summary

  * Android provides a range of concurrency mechanisms that apps can use to manage multiple threads that run concurrently within a process
  * Some mechanisms are based on standard Java threading and synchronization mechanisms
  * Other mechanisms are based on Android concurrency idioms
  * There are many patterns underlying these Android concurrency mechanisms


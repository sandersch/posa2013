## Android Networking
Presents an overview of Android mechanism available to implement _networked_ apps that:

  * Communicate via the Sockets API, and
  * Use other Android-specific IPC mechanisms

### Overview of Android Communication Mechanisms

  * Android provides mechanisms for local IPC between processes on a device
    * AIDL/[Binder](https://www.nds.rub.de/media/attachments/files/2012/03/binder.pdf)
  * Many Android apps also use data and services via the Internet
    * e.g. Browser, Email, Calendar, Contacts, etc.
    * These apps typically use Sockets and TCP and/or HTTP to communicate
    * [Android Networking Tutorial](https://developer.android.com/training/basics/network-ops/connecting.html)

### Overview of Android Binder and AIDL IPC

  * **Binder**
    * The Binder provides a local RPC mechanism for cross-process calls
    * The Binder Driver is a installed in the Linux kernel to accelerate IPC
    * Uses shared memory and per-process thread pool for high performance
    * Android system services can be written in C/C++, as well as Java
    * [Overview of Binder](https://sites.google.com/site/io/anatomy--physiology-of-an-android)
  * **AIDL**
    * Binder services described via Android Interface Definition Language (AIDL), which similar to Java interfaces

      ```java
      interface IDownloadImage {
        String downloadImage
            (String url);
      }
      ```
    * Caller's data is marshaled into parcel, copied to callee's process, and demarshaled into what callee expects
    * AIDL support synchronous calls, asynchrony supported via callbacks
    * [Overview of AIDL](https://developer.android.com/guide/components/aidl.html)

### Overview of Android Network Programming

  * Android includes multiple network programming classes, e.g.
    * `java.net` &ndash; Socket, URL, etc.
    * `org.apache` &ndash; `HttpRequest`, `HttpResponse`, etc.
    * `android.net` &ndash; `AndroidHttpClient`, URI, `AudioStream`, etc.
  * Under the hood, Android's HTTP libraries use the Java Sockets API
  * Even deeper under the hood Android's `java.net` implementation uses the Linux C Socket API via JNI
  * Sockets are a common programming interface for network communication

### Overview of Java Sockets
  1. _Passive Role_ &ndash; `ServerSocket`
    * Represents a server-side factory that waits for incoming client connections and creates connected sockets
    * `accept()`
    * `bind()`
    * `close()`
  2. _Active Role_ &ndash; `Socket`
    * Provides a client-side (and server-side) TCP socket
    * `bind()`
    * `close()`
    * `connect()`
    * `getInputStream()`
    * `getOutputStream()`
  3. _Communication Role_
    * `InputStream` and `OutputStream` are used for app service processing

### Summary
  * Android provides a wide range of locale and remote IPC mechanisms
  * There are many patterns underlying these Android IPC mechanisms, e.g.
    * [Wrapper Facade](https://www.dre.vanderbilt.edu/~schmidt/PDF/wrapper-facade.pdf)
    * [Broker](http://www.kircher-schwanninger.de/michael/publications/BrokerRevisited.pdf)

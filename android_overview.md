## Android

### What is Android?
Android provides a _layered_ software stack for mobile devices, including

  * A variant of the Linux OS optimized for power conservation and local IPC
  * An optimized Java Virtual Machine (Dalvik), a subset of Java libraries running on Dalvik, native C/C++ libraries, and a hardware abstraction layer
  * Middleware, including:
    * GUIs
    * Telephony services
    * Camera
    * Multimedia
    * App frameworks
    * App distribution
    * and more...
  * Common set of apps
  * [More Info](https://developer.android.com/guide/basics/what-is-android.html)

### Linux Kernel

  * Provides infrastructure mechanisms to manage mobile device resources
    * Memory, process, and thread management
    * Network and inter-process communication stack
    * Device driver framework
    * Security
  * Android-specific enhancements
    * _Binder_ &ndash; optimized inter-process communication (IPC)
    * Android shared memory
    * Power management
    * Alarm driver
    * Low memory killer
    * Kernel debugger and logger

### Hardware Abstraction Layer (HAL)

  * User space C/C++ library layer that defines the interface Android requires hardware _drivers_ to implement
  * The HAL helps to decouple
    * Android platform logic from hardware interface
    * Android frameworks from Linux kernel
  * Motivation for a user-space HAL
    * Not all components have standardize kernel driver interfaces
    * Android has specific requirements for hardware drivers
    * Kernel drivers are GPL, which exposes proprietary intellectual property of Android
    * Implementations of HAL components are often _not_ open-source

### Native C/C++ Libraries

  * **Systems C library** &ndash; bionic libc
  * **Surface manager** &ndash; display management
  * **Media Framework** &ndash; audio/video streaming
  * **FreeType** &ndash; library for rendering fonts
  * **WebKit** &ndash; web browser engine
  * **OpenGL ES, SGL** &ndash; graphics engines
  * **SQLite** &ndash; lightweight relational database engine
  * **SSL** &ndash; secure sockets layer

### Android Runtime
Support services for executing apps and frameworks

  * **Dalvik Virtual Machine (VM)**
    * Android apps typically written in Java, but don't run in a standard Java VM
    * Bytecode executed in Dalvik VM _register machine_
    * **dx** program transforms java classes into .dex-formatted bytecode
    * Just-In-Time (**JIT**) compiler available
    * Apps typically run in their own processes, inside their own Dalvik VM instance
  * **Core Libraries/Java Classes**
    * `android.*`
    * `java.*`,`javax.*`
    * `junit.*`
    * `org.apache.*`,`org.json.*`,`org.xml.*`

### Application Frameworks
Provide services that are essential to the Android platform

  * **Window Manager** &ndash; manages top-level window's look and behavior
  * **View System** &ndash; lists, grids, text boxes, buttons, etc.
  * **Content Providers** &ndash; inter-application data sharing
  * **Activity Manager** &ndash; application lifecycle and common navigation stack
  * **Package Manager** &ndash; manages application packages
  * **Telephony Manager** &ndash; state of telephony services
  * **Resource Manager** &ndash; manages non-code resources: strings, graphics, and layout files
  * **Location Manager** &ndash; access to system location services
  * **Notification Manager** &ndash; notify users when events occur

### Applications

  * **Home** &ndash; main screen
  * **Contacts** &ndash; contacts database
  * **Calendar** &ndash; track schedules
  * **Camera** &ndash; take photos and videos
  * **Phone** &ndash; dial phone numbers
  * **Browser** &ndash; view web pages
  * **Email Client** &ndash; Gmail, IMAP, POP3, etc.
  * **Media Player** &ndash; player songs and watch movies
  * **SMS/MMS** &ndash; instant messaging

### Key Types of Android Components

  * **Activity**
    * Represents a single screen with a user interface
    * Can be started by creating an Intent object and passing it to `startActivity()`
    * Parameters can be passed as "extras" to the _Intent_ used to start the _Service_
  * **Service**
    * Runs in the background to perform long-running operations or to access remote resources
    * _Started Service_
      * Often performs a single operation and usually doesn't return a result to the caller directly
      * Parameters can be passed as "extras" to the _Intent_ used to start the _Service_
    * _Bound Service_
      * Offers a client-server interface that allow compnents to interact with the _Service_
      * e.g. via he Android Interface Definition Language (AIDL) and Binder RPC
  * **Content Provider**
    * Manages a shared set of application data
    * Data typically stored in a SQLite database
    * Never accessed directly, but via a Content Resolver
    * [More info on Content Providers](https://developer.android.com/guide/topics/providers/content-providers.html)
  * **Broadcast Receiver**
    * A component that responds to system-wide _Intent_ broadcast announcements
    * Support complex _Intent_ filtering
    * [More info on Broadcast Receivers](https://developer.android.com/reference/android/content/BroadcastReceiver.html)

### Additional Android Resources

  * Most of the [Android source code](https://source.android.com) is open source
  * [Presentation explaining Android Layers](https://sites.google.com/site/io/anatomy--physiology-of-an-android)
  * [Android Framework Component Fundamentals](https://developer.android.com/guide/components/fundamentals.html)

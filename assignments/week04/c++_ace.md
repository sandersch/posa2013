**ATTN: As with all peer-assessments, you will receive the average of your 4 scores.  For the programming assignments, you will receive the maximum score out of the ones you submit (so if you get 20/20 for Java and 15/20 for C++, you will get 20/20 for Programming Assignment 1).**

You are to design a simple Java program where you create two threads, Ping and Pong, to alternately display "Ping" and "Pong" respectively on the console.  The program should create output that looks like this:

**Ready... Set... Go!

Ping!
Pong!
Ping!
Pong!
Ping!
Pong!
Done!**

It is up to you to determine how to ensure that the two threads alternate printing on the console, and how to ensure that the main thread waits until they are finished to print: âDone!â  The order does not matter (it could start with "Ping!" or "Pong!").

 Consider using any of the following concepts discussed in the videos:

  * `wait()` and `notify()`
  * Semaphores
  * Mutexes
  * Locks

It is up to you to determine how to ensure that the two threads alternate printing on the console, and how to ensure that the main thread waits until they are finished to print: “Done!”  The order does not matter (it could start with "Ping!" or "Pong!").

 Consider using any of the following concepts discussed in the videos:

  * `ACE_Condition::wait()` and `ACE_Condition::signal()`
  * `ACE_Thread_Semaphore`
  * `ACE_Thread_Mutex`
  * `ACE_Task`
  * `ACE_Thread_Mutex`

Please design this program in C++ using the the ACE library (which you can download here) and contain code in a single file.  An evaluator should be able to compile it with a command such as `c++ program.cc`  and execute it with `./a.out` and your program should successfully run! Please add the used C++ compiler version and implementation (e.g. g++ 4.4, 4.5, clang++ 3.2, 3.3, Intel cc, ...) as well as the version of ACE you used as a comment into the source code.  If you have questions about installing/using ACE please post them to the ACE mailing list via the instructions here.

## Rubric
20 possible points

  * 5 points &ndash; code is well-structured and design makes sense
  * 5 points &ndash; concurrency controls are used correctly
  * 5 points &ndash; code demonstrates the appropriate level of readability for others to understand the intent and execution of the program
  * 5 points &ndash; code compiles and runs smoothly

**NOTE: Name your file something like "Program.txt" instead of "Program.java" so that the uploader will accept your code!**

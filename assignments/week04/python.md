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

Please design this program in Python using the threading library and contain code in a single file.  Someone should be able to run something like “python program.py” and your program should successfully run! Please add the Python version and implementation (cpython, jython, pypy, ...) you used as a comment into the source code.

## Rubric
20 possible points

  * 5 points &ndash; code is well-structured and design makes sense
  * 5 points &ndash; concurrency controls are used correctly
  * 5 points &ndash; code demonstrates the appropriate level of readability for others to understand the intent and execution of the program
  * 5 points &ndash; code compiles and runs smoothly

**NOTE: Name your file something like "Program.txt" instead of "Program.java" so that the uploader will accept your code!**

# Dining Philosophers

**ATTN: As with all peer-assessments, you will receive the average of your 4 scores.  For the programming assignments, you will receive the maximum score out of the ones you submit (so if you get 20/20 for Ruby and 15/20 for C++, you will get 20/20 for Programming Assignment 1).**

## Description

The Dining Philosophers problem is as follows:  A group of philosophers are sitting down at a circular table with food in the middle of the table, and a chopstick on each side of each philosopher.  At any time, they are either thinking or eating.  In order to eat, they need to have two chopsticks.  If the chopstick to their left or right is currently being used, they must wait for the other philosopher to put it down.  You may notice that if each philosopher decides to eat at the same time, and each picks up the chopstick to his or her right, he or she will not be able to eat, because everyone is waiting for the chopstick on their left.  This situation is called "deadlock".  In this assignment, you will use the Monitor Object pattern in an algorithm to prevent deadlock.

You are to design a simple model of the Dining Philosophers problem in Ruby and an algorithm using the Monitor Object pattern to prevent deadlock.  There should be 5 philosophers and 5 chopsticks, and each philosopher should eat exactly five times, and be represented by a Thread.  The program should create output that looks something like this:

```
Dinner is starting!

Philosopher 1 picks up left chopstick.
Philosopher 1 picks up right chopstick.
Philosopher 1 eats.
Philosopher 3 picks up left chopstick
Philosopher 1 puts down right chopstick.
Philosopher 3 picks up right chopstick.
Philosopher 2 picks up left chopstick.
Philosopher 1 puts down left chopstick.
Philosopher 3 eats.
Philosopher 2 picks up right chopstick.
Philosopher 2 eats.
Philosopher 2 puts down right chopstick.
Philosopher 2 puts down left chopstick.
Philosopher 3 puts down right chopstick.
Philosopher 3 puts down left chopstick.
...
Dinner is over!
```

## Helpful Ruby Information

It is up to you to implement the Monitor Object pattern in Ruby to prevent deadlock. You can use Monitor, Thread, Mutex, Queue classes

http://www.ruby-doc.org/stdlib-2.0/libdoc/monitor/rdoc/Monitor.html 

http://www.ruby-doc.org/core-1.9.3/Thread.html

http://www.ruby-doc.org/core-1.9.3/Mutex.html

http://www.ruby-doc.org/stdlib-1.9.3/libdoc/thread/rdoc/Queue.html

Please design this program in in Ruby 1.9.3 or new and shiny Ruby 2.0.0 and contain code in a single file.  Someone should be able to run something like "ruby program.rb" (txt) and your program should successfully run!

Please refer to the official site  http://www.ruby-lang.org/en/ for help on installing Ruby on your machine

## Rubric

20 possible points

  * 5 points &ndash; code is well-structured and design makes sense
  * 5 points &ndash; Monitor Object pattern is used correctly
  * 5 points &ndash; code demonstrates the appropriate level of readability for others to understand the intent and execution of the program
  * 5 points &ndash; code compiles and runs smoothly

**NOTE**: _Name your file something like "Program.txt" instead of "Program.rb" so that the uploader will accept your code!_

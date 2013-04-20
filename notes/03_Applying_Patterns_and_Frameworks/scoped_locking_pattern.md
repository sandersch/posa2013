# Scoped Locking Pattern

## Context 
A shared resource that is concurrently accessed and updated by multiple threads must be protected by a lock.

## Problem
If programmers acquire and release locks explicitly, it's hard to ensure locks are released in all code paths

## Solution
Apply the _Scoped Locking_ pattern to automatically acquire a lock when control enters a scope and automatically release the lock when control leaves the scope

## Details
_Scoped Locking_ ensures that entering a critical section becomes thread-safe and leaving the critical section releases all acquired locks

## Benefit of Scoped Locking Pattern

#### Increased Robustness
This pattern increases the robustness of concurrent applications by eliminating common programming errors related to synchronization and multi-threading

By applying _Scoped Locking_, locks are acquired and released automatically when control enters and leaves critical sections defined by C++ method and block scopes

See https://en.wikipedia.org/wiki/Resource_Acquisition_Is_Initialization for RAII C++ idiom

## Limitations

#### Potential for deadlock when used for recursively
If a method that uses _Scoped Locking_ calls itself recursively, **self-deadlock** will occur if the lock is not a recursive mutex

#### Limitations with language-specific semantics
_Scoped Locking_ is based on programming language features and thus isn't integrated with OS-specific system calls

Locks may therefore not be release automatically when threads abort or exit inside a guarded critical section, e.g. via `longjmp()`

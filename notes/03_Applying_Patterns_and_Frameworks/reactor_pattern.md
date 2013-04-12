# Reactor Pattern

## Context
Web servers must demux and process multiple types of indication events arriving from clients simultaneously

## Problem
Developers often tightly couple event demuxing and connection code with app protocol processing code, which impedes understanding, reuse, and optimization

## Solution
Apply **Reactor** pattern and Acceptor-Connector pattern to separate the generic event demuxing and connection code from the JAWS protocol code

## Structure
http://en.wikipedia.org/wiki/Reactor_pattern

_Reactor_ structures event-driven software to cleanly demux and dispatch service requests received from one or more clients

## Benefits
#### Separation of Concerns
Decouples generic demuxing and dispatching mechanisms from app-specific functionality

#### Modularity, reusability, and configurability
Separates event-driven app functionality into several loosely coupled components

#### Portability
Can run on any platform that supports synchronous muxers

#### Coarse-grained concurrency control
Serializes the invocation of event handlers at the level of event demuxing and dispatching within an application process

## Limitations

#### Restricted applicability
Can be applied efficiently only if OS supports synchronous event demuxing

#### Non-pre-emptive and non-scalable
Event handlers borrow reactor thread and run to completion, preventing other event handler dispatching. Can't leverage multi-CPUs/cores

#### Complex debugging and testing
It is hard to debug apps structured using inversion of control, which oscillates between framework infrastructure and method callbacks on app-specific event handlers

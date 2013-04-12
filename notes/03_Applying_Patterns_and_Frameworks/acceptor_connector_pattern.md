# Acceptor-Connector Pattern

## Context
Web servers must demux and process multiple types of indication events arriving from clients simultaneously

## Problem
Developers often tightly couple event demuxing and connection code with app protocol processing code, which impedes understanding, reuse, and optimization

## Solution
Apply Reactor pattern and **Acceptor-Connector** pattern to separate the generic event demuxing and connection code from the JAWS protocol code

## Details

http://www.cs.wustl.edu/~schmidt/PDF/Acc-Con.pdf

## Benefits
#### Reusability, portability, and extensibility
Decouples mechanisms for connecting and initializing service handlers from the service processing performed after service handlers are connected and initialized

#### Robustness
Strongly decouples the service handler from acceptor and connector, which ensures that a data-mode transport endpoint can't accidentally be used to accept or connect

#### Efficiency
Can establish connections actively with many hosts asynchronously and efficiently over long-latency wide area networks

## Limitations

#### Additional indirection
Can incur additional indirection compared to using the underlying network programming interfaces directly

#### Additional complexity
May add unnecessary complexity for simple client applications that connect with only one server and perform one service using a single network programming interface

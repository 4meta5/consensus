# `Futures` Playground

Futures provides a robust way of handling asynchronous computation. Keep written notes [here](https://github.com/AmarRSingh/rust-playground/tree/master/async) and this repository is primarily for practicing with building futures to optimize processes in Substrate and Libp2p. There should be many applications of this emerging primitive to these libraries ([src](http://aturon.github.io/2016/08/11/futures/)).

Also, look at *Optimizing Rust Code* post by `trouble.md`.

**Examples**
* **database query** that's executing in a thread pool. When the query finishes, the future is completed, and its value is the result of the query.
* **An RPC Invocation** to a server. When the server replies, the future is completed, and its value is the server's response.
* **A timeout**. When the time is up, the future is completed, and its value is just `()`
* **A long-running CPU-intensive task**, running on a thread pool. When the task finishes, the future is completed, and its value is the return value of the task.
* **Reading bytes from a socket**. When the bytes are ready, the future is completed -- and depending on the buffering strategy, the bytes might be returned directly, or written as a side-effect into some existing buffer.

## TODO

* add notes from playground

## Projects and Ideas

* consensus algorithms (experiment with existing synchronous Rust implementations)
    * how does borrowing across yield points influence what we can do with Aura (ie retroactively checking the delay on an offline report and unslashing?)

* Networking
    * [dat-rs]https://github.com/datrs) `=>` libp2p

* Pet Projects
    * [fitzgen/state_machine_future](https://github.com/fitzgen/state_machine_future) -- easily create type-safe `Future`s from state machines

## Core CONCEPTS

* tokio (read docs often)
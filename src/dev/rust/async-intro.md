# Rust Async introduction

## Tokio

![Tokio](https://tokio.rs/) is a runtime for writing reliable asynchronous applications with Rust. It provides async I/O, networking, scheduling, timers, and more.

### Example

Example with two function a and b. In the first one, in a non-async function main, we create a tokio runtime. `let rt = Runtime::new().unwrap();` This object will handle all the async/concurrency for us.

~~~admonish note collapsible=true title="But ! What the heck is a tokio runtime ? 😵"
Tokio is an asynchronous runtime for Rust, built on top of the futures and async/await primitives.
It provides a set of tools for building high-performance, concurrent, and scalable network applications.

The key idea behind Tokio is that it provides an event loop, which is responsible for driving I/O operations and executing tasks that are scheduled by the program.
When an I/O operation is initiated, Tokio adds it to the event loop, and then continues executing other tasks.
When the I/O operation completes, Tokio wakes up the task that initiated it, allowing it to continue its execution.

Tokio also provides a number of utilities and abstractions for building asynchronous applications, such as futures, streams, and channels. 
These abstractions make it easy to express complex asynchronous workflows in a clear and concise way, while still maintaining high performance.
~~~

OK then next ? what can i do with this instanciated struct runtime `rt` ?

let's take a look to the function block_on. With the signature: `pub fn block_on<F: Future>(&self, future: F) -> F::Output`
Which says to us:
Runs a future to completion on the Tokio runtime. This is the runtime’s entry point.

This runs the given future on the current thread, blocking until it is complete, and yielding its resolved result. Any tasks or timers which the future spawns internally will be executed on the runtime.
```rust
use futures::stream::{self, StreamExt};
use tokio::task;
use tokio::runtime::Runtime;

async fn a() {
    println!("Starting a");
    // ... do some asynchronous work ...
    println!("Finished a");
}

async fn b() {
    println!("Starting b");
    // ... do some asynchronous work ...
    println!("Finished b");
}


 fn main() {

    let rt = Runtime::new().unwrap();
    rt.block_on(async move {
        // ... we will do something here...
    });
}

```

Then how to implement something inside the `block_on` ?

we will use `async move` which is a combination of two things:

- `async` indicates that the function returns a future. This means that the function will not block when it is called, but instead it will return a future immediately that can be executed later on.
- `move` indicates that the future should take ownership of all variables captured from the enclosing scope. This is necessary because the future may be executed on a different thread, so it needs to own its own data.

In the example, rt.block_on() is used to run the future returned by the async move closure that contains the call to stream::iter(). The async move closure is necessary because it captures the tasks variable from the enclosing scope, which needs to be owned by the future.

```rust
use futures::stream::{self, StreamExt};
use tokio::task;
use tokio::runtime::Runtime;

async fn a() {
    println!("Starting a");
    // ... do some asynchronous work ...
    println!("Finished a");
}

async fn b() {
    println!("Starting b");
    // ... do some asynchronous work ...
    println!("Finished b");
}


 fn main() {

    let rt = Runtime::new().unwrap();
    rt.block_on(async move {
        let tasks = vec![task::spawn(a()), task::spawn(b())];
        stream::iter(tasks)
            .buffer_unordered(2) // execute up to 2 tasks concurrently
            .collect::<Vec<_>>()
            .await;
    });
}

```

OK there is more to tell:

- `let tasks = vec![task::spawn(a()), task::spawn(b())];, task::spawn()` creates a 
JoinHandle for each of the functions `a()` and `b()`, which represents an asynchronous task that can be executed 
in a Tokio runtime.
- JoinHandle is a future that runs the async function in the background and produces a result when it completes.
It is a way to start a new task and obtain a handle to the result of that task.
- By collecting the JoinHandles in a vector, we can then use them to create a stream of tasks that can be executed
concurrently using buffer_unordered() method from futures::stream.


## Attribute
Using `#[tokio::main]` attribute:

The #[tokio::main] attribute is a shorthand for creating a Tokio runtime and running the async 
main function using that runtime.
It essentially wraps your entire main function in a `tokio::runtime::Runtime::new().unwrap().block_on(async { ... }) block`,
so you don't have to create the runtime manually.

```rust
use futures::stream::{self, StreamExt};
use tokio::task;

async fn a() {
    println!("Starting a");
    // ... do some asynchronous work ...
    println!("Finished a");
}

async fn b() {
    println!("Starting b");
    // ... do some asynchronous work ...
    println!("Finished b");
}

#[tokio::main]
async fn main() {
    let tasks = vec![task::spawn(a()), task::spawn(b())];
    stream::iter(tasks)
        .buffer_unordered(2) // execute up to 2 tasks concurrently
        .collect::<Vec<_>>()
        .await;
}
```

## How many task are lauch concurrently ?

`.buffer_unordered(n)` tell to the runtime how many task (i.e futures) you want to execute.

3 tasks, but 2 executed concurrently:

```rust
use futures::stream::{self, StreamExt};
use tokio::task;

async fn a() {
    println!("Starting a");
    // ... do some asynchronous work ...
    println!("Finished a");
}

async fn b() {
    println!("Starting b");
    // ... do some asynchronous work ...
    println!("Finished b");
}

async fn c() {
    println!("Starting c");
    // ... do some asynchronous work ...
    println!("Finished c");
}

#[tokio::main]
async fn main() {
    let tasks = vec![task::spawn(a()), task::spawn(b()), task::spawn(c())];
    stream::iter(tasks)
        .buffer_unordered(2) // execute up to 2 tasks concurrently
        .collect::<Vec<_>>()
        .await;
}
```
In this example, a and b will be executed concurrently,
while c will be executed only after a or b completes.

~~~admonish note title="Conclusion"
Tokio runtime is designed to manage the execution of asynchronous tasks,
which are represented as futures. When a future is spawned on the runtime,
the runtime manages its execution and schedules it to run on one of the available threads.
The runtime uses a thread pool to efficiently manage the scheduling of tasks across multiple threads,
taking into account the number of available CPU cores on the machine.
This allows the runtime to effectively utilize the available resources and maximize performance.

TL;DR:
Tokio runtime works with tasks/futures and under the hood orchestrate theses futures on threads accordingly
with the number of cpu of the machine.

You can change the number of threads OFC : 
```rust
use tokio::runtime::Builder;

...

let runtime = Builder::new().num_threads($valueHere).build().unwrap();
```
~~~

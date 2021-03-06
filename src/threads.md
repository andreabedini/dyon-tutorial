# Threads

In Dyon, a thread is created with the `go` keyword.
The type is `thr`, which defaults to `thr[any]`.

```rust
fn find_sum(n: f64) -> f64 {
    return sum i n { i + 1 }
}

fn main() {
    a := go find_sum(1_000_000)
    println(unwrap(join(thread: a))) // prints `500000500000`
}
```

A thread runs in parallel.

### Current objects are not passed between threads

Dyon does a clone of variables that are passed to a `go` call.
The new thread starts with an empty stack.
This means that current objects are not shared between threads.

### Some useful functions

- `fn join__thread(thr[any]) -> res[any]` - waits for the thread to finish, then returns the result

### Box, Shared-State Concurrency & Iterators

#### `Box<T>` to Point to Data on the Heap
The most straightforward smart pointer is a box, whose type is written `Box<T>`. Boxes allow you to store data on the heap rather than the stack. What remains on the stack is the pointer to the heap data.

##### Typical Use Cases for `Box<T>`
- When you have a type whose size can’t be known at compile time and you want to use a value of that type in a context that requires an exact size
- When you have a large amount of data and you want to transfer ownership but ensure the data won’t be copied when you do so
- When you want to own a value and you care only that it’s a type that implements a particular trait rather than being of a specific type

`TODO` more on `Box<T>`

#### Shared-State Concurrency
##### Mutexes
If you know about the Readers/Writers Dilemma then you likely have been introduced to mutual exclusion (in short `mutex`). A  `mutex` allows only one thread to access some data at any given time. To access the data in a mutex, a thread must first signal that it wants access by asking to acquire the `mutex’s`lock. The lock is a data structure that is part of the `mutex` that keeps track of who currently has exclusive access to the data. Therefore, the `mutex` is described as guarding the data it holds via the locking system.

An example for `Mutex<T>`
```rust
use std::sync::Mutex;

fn main() {
    let m = Mutex::new(5);

    {
        let mut num = m.lock().unwrap();
        *num = 6;
    }

    println!("m = {:?}", m);
}
```
### Box, Shared-State Concurrency & Iterators

#### `Box<T>` to Point to Data on the Heap
The most straightforward smart pointer is a box, whose type is written `Box<T>`. Boxes allow you to store data on the heap rather than the stack. What remains on the stack is the pointer to the heap data.

##### Typical Use Cases for `Box<T>`
- When you have a type whose size can’t be known at compile time and you want to use a value of that type in a context that requires an exact size
- When you have a large amount of data and you want to transfer ownership but ensure the data won’t be copied when you do so
- When you want to own a value and you care only that it’s a type that implements a particular trait rather than being of a specific type

`TODO`
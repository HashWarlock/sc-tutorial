### Memory

##### Values, Variables & Pointers
- A value is a combination of a type & an element of that type's domain of values
- A variable is a value slot on the stack of memory
- A pointer is the address of on the stack that points to a value slot. Dereferencing the pointer will access the value stored in the memory location.

Ex:
```rust
// variable = value
let x = 1;
// variable = pointer
let y = &x;
// variable = dereferenced pointer y to get x value
let z = *y;
assert_eq!(z,x);
```

🎥 Rustling: Variables Example [TODO: Replace w/ commentary video later]

[![Rustling: Variables](https://i9.ytimg.com/vi/VzkJ-FO_ThE/mq2.jpg?sqp=CLCe7YoG&rs=AOn4CLC06pg8HXQseCym0pxboj1dif8VLQ)](https://youtu.be/VzkJ-FO_ThE)

##### Memory Regions
- The Stack
    - A contiguous chunk of memory called a frame where function calls are temporarily allocated on top of the stack (at the bottom resides the `main` function) where the frame contains the function's variables and parameters until the function returns. When the function returns, the stack frame is reclaimed.
- The Heap
    - A pool of memory not tied to the current call stack of the program. The heap allows you to explicitly allocate segments of memory until you deallocate the memory (a.k.a freezing). Essentially your program determines the lifespan of the memory you allocate on the heap.
    - Primarily used for `Box` type
        - `Box::new(value)` create new value on the heap
        - returns a pointer `Box<T>` to value on the heap
    - If you do not deallocate your memory on the heap this will cause a memory leak where that piece of memory will use its free rent & a healthy amount of memory to eat away.
- Static Memory
    - Regions of memory automatically loaded into the program's memory & lives for the entirety of your program's lifetime.
    - Static references that don't point to static memory will live up to what your program dictates or until the program dies. These will be signified with the `static` keyword

🎥 Rustling: Functions Example [TODO: Replace w/ commentary video later]

[![Rustling: Functions](https://i9.ytimg.com/vi/VzkJ-FO_ThE/mq2.jpg?sqp=CLCe7YoG&rs=AOn4CLC06pg8HXQseCym0pxboj1dif8VLQ)](https://youtu.be/VzkJ-FO_ThE)
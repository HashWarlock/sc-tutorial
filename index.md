## Welcome to the Smart Contracts Tutorial
This tutorial will address the differences between Solidity Smart Contracts on Ethereum & ink! Smart Contracts on Polkadot. We will then address how to create, compile, deploy and interact with a Smart Contract on Ethereum then step through how to write the equivalent Smart Contract in ink! on Polkadot.


### Key Differences
Displayed below is a table signifying the diffrences between ink! and Solidity. This table is a reference to Parity's documentation on [ink! Smart Contracts](https://paritytech.github.io/ink-docs/ink-vs-solidity/):

<div class="comparison">

||ink!|Solidity|
|:---|:---|:---|
|Virtual Machine|Any Wasm VM|EVM|
|Encoding|[Wasm](https://rustwasm.github.io/docs/book/what-is-webassembly.html)|[EVM Byte Code](https://www.ethervm.io/)|
|Language|[Rust](https://paritytech.github.io/ink/ink_lang/index.html)|[Standalone](https://docs.soliditylang.org/en/latest/layout-of-source-files.html)|
|Overflow Protection|[Enabled by default](https://paritytech.github.io/ink-docs/faq#overflow-safety)|None|
|Constructor Functions|[Multiple](https://paritytech.github.io/ink-docs/macros-attributes/constructor)|[Single](https://docs.soliditylang.org/en/v0.8.9/contracts.html?highlight=constructor#constructors)|
|Tooling|Anything that supports Rust|[Custom](https://docs.soliditylang.org/en/v0.8.9/resources.html?highlight=tool#solidity-tools)|
|Versioning|Semantic|Semantic|
|Has Metadata?|[Yes](https://paritytech.github.io/ink-docs/getting-started/building-your-contract)|[Yes](https://docs.soliditylang.org/en/v0.8.9/metadata.html?highlight=metadata#contract-metadata)|
|Multi-File Project|Planned|[Yes](https://docs.soliditylang.org/en/v0.8.9/contracts.html?highlight=multiple#multiple-inheritance-and-linearization)|
|Storage Entries|[Variable](https://paritytech.github.io/ink-docs/datastructures/overview)|[256 bits](https://docs.soliditylang.org/en/v0.8.9/introduction-to-smart-contracts.html?highlight=256%20bit#storage-memory-and-the-stack)|
|Supported Types|[Docs](https://paritytech.github.io/ink-docs/basics/storing-values)|[Docs](https://docs.soliditylang.org/en/v0.8.9/types.html)|
|Has Interfaces?|Yes ([Rust Traits](https://paritytech.github.io/ink-docs/basics/trait-definitions))|[Yes](https://docs.soliditylang.org/en/v0.8.9/contracts.html?highlight=interface#interfaces)|

</div>

### Rust
Rust is the programming language for !ink Smart Contracts. Diving into Rust and the capabilities offered will allow for a developer to be more flexible & generic than Domain Specific Languages like Solidity. Next will dive into the fundamentals of Rust. 
#### Memory

##### Values, Variables & Pointers
- A value is a combination of a type & an element of that type's domain of values
- A variable is a value slot on the stack of memory
- A pointer is the address of on the stack that points to a value slot. Dereferencing the pointer will access the value stored in the memory location.

Ex:
```
// variable = value
let x = 1;
// variable = pointer
let y = &x;
// variable = dereferenced pointer y to get x value
let z = *y;
assert_eq!(z,x);
```

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


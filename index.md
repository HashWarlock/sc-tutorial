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

### Comments
We start out with comments bc the most important part to building an efficient solution starts at documentation & proper debug logs for troubleshooting. Let's take a look at types of comments:

<div class="comparison">

|Comment Type|Syntax|Example|
|:---|:---|:---|
|Regular|`//`|`// Line comment to end of line`|
|Regular|`/*`|`/* Block comment to the delimeter */`|
|Docs|`///`|`/// Generate library docs for the following item`|
|Docs|`//!`|`//! Generate library docs for the enclosing item`|

</div>

Formatting your printed strings using `macros` from `std::fmt`

<div class="comparison">

|Format Syntax|Definition|
|:---|:---|
|`format!`|Write formatted text to `String`|
|`print!`|Similar to `format!` but printed to the console `io::stdout`|
|`println!`|Same as `print!` with appended `newline`|
|`eprint!`|Similar to `print!` but printed to the standard error `io::stderr`|
|`eprintln!`|Same as `eprint!` with appended `newline`|
</div>

#### Debug `fmt::Debug`
Example from Rust by Example
```rust
// Derive the `fmt::Debug` implementation for `Structure`. `Structure`
// is a structure which contains a single `i32`.
#[derive(Debug)]
struct Structure(i32);

// Put a `Structure` inside of the structure `Deep`. Make it printable
// also.
#[derive(Debug)]
struct Deep(Structure);

fn main() {
    // Printing with `{:?}` is similar to with `{}`.
    println!("{:?} months in a year.", 12);
    println!("{1:?} {0:?} is the {actor:?} name.",
             "Slater",
             "Christian",
             actor="actor's");

    // `Structure` is printable!
    println!("Now {:?} will print!", Structure(3));
    
    // The problem with `derive` is there is no control over how
    // the results look. What if I want this to just show a `7`?
    println!("Now {:?} will print!", Deep(Structure(7)));
}
```

#### Display `fmt::Display`
`TODO`

#### Formatting
`TODO`

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


### Ownership
- Only one owner for all values & enforced by the borrow checker
- If a value is moved to a new ownership it is no longer accessible unless the value's type implements the `Copy` trait
- Types that contain non-copy types or types that require deallocation when a value is dropped cannot use `Copy` trait
- Rust automatically drops values when they go out of scope. The rule drop order for rust is:
  - variables (including function args) are dropped in reverse order
  - nested-values are dropped in source code order
  - A hash table with a key value pair will drop the table first before the key value pair

#### Ownership Rules
- Each value has a variable that's called the owner
- Only one owner at a time
- Value is dropped when owner leaves scope

### Borrowing and Lifetimes
- The value a shared reference points will be read once & reused by the rust compiler
Example from Rust for Rustaceans rust assumes shared references are immutable
```rust
fn cache(input: &i32, sum: &mut i32) {
  *sum = *input + *input;
  assert_eq!(*sum, 2 * *input);
}
```
- Another shared reference is a mutable reference `&mut T` 
Example from Rust for Rustaceans rust assumes mutable references are exclusive i.e `noalias(&x, &mut x)` is not possible
```rust
fn noalias(input: &i32, output: mut &i32) {
  if *input == 1 {
    *output = 2;
  }
  if *input != 1 {
    *output = 3;
  }
}
```
Example from Rust for Rustaceans mutability applies only to the immediately referenced memory
```rust
let x = 1;
let mut y = &x; // y is of type &i32
let z = &mut y; //z is of type &mut &i32
```
- Interior Mutability
  - Rely on additional mechanisms like atomic CPU instructions or invariants to provide safe mutability without relying on the semantics of exclusive reference.
- Lifetime is a region of code that some reference should be valid for.

#### Mutable References
- Variables are immutable by default & this also applies to references. Also, note that you cannot modify a reference that is not mutable.
- Mutable references have one big restriction: you can have only one mutable reference to a particular piece of data in a particular scope.
  Example from Rust Programming Language
```rust
fn main() {
    let mut s = String::from("hello");

    change(&mut s);
}

fn change(some_string: &mut String) {
    some_string.push_str(", world");
}

// Notice below is illegal due to the code have more than 1 mutable references
fn illegal() {
  let mut s = String::from("hello");

  let r1 = &mut s;
  let r2 = &mut s;

  println!("{}, {}", r1, r2);
}
```
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
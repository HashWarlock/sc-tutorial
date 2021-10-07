### Primitives
Rust has many primitives. Let's start with an intro to the types
#### Scalar Types
<div class="comparison">

|Scalar Type|Syntax|
|:---|:---|
|`singed integers`|`i8`, `i16`, `i32`, `i64`, `i128` & `isize` (pointer size)|
|`unsigned integers`|`u8`, `u16`, `u32`, `u64`, `u128` & `usize` (pointer size)|
|`floating point`|`f32`, `f64`|
|`char`|Unicode scalar values like `a`, `α` and `∞` (4 bytes each)|
|`bool`|`false` or `false`|
|`unit type`|`()` only an empty tuple|

</div>

Example from Rust by Example
```rust
fn main() {
    // Variables can be type annotated.
    let logical: bool = true;

    let a_float: f64 = 1.0;  // Regular annotation
    let an_integer   = 5i32; // Suffix annotation

    // Or a default will be used.
    let default_float   = 3.0; // `f64`
    let default_integer = 7;   // `i32`
    
    // A type can also be inferred from context 
    let mut inferred_type = 12; // Type i64 is inferred from another line
    inferred_type = 4294967296i64;
    
    // A mutable variable's value can be changed.
    let mut mutable = 12; // Mutable `i32`
    mutable = 21;
    
    // Error! The type of a variable can't be changed.
    mutable = true;
    
    // Variables can be overwritten with shadowing.
    let mutable = true;
}
```

#### Compound Types
<div class="comparison">

|Compound Type|Definition|Example|
|:---|:---|:---|
|`array`|`[T, length]` An array (length known at compile time) is a collection of objects of the same type `T`, stored in contiguous memory|`let xs: [i32; 5] = [1, 2, 3, 4, 5];`|
|`slice`| `&[i32]`  slice is a two-word object, the first word is a pointer to the data, and the second word is the length of the slice|`let sl: &[i32] = &xs[1 .. 4];`|
|`tuple`|`(T1, T2, ...)` A tuple is a collection of values of different types|`let long_tuple = (1u8, 2u16, 3u32, 4u64, 'a', true);`|

</div>
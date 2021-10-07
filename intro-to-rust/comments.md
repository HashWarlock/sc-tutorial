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
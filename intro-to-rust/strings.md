## Strings
Rust has two string types, a string slice (`&str`) and an owned string (`String`).

### Creating a New String
```rust
// Creates an empty String to load data into
let mut s = String::new();

// Create String using the Display trait method to_string()
let word = "word";
let w = word.to_string();

// Create String using from
let f = String::from("howdy");
```

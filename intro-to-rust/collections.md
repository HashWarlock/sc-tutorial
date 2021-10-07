### Collections: `Vec<T>` & `HashMap<K, V>`
Vectors allow you to store more than one value in a single data structure that puts all the values next to each other in memory. Vectors can only store values of the same type. They are useful when you have a list of items, such as the lines of text in a file or the prices of items in a shopping cart.

Hash maps are useful when you want to look up data not by using an index, as you can with vectors, but by using a key that can be of any type.

<div class="comparison">

|Collection Type|Syntax|Description|
|:---|:---|:---|
|Vector|`Vec<T>`|`let v: Vec<i32> = Vec::new();`|
|HashMap|`HashMap<K, V>`|`let mut scores = HashMap::new();`|

</div>

#### Updating, Reading, Iterating, Storing Vectors
```rust
// Create & updating a vector
let mut v = Vec::new();

v.push(5);
v.push(6);
v.push(7);
v.push(8);

// Iterating over a vector basic
let v = vec![100, 32, 57];
for i in &v {
    println!("{}", i);
}

// Iterating over a vector. Note you must dereference i to before using an operator on the variable
let mut v = vec![100, 32, 57];
for i in &mut v {
    *i += 50;
}

// Storing multiple values in an enum
enum SpreadsheetCell {
    Int(i32),
    Float(f64),
    Text(String),
}

let row = vec![
    SpreadsheetCell::Int(3),
    SpreadsheetCell::Text(String::from("blue")),
    SpreadsheetCell::Float(10.12),
];
```

#### Updating HashMaps
`TODO`
```rust
// Create HashMap
fn main() {
    use std::collections::HashMap;

    let mut scores = HashMap::new();

    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);
}


```

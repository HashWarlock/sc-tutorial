### Custom Types
##### Structures
<div class="comparison">

|Structures|Definition|Example|
|:---|:---|:---|
|`tuple struct`|Named tuples|`let xs: [i32; 5] = [1, 2, 3, 4, 5];`|`struct Pair(i32, f32);`|
|`C struct`|A composite data type (or record) declaration that defines a physically grouped list of variables under one name in a block of memory, allowing the different variables to be accessed via a single pointer or by the struct declared name which returns the same address |`struct Point { x: f32, y: f32,}`|
|`unit struct`|Is field-less & useful for generics|`struct Unit;`|

</div>

##### Enums
The `enum` keyword allows the creation of a type which may be one of a few different variants. Any variant which is valid as a `struct` is also valid as an `enum`.

Example from Rust by Example
```rust
// Create an `enum` to classify a web event. Note how both
// names and type information together specify the variant:
// `PageLoad != PageUnload` and `KeyPress(char) != Paste(String)`.
// Each is different and independent.
enum WebEvent {
    // An `enum` may either be `unit-like`,
    PageLoad,
    PageUnload,
    // like tuple structs,
    KeyPress(char),
    Paste(String),
    // or c-like structures.
    Click { x: i64, y: i64 },
}
```
An example & interesting quote about the `IpAddr` standard library from Rust Programming Language:
```rust
struct Ipv4Addr {
    // --snip--
}

struct Ipv6Addr {
    // --snip--
}

enum IpAddr {
    V4(Ipv4Addr),
    V6(Ipv6Addr),
}
```

>"You can put any kind of data inside an enum variant: strings, numeric types, or structs, for example. You can even include another enum! Also, standard library types are often not much more complicated than what you might come up with."

Lets's create an `enum` called SwitchPort with variants to describe a switch port configuration.
```rust
/* SwitchPort characteristics
 * 1) PortType(String) Access, Hybrid, Trunk
 * 2) Vlan make this an enum
 *    - NativeVlan
 *    - AllowedVlan
 * 3) Status
 * 4) Neighbor
 */
```

###### `match` Control Flow Operator
`match` allows you to compare a value against a series of patterns and then execute code based on which pattern matches.

Example from Rust Programming Language
```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter,
}

fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}
```

As you can see ing the code above, the `match` in the method `value_in_cents(coin: Coin)` takes in the `enum` `Coin` and will `match` the `coin` parameter to the correct `u8` value as a result.

Another interesting use is matching with `Option<T>`. The example below goes to add one to the `Option<i32>` but if the value is not defined then the function won't attempt to do the addition and return `None`. Just make sure you do not pass `i32` or else the compiler will throw an error for a mismatch of `Option<i32>` not the same type as `i32`. 

```rust
    fn plus_one(x: Option<i32>) -> Option<i32> {
        match x {
            None => None,
            Some(i) => Some(i + 1),
        }
    }

    let five = Some(5);
    let six = plus_one(five);
    let none = plus_one(None);
```

`match` is also exhaustive so if you do not handle every case of your function the compiler will let you know. Rust compiler showing the benefits of preventing easy to miss bugs from slipping into production. Also. note that `_` when you want to match on any other possible `match` then you can use th `_` placeholder. Check the example below for `u8` values:

```rust
    let some_u8_value = 0u8;
    match some_u8_value {
        1 => println!("one"),
        3 => println!("three"),
        5 => println!("five"),
        7 => println!("seven"),
        _ => (),
    }
```
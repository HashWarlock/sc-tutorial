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
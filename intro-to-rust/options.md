### Options
`Option<T>` is an `enum` that is generic over type T and has two variants: Some, which holds one value of type T, and a None variant that doesn’t hold any value.
```rust
enum Option<T> {
    Some(T),
    None,
}
```
`Option<T>` has a number of uses:
- Initial values
- Return values for functions that are not defined over their entire input range (partial functions)
- Return value for otherwise reporting simple errors, where `None` is returned on error
- Optional struct fields
- Struct fields that can be loaned or "taken"
- Optional function arguments
- Nullable pointers
- Swapping things out of difficult situations

### Options
`Option<T>` is an `enum` that is generic over type T and has two variants: Some, which holds one value of type T, and a None variant that doesn’t hold any value.
```rust
enum Option<T> {
    Some(T),
    None,
}
```
`TODO` Continue from here
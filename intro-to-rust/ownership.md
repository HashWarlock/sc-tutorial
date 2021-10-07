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
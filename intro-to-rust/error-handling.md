### Error Handling

#### Recoverable Errors with `Result`
Some errors may require the program to come to a halt, but that is not the case most of the time. For instance, if we are checking for a file that does not exists, we can add logic to instead create the file. Here is a basic example of a `Result` `enum`:
```rust
enum Result<T, E> {
    Ok(T),
    Err(E),
}
```
`T` and `E` represent generic types and in the case the `Result` returns successfully then the `T` is returned within the variant `Ok`, when an error is detected `E` is returned within the `Err` variant.
Here is an example from The Rust Programming Language where we open a file & if there is an error we return a `panic!` with the `error`:
```rust
use std::fs::File;

fn main() {
    let f = File::open("hello.txt");

    let f = match f {
        Ok(file) => file,
        Err(error) => panic!("Problem opening the file: {:?}", error),
    };
}
```

What if we wanted to extend our flexibility and instead try to create the missing file. We would then want to only return a `panic!` if we do not have permissions to read or write the file we are looking to open. Here is an example:
```rust
use std::fs::File;
use std::io::ErrorKind;

fn main() {
    let f = File::open("hello.txt").unwrap_or_else(|error| {
        if error.kind() == ErrorKind::NotFound {
            File::create("hello.txt").unwrap_or_else(|error| {
                panic!("Problem creating the file: {:?}", error);
            })
        } else {
            panic!("Problem opening the file: {:?}", error);
        }
    });
}
```

#### Shortcuts for Panic on Error: `unwrap` and `expect`
`unwrap` will allow us to cut down on code since it will call `panic!` when an error is detected. However, if you want a more descriptive error then using the `expect` function may be better use. Check out the following examples for each case:
```rust
// unwrap syntax for an error when opening hello.txt file
use std::fs::File;

fn main() {
    let f = File::open("hello.txt").unwrap();
}

// expect syntax for reporting an error message when an error is detected when opening hello.txt
use std::fs::File;

fn main() {
    let f = File::open("hello.txt").expect("Failed to open hello.txt");
}
```

#### A Shortcut for Propagating Errors: the ? Operator
`TODO`
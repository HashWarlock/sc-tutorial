### Tests
Tests are Rust functions that verify that the non-test code is functioning in the expected manner. Tests usually are composed of 3 actions:
- Set up any needed data or state
- Run the code to test
- Assert the results are what you expect

To change a function into a test function, add `#[test]` on the line before `fn`.

```rust
#[cfg(test)]
mod tests {
    #[test]
    fn it_works() {
        assert_eq!(2 + 2, 4);
    }
}
```

#### Unit Tests
The purpose of unit tests is to test each unit of code in isolation from the rest of the code to quickly pinpoint where code is and isn’t working as expected. You’ll put unit tests in the `src` directory in each file with the code that they’re testing. The convention is to create a module named tests in each file to contain the test functions and to annotate the module with `cfg(test)`.

`TODO` more in depth

#### Integration Tests
In Rust, integration tests are entirely external to your library. They use your library in the same way any other code would, which means they can only call functions that are part of your library’s public API. Their purpose is to test whether many parts of your library work together correctly. Units of code that work correctly on their own could have problems when integrated, so test coverage of the integrated code is important as well. To create integration tests, you first need a tests directory.

```rust
// tests/integrations_test.rs
use adder;

#[test]
fn it_adds_two() {
    assert_eq!(4, adder::add_two(2));
}
```

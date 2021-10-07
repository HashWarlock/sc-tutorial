### Modules, Crates, Packages & Paths Management
Rust has a number of features that allow you to manage your code’s organization, including which details are exposed, which details are private, and what names are in each scope in your programs. These features, sometimes collectively referred to as the module system, include:
- Packages: Cargo features for build, test & share crates
- Crates: A tree of modules that produces library or executable
- Modules and use: Control the organization, scope & privacy of path
- Paths: A naming for struct, function or module

#### Crates and Packages
- A `crate` is a binary or library. 
- The `crate root` is a source file that the Rust compiler starts from and makes up the root module of your crate. 
- A `package` is one or more crates that provide a set of functionality. A package contains a Cargo.toml file that describes how to build those crates.

#### Modules
- A package is one or more crates that provide a set of functionality. A package contains a Cargo.toml file that describes how to build those crates.

Example from Rust Programming Language
```rust
mod front_of_house {
    mod hosting {
        fn add_to_waitlist() {}

        fn seat_at_table() {}
    }

    mod serving {
        fn take_order() {}

        fn serve_order() {}

        fn take_payment() {}
    }
}
```

#### Paths
When accessing a path there are 2 forms you'll likely encounter:
- `absolute path` starts from a crate root by using a crate name or a literal crate
- `relative path` starts from the current module and uses `self`, `super`, or an identifier in the current module

Both absolute and relative paths are followed by one or more identifiers separated by double colons (::)

#### `pub`, `use`, & privacy
`TODO`
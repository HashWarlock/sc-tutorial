### Generic Types, Traits & Lifetimes
#### Generic Data Types
Generics can create definitions for items like function signatures or structs, which we can then use with many different concrete data types.

Let's take a look at an example that can be optimized with the use of generics from The Rust Programming Language:
```rust
fn largest_i32(list: &[i32]) -> i32 {
    let mut largest = list[0];

    for &item in list {
        if item > largest {
            largest = item;
        }
    }

    largest
}

fn largest_i128(list: &[i128]) -> i128 {
    let mut largest = list[0];

    for &item in list {
        if item > largest {
            largest = item;
        }
    }

    largest
}

fn main() {
    let number_list_i32 = vec![34, 50, 25, 100, 65];

    let result = largest_i32(&number_list_i32);
    println!("The largest number is {}", result);
    assert_eq!(result, 100);

    let number_list_i128 = vec![3400, 50000, 25000, 100000, 650000];

    let result = largest_i128(&number_list_i128);
    println!("The largest char is {}", result);
    assert_eq!(result, 91235);
}
```

As you can see there are a couple pieces in the code that standout:
- `largest_i32()` & `largest_i128()` use the same code except for their parameter and return types
- both functions are very similar

We can cut down on this code by utilizing generic type `T` & combine the 2 functions into 1 function called `largest`. Here is what the final code would look like:
```rust
fn largest<T>(list: &[T]) -> T {
    let mut largest = list[0];

    for &item in list {
        if item > largest {
            largest = item;
        }
    }

    largest
}
fn main() {
    let number_list = vec![34, 50, 25, 100, 65];

    let result = largest(&number_list);
    println!("The largest number is {}", result);
    assert_eq!(result, 100);

    let number_list = vec![3400, 50000, 25000, 100000, 650000];

    let result = largest(&number_list);
    println!("The largest char is {}", result);
    assert_eq!(result, 91235);
}
```

#### Performance of Code Using Generics
You might be wondering whether there is a runtime cost when you’re using generic type parameters. The good news is that Rust implements generics in such a way that your code doesn’t run any slower using generic types than it would with concrete types.

Rust accomplishes this by performing monomorphization of the code that is using generics at compile time. Monomorphization is the process of turning generic code into specific code by filling in the concrete types that are used when compiled.

#### Bounds
When working with generics, the type parameters often must use traits as bounds to stipulate what functionality a type implements.

Bounding restricts the generic to types that conform to the bounds. That is (From Rust By Example):
```rust
struct S<T: Display>(T);

// Error! `Vec<T>` does not implement `Display`. This
// specialization will fail.
let s = S(vec![1]);
```

`TODO` elaborate more on Generics & use cases

#### Lifetime Annotation Syntax
Lifetime annotations have a slightly unusual syntax: the names of lifetime parameters must start with an apostrophe `(')` and are usually all lowercase and very short, like generic types. Most people use the name `'a`. We place lifetime parameter annotations after the `&` of a reference, using a space to separate the annotation from the reference’s type.

Here is an example from The Rust Programming Languagw:
```rust
&i32        // a reference
&'a i32     // a reference with an explicit lifetime
&'a mut i32 // a mutable reference with an explicit lifetime
```
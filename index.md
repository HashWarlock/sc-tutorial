## Welcome to the Smart Contracts Tutorial
This tutorial will address the differences between Solidity Smart Contracts on Ethereum & ink! Smart Contracts on Polkadot. We will then address how to create, compile, deploy and interact with a Smart Contract on Ethereum then step through how to write the equivalent Smart Contract in ink! on Polkadot.


### Key Differences
Displayed below is a table signifying the diffrences between ink! and Solidity. This table is a reference to Parity's documentation on [ink! Smart Contracts](https://paritytech.github.io/ink-docs/ink-vs-solidity/):

<div class="comparison">

||ink!|Solidity|
|:---|:---|:---|
|Virtual Machine|Any Wasm VM|EVM|
|Encoding|[Wasm](https://rustwasm.github.io/docs/book/what-is-webassembly.html)|[EVM Byte Code](https://www.ethervm.io/)|
|Language|[Rust](https://paritytech.github.io/ink/ink_lang/index.html)|[Standalone](https://docs.soliditylang.org/en/latest/layout-of-source-files.html)|
|Overflow Protection|[Enabled by default](https://paritytech.github.io/ink-docs/faq#overflow-safety)|None|
|Constructor Functions|[Multiple](https://paritytech.github.io/ink-docs/macros-attributes/constructor)|[Single](https://docs.soliditylang.org/en/v0.8.9/contracts.html?highlight=constructor#constructors)|
|Tooling|Anything that supports Rust|[Custom](https://docs.soliditylang.org/en/v0.8.9/resources.html?highlight=tool#solidity-tools)|
|Versioning|Semantic|Semantic|
|Has Metadata?|[Yes](https://paritytech.github.io/ink-docs/getting-started/building-your-contract)|[Yes](https://docs.soliditylang.org/en/v0.8.9/metadata.html?highlight=metadata#contract-metadata)|
|Multi-File Project|Planned|[Yes](https://docs.soliditylang.org/en/v0.8.9/contracts.html?highlight=multiple#multiple-inheritance-and-linearization)|
|Storage Entries|[Variable](https://paritytech.github.io/ink-docs/datastructures/overview)|[256 bits](https://docs.soliditylang.org/en/v0.8.9/introduction-to-smart-contracts.html?highlight=256%20bit#storage-memory-and-the-stack)|
|Supported Types|[Docs](https://paritytech.github.io/ink-docs/basics/storing-values)|[Docs](https://docs.soliditylang.org/en/v0.8.9/types.html)|
|Has Interfaces?|Yes ([Rust Traits](https://paritytech.github.io/ink-docs/basics/trait-definitions))|[Yes](https://docs.soliditylang.org/en/v0.8.9/contracts.html?highlight=interface#interfaces)|

</div>

### Rust
Rust is the programming language for !ink Smart Contracts. Diving into Rust and the capabilities offered will allow for a developer to be more flexible & generic than Domain Specific Languages like Solidity. Next will dive into the fundamentals of Rust. 

#### [Comments](./intro-to-rust/comments.md)
We start out with comments bc the most important part to building an efficient solution starts at documentation & proper debug logs for troubleshooting.

- Display `fmt::Display` `TODO`
- Formatting `TODO`

#### [Primitives](./intro-to-rust/primitives.md)
Rust has many primitives. Let's start with an intro to the types.

#### [Strings](./intro-to-rust/strings.md)
Rust has two string types, a string slice (`&str`) and an owned string (`String`).

#### [Structs](./intro-to-rust/structs.md)
A struct, or structure, is a custom data type that lets you name and package together multiple related values that make up a meaningful group.

#### [Custom Types](./intro-to-rust/custom-types.md)
With great power, comes unlimited possibilities. A dive into structs and enums.

#### [Memory](./intro-to-rust/memory.md)
Bending the bits & understanding the values of handling your memory efficiently.

#### [Ownership](./intro-to-rust/ownership.md)
Ownership according to Rust.

#### [Borrowing and Lifetimes](./intro-to-rust/borrowing-and-lifetimes.md)
Understanding what a lifetime is for Rust & how lifetimes are dictated according to Rust.

#### [Modules, Crates, Packages & Paths](./intro-to-rust/modules.md)
Learn to manage your rust projects with Packages, Crates and Modules

#### [Patterns & Matching](./intro-to-rust/patterns-and-matching.md)
`TODO`

#### [Error Handling](./intro-to-rust/error-handling.md)
Different ways to handle errors from the basics to optimal uses of the operator `?`

#### [Generic Types, Traits, & Lifetimes](./intro-to-rust/generics.md)
Understanding the performance advantage of generics & how to utilize them in your code

#### [Options](./intro-to-rust/options.md)
`Option<T>` is an `enum` that is generic over type T and has two variants: Some, which holds one value of type T, and a None variant that doesn’t hold any value. 

#### [Traits](./intro-to-rust/traits.md)
A trait is a collection of methods.

#### [Tests](./intro-to-rust/tests.md)
Tests are Rust functions that verify that the non-test code is functioning in the expected manner.

#### [Box, Shared-State Concurrency & Iterators](./intro-to-rust/standard-library-types.md)
A look into some standard library types.
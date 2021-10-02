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

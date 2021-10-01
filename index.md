## Welcome to the Smart Contracts Tutorial
This tutorial will address the differences between Solidity Smart Contracts on Ethereum & ink! Smart Contracts on Polkadot. We will then address how to create, compile, deploy and interact with a Smart Contract on Ethereum then step through how to write the equivalent Smart Contract in ink! on Polkadot.


### Key Differences
Displayed below is a table signifying the diffrences between ink! and Solidity. This table is a reference to Parity's documentation on [ink! Smart Contracts](https://paritytech.github.io/ink-docs/ink-vs-solidity/):

<div class="comparison">

||ink!|Solidity|
|:---|:---|:---|
|Virtual Machine|Any Wasm VM|EVM|
|Encoding|Wasm|EVM Byte Code|
|Language|Rust|Standalone|
|Overflow Protection|Enabled by default|None|
|Constructor Functions|Multiple|Single|
|Tooling|Anything that supports Rust|Custom|
|Versioning|Semantic|Semantic|
|Has Metadata?|Yes|Yes|
|Multi-File Project|Planned|Yes|
|Storage Entries|Variable|256 bits|
|Supported Types|Docs|Docs|
|Has Interfaces?|Yes (Rust Traits)|Yes|

</div>

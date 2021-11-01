## Structs
A `struct`, or structure, is a custom data type that lets you name and package together multiple related values that make up a meaningful group.

To define a struct, we enter the keyword struct and name the entire struct. A struct’s name should describe the significance of the pieces of data being grouped together. Then, inside curly brackets, we define the names and types of the pieces of data, which we call fields.

Here is an example of a `struct` in a Phala confidential smart contract
```rust
pub struct GhostAuctioneerBot {
    owner: AccountId,
    bot_token: String,
    chat_id: String,
    nft_id: String,
    reserve_price: u64,
    auto_bid_increase: u64,
}
```

Next lets create an instance of the `struct`
```rust
let ghost_bot = GhostAuctioneerBot {
    owner: contracts::account_id_from_hex(ALICE),
    bot_token: "234819o82:jslkdf9833dklj",
    chat_id: "2813308004",
    nft_id: "9571432-c242166657ef41f61c-LOX47-HUMN-0000000000000004",
    reserve_price: 1,
    auto_bid_increase: 1,
};
```

Let's change the `reserve_price`
```rust
ghost_bot.reserve_price = 2;
```

Now we can try another way of defining a `GhostAuctioneerBot` by passing `nft_id`, `reserve_price`, and `auto_bid_increase` to a function named `build_ghost_bot`
```rust
fn build_ghost_bot(nft_id: String, reserve_price: u64, auto_bid_increase: u64) -> GhostAuctioneerBot {
    GhostAuctioneerBot {
        owner: contracts::account_id_from_hex(ALICE),
        bot_token: "234819o82:jslkdf9833dklj",
        chat_id: "2813308004",
        nft_id: nft_id,
        reserve_price: reserve_price,
        auto_bid_increase: auto_bid_increase,
    }
}
```

What if we want to create another `GhostAuctioneerBot` with some values of `ghost_bot`? Here is how that would work.
```rust
let ghost_bot2 = GhostAuctioneerBot {
    owner: ghost_bot.owner,
    bot_token: 1243999:lkajdfhhhhdkfel35,
    chat_id: ghost_bot.chat_id,
    nft_id: "9571432-c242166657ef41f61c-LOX47-HASHWARLOCK-0000000000000001",
    reserve_price: ghost_bot.reserve_price,
    auto_bid_increase: 2,
};
```
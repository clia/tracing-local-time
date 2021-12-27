# tracing-local-time

A patch to fix tracing LocalTime problem. `Deprecated`

Tracing-subscriber now has a bug in LocalTime, so build ourselves' to fix it.
In this patch, we use fixed timezone +8 for China usage.

## Deprecated

Use this crate: [clia-local-time](https://crates.io/crates/clia-local-time)

## Example

Cargo.toml:
```toml
[dependencies]
time = { version = "0.3", features = ["macros"] }
tracing-subscriber = { version = "0.3", features = ["fmt", "std", "time", "local-time"] }
tracing-local-time = { git = "https://github.com/clia/tracing-local-time.git" }
```

main.rs:
```rust
use time::macros::format_description;
use tracing_local_time::LocalTime;

fn main {
    let timer = LocalTime::new(format_description!(
        "[year]-[month]-[day] [hour]:[minute]:[second].[subsecond digits:3]"
    ));
    tracing_subscriber::fmt()
        .with_timer(timer)
        .init();
}
```

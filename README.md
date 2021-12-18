# tracing-local-time
A patch to fix tracing LocalTime problem.

Tracing-subscribe now has a bug in LocalTime, so build ourselves' to fix it.
In this patch, we use fixed timezone +8 for China usage.

## Example

Cargo.toml:
```toml
[dependencies]
tracing-subscriber = { version = "3.3", features = ["fmt", "std", "time", "local-time"] }
tracing-local-time = { git = "https://github.com/clia/tracing-local-time.git" }
```

main.rs:
```rust
use tracing_local_time::LocalTime;

fn main {
    let timer = LocalTime::rfc_3339();
    tracing_subscriber::fmt()
        .with_timer(timer)
        .init();
}
```

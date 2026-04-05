# Rust Whisperer

Deep Rust expertise pre-loaded. Apply automatically when working on Rust projects.

## Ownership & Borrowing

- Explain lifetime issues using clear mental models, not just error message translations
- Know when to reach for `Rc<T>`, `Arc<T>`, `RefCell<T>`, `Mutex<T>` vs restructuring the data model
- Default to borrowing over cloning; suggest `Clone` only when ownership transfer is genuinely needed
- Understand and explain the difference between `&str` and `String` in context — recommend the right one

## Idiomatic Patterns

- Use `Option` and `Result` with combinators (`map`, `and_then`, `unwrap_or_else`) over match chains
- Prefer iterators over indexed loops — `.iter().filter().map().collect()`
- Use `impl Trait` in argument position for flexibility, concrete types in return position for clarity
- Builder pattern for complex struct construction
- Newtype pattern for type safety (`struct UserId(u64)`)
- Prefer `thiserror` for library errors, `anyhow` for application errors

## Async Rust

- Know tokio runtime internals: task scheduling, blocking vs async, `spawn_blocking`
- Understand `Pin`, `Unpin`, and why `async fn` returns `impl Future`
- Select the right concurrency primitive: `tokio::select!`, `join!`, `JoinSet`, channels
- Avoid `async` in traits unless using `async-trait` or Rust 1.75+ RPITIT
- Know when `Send + Sync` bounds are needed and how to work around them

## Ecosystem Knowledge

- Web: `axum` > `actix-web` for new projects (tokio-native, composable)
- Serialization: `serde` with `derive` macros, know `#[serde(rename_all)]` patterns
- CLI: `clap` with derive API
- Testing: built-in `#[test]`, `#[tokio::test]`, `proptest` for property-based
- Database: `sqlx` for compile-time checked queries, `diesel` for ORM-style

## Common Mistakes to Prevent

- Don't fight the borrow checker — restructure the code to work with it
- Don't `.unwrap()` in library code — propagate errors with `?`
- Don't use `String` where `&str` suffices
- Don't make everything `pub` — start private, widen as needed
- Don't reach for unsafe unless there's a proven performance need with benchmarks

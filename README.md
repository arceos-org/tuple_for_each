# tuple_for_each

[![crates.io](https://img.shields.io/crates/v/tuple_for_each.svg)](https://crates.io/crates/tuple_for_each)
[![Docs.rs](https://docs.rs/tuple_for_each/badge.svg)](https://docs.rs/tuple_for_each)
[![CI](https://github.com/arceos-org/tuple_for_each/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/arceos-org/tuple_for_each/actions/workflows/ci.yml)

Provides macros and methods to iterate over the fields of a tuple struct.

Added methods:
- `is_empty() -> bool`: Whether the tuple has no field.
- `len() -> usize`: Number of items in the tuple.

Generated macros:

- `<tuple_name>_for_each!(x in tuple { ... })`
- `<tuple_name>_enumerate!((i, x) in tuple { ... })`

## Examples

```rust
use tuple_for_each::TupleForEach;

#[derive(TupleForEach)]
struct FooBar(u32, &'static str, bool);

let tup = FooBar(23, "hello", true);
assert!(!tup.is_empty());
assert_eq!(tup.len(), 3);

// prints "23", "hello", "true" line by line
foo_bar_for_each!(x in tup {
    println!("{}", x);
});

// prints "0: 23", "1: hello", "2: true" line by line
foo_bar_enumerate!((i, x) in tup {
    println!("{}: {}", i, x);
});
```

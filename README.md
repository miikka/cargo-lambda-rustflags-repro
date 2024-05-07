Reproducing [cargo-lambda/cargo-lambda#649](https://github.com/cargo-lambda/cargo-lambda/issues/649).
To build this repo correctly, you need to use `--cfg my_flag`, which is set in `.cargo/config.toml`.

```sh
# compiles
cargo build
cargo build --release
cargo lambda build
RUSTFLAGS="--cfg my_flag" cargo lambda build --release

# does not compile
cargo lambda build --release
```

The error message:

```
   Compiling cargo-lambda-rustflags-repro v0.1.0 (/Users/miikka.koskinen/mess/2024-19/cargo-lambda-rustflags-repro)
error[E0425]: cannot find function `dummy` in this scope
  --> src/main.rs:18:5
   |
18 |     dummy();
   |     ^^^^^ not found in this scope

For more information about this error, try `rustc --explain E0425`.
error: could not compile `cargo-lambda-rustflags-repro` (bin "cargo-lambda-rustflags-repro") due to 1 previous error
```

Versions in use:

```
rustc 1.78.0 (9b00956e5 2024-04-29)
cargo 1.78.0 (54d8815d0 2024-03-26)
cargo-lambda 1.2.1 (12f9b61 2024-04-05Z)
```

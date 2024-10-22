> [!IMPORTANT]  
> `reqwest-wasmcloud` is a fork of [seanmonstar/reqwest](https://github.com/seanmonstar/reqwest), a prevalent Rust HTTP client library. This crate exists so that reqwest is available for Rust developers targeting `wasm32-wasip2` on the stable toolchain. When [reqwest PR #2453](https://github.com/seanmonstar/reqwest/pull/2453) is merged, this crate will be deprecated in favor of the original crate.
>
> `reqwest-wasmcloud` depends on [rust-url-wasmcloud](https://github.com/wasmCloud/rust-url-wasmcloud) because of an unstable library feature that prevents the `url` crate from compiling on stable `wasm32-wasip2`.

# reqwest-wasmcloud

[![crates.io](https://img.shields.io/crates/v/reqwest.svg)](https://crates.io/crates/reqwest-wasmcloud)
[![Documentation](https://docs.rs/reqwest/badge.svg)](https://docs.rs/reqwest-wasmcloud)
[![MIT/Apache-2 licensed](https://img.shields.io/crates/l/reqwest.svg)](./LICENSE-APACHE)

An ergonomic, batteries-included HTTP Client for Rust.

- Async and blocking `Client`s
- Plain bodies, JSON, urlencoded, multipart
- Customizable redirect policy
- HTTP Proxies
- HTTPS via system-native TLS (or optionally, rustls)
- Cookie Store
- WASM


## Example

This asynchronous example uses [Tokio](https://tokio.rs) and enables some
optional features, so your `Cargo.toml` could look like this:

```toml
[dependencies]
reqwest = { version = "0.12", features = ["json"] }
tokio = { version = "1", features = ["full"] }
```

And then the code:

```rust,no_run
use std::collections::HashMap;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    let resp = reqwest::get("https://httpbin.org/ip")
        .await?
        .json::<HashMap<String, String>>()
        .await?;
    println!("{resp:#?}");
    Ok(())
}
```

## Commercial Support

For private advice, support, reviews, access to the maintainer, and the like, reach out for [commercial support][sponsor].

## Requirements

On Linux:

- OpenSSL with headers. See https://docs.rs/openssl for supported versions
  and more details. Alternatively you can enable the `native-tls-vendored`
  feature to compile a copy of OpenSSL.

On Windows and macOS:

- Nothing.

Reqwest uses [rust-native-tls](https://github.com/sfackler/rust-native-tls),
which will use the operating system TLS framework if available, meaning Windows
and macOS. On Linux, it will use the available OpenSSL or fail to build if
not found.


## License

Licensed under either of

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or http://apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall
be dual licensed as above, without any additional terms or conditions.

## Sponsors

Support this project by becoming a [sponsor][].

[sponsor]: https://seanmonstar.com/sponsor

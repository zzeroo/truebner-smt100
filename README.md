# TRUEBNER SMT100 Soil Moisture Sensor

Device drivers for the [TRUEBNER SMT100 Soil Moisture Sensor](http://www.truebner.de/smt100).

[![Crates.io version](https://img.shields.io/crates/v/truebner-smt100.svg)](https://crates.io/crates/truebner-smt100)
[![Build status](https://travis-ci.org/slowtec/truebner-smt100.svg?branch=master)](https://travis-ci.org/slowtec/truebner-smt100)

Sensor values are accessible through the generic `Capabilities` trait independent of
the actual connection and protocol. Proxy objects provide concrete implementations of
this trait:

- Modbus RTU
- Mock (only for testing and simulation)

## Example

### Build

```sh
cargo build --example modbus-rtu
```

### Run

Set the log level to `info` for observing the current measurements:

```sh
RUST_LOG=info cargo run --example modbus-rtu
```

Due to known limitations in `tokio-proto` the serial port within the Modbus RTU
context needs to be reconnected after a slave failed to send a response in time,
i.e. after the request was aborted by the client due to a timeout. The example
demonstrates how to cope with this situation and displays a warning message.

## Resources

- [TRUEBNER GmbH - Home Page](http://www.truebner.de/en/)
- [SMT100 - Product Page](http://www.truebner.de/en/smt100)
- [AN002: SMT100 Modbus Quickstart Guide](http://www.truebner.de/sites/default/files/AN002.pdf)
- [AN005: SMT100 ASCII Text Command Guide](http://www.truebner.de/sites/default/files/AN005.pdf)

## License

Copyright (c) 2018 - 2019, [slowtec GmbH](https://www.slowtec.de)

Licensed under either of

* Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or
  http://www.apache.org/licenses/LICENSE-2.0)
* MIT license ([LICENSE-MIT](LICENSE-MIT) or
  http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in `truebner-smt100` by you, as defined in the Apache-2.0 license,
shall be dual licensed as above, without any additional terms or conditions.

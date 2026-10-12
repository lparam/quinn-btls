# quinn-btls

A high-performance BoringSSL crypto provider for [quinn](https://github.com/quinn-rs/quinn) and [quinn-proto](https://github.com/quinn-rs/quinn/tree/main/quinn-proto), designed for robust QUIC/WebTransport transport with browser TLS fingerprint emulation (uTLS/BoringSSL) and ECH (Encrypted Client Hello) support.

## Overview & Maintenance Notice

This crate is an actively maintained fork of [0x676e67/quinn-btls](https://github.com/0x676e67/quinn-btls) (which originally originated as a hard fork of [quinn-boring](https://github.com/quinn-rs/quinn-boring)). Following the archiving of upstream, this repository serves as the dedicated crypto provider powering [rkt](https://github.com/lparam/rkt) and related networking components.

### Key Enhancements

- **Client Configuration Hooks**:
  - `ssl_init_hook`: Direct mutable access to `btls::ssl::Ssl` during handshake initialization for applying browser fingerprints and custom extensions.
  - `transport_params_hook`: Byte-level inspection and override of raw QUIC Transport Parameters prior to transmission.
- **ECH Support**: Native BoringSSL Encrypted Client Hello integration, including ECH retry config extraction and injection.
- **Robustness & Stability**: Fixed edge-case panics in session state handling when TLS secrets are not yet finalized.
- **Modern Quinn Compatibility**: Actively tracking Quinn 0.11+ and BoringSSL (`btls`).

## License

Dual-licensed under either of:

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

## Credits & Accolades

- Original implementation by [0x676e67](https://github.com/0x676e67) and [quinn-boring](https://github.com/quinn-rs/quinn-boring) contributors.
- Underlying BoringSSL Rust bindings provided by [btls](https://github.com/0x676e67/btls).
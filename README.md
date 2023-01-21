<!--lint disable no-literal-urls-->
<div align="center">
  <h1>TURN-RS</h1>
</div>
<br/>
<div align="center">
  <strong>TURN Server implemented by ❤️ Rust</strong>
</div>
<div align="center">
  <img src="https://img.shields.io/github/actions/workflow/status/mycrl/turn-rs/cargo-test.yml?branch=main"/>
  <img src="https://img.shields.io/github/license/mycrl/turn-rs"/>
  <img src="https://img.shields.io/github/issues/mycrl/turn-rs"/>
  <img src="https://img.shields.io/github/stars/mycrl/turn-rs"/>
</div>
<br/>
<br/>

A pure rust-implemented turn server, different from coturn, provides a more flexible external control API and provides the same performance and memory footprint, this project is most compatible with the scenario of using stun/turn server in webrtc.


## Who uses it?

* [`Psyai`](https://psyai.com)
* [`Faszialespecialist`](https://faszialespecialist.com/)


## Table of contents

* [features](#features)
* [crates](#crates)
* [usage](#usage)
  * [docker](#docker)
* [building](#building)
* [usage](#usage)
* [benchmark](#benchmark)


## Features

- external controller api. <sup>(`http`)</sup>
- webhooks api. <sup>(`http`)</sup>
- only long-term authentication is supported.
- static identity in configuration file.
- only use udp protocol.
- virtual port support. <sup>(`allocate request does not allocate real udp ports`)</sup>


## Crates

* [`stun`], fast and zero-cost stun message decoder and encoder. <sup>([`crate`](https://crates.io/crates/faster-stun))</sup>.
* [`turn`], a library for handling turn sessions. <sup>([`crate`](https://crates.io/crates/turn-rs))</sup>.
* [`turn-server`], implementation of turn server based on turn library. <sup>([`api`])</sup>

[`api`]: https://github.com/mycrl/turn-rs/wiki/Controller-API-Reference
[`stun`]: https://github.com/mycrl/turn-rs/tree/main/stun
[`turn`]: https://github.com/mycrl/turn-rs/tree/main/turn
[`turn-server`]: https://github.com/mycrl/turn-rs/tree/main/turn-server


## Usage

```bash
cargo install turn-server
```

Start with configuration file:

```bash
turn-server --config=/etc/turn_server/config.toml
```

Please check the example configuration file for details: [turn_server.toml](./turn_server.toml)


### docker

```bash
docker pull quasipaa/turn-server
```
The custom configuration file overrides the `/etc/turn-server/config.toml` path inside the image through `-v`.


## Building

#### Prerequisites

You need to install the Rust toolchain, if you have already installed it, you can skip it, [Install Rust](https://www.rust-lang.org/tools/install), then get the source code:

```bash
git clone https://github.com/mycrl/turn-rs
```

#### Build workspace

Compile the entire workspace in release mode:

```bash
cd turn-rs
cargo build --release
```

After the compilation is complete, you can find the binary file in the "target/release" directory.


## Benchmark

```
stun_decoder/channel_bind ...[time: 20.606 ns] ...[thrpt: 4.8812 GiB/s]
stun_decoder/binding_request ...[time: 20.862 ns] ...[thrpt: 4.2856 GiB/s]
```


## License

[GPL](./LICENSE)
Copyright (c) 2022 Mr.Panda.

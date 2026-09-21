# STATUS — quicunnel (archive snapshot)

## What this is

A small QUIC tunnel library in Rust with mTLS authentication, automatic reconnection, and stream multiplexing. Designed as a low-dependency alternative to running a full VPN for short-lived encrypted tunnels between two endpoints.

This is one of the **local archived snapshots** of `quicunnel` from the broader `SuperInstance` working environment. There is a separate live upstream at `github.com/SuperInstance/quicunnel` (description: *"High-performance QUIC tunnel with mTLS authentication and automatic reconnection"*) — this archive snapshot represents an **earlier local state** and is preserved for the ideas it contains, not as a competing release.

## What's interesting here

- **mtls_setup.rs example.** A self-contained example showing how to generate test certs, configure the endpoint, and connect. Many QUIC tutorials hand-wave the cert part. This one doesn't.
- **reconnection.rs.** A reconnection strategy is one of those things that looks trivial until you have to write it. The example here shows the *minimum* viable reconnection loop with backoff — useful as a starting point.
- **tunnel.rs / endpoint.rs split.** Rather than a single `Tunnel` struct that does everything, the crate separates "the thing that listens for connections" (endpoint) from "the thing that carries bytes" (tunnel). Two-file split, clean responsibility boundary.
- **Five examples, one library.** As with `hwscan`, the example-as-testbench pattern shows what the library actually does without forcing the reader to write glue code.

## Why this is archived as a snapshot

The local working copy had 1558 files of `target/` debug build artifacts and a `Cargo.lock` committed by mistake (the `.gitignore` was present but added after the files were committed). The archived snapshot at `quicunnel-archive` strips these out so the source tree is what gets published.

This is also why we use the `-archive` suffix: the upstream `quicunnel` continues to live at `github.com/SuperInstance/quicunnel`. This archive is the **earlier slice** from before that work moved upstream.

## What changed vs the upstream repo

This snapshot was captured before the upstream migration. The biggest differences you're likely to see:
- No published docs.rs/crate.io metadata
- No CHANGELOG
- Possibly an older API surface — newer methods added upstream may not be present here
- `.gitignore` is present but tracked-but-ignored state on `target/` and `Cargo.lock` has been removed in this snapshot

## License

Dual-licensed MIT OR Apache-2.0. Both `LICENSE-MIT` and `LICENSE-APACHE` are present.

## Date

Snapshot archived 2026-09-21 from local working copy at `C:\reseachlocal\claudeSuperInstance\quicunnel`.
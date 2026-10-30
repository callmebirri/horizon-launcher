# Horizon Launcher Workspace

The Horizon launcher: downloads, prepares, and manages Horizon builds.

## Workspace Crates

| Crate | Path | Description |
|---|---|---|
| `horizon-launcher` | `launcher/` | GPUI desktop launcher application |
| `horizon-theme` | `crates/horizon-theme` | Design tokens, fonts, and icons |
| `horizon-core` | `crates/horizon-core` | Basic primitives and positions |
| `horizon-prepare` | `crates/horizon-prepare` | Prepares assets and resources from vanilla Minecraft |
| `horizon-friends` | `crates/horizon-friends` | Friend invite codes and encrypted tunnel protocol |
| `horizon-bench` | `crates/horizon-bench` | Benchmark report format |
| `horizon-port-pack` | `crates/horizon-port-pack` | Modpack import and porting pipeline |
| `horizon-mods` | `crates/horizon-mods` | Mod files, manifests, and registry index checks |
| `horizon-release-sign` | `crates/horizon-release-sign` | Release checksum verification and signing keys |
| `horizon-telemetry` | `crates/horizon-telemetry` | Opt-in telemetry outbox, batching, and upload |
| `horizon-shader-api` | `crates/horizon-shader-api` | WGSL shader pack verification and parsing |
| `horizon-world` | `crates/horizon-world` | NBT parsing and world/server list data |

## Building & Testing

```sh
cargo check --workspace --all-targets
cargo test --workspace
```

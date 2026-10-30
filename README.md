<p align="center">
  <img src="docs/media/logo.png" alt="Horizon Launcher Logo" width="128">
</p>

# Horizon Launcher

A lightweight, modern, native desktop launcher and manager for Minecraft and Horizon builds, built entirely in Rust with [GPUI](https://www.gpui.rs).

Unlike official and conventional third-party launchers, **Horizon Launcher does NOT require a Microsoft account** to launch or play. You can immediately set an offline player name, customize your offline skin and cape, and start playing right away.

---

## Highlights

- **No Microsoft Account Required:** Play offline without any owner gate or mandatory Microsoft sign-in. Set any custom username (3–16 alphanumeric characters and underscores) with zero barriers.
- **Custom Offline Skins & Capes:** Load custom skin PNGs (classic or slim) and capes for each of your offline player profiles.
- **Instant Preparation from Local Installs:** Reuses and prepares assets, jars, and libraries directly from your existing Minecraft installations (Official Launcher, Prism, MultiMC, Modrinth, etc.) without redownloading.
- **Isolated Instances & Profiles:** Manage multiple independent game directories with dedicated worlds, configs, and resource packs.
- **Integrated Mod & Pack Management:** Browse Modrinth, import `.mrpack` or CurseForge archives, and manage resource packs with automated integrity checks.
- **Server Hosting & Backups:** Create, configure, and manage local or Tailscale-backed servers directly from the GUI.
- **Full CLI & MCP Server:** Automation-ready command-line tool (`horizon-launcher`) and MCP server (`horizon-launcher mcp`) for scriptable game and instance management.

---

## Offline Play

You can jump into the game with any offline name of your choice:

### Via GUI
1. Open the launcher.
2. In the top-right account menu or under **Settings > Accounts**, enter your preferred offline username under **Offline name** and click **Add** / **Play as**.
3. Click **Play** on the main screen. If the version is not prepared yet, clicking Play will automatically prepare resources from your existing local Minecraft install and start the game.

### Via CLI
```sh
# Set your offline player name
horizon-launcher account offline Steve

# Check active player profile
horizon-launcher account list

# Launch the game
horizon-launcher play
```

*(Optional) Microsoft account authentication remains available for players who wish to log into official Mojang-authenticated servers.*

---

## CLI Quick Reference

```sh
# Accounts & Profiles
horizon-launcher account list                      # List accounts and offline names
horizon-launcher account offline <NAME>            # Switch to an offline name
horizon-launcher account select <NAME>             # Select an active account or offline name
horizon-launcher account skin <NAME> --file <PATH> # Assign a skin to an offline profile

# Instances & Launching
horizon-launcher play                              # Launch the selected instance
horizon-launcher play --instance <NAME>            # Launch a specific instance
horizon-launcher instance list                     # List all instances
horizon-launcher prepare                           # Prepare game assets from local install

# Servers & Multiplayer
horizon-launcher servers list                      # List configured servers
horizon-launcher multiplayer list                  # List saved multiplayer servers
```

Full CLI and tool documentation is available in [docs/launcher-commands.md](docs/launcher-commands.md).

---

## Building from Source

### Prerequisites
- **Rust:** Stable toolchain (`1.90+`).
- **Operating System:** Windows (x64), Linux (x86-64), or macOS (Apple Silicon).
- On Linux: ALSA and udev headers (`libasound2-dev`, `libudev-dev`).

### Build & Run
```sh
# Build the launcher
cargo build --release -p horizon-launcher

# Run GUI launcher
cargo run --release -p horizon-launcher

# Or run CLI directly
cargo run --release -p horizon-launcher -- play
```

### Running Tests & Verification
```sh
cargo check --workspace --all-targets
cargo test --workspace
```

---

## Workspace Structure

The repository focuses strictly on the launcher application and its essential dependencies:

| Component | Path | Description |
|---|---|---|
| `horizon-launcher` | `launcher/` | GPUI desktop launcher application and CLI |
| `horizon-theme` | `crates/horizon-theme` | Design tokens, typography, and styling |
| `horizon-core` | `crates/horizon-core` | Core primitives and shared structures |
| `horizon-prepare` | `crates/horizon-prepare` | Prepares assets from vanilla Minecraft installs |
| `horizon-friends` | `crates/horizon-friends` | Friend invite codes and tunnel protocol |
| `horizon-mods` | `crates/horizon-mods` | Mod files, manifests, and registry index checks |
| `horizon-port-pack` | `crates/horizon-port-pack` | Modpack import and porting pipeline |
| `horizon-world` | `crates/horizon-world` | NBT parsing and world/server list data |
| `horizon-telemetry` | `crates/horizon-telemetry` | Opt-in telemetry batching and reporting |
| `horizon-release-sign` | `crates/horizon-release-sign` | Release verification and key signatures |
| `horizon-shader-api` | `crates/horizon-shader-api` | WGSL shader pack verification and parsing |
| `horizon-bench` | `crates/horizon-bench` | Benchmark report format |

---

## License

This project is licensed under the [MIT License](LICENSE).

> **Disclaimer:** Horizon Launcher is an unofficial, community-developed launcher and is not approved by, endorsed by, or affiliated with Mojang Studios or Microsoft.

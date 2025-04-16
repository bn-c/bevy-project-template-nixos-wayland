# An opinionated Template for Bevy project using Nix

## 🚀 Quick Start

### Running the example project
```bash
git clone https://github.com/bn-c/bevy-project-template-nixos-wayland
cd bevy-project-template-nixos-wayland
direnv allow
cargo run -p app-bevy
```

### Configuring rust toolchain
Simply edit the `rust-toolchain.toml`
```toml
[toolchain]
channel = "nightly"
components = ["rustfmt", "clippy", "rust-src", "rust-analyzer", "clippy"] 
```

## 🛠 Project Structure

- `Cargo.toml`: Workspace configuration
- `app-bevy/`: Main Bevy application crate
  - `Cargo.toml`: Bevy app manifest
  - `src/main.rs`: Main application code
- `lib-utils/`: Utility crate
  - `Cargo.toml`: Utils crate manifest
  - `src/lib.rs`: Utility functions and plugins
- `.cargo/config.toml`: LLD linker configuration
- `rust-toolchain.toml`: Nightly Rust specification
- `flake.nix`: Nix development environment definition
- `.envrc`: Direnv configuration for Nix flake

## 🧰 Development Environment

- **Nix Flakes**: Reproducible development setup
- **Direnv**: Automatic environment loading
- **Rust Nightly**: Latest features necessary with our build flags

## 📝 Notes

- Requires [Nix](https://nixos.org/) and [direnv](https://direnv.net/)
- `.direnv` is gitignored
- Update `flake.lock` with `nix flake update` after `flake.nix` changes
- Works for me using VSCode: [direnv extension](https://marketplace.visualstudio.com/items?itemName=cab404.vscode-direnv)

## 🚫 Limitations

- No WebGPU or web serving capabilities ensured right now, add that yourself
- Designed for local development (well tested in emacs with direnv-mode)

## 🔧 Using This Template for Your Project

1. Clone the repository:
   ```bash
   git clone https://github.com/drxm1/bevy-project-template-nixos-wayland.git your-project-name
   cd your-project-name
   ```
2. Remove the existing git history:
   ```bash
   rm -rf .git
   ```
3. Initialize a new git repository:
   ```bash
   git init
   ```
4. Update the project name in `Cargo.toml`, `app-bevy/Cargo.toml`, `lib-utils/Cargo.toml`, and `flake.nix`.
5. Update this README.md with your project details.
6. Create your initial commit:
   ```bash
   git add .
   git commit -m "Initial commit: Bevy project setup from template"
   ```
7. Link to your new GitHub repository:
   ```bash
   git remote add origin https://github.com/yourusername/your-project-name.git
   git branch -M main
   git push -u origin main
   ```
8. Start developing your Bevy game!
9. For the final release build:
   - Refer to the [Bevy setup guide](https://bevyengine.org/learn/quick-start/getting-started/setup/) for optimal release configurations.
   - Note that you'll likely need to build the final version without dynamic linking for better performance and portability.
   - Update your `app-bevy/Cargo.toml` to remove the `dynamic_linking` feature for release builds:
     ```toml
     [dependencies]
     bevy = { version = "0.14.0", features = ["wayland"] }
     
     [features]
     default = ["bevy/wayland"]
     dev = ["bevy/dynamic_linking"]
     ```
   - Build your release version with:
     ```bash
     cargo build --release --package app-bevy
     ```

Remember to customize the `flake.nix` if you need additional dependencies for your specific project.

## 📦 Working with Multiple Crates

- To run the main application: `cargo run -p app-bevy` or just `cargo run`
- To run tests for all crates: `cargo test --workspace`
- To add a new dependency to the utils crate: `cargo add <dependency> --package lib-utils`
- Add more crates to the workspace by updating the root `Cargo.toml` file.

# bevy - Starter Template
This is just following the first few pages on how to setup good linker and compiler options for using the bevy engine.
It serves as a template that can be used in NixOS with lorri and direnv set up.

## What is included
Main parts to look at are

#### .cargo/config.toml
lld is faster.

#### rust-toolchain.toml
nightly

#### cargo.toml
Opt levels, workspace resolver, and dynamic_linking and wayland as bevy features. Without the wayland feature it would crash sometimes on wayland with nvidia gpu.

#### shell.nix
This installs the environment, need to run 'rustup default nightly' manually for once now when in the environment that it works.
Reads from rust-toolchain.toml.

#### .envrc
generated by lorri init

## What is not included
Includes no setup for webgpu and no serving of a webpage. Can be run locally.

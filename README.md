# Pkl Plugin

[![ci](https://github.com/fluentci-io/pkl-plugin/actions/workflows/ci.yml/badge.svg)](https://github.com/fluentci-io/pkl-plugin/actions/workflows/ci.yml)

This plugin sets up your CI/CD pipeline with a specific version of [pkl](https://pkl-lang.org/).

## 🚀 Usage

Add the following command to your CI configuration file:

```bash
fluentci run --wasm pkl setup
```

## Functions

| Name   | Description                             |
| ------ | --------------------------------------- |
| setup  | Installs a specific version of pkl.     |
| eval   | Render pkl module(s)                    |
| test   | Run tests within the given module(s)    |

## Code Usage

Add `fluentci-pdk` crate to your `Cargo.toml`:

```toml
[dependencies]
fluentci-pdk = "0.1.9"
```

Use the following code to call the plugin:

```rust
use fluentci_pdk::dag;

// ...

dag().call("https://pkg.fluentci.io/pkl@v0.1.0?wasm=1", "setup", vec!["latest"])?;
```

## 📚 Examples

Github Actions:

```yaml
- name: Setup Fluent CI CLI
  uses: fluentci-io/setup-fluentci@v5
  with:
    wasm: true
    plugin: pkl
    args: |
      setup
- name: Show pkl version
  run: |
    type pkl
    pkl --version
```

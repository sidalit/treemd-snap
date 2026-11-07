<div align="center">

# treemd

**Navigate, query and edit markdown documents in your terminal.**

[![treemd](https://snapcraft.io/treemd/badge.svg)](https://snapcraft.io/treemd)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64, arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [treemd](https://github.com/Epistates/treemd), a markdown viewer with a tree outline, rich rendering, in-place editing and a jq-like query language.

</div>

---

## Getting Started

<a href="https://snapcraft.io/treemd"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install treemd
treemd README.md
```

Press `?` for keyboard shortcuts. Use `treemd -q '.h2' README.md` to query a document, or pass a markdown URL instead of a file.

## Configure

There are no `snap set` options. treemd saves theme and outline changes from the TUI to `~/snap/treemd/current/.config/treemd/config.toml`:

| Setting | Accepted values | Default |
| --- | --- | --- |
| `ui.theme` | A theme name, see `t` in the TUI | `OceanDark` |
| `ui.outline_width` | `20`, `30`, `40` | `30` |
| `terminal.color_mode` | `auto`, `rgb`, `256`, `none` | `auto` |
| `content.code_fences` | `full`, `label`, `none` | `full` |
| `images.enabled` | `true`, `false` | `true` |

For documents on removable storage:

```bash
sudo snap connect treemd:removable-media
```

## Limitations

- Documents must be in a normal folder under your home directory or on connected removable storage. Hidden folders directly under your home directory are not accessible.
- Host editors are unavailable, so the `e` key cannot open `$VISUAL` or `$EDITOR`. In-place edits of checkboxes and table cells still work.
- Image detection inside tmux cannot query the host's tmux. Run treemd outside tmux, or use `--no-images`.
- A configuration in the host's `~/.config/treemd` is not read.

## Build

```bash
git clone https://github.com/sidalit/treemd-snap.git
cd treemd-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/treemd-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/Epistates/treemd/issues).

## License

Snap packaging: [MIT](LICENSE).

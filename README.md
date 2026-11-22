# xezim-package

Prebuilt [xezim](https://github.com/aionhw/xezim) binaries. This repo does not contain the simulator.

The build workflow compiles `xezim` on **ubuntu-24.04** and **ubuntu-26.04** and attaches both tarballs to one release:

- `xezim-ubuntu-26.04.tar.gz` — `ubuntu-26.04` / `ubuntu-latest` (while latest is 26.04)
- `xezim-ubuntu-24.04.tar.gz` — `ubuntu-24.04`

[`daxzio/setup-xezim`](https://github.com/daxzio/setup-xezim) picks the matching asset automatically.

The binary is built from the upstream tag with default features (no JIT, no profile-guided optimization). It is licensed the same way as [aionhw/xezim](https://github.com/aionhw/xezim) (MIT OR Apache-2.0).

## Publish a version

Actions → Build → Run workflow. Set `tag` to an upstream tag such as `0.11.7` (no `v` prefix). Tags `0.11.6` and later need Rust 1.100 on the builder (already configured in the workflow).

- `targets` — build both images (`all`), or only `24.04` or `26.04`.

Asset URLs:

```text
https://github.com/daxzio/xezim-package/releases/download/<tag>/xezim-ubuntu-26.04.tar.gz
https://github.com/daxzio/xezim-package/releases/download/<tag>/xezim-ubuntu-24.04.tar.gz
```

## Release notifications (subscribers)

When **Build** publishes a release with **latest** enabled, it notifies [daxzio/setup-xezim](https://github.com/daxzio/setup-xezim) (`xezim-package-published`). That repo fans out to downstream repos (for example PeakRDL-etana) that list themselves as subscribers.

See [setup-xezim/SUBSCRIBING.md](https://github.com/daxzio/setup-xezim/blob/main/SUBSCRIBING.md). Secret on **this** repo: **`SETUP_XEZIM_DISPATCH`** (PAT that may trigger events on `daxzio/setup-xezim`). If unset, the announce step is skipped and the release still succeeds.
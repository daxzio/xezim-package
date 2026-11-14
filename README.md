# xezim-package

Prebuilt [xezim](https://github.com/aionhw/xezim) binaries. This repo does not contain the simulator.

The build workflow checks out an upstream tag, compiles `xezim` on `ubuntu-24.04`, and attaches `xezim-ubuntu-24.04.tar.gz` to a release of the same name. The archive contains `bin/xezim`. [`daxzio/setup-xezim`](https://github.com/daxzio/setup-xezim) downloads that asset. A workflow that uses the action does not compile xezim.

The binary is built from the upstream tag with default features (no JIT, no profile-guided optimization). It is licensed the same way as [aionhw/xezim](https://github.com/aionhw/xezim) (MIT OR Apache-2.0).

## Publish a version

Actions → Build → Run workflow. Set `tag` to an upstream tag such as `0.11.6` (no `v` prefix). Tags `0.11.6` and later need Rust 1.100 on the builder (already configured in the workflow).

The asset URL is:

```text
https://github.com/daxzio/xezim-package/releases/download/<tag>/xezim-ubuntu-24.04.tar.gz
```

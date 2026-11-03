<!--
SPDX-FileCopyrightText: 2026 roolrz
SPDX-License-Identifier: Apache-2.0
-->

# lib-clap

Shared clap runtime for Native command delivery.

Applications own their argument declarations and derive expansions. This crate reexports
the parser, validation and help runtime as one shared Rust library built with the
selected toolchain.

See the [implementation entry](src/lib.rs) and [component declaration](component.json)
for the public interfaces, build dependencies and delivered artifacts.

## Boundaries

The feature selection is owned by component.json, including derive support. Rust shared-
library consumers must be built and delivered with the same toolchain and compatible
dependency graph; this is not a stable C ABI.

## Build and test

Use this checkout inside the [repo-managed workspace](https://github.com/HypeR-Proj/HypeR).
From this repository directory:

```sh
make
make test
```

An absolute `OUT=/path/to/out` selects a shared output directory. The module
entry delegates to build/system, which prepares the installed SDK and declared
dependencies. Native binaries require HypeR; host module checks cover the tests
selected by component.json. A standalone clone does not contain the workspace’s
other source repositories or Native SDK.

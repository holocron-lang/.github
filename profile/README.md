<div align="center">

# Holocron

**A declarative, compiler-checked data layer.**

One YAML file is the single source of truth for your SQL schema *and* a
type-checked query catalog. Every query is validated against the catalog
**before it runs** — with no database connection needed, because the
YAML *is* the schema.

[![crates.io](https://img.shields.io/crates/v/holocron.svg)](https://crates.io/crates/holocron)
[![docs.rs](https://img.shields.io/docsrs/holocron)](https://docs.rs/holocron)
[![Pages](https://img.shields.io/badge/site-holocron--lang.github.io-blue)](https://holocron-lang.github.io/holocron/)
[![License](https://img.shields.io/badge/license-MPL%202.0-green.svg)](https://github.com/holocron-lang/holocron/blob/main/LICENSE)

</div>

---

## What this is

Holocron is a **compiler whose target language is SQL**. You write one
declarative YAML file defining your tables, views, and the rules for how
the app is allowed to query them. The compiler validates every query
statically — *unknown field*, *not filterable*, *wrong operator for
type* are all caught at build time, never at runtime.

> **The guarantee:** any query that compiles is well-formed against the
> declared schema, every field exists, every operator is valid for its
> type, and the emitted SQL is runnable.

## Projects

| Repo | What it is |
|---|---|
| **[holocron](https://github.com/holocron-lang/holocron)** | The compiler core — parser, catalog, resolver, type-checker, SQL emitter; ships the `holocron` CLI. Written in Rust. |
| **[holocron-lsp](https://github.com/holocron-lang/holocron-lsp)** | The Language Server. Live diagnostics for `.holocron.yaml` over standard LSP. |
| **[zed-holocron](https://github.com/holocron-lang/zed-holocron)** | [Zed](https://zed.dev) editor extension — wires `holocron-lsp` into Zed. |
| **[vscode-holocron](https://github.com/holocron-lang/vscode-holocron)** | VS Code / Cursor extension — wires `holocron-lsp` over LSP. |
| **[homebrew-holocron](https://github.com/holocron-lang/homebrew-holocron)** | Homebrew tap with formulas for the CLI and the LSP. |

## Quick start

```sh
cargo install holocron
```

Installs two binaries:

- **`holocron`** — the CLI compiler (YAML → PostgreSQL DDL).
- **`holocron-lsp`** — the LSP server for live, in-editor diagnostics.

Or grab platform binaries from the
[latest release](https://github.com/holocron-lang/holocron/releases/latest)
(macOS, Linux, Windows; one archive contains both binaries).

See the [samples directory](https://github.com/holocron-lang/holocron/tree/main/samples)
for working schemas — and error samples that demonstrate every diagnostic.

## Status

🚧 **Active development.** The compiler pipeline (parse → catalog →
resolve → check → emit) is working end-to-end for PostgreSQL DDL, with
rich rustc-style diagnostics underlining the exact YAML token at fault
and reporting every error in a file in one pass. The LSP server gives
live in-editor squiggles. Still in flight: DML emit for queries, and
the RSQL parser.
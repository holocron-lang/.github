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
| **[holocron](https://github.com/holocron-lang/holocron)** | The compiler — CLI + LSP server, written in Rust. |
| _coming soon_ | Editor extensions (Zed, VS Code), Homebrew tap, language reference. |

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
rich rustc-style diagnostics underlining the exact YAML token at fault.
The LSP server gives live in-editor squiggles. Still in flight:
error-collection (currently bail-on-first), DML emit for queries, and
the RSQL parser.
# Contributing to holocron-lang projects

Thanks for considering a contribution! These guidelines apply across
every repo in the [`holocron-lang`](https://github.com/holocron-lang)
organisation unless the project overrides them with its own
`CONTRIBUTING.md`.

## Code of Conduct

Be respectful. Disagree with code, not people. Personal attacks,
harassment, or discrimination won't be tolerated.

## Conventional Commits

Every commit must follow
[Conventional Commits](https://www.conventionalcommits.org/). This is
enforced by CI on each push. The automated release pipeline reads commit
types to compute semantic-version bumps:

| Type | Effect |
|---|---|
| `feat:` | minor bump (releasing) |
| `fix:` | patch bump (releasing) |
| `feat!:` / footer `BREAKING CHANGE:` | major bump (releasing) |
| `chore:`, `ci:`, `docs:`, `refactor:`, `test:`, `build:`, `style:` | no bump |

Pick the type deliberately — releases go straight to crates.io and are
permanent.

## Before opening a PR

1. **Read the project's `CLAUDE.md`** (if present). It captures
   project-specific rules and conventions. Following them avoids churn
   in review.
2. **Run the local checks**:
   ```sh
   cargo fmt --all
   cargo clippy --workspace -- -D warnings
   cargo check --workspace
   cargo test
   ```
3. **Install pre-commit hooks** (they mirror CI):
   ```sh
   pre-commit install --install-hooks --hook-type commit-msg
   ```

## Discuss → lock → implement

For non-trivial changes, open an issue or draft PR with the design
*first*. Locking the approach before writing code saves us both time
and avoids "no, not that" review cycles.

## License

By contributing, you agree your contributions will be licensed under
each project's stated license (e.g. MPL-2.0 for `holocron`).
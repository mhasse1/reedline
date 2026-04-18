# Upstream relationship

rushline is a fork of [nushell/reedline](https://github.com/nushell/reedline). This
file tracks what's different and why.

## Status legend

- **🔼 upstream-ready** — change is general-purpose, plan to submit as a PR
- **🤝 upstream-merged** — change has been accepted into reedline
- **🏠 rush-only** — change is Rush-shell-specific, unlikely to upstream
- **🔧 workaround** — would prefer a better solution; temporary

## Commits on top of upstream (newest first)

*(refreshed by `git log upstream/main..main --oneline`)*

| Commit  | Subject                                                                          | Status         |
|---------|----------------------------------------------------------------------------------|----------------|
| fbefc5b | engine: don't re-query completion after immediate-replace mutates buffer        | 🔼 upstream-ready |
| 9786d55 | IdeMenu: apply selection moves synchronously; populate values on activation     | 🔼 upstream-ready |
| c91b96c | ColumnarMenu: don't auto-descend after unique partial completion (#225)         | 🔼 upstream-ready |
| 4aeaae3 | Vi: don't open editor when 'v' is consumed as f/F/t/T target                    | 🔼 upstream-ready |
| 732c0b9 | Menu: add has_selection() so Enter before navigation submits the typed line     | 🔼 upstream-ready |
| 0b7f8df | FileBackedHistory: implement delete, add delete_last_history_entry              | 🔼 upstream-ready |
| 34e00dc | Vi: add Ctrl+R redo in normal mode, immediate_completions flag                  | 🔼 upstream-ready |
| e1d7840 | Vi: $ accepts hint after moving to end of buffer                                 | 🔼 upstream-ready |
| c6b3255 | Add immediate_completions: insert menu selection into buffer on navigate        | 🔼 upstream-ready |
| 4b1f0d4 | Vi: accept hint text via motions at end of buffer                                | 🔼 upstream-ready |
| 1e39704 | Vi: remove HistoryHintComplete from l motion (fixes history corruption)         | 🔼 upstream-ready |
| 2791ada | Vi mode improvements: v=OpenEditor, n/N search repeat, Esc moves back           | 🔼 upstream-ready |
| f9b189c | Revert "Menu: replace buffer on every navigation, not just Enter"               | 🔼 upstream-ready |
| 9c4a49d | Menu: fix inline cycling by saving/restoring original buffer before each replacement | 🔼 upstream-ready |
| 3ea6c63 | Menu: replace buffer on activation (first item) and fix navigation sync         | 🔼 upstream-ready |
| 51b71d9 | Vi: add / as forward history search (same as ?)                                  | 🔼 upstream-ready |

All commits currently on top of upstream are considered upstream-ready.
Rush-specific divergence (if any) will be marked 🏠 as it accumulates.

## Contributing back

When a change is marked 🔼, the intent is to prepare a PR against
`nushell/reedline` once it's stable on `rushline` main. The [tracking
issue in rush is #193](https://github.com/mhasse1/rush/issues/193).

## Switching between reedline and rushline

The crate names differ (`reedline` vs `rushline`) but the API surface is
identical at any given revision. To switch a project from one to the
other:

```toml
# Cargo.toml
# rushline = { git = "https://github.com/mhasse1/rushline.git" }
reedline = "*"
```

```rust
// main.rs
// use rushline::{...};
use reedline::{...};
```

And vice versa.

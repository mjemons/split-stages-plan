# stage schemas

The CLI contract for each stage, as data. One file per interface,
`<interface>.json`, owned by this benchmark. A module vendors the ones it
implements (via the boilerplate's `pull.py`) and injects them onto its own
argument parser with the shared `cli` helpers, so every module that implements a
stage exposes the same flags.

- `_base.json` — universal args every module gets (`--output_dir`, `--name`).
- `<interface>.json` — one stage's I/O contract (e.g. `embedding`, `knn`). An
  interface name is the module **entrypoint** it binds to, not the plan stage id.

Each arg is `{flag, type, help?, dest?, choices?}`; `type` is one of
`path | string | integer | number`. See the boilerplate's `docs/stage-interfaces.md`
for the format, and `docs/cli.md` for how a module consumes these.

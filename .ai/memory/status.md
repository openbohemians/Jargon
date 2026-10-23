# Status

*Updated 2026-10-23*

## Released

- **jargon.cr v0.22.2** (`29b4cc6`, 2026-10-22), tagged and on GitHub
  releases. v0.22.0 fixed the bugs the Rust port found, v0.22.1 names
  schema types in type errors ("expected integer, got object"), and
  v0.22.2 reports a value that doesn't convert once, not twice.
- **jargon.rs**: `main` at `842dfb3`, its cases synced from jargon.cr
  v0.22.2. The crate `jargonaut` is **not on crates.io yet**.

## Open

- **jargon.rs's API shape**: waiting on the user's review; the questions
  are in [port.md](port.md).
- **Publishing jargonaut** to crates.io: not done.
- **Renaming `trans/jargon` to `jargon.cr`**: expected, not done (see
  [layout.md](layout.md)).
- **A `ui:` keyword**: a strong proposal (the user's words, 2026-06-12) to
  bless `ui:` as a first-class opaque keyword, like `service:`, as sugar
  for GUI hints, which today go in `x-ui`. Not decided; don't treat it as
  settled.
- **The parse/resolve boundary**: a README section saying Jargon stops at
  a valid string and resolving it is the program's job (transfs's
  requirement #3, jargon.cr's `notes/transfs-requirements.md`). Small and
  uncontroversial, not scheduled.
- **Follow-ups for completions, positionals and config loading**: in
  jargon.cr's `TODO.md`.
- **A warning when `project: false` skips a project config that exists**:
  offered to the user on 2026-10-22, not taken up.
- **Registered config formats in jargon.cr**, like jargon.rs's
  `config_format`, so a program can use any parser (oyl.cr, say). The
  user: "we might end up doing for the crystal what we did for rust ...
  that makes a lot of sense to me" (2026-10-23). Not decided; to be
  discussed before building, including whether built-in YAML stays.

# Status

*Updated 2026-10-24*

## Released

- **jargon.cr v0.23.0** (`5ad886b`, 2026-10-24), tagged and on GitHub
  releases: `help(subcommand)` raises `ArgumentError` for an unknown
  subcommand (`9ba7b9c`, from the user's API review of jargonaut,
  [port.md](port.md)), where it returned "Unknown subcommand: x" as
  help. Before it, v0.22.0 fixed the bugs the Rust port found, v0.22.1
  named schema types in type errors, and v0.22.2 reported a value that
  doesn't convert once, not twice.
- **jargonaut 0.1.0** on crates.io (2026-10-23), published from jargon.rs
  `6da8860` and tagged `v0.1.0` there; its cases are synced from
  jargon.cr `9ba7b9c`, so it matches v0.23.0. Its API docs are docs.rs's.

## Open

- **The old path, `trans/jargon`**, after the move to
  `openbohemians/jargon.cr` (2026-10-23, [layout.md](layout.md)). GitHub
  redirects it, so nothing is broken, but these still name it:
  - other shards' `shard.yml` and `shard.lock` (`github: trans/jargon`),
    for their own agents or the user to change;
  - shards.info and crystaldoc.info, which have only the old path so far.
    The site's Shard stats link stays on shards.info's old page until it
    has the new one.
- **The site** is live at https://jargon.openbohemians.org since
  2026-10-23 (see [layout.md](layout.md)), and
  https://openbohemians.org/jargon.cr/ serves jargon.cr's API docs;
  jargonaut's are at https://docs.rs/jargonaut. Its Rust tab shows
  jargonaut 0.1 from crates.io and `cli.parse()` (`cf8d15e`, `93c9853`).
- **Help layout**, noticed 2026-10-23: a description sat at the same
  indent as a long-only flag, so it read as another option, and an
  enum's values weren't listed. The user chose (2026-10-24) two columns,
  aligned like `Commands:`, and an enum's values written `[fast|safe]`
  after the description (not "possible values"), then `(required)` and
  `[default: …]`. The column stops 32 characters in; a wider flag has
  its description on the next line. **Committed, not yet released**:
  jargon.cr `660cb9d` (after `ea32f23`, which drops the stale TODO entry
  for the double variadic error), jargon.rs `3673600`, synced from
  `660cb9d`. The user made this 0.24. After the releases, the site's help demo in `docs/index.html`
  needs the new output.
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

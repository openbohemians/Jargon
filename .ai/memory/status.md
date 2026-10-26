# Status

*Updated 2026-10-26*

## Released

- **jargon.cr v0.24.0** (`ea8c9bf`, 2026-10-26), tagged and on GitHub
  releases, a minor bump, since sections change which config keys reach
  a subcommand's data:
  - Config sections for subcommands: a mapping under a subcommand's name
    is its section, any other key global; a subcommand takes the globals
    it has an option for, then its whole section (`54440a2`). The user
    chose sections plus globals, sections passed whole, and the bare
    subcommand name over a reserved key (2026-10-26).
  - `config_format`, the block returning anything that can be written as
    JSON (the user's point, 2026-10-26); YAML stays built in (`8737fe5`).
    A format can have several extensions, named on the call
    (`config_format("yaml", "yml")`), not paired by Jargon (the user
    chose this, 2026-10-26; `6ab33e2`). More specs in `cb64746`.
  - Project config per subcommand deferred until a program needs it (the
    user, 2026-10-26); the shape that adds it without breaking anything
    is in jargon.cr's TODO.md.

  Before it, v0.23.1 laid help out in two columns and fixed completion
  after an abbreviated subcommand and for the default subcommand, and
  v0.23.0 made `help(subcommand)` raise `ArgumentError` for an unknown
  subcommand.
- **jargonaut 0.2.0** on crates.io (2026-10-26), published from jargon.rs
  `9a1a884` and tagged `v0.2.0` there (no GitHub release, as before):
  the same sections (`542ce7c`), and `config_format` taking several
  extensions through a `ConfigExtensions` trait, one string or an array,
  slice, or `Vec` of them, owned or borrowed (`44aaffb`, `39f5db5`). Its
  cases are synced from jargon.cr `cb64746`, so it matches v0.24.0. Its
  API docs are docs.rs's.

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
  jargonaut 0.2 from crates.io and `cli.parse()` (`cf8d15e`, `93c9853`).
  Its help demos show v0.23.1's two columns (`c8102e0`), and its terminal
  scrolls long lines sideways on a phone rather than wrapping them
  (`5946a8e`).
- **A `ui:` keyword**: a strong proposal (the user's words, 2026-06-12) to
  bless `ui:` as a first-class opaque keyword, like `service:`, as sugar
  for GUI hints, which today go in `x-ui`. Not decided; don't treat it as
  settled.
- **Follow-ups for completions, positionals and config loading**: in
  jargon.cr's `TODO.md`.
- **A warning when `project: false` skips a project config that exists**:
  offered to the user on 2026-10-22, not taken up.

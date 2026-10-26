# Status

*Updated 2026-10-26*

## Released

- **jargon.cr v0.23.1** (`a7a1b0c`, 2026-10-26), tagged and on GitHub
  releases, a patch bump (the user, 2026-10-24): help in two columns,
  with an enum's values as `[fast|safe]` and `""` for an empty string
  (the user's choices); completion after an abbreviated subcommand and
  for the default subcommand (the user chose to offer the default's
  values at the first word, 2026-10-25); and the README's "Where Parsing
  Stops", transfs's requirement #3. Before it, v0.23.0 made
  `help(subcommand)` raise `ArgumentError` for an unknown subcommand,
  v0.22.0 fixed the bugs the Rust port found, v0.22.1 named schema types
  in type errors, and v0.22.2 reported a value that doesn't convert once.
- **jargonaut 0.1.1** on crates.io (2026-10-26), published from jargon.rs
  `3360456` and tagged `v0.1.1` there (no GitHub release, as for 0.1.0);
  its cases are synced from jargon.cr `bea8e7a`, so it matches v0.23.1.
  Its API docs are docs.rs's.

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
- **Registered config formats in jargon.cr**, like jargon.rs's
  `config_format`, so a program can use any parser (oyl.cr, say). The
  user: "we might end up doing for the crystal what we did for rust ...
  that makes a lot of sense to me" (2026-10-23). Not decided; to be
  discussed before building, including whether built-in YAML stays.

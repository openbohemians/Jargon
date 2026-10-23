# Status

*Updated 2026-10-23*

## Released

- **jargon.cr v0.22.2** (`29b4cc6`, 2026-10-22), tagged and on GitHub
  releases. v0.22.0 fixed the bugs the Rust port found, v0.22.1 names
  schema types in type errors ("expected integer, got object"), and
  v0.22.2 reports a value that doesn't convert once, not twice.
- **jargonaut 0.1.0** on crates.io (2026-10-23), published from jargon.rs
  `6da8860`, after the user's API review ([port.md](port.md)); its cases
  are synced from jargon.cr `9ba7b9c`. Not tagged in git yet. Its API
  docs are docs.rs's.

## Open

- **The site after publishing**: its Rust tab and demo still show the
  git dependency and `parse(&args)`; they should show `cargo add
  jargonaut` and `parse()`.
- **jargon.cr's `help(subcommand)` raises** for an unknown subcommand
  (part of the same review), in `9ba7b9c`, not yet released; a changed
  public method, so 0.23.0.
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
  jargonaut's are at https://docs.rs/jargonaut.
- **Help layout**, noticed 2026-10-23 while checking the site's demo
  against real output: a description sits at the same indent as a
  long-only flag (six spaces), so it reads as another option, and an
  enum's values aren't listed. The same in both implementations. Not
  discussed with the user yet.
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

# Status

*Updated 2026-10-25*

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
- **Next release: jargon.cr 0.23.1 and jargonaut 0.1.1**, patch bumps,
  since only output and fixes changed (the user, 2026-10-24). Committed,
  not pushed or released:
  - Help in two columns (jargon.cr `660cb9d`, jargon.rs `3673600`). The
    user chose two columns, aligned like `Commands:`, and an enum's values
    as `[fast|safe]` after the description (not "possible values"), then
    `(required)` and `[default: …]`. The column stops 32 characters in; a
    wider flag has its description on the next line.
  - `Commands:` descriptions laid out the same way, an empty string shown
    as `""` (the user's choice), the column limit private (`1611f7e`,
    `926239a`).
  - Completion after an abbreviated subcommand, the TODO follow-up
    (`ca10721`, `096040c`).
  - Completion for the default subcommand: words that name no subcommand
    go to the default, as for `parse`, and the first word offers the
    default's flags and values alongside the subcommand names (the user
    chose that, 2026-10-25; `bea8e7a`, `ba20089`).
  - Where parsing stops, in both READMEs: transfs's requirement #3,
    jargon.cr's `notes/transfs-requirements.md` (`a8b3d15`, `1aede85`).
  - The stale TODO entry for the double variadic error dropped
    (`ea32f23`).

  jargon.rs's cases are synced from `bea8e7a`. The site's two help
  demos (`docs/index.html`, the terminal's in `docs/script.js`) show the
  new layout, committed with this line; push them with the releases,
  since 0.23.0 still prints the old one.
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

# Status

*Updated 2026-10-28*

## Released

- **jargon.cr v0.25.0** (`1dba094`, 2026-10-28), tagged and on GitHub
  releases, and **jargonaut 0.3.0** on crates.io, published from jargon.rs
  `988b369` and tagged `v0.3.0` (the user said to release them,
  2026-10-28). Both break existing CLIs: JSON from stdin is `-@`, and
  arrays split only at a named `separator`. Also in them: repeated array
  options add up, a lone `-` is a value, and a short flag takes an
  attached value; see Conventions, below. The site shows `-@` and
  jargonaut 0.3. jargonaut's cases are synced from jargon.cr `10735d5`,
  the last spec change before v0.25.0.
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
  jargonaut 0.3 from crates.io and `cli.parse()` (`cf8d15e`, `93c9853`).
  Its help demos show v0.23.1's two columns (`c8102e0`), and its terminal
  scrolls long lines sideways on a phone rather than wrapping them
  (`5946a8e`).
- **A `ui:` keyword**: a strong proposal (the user's words, 2026-06-12) to
  bless `ui:` as a first-class opaque keyword, like `service:`, as sugar
  for GUI hints, which today go in `x-ui`. Not decided; don't treat it as
  settled.
- **Follow-ups for completions, positionals and config loading**: in
  jargon.cr's `TODO.md`.
- **Conventions existing commands use that Jargon lacks** (repeated
  options, `-` as an argument, a value attached to a short option, and
  more), found running real command lines against the user's schemas in
  jargon.cr's `schemas/coreutils/`: listed in jargon.cr's `TODO.md`
  (`da75c70`) with priorities I proposed. Released in v0.25.0 and 0.3.0
  (above):
  - the uncontroversial ones (the user, 2026-10-27): repeated array
    options add up, a lone `-` among other arguments is a value, and a
    short flag takes an attached value as getopt does (`-w80`, `-o=x`
    gives `=x`), in jargon.cr `4ae4bf4` and jargonaut `0feb0ae`;
  - arrays split only where a property's `separator` says, from four
    names, not characters (`comma`, `colon`, `semicolon`, `whitespace`,
    or a list), as the user chose (2026-10-28); breaking, in jargon.cr
    `5496d56` and jargonaut `39d617c`;
  - JSON from stdin is `-@` for every CLI, not a lone `-` (the user chose
    it, 2026-10-28, over `--`, a reserved long option, and `@-`; files via
    `-@ < file`), in jargon.cr `10735d5` and jargonaut `09afe6b`; also
    breaking. The site shows it (`196948b`), and `eg/pretty.cr` splits its
    tags at commas (`cd1ee5c`). xerp was mailed (2026-10-28,
    `mail/sent/`): it is pinned at jargon 0.15.0 and has no array
    options, so only `-@` affects it.

  Unreleased: a `*` marks the variadic positional, wherever it is
  (`["sources*", "dest"]`), and the positionals after it take the last
  words of its run, so `cp a b dir/` works. The user proposed the `*` and
  chose to require it (2026-10-28) over keeping the last array implicitly
  variadic. Breaking, in jargon.cr `d1c6fbd` and jargonaut `ee9b420`; the
  README says "Before 0.26.0", the version I'd suggest, not yet decided.
  It also fixed a variadic's run stopping at `--` and dropping the words
  after it.

  Also unreleased: a positional given by name gives up its slot, wherever
  the option is, so `grep -e foo a b` and `cp -t dir/ a b` read right, and
  options can come anywhere among a variadic's words (`cat a -n b`). Help
  lists positionals under Options too, and completion offers them as
  flags. The user wanted no exceptions (2026-10-28): every property is an
  option and `positional` adds the words. They turned down letting `short`
  mark a positional as an option, and asked about defining positionals
  apart from `properties` before choosing this. In jargon.cr `88b0dae` and
  jargonaut `6cad22a`.

  The rest of the list is open; discuss optional option values before
  implementing.
- **CI** runs in both repos since 2026-10-27: jargon.cr on Crystal 1.18.2
  and the latest, with format and ameba; jargonaut on Rust 1.88 and
  stable, with fmt, clippy and docs.
- **A warning when `project: false` skips a project config that exists**:
  offered to the user on 2026-10-22, not taken up.

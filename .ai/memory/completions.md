# Dynamic shell completions

*Updated 2026-10-23*

Shipped in jargon.cr v0.19.0 (`cdfce65`, 2026-06-14), for transfs's
requirement #2: Tab offering candidates the schema can't know, such as
live data. jargon.rs ports the same design. The design was agreed with the
user before it was built; why it is shaped this way:

- **All-callback.** The generated script is a shim: on every Tab it
  passes the cursor index and all the words to a command and prints the
  candidates it gets back. It encodes no grammar, so it never changes when
  the CLI does. The program computes every candidate, static (flags, enums,
  subcommands) and dynamic, in one path.
- **The target command is configurable** (`command:` on the shim
  generators): by default the program itself, or a small helper so a large
  program isn't started on every keypress. A helper only pays off if the
  candidates can be had cheaply (an index, a cache, a daemon); that is the
  program's side, not Jargon's.
- **No schema keyword.** Completers are registered by field path
  (`cli.completer("forget.query") { |ctx| ... }`), and registering one
  checks the path against the schema, so a typo or rename fails at once.
  GUI hints already go in `x-ui`.
- **Two layers.** The wire (shim to program) is raw and frozen: the words
  as real arguments after `--`, plus the cursor index, so an empty word
  isn't lost. What a completer sees is structured and can grow:
  `ctx.partial`, `ctx.subcommand`, `ctx.arguments` (a lenient parse of
  what's typed so far), `ctx.words`.
- **`handle_completion` stands alone**, so a program can answer before its
  heavy setup; `run` calls it first. `__complete` is internal to the shim
  and `handle_completion`; programs never write it.
- No value completion after a boolean flag, since a boolean doesn't take
  the next word (it would clash with positional completion).

**Known limits:** completers apply to root fields only (not `--a.b`);
subcommand abbreviations aren't resolved during completion; the bash shim
needs bash 4 (`readarray`), so not macOS's bash 3.2. Further follow-ups
are in jargon.cr's `TODO.md`.

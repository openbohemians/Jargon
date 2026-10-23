# jargon.rs: the Rust port

*Updated 2026-10-23*

Started 2026-10-22 at the user's request. It covers all of jargon.cr's
API: parsing, subcommands, multi-document schemas, validation, defaults,
environment variables, JSON on stdin, help, merge, flatten, completion
(engine, completers, bash/zsh/fish shims), config loading and `run`.

## How it stays in step

- jargon.cr's `conformance/recorder.cr` wraps the public API. It is
  compiled in only when `JARGON_RECORD` is set (`just conformance`, via a
  macro in `spec/spec_helper.cr`), and a spec run then writes each call's
  inputs and results to `conformance/*.json`.
- jargon.rs copies them with `just sync` (`scripts/sync-conformance.sh`,
  from `../jargon.cr` unless given a path), which writes the source commit
  to `tests/conformance/COMMIT`; `tests/conformance.rs` replays them.
  Deliberate differences are its `DIFFERENCES` list.
- YAML ops carry `documents`, the YAML's documents as JSON (null when the
  YAML doesn't parse), so jargon.rs replays them without a YAML parser.
- Config loading and `run` aren't recorded; unit tests cover them in
  jargon.rs.
- After a change to jargon.cr: `just conformance` there, then `just sync`
  and `cargo test` in jargon.rs.

## Decided (the user, 2026-10-22)

- The crate is `jargonaut`, since `jargon` is taken on crates.io. Edition
  2024, MSRV 1.88 (it uses let-chains).
- No YAML: users convert YAML to JSON with whatever library they like. In
  its place, `Cli::from_values(docs, program)` takes documents already
  parsed, and `cli.config_format(ext, parse)` adds a config format, tried
  ahead of JSON.
- Its dependencies are serde_json (`preserve_order`), indexmap and
  fancy-regex.

## Open: the API shape, for the user's review

`set_` setters; `ParseOptions`; a panic on a CLI with neither a schema nor
subcommands; the name `help_for`; the `Shell` enum; the completer
signature; `handle_completion` not exiting; `ConfigOptions`, with warnings
a per-call field instead of jargon.cr's global switch; `config_paths`
taking `ConfigOptions`; `run` taking explicit args.

## Lessons

- Porting found six bugs in jargon.cr, fixed in v0.22.0 (`774e78d`) and
  listed under Completed in its `TODO.md`. Nested help, ipv4 and ASCII
  digits were wrong in jargon.rs as well.
- Crystal's PCRE2 regexes have UCP on, so `\d` and `\s` match Unicode
  there as they do in Rust. Formats use `[0-9]` and `\A…\z` in both, and
  jargon.cr compiles `pattern` with DOLLAR_ENDONLY, which keeps UCP. An
  earlier claim that only Rust's were Unicode was wrong.
- Crystal's YAML makes a plain `2026-10-22` a time. `Jargon::YAMLReader`
  keeps such a scalar as the text it was written as.

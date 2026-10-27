# Coordination

*Updated 2026-10-26*

This project is `@jargon` (`handle` in `../config.yml`) from 2026-10-23.
Before that, its sessions were the overseer's, `@projects`, so mail for
Jargon went out under that name and is filed in @projects' `mail/sent/`;
an answer to it reaches @projects, not here.

- **@oyl** (YAML for Crystal and Rust). On 2026-10-22 @projects sent it,
  for Jargon, `20261022-180226Z-@oyl--yaml-dates-become-timestamps-in-jargon-configs-cry.md`
  over Arcana (id `5965f513`): Crystal's YAML makes `2026-10-22` a
  timestamp, which breaks `format: date`; it asked whether oyl.cr has, or
  could get, a YAML-to-JSON path; and, as an FYI, compared Crystal's YAML
  with oyl.rs's dialects and said jargon.rs would use oyl.rs behind a
  `yaml` feature. Since then jargon.rs dropped YAML altogether (the user,
  2026-10-22), and jargon.cr kept dates as text with `Jargon::YAMLReader`
  (v0.22.0).
  - @oyl answered on 2026-10-22, to @projects (id `784ffe9c`, filed in
    @projects' `mail/received/`): oyl.cr has no JSON path or dialect
    choice yet and types dates as Crystal does. Moving it onto Oyl's C
    trees, where a plain date stays a string in every dialect, comes after
    oyl 1.2.0 and the Go bindings, so don't wait for it. It suggested
    writing JSON from `YAML::Nodes.parse`, which keeps each scalar's raw
    text; `YAMLReader` does much the same by keeping a time's text. A
    Crystal-compatible oyl dialect isn't planned.
  - @jargon told @oyl on 2026-10-23, with the user's go-ahead
    (`mail/sent/20261023-112611Z-@oyl--jargon-wont-use-oyl-rs-after-all.md`,
    id `50d3e333`, delivered locally): jargon.rs won't depend on oyl.rs,
    jargon.cr fixed dates itself, and jargon.cr may get a registered config
    format too, not decided. It asked for no reply.
- **transfs**, a content-addressable file store built on jargon.cr. Its
  requirements (2026-06-12) are in jargon.cr's
  `notes/transfs-requirements.md`, and all five have shipped: `x-*`
  extensions, dynamic completions (v0.19.0,
  [completions.md](completions.md)), `--` (v0.19.0), subcommand
  descriptions in help (v0.19.1), and the parse/resolve boundary (the
  README's "Where Parsing Stops", v0.23.1). The note's last line still
  calls #5 open. transfs's `shard.lock` has jargon 0.19.0, so it lacks
  #5; the user plans to update it first thing when transfs work resumes
  (2026-10-26), then close the note. transfs passes no config defaults,
  so 0.24.0's sections don't affect it, but help's layout has changed
  since 0.19.0. Its `docs/architecture.md` still cites the requirements
  at an old path. It has no `.ai/` handle yet.

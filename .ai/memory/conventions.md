# Conventions

*Updated 2026-10-23*

## Designing APIs (the user)

- Exact, explicit lookups over convenience aliasing. The user had
  `Property#extension("ui")`, which also matched `"x-ui"`, removed: "If so
  then they should be explicit." Extensions are read as written
  (`extensions["x-ui"]?`). Implicit normalization makes shapes that aren't
  supported look supported.
- Raise design choices and discuss them before implementing; "there
  aren't just givens".
- Commit and push only when the user asks.

## jargon.cr's lint (ameba 1.7.0)

- `just ameba` builds it (1.7.0 no longer builds `bin/ameba` on install),
  then `just lint`. Clean as of 2026-10-22.
- `Style/MultilineStringLiteral` is off in `.ameba.yml`: inline `%({...})`
  schemas are the spec idiom.
- A bare `return`, not `return nil`. The nilable defaults parameter is
  written `Defaults?` (`alias Jargon::Defaults`).
- `valid_format?` in `validator.cr` is a plain `case` calling one
  `valid_format_<name>?` per format. The user chose it over a Proc table
  ("worse") and over macro dispatch. It scores 11 of ameba's 12, so one
  more format fits; after that, an inline `# ameba:disable` rather than a
  restructure.

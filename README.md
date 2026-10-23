# Jargon

The project folder for Jargon, command line parsing via JSON Schema: a
program describes its options as a schema, and Jargon parses, validates
and documents its command line from it. Jargon is two implementations:
[jargon.cr](https://github.com/openbohemians/jargon.cr) in Crystal (the shard
`jargon`), and [jargon.rs](https://github.com/openbohemians/jargon.rs) in
Rust (the crate `jargonaut`), which replays cases recorded from the Crystal
spec suite to stay in step. This repository holds neither's code. It holds
what they share: `.ai/`, the notes and mail of the project's agent,
`@jargon`, kept the dot-ai way.

```
Jargon/              this repository
  .ai/               the project's notes, mail and config.yml
  docs/              the project's site
  jargon.cr/         its own clone, ignored here
  jargon.rs/
```

A session in either, or in the folder itself, finds `.ai/` by looking
upward, so it is `@jargon` wherever it starts.

## The site

`docs/` is published with GitHub Pages at
[jargon.openbohemians.org](https://jargon.openbohemians.org). The API docs
belong to each implementation: jargon.cr publishes its own from its
`docs/`, at [openbohemians.org/jargon.cr](https://openbohemians.org/jargon.cr/),
and jargon.rs's will be on docs.rs once the crate is published.

## Setting up

```sh
git clone git@github.com:openbohemians/Jargon.git
cd Jargon
git clone git@github.com:openbohemians/jargon.cr.git
git clone git@github.com:openbohemians/jargon.rs.git
```

The repositories are listed under `repos:` in `.ai/config.yml`.

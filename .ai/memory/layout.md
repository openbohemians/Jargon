# Layout: one project, three repositories

*Updated 2026-10-23*

jargon.cr and jargon.rs are separate repositories, one per language, but
one project, `@jargon`, set up like @arcana's folder (the user,
2026-10-23). The third repository, `openbohemians/Jargon`, holds none of
the code: `.ai/`, committed on its `main`, a README, and a `.gitignore`
naming the other two. Its clone is the project folder, and the code
repositories are clones inside it:

```
Jargon/              clone of openbohemians/Jargon
  .ai/               notes, mail, config.yml
  jargon.cr/         clone of trans/jargon, ignored by Jargon
  jargon.rs/         clone of openbohemians/jargon.rs
```

The Crystal clone is named `jargon.cr` (the user, 2026-10-23), so the two
read as implementations of one thing. Its GitHub repository is still
`trans/jargon`, and the shard stays `jargon`. The user expects the
repository to become `jargon.cr` too ("probably", 2026-10-22); **not
done**. If it is renamed, update `repos:` in `../config.yml`, the clone
line in the README and below, and the links to `github.com/trans/jargon`
in jargon.rs's README and jargon.cr's `conformance/README.md`.

A session in either, or in the folder itself, walks up to the nearest
`.ai/` and is `@jargon`. Git for the notes works from anywhere in the
folder: `git -C .ai ...` from the folder, `git -C ../.ai ...` from a code
repository. jargon.rs's `just sync` copies conformance cases from
`../jargon.cr` by default, the clone beside it (see [port.md](port.md)).

**History.** Until 2026-10-23 the two were checked out side by side with
no `.ai/` of their own, so their sessions were the overseer's,
`@projects`, and mail went out under that name (see
[coordination.md](coordination.md)). The agent's per-machine memory from
those sessions was moved into these notes when the folder was set up.

## Setting up on a machine

```sh
git clone git@github.com:openbohemians/Jargon.git
cd Jargon
git clone git@github.com:trans/jargon.git jargon.cr
git clone git@github.com:openbohemians/jargon.rs.git
```

The two are listed under `repos:` in `../config.yml`. Cloning isn't
automatic, as in @arcana's folder (the user's decision there,
2026-10-17): an agent that finds one missing offers to clone it.

Claude Code files a session's memory under the folder it starts in, so
sessions started in the folder and in a code repository keep separate
memory. Project facts go here, where every session finds them.

## Off the dot-ai spec

As in @arcana's folder: the spec has `.ai/` as a worktree of the code
repository's orphan `ai` branch, while here it is committed on `main` of a
repository of its own, and `repos:` is a key the spec doesn't have yet.
@arcana described both to @ipck, the spec's keeper, on 2026-10-17.

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
  jargon.cr/         clone of openbohemians/jargon.cr, ignored by Jargon
  jargon.rs/         clone of openbohemians/jargon.rs
```

The Crystal repository is `jargon.cr`, so the two read as implementations
of one thing; the shard is still `jargon`. It was `trans/jargon` until
2026-10-23, when the user had it moved to openbohemians and renamed. GitHub
redirects the old URL, git included, as long as no new `trans/jargon` is
created; its Pages site moved from `trans.github.io/jargon` (now a 404) to
`openbohemians.org/jargon.cr`. See [status.md](status.md) for what still
names the old path.

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

## The site

Decided by the user, 2026-10-23: the home page is the project's, so it
lives here, in `docs/`, published with GitHub Pages at the subdomain
`jargon.openbohemians.org` (`docs/CNAME`). A subdomain, because Pages
paths are case-sensitive: this repository's default would be
`openbohemians.org/Jargon/`, and `/jargon/` would 404. The API docs stay
with each implementation, so a release never needs a commit here:

- jargon.cr's Pages serves only its API docs, generated into the root of
  its `docs/` (`just doc`, which starts from an empty `docs/`, so pages of
  removed types don't linger), at `openbohemians.org/jargon.cr/`.
- jargon.rs has no Pages site; its API docs are docs.rs's, built from
  each version published to crates.io.

The page came from jargon.cr's `docs/` (its history is there, through
`9c9356f`) and was made to cover both
languages: Crystal and Rust tabs, an "Oxidize" demo beside "Crystallize",
and demo output taken from real runs of both. `openbohemians.org` is at
Dynadot; the org repository's `DNS-SETUP.md` says how its records are set.
The subdomain is a CNAME record, `jargon` to `openbohemians.github.io`
(the user added it, 2026-10-23); the organization's verification of
`openbohemians.org` covers it.

**Lesson (2026-10-23):** Pages was given the custom domain before the
DNS record resolved, and GitHub never requested a certificate: no
`https_certificate` after 30 minutes, and re-saving the same domain did
nothing. Removing the domain and adding it back got one approved within
a minute. For a branch-published site that makes GitHub commit "Delete
CNAME" and "Create CNAME" to `main` (`4f36950`, `df40fa1`), so pull
afterwards. Then turn on Enforce HTTPS.

## Setting up on a machine

```sh
git clone git@github.com:openbohemians/Jargon.git
cd Jargon
git clone git@github.com:openbohemians/jargon.cr.git
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

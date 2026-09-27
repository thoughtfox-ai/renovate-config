# renovate-config

Public mirror of ThoughtFox's shared Renovate preset. It exists for one reason: Renovate resolves
a `github>owner/repo//path` preset using the GitHub account's own installation token, which cannot
read a **private** repo owned by a *different* account. `thoughtfox-ai/FoxKit` (the source of
truth for this preset) is private, so any repo outside the `thoughtfox-ai` org — personal repos
under `nikibh`, the `ClarindaVentures` repos, `Lelylaan-Ventures/Website` — could not extend it.

This repo holds only [`default.json`](default.json): the preset's rules. No code, no secrets, no
credentials — a plain copy of `packages/tooling/config/renovate/default.json` from FoxKit.

## Source of truth

**Edit `thoughtfox-ai/FoxKit`, not this repo.** `packages/tooling/config/renovate/default.json` there is
the real file; this one is a manually-synced copy. After any change to FoxKit's preset, copy the
updated file here verbatim and push. There is no automation for this yet — check FoxKit's
`memory.md` for the current sync process before assuming one exists.

## Usage

In any repo's `renovate.json`:

```json
{ "extends": ["github>thoughtfox-ai/renovate-config"] }
```

Repos that are members of the `thoughtfox-ai` org (or otherwise have read access to
`thoughtfox-ai/FoxKit`) should extend the private original instead:
`github>thoughtfox-ai/FoxKit//renovate/default`.

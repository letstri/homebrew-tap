# letstri/homebrew-tap

Homebrew formulae for [letstri](https://github.com/letstri)'s projects.

```sh
brew install letstri/tap/<formula>
```

`brew` resolves `letstri/tap` to this repository, so no `brew tap` step is needed first.

## Formulae

| Formula | Project | Maintained by |
| --- | --- | --- |
| `druk` | [druk](https://github.com/letstri/druk) — a terminal code editor | generated |

## How formulae get here

A **generated** formula is written by its own project's release workflow, which commits it
here on every release with checksums matching the archives that release actually uploaded.
Do not edit one by hand — the next release overwrites it. The generator is the place to fix
anything wrong with it (for druk, `scripts/formula.ts`).

A hand-written formula is fine too; nothing here assumes every file is generated.

## Adding another project

The project needs a job in its release workflow that checks this repository out and commits
`Formula/<name>.rb`. That job authenticates with a fine-grained PAT — `contents: write` on
this repository alone — stored as a secret in the project's own repository, because a
workflow's built-in `GITHUB_TOKEN` cannot write to a different repository. druk's `tap` job
in `.github/workflows/release.yml` is the working example.

Two things to keep in mind once more than one project publishes here: each writes only its
own `Formula/<name>.rb`, and two releases landing at the same moment can collide on the
push, so a job worth trusting retries on top of whatever it finds.

Leave `main` unprotected — the release jobs push to it directly as `github-actions[bot]`.

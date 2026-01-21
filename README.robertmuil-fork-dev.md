# Dev Branch for forked work

Experimenting here with using a `dev` branch for everything that will not be pushed upstream AS WELL AS everything that will.

`main` should only be updated from rdflib/main (from the original repo).

`dev` should *never* be merged into `main` (nor should any other branch).

This means we can maintain some changes that are local to this fork - e.g. converting the `pyproject.toml` to use uv.

This might be cumbersome. Let's see.

## Features *not* intended for upstream


These features can be merged directly into `dev`, and the branches can be deleted, because we don't need to preserve the individual set of changes for proper PR upstream.

This is the workflow for branches that are not intended for merging into origin fork.
1. create a new branch `forkonly-<name>`
2. make changes there
3. PR to `dev`
4. merge
5. delete `forkonly-<name>`

Alternatively:
6. make changes directly in `dev`

## Features intended for upstream

New features should be PRed into `rdflib/main`, and thus until they're accepted they won't be in our `main`.
We can also merge those feature branches into `dev` but we don't merge into `main`.

1. create a new branch `<name>` (no naming convention other than *not* starting with `forkonly-`
2. make changes there
3. PR to `dev`
4. merge
5. PR to `rdflib/main`
6. merge
7. Sync `rdflib/main` to `main`
8. delete new branch `<name>`

**NB: it's important that the new feature branch is *not* deleted before it is merged to `rdflib/main` because there is no other way of determining what commits are intended for upstream and what are not.**

## Features in Fork

These are the features in the fork that are intended for PR to upstream but not yet in the original repo. These should all correspond to a branch, until they are merged upstream.

1. 
1. 

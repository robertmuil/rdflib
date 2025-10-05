# Dev Branch for forked work

Experimenting here with using a `dev` branch for everything that will not be pushed upstream AS WELL AS everything that will.

`main` should only be updated from rdflib/main (from the original repo).

New features should be PRed into rdflib/main, and thus until they're accepted they won't be in our main.
We can also merge those feature branches into `dev` but we don't merge into `main`.

This means - we can maintain some changes that are local to this fork - e.g. converting the `pyproject.toml` to use uv.

This might be cumbersome. Let's see.

Suggest using `<name>-forkonly` for branches that are not intended for merging into origin fork.
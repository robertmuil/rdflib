# Dev Branch for forked work

Experimenting here with using a `dev` branch for everything that will not be pushed upstream AS WELL AS everything that will.

`main` should only be updated from rdflib/main (from the original repo).

New features should be PRed into rdflib/main, and thus until they're accepted they won't be in our main.
We can also merge those feature branches into `dev` but we don't merge into `main`.

This means - we can maintain some changes that are local to this fork - e.g. converting the `pyproject.toml` to use uv.

This might be cumbersome. Let's see.

Suggest using `<name>-forkonly` for branches that are not intended for merging into origin fork.

## Features in Fork

These are the features in the fork and not yet in the original repo. These should all correspond to a branch, I think.

1. `uv`
1. 

## Tasks

This is a list of things to do in this fork.

1. Make a `Triple` class easy to get to for type-checking (and creation)
1. Allow a `DefinedNamespace` to be generated from an RDFS/OWL ontology.
    - already implemented!
1. When adding a `DefinedNamespace` to a `Graph`, add new methods to the `Graph` object that allow type-checked addition of each defined property:
    1. a `Graph` to which a `DefinedNamespace` is bound will have, for every property in the namespace, a method called `g.add<PropertyID>(subject: <domain>, object: <range>)` added to it.
        1. `<PropertyID>` is a suitably processed (CamelCase?) string taken from the property's local name (and potentially prefix, see below)
        1. `<domain>`is the Python class corresponding to the domain of the property
        1. `<range>` is likewise for range
    1. e.g. a `DefinedNamespace` called `ex` defines `ex:sumpin` whose domain is `ex:Machine` and range is `foaf:Agent` and is bound to a `Graph` `g` - then there will method `g.addSumpin(subject: <domain>, object: <range>)` 
    1. Q: should we add the namespace always to the PropertyID? Will avoid conflicts... but make usage with most graphs more difficult.
        1. perhaps offer it as a default-True option when creating the graph?
# ts-rs (dx-corp projection)

This repository is a generated projection of dx-corp/mono. Do not edit it
directly; changes land in Mono and are published here.

`macros/` is `ts-rs-macros` 12.0.1 from
[Aleph-Alpha/ts-rs](https://github.com/Aleph-Alpha/ts-rs) at commit
`7182ad8289596097235406b715fa04506443b4ad` (path `macros`), MIT licensed
(`LICENSE`), with one repair in `macros/ts-rs-macros-12.0.1.patch`: the derive
emits its dependency visits and generated `where` bounds in a sorted order
instead of `HashSet` order, so two compilations of the same source expand
identically (required for Bazel pipelined compilation and reproducible
builds). Generated TypeScript is unchanged.

Upstream pull request: pending. The repair is dropped once an upstream release
contains it.

## Validation

From the repository root, check the standalone macro crate with:

```sh
cargo check --manifest-path macros/Cargo.toml
```

There is no committed lockfile in this source projection; Cargo resolves the
manifest's dependencies and creates a local lockfile. The publication validator
checks the standalone `ts-rs-macros` 12.0.1 proc-macro identity, local dependency
closure, required source files, and that the included patch matches the applied
repair. Destination CI supplies the compilation check above.

Compilation confirms the crate builds. It does not establish deterministic
macro expansion: that requires comparing expansions of the same derive input
across independent compiler processes, including dependency visits and generated
`where` bounds.

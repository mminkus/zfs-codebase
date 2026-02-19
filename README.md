# How to Read the OpenZFS Codebase

A guided walkthrough for engineers who want to navigate, understand, and contribute to OpenZFS.

This isn't "what ZFS is." It's "if you're new to the OpenZFS codebase, here's how I would approach understanding it."

## The Series

1. **[Architecture Overview](docs/01-architecture-overview.md)** — Mental model of the ZFS layer stack: SPA, DMU, ZIO, DSL, ZPL, ARC, and how they connect.

2. **[Repository Layout](docs/02-repo-layout.md)** — Directory-by-directory map of the OpenZFS source tree. What lives where and why.

3. **[The I/O Path](docs/03-io-path.md)** — Trace a 4KB write from `write()` syscall through ZPL, DMU, ZIO pipeline, VDEV layer, to disk.

4. **[Block Pointers in Code](docs/04-block-pointers.md)** — How `blkptr_t`, DVAs, checksums, and compression map from on-disk format to source code.

5. **[Feature Flags](docs/05-feature-flags.md)** — How ZFS manages feature compatibility: registration, enabling, activation, and how to add your own.

6. **[Contributing Guide](docs/06-contributing-guide.md)** — Building OpenZFS, running tests, using `zdb`/`zhack`/`ztest`, and submitting changes.

## Source Reference

All source references point to the [OpenZFS repository](https://github.com/openzfs/zfs). Clone it locally to follow along:

```bash
git clone https://github.com/openzfs/zfs.git
```

## License

MIT

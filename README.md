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

7. **[Pool Import](docs/07-pool-import.md)** — How a pool comes up: userland label scanning, the `spa_load` state machine, trusted vs untrusted configs, MMP, feature gates, rewind, and where imports fail in practice.

8. **[Send and Receive](docs/08-send-receive.md)** — The replication path: the stream format as a compatibility contract, the kernel send pipeline, the receive gauntlet, resume tokens, raw sends, and a worked case study of a real stream-contract bug.

9. **[The Debugging Toolbox](docs/09-debugging-toolbox.md)** — zdb, zhack, zinject, ztest, and the kernel-side observability suite; why the userland tools are libzpool pool imports, and what that means in practice.

## Status

The planned series is complete. In August 2026 every chapter was
cross-referenced claim-by-claim against the OpenZFS source: function
names, call chains, constants, and line anchors verified at the
reference revision below.

The guide is maintained: it receives occasional updates as OpenZFS
evolves. Corrections are welcome -- if a claim here disagrees with the
OpenZFS source, the source is right and this is a bug.

Possible future chapters, in no particular order: ARC and dbuf
lifecycle, scrub and resilver, DSL internals and sync tasks, and the
locking model.

## Source Reference

All source references point to the [OpenZFS repository](https://github.com/openzfs/zfs). Clone it locally to follow along:

```bash
git clone https://github.com/openzfs/zfs.git
```

Reference revision used for line-number anchors in this guide:

- OpenZFS commit `0f9564e85b0103aef43951cd931cb88fa9a68d6c` (master, 2026-02-16)

Line numbers will drift as OpenZFS evolves. When they do, use the symbol/function names in each chapter (`rg`/search in tree) to relocate the code quickly.

Related on-disk format documentation:

- https://github.com/mminkus/zfs-ondiskformat/

## Contributing & Community Links

- Main PR and commit procedure: https://github.com/openzfs/zfs/blob/master/.github/CONTRIBUTING.md
- OpenZFS "Participate": https://openzfs.org/wiki/Participate
- OpenZFS "Developer resources": https://openzfs.org/wiki/Developer_resources
- OpenZFS GitHub contribution entrypoint: https://github.com/openzfs/zfs/contribute

## License

MIT

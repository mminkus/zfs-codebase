# How to Read the OpenZFS Codebase

> A guided walkthrough for engineers who want to navigate, understand, and contribute to OpenZFS.

This is not "what ZFS is." It is "if you are new to the OpenZFS codebase, here is how I would approach understanding it."

## The Series

1. **[Architecture Overview](01-architecture-overview.md)** -- Mental model of the ZFS layer stack: SPA, DMU, ZIO, DSL, ZPL, ARC, and how they connect.
2. **[Repository Layout](02-repo-layout.md)** -- Directory-by-directory map of the OpenZFS source tree. What lives where and why.
3. **[The I/O Path](03-io-path.md)** -- Trace a 4KB write from `write()` syscall through ZPL, DMU, ZIO pipeline, VDEV layer, to disk.
4. **[Block Pointers in Code](04-block-pointers.md)** -- How `blkptr_t`, DVAs, checksums, and compression map from on-disk format to source code.
5. **[Feature Flags](05-feature-flags.md)** -- How ZFS manages feature compatibility: registration, enabling, activation, and how to add your own.
6. **[Contributing Guide](06-contributing-guide.md)** -- Building OpenZFS, running tests, using `zdb`/`zhack`/`ztest`, and submitting changes.
7. **[Pool Import](07-pool-import.md)** -- How a pool comes up: userland label scanning, the `spa_load` state machine, trusted vs untrusted configs, MMP, feature gates, rewind, and where imports fail in practice.
8. **[Send and Receive](08-send-receive.md)** -- The replication path: the stream format as a compatibility contract, the kernel send pipeline, the receive gauntlet, resume tokens, raw sends, and a worked case study of a real stream-contract bug.
9. **[The Debugging Toolbox](09-debugging-toolbox.md)** -- zdb, zhack, zinject, ztest, and the kernel-side observability suite; why the userland tools are libzpool pool imports, and what that means in practice.

## Following Along

All source references point to the [OpenZFS repository](https://github.com/openzfs/zfs). Clone it locally:

```bash
git clone https://github.com/openzfs/zfs.git
```

Line-number anchors are pinned to OpenZFS commit `0f9564e85b0103aef43951cd931cb88fa9a68d6c` (master, 2026-02-16). Line numbers drift as OpenZFS evolves; when they do, use the symbol and function names in each chapter to relocate the code quickly.

The planned series is complete; every chapter has been cross-referenced claim-by-claim against the OpenZFS source. If a claim here disagrees with the source, the source is right and this is a bug -- [corrections welcome](https://github.com/mminkus/zfs-codebase).

Companion on-disk format reference: [ZFS On-Disk Format](https://github.com/mminkus/zfs-ondiskformat/).

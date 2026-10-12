# Repolex Knowledge Graph of Tinche/aiofiles

RDF knowledge graph data for [Tinche/aiofiles](https://github.com/Tinche/aiofiles), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download Tinche/aiofiles
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 3c2180f7f45f1f7f374f3281597fb4144e901e38
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 3c2180f7f45f1f7f374f3281597fb4144e901e38
│           └── chunk-001.nq.gz
├── blob
│   ├── 0e625909b6c960ebed4a0ed99941b28156fbf2d1.nq.gz
│   ├── 0f8a25a9d448496f262d432590487b764a229731.nq.gz
│   ├── 153d65d58be3606da2fd1cacc8ce193237d15b5b.nq.gz
│   ├── 1cf401e3ea3ee74db9b16395c195fb20a3552202.nq.gz
│   ├── 2b78374454cd946d673e4a11e034473883ea3131.nq.gz
│   ├── 2c75becaf7d7341a24fccc2c095f5333ec2469a8.nq.gz
│   ├── 31e43ac52d1a29604e1287270f3d8b568d426b86.nq.gz
│   ├── 3aa8657ebcc9e5066982ce446656257b34a7afc0.nq.gz
│   ├── 5084e0ac1197d237d288b09392ce996bd74ae4ab.nq.gz
│   ├── 53614c34a2ce58157b1110644eaf8ee31bededa2.nq.gz
│   ├── 5f62158ed47f905112bb2f594ba4de7e711551e8.nq.gz
│   ├── 63fcaff25959472c3282674a0c9e95160a8210b7.nq.gz
│   ├── 6670083be27501d6880a1edd7dbaa6502a451456.nq.gz
│   ├── 6c77f826f0e1ed8ad7d575e4ffa33ffd65c3a8e9.nq.gz
│   ├── 7959c2138e7a241bb3e75d3ef8d9751073552141.nq.gz
│   ├── 8054034d2bba3bbe24485a8b94e868dc58e94b82.nq.gz
│   ├── 8ae503276d65ce2a21dcae3dfebd5c715f5d5fca.nq.gz
│   ├── a690c6268862a83d7c75f5d9c9b04e60a11dd51e.nq.gz
│   ├── ad471007bd7f5983d273b9584e5629230150fd54.nq.gz
│   ├── b3b5b4bac93425048e6434c8a955db72e9b2a034.nq.gz
│   ├── b4cd5caef07806f53c440bb9742ebbfab61ce657.nq.gz
│   ├── cbb75e289da52ef1e91a9ad1aa032cecc0f6cfa7.nq.gz
│   ├── ccae1b8cae28bb4d9809dc05008cd0fde6a8b131.nq.gz
│   ├── d134f281ef732a3697f32b24b42ce8c4c07f9019.nq.gz
│   ├── d8f8be384f7001f05ea2cb2880c35560ef1c611c.nq.gz
│   ├── da9c516dd744b6c88dd8c91f58f7bcf8f7e8341b.nq.gz
│   ├── dfd7ced0b6d70a021a219bf4353f952ceedaa0ff.nq.gz
│   ├── e06d2081865a766a8668acc12878f98b27fc9ea0.nq.gz
│   ├── e56b197a3cf69dc2d955504544a1b5b3bde87941.nq.gz
│   ├── eb975036a58ce74da0ba6e3e9faaafad6d3149cf.nq.gz
│   ├── ed38a36e21db843b09959d83b00266214016eee6.nq.gz
│   ├── f47f15018a7fa0d4c912b83aa1c9b729e6da0be1.nq.gz
│   ├── fd86f7cc76e00ab66bf598f95e73dfaa33a6a463.nq.gz
│   └── fd9767a8aea444343b030f200fc04268c5a35182.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 3c2180f7f45f1f7f374f3281597fb4144e901e38.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 42 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[Tinche/aiofiles](https://github.com/Tinche/aiofiles)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*

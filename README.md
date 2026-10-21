# Repolex Knowledge Graph of glue-viz/glueviz

RDF knowledge graph data for [glue-viz/glueviz](https://github.com/glue-viz/glueviz), parsed by [repolex](https://repolex.ai).

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
rlex download glue-viz/glueviz
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 7b3845a736d94bf81a10c4ca8b893d601dfab381
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 7b3845a736d94bf81a10c4ca8b893d601dfab381
│           └── chunk-001.nq.gz
├── blob
│   ├── 0c43bffcb8d2b0b962c0fb76765b29fc4233d062.nq.gz
│   ├── 788a16b26bf43b6bd6daa661eea8747d90770888.nq.gz
│   ├── 7ac89dfd8a920faac3eb74ea16c3b8a92ccc8252.nq.gz
│   ├── a2c2c72a4ad3ec67f1c572b8d4ab941a4ff178b5.nq.gz
│   ├── bd10190fa6ba50748833e8c5052c80fbc719c562.nq.gz
│   └── e77210d61c5af6b416a8a40a5657007acdb2a151.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 7b3845a736d94bf81a10c4ca8b893d601dfab381.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 13 files
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

[glue-viz/glueviz](https://github.com/glue-viz/glueviz)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*

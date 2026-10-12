# Repolex Knowledge Graph of datasette/datasette-llm

RDF knowledge graph data for [datasette/datasette-llm](https://github.com/datasette/datasette-llm), parsed by [repolex](https://repolex.ai).

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
rlex download datasette/datasette-llm
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── b54d325aa3c8c5498d238b2c72dee5764cabc7be
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── b54d325aa3c8c5498d238b2c72dee5764cabc7be
│           └── chunk-001.nq.gz
├── blob
│   ├── 19f8f036ff0d650b7713bcec7b512071b7792d7c.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 2ea048e409457cc9d0227c18d4e8aa797275d8d5.nq.gz
│   ├── 3eb871944ba060e652582342cecb018b41f78bda.nq.gz
│   ├── 480809590fe34236e5289680ea9b83562a78784e.nq.gz
│   ├── 7b493a993eb2995cc6c54f1d50bdf9edffe13755.nq.gz
│   ├── d49d309499efb2c0c1d38efdd53056249a7d74d8.nq.gz
│   ├── eb22e74eaaaf0edc4aa2c0f8900a55750d1660f9.nq.gz
│   └── f4fb56e2907dfc47694af56cd0624101882cb079.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── b54d325aa3c8c5498d238b2c72dee5764cabc7be.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 17 files
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

[datasette/datasette-llm](https://github.com/datasette/datasette-llm)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*

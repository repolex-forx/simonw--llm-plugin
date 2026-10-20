# Repolex Knowledge Graph of simonw/llm-plugin

RDF knowledge graph data for [simonw/llm-plugin](https://github.com/simonw/llm-plugin), parsed by [repolex](https://repolex.ai).

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
rlex download simonw/llm-plugin
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 06510bdd7d431b13cbd20bcd0d5340d912459672
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 06510bdd7d431b13cbd20bcd0d5340d912459672
│           └── chunk-001.nq.gz
├── blob
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 27956bc58c08b54f3db04222127c1401b1347b3b.nq.gz
│   ├── 32c2dd06a0650ae07cd0278616c9c94342a62152.nq.gz
│   ├── 344dd6d6f1ebdccac9e24b470511bdb7ebe3b572.nq.gz
│   ├── 4079898401123cb38009fbc49175d02d937b77ae.nq.gz
│   ├── 433dd0fd24401ed03c6ce263cebd27b5841b24fa.nq.gz
│   ├── 556340df664c494d91a742eee6105374f7dd6605.nq.gz
│   ├── 6d1a2a6a3dafd9cd91546661d1c639e135621400.nq.gz
│   ├── 89a420fa091d66f6a225674c8ed702ca8d8c9f83.nq.gz
│   ├── 96408826a93670b675f043bbad368650fdd83a0b.nq.gz
│   ├── a89254357634116be643a28e1e214432a71c7b87.nq.gz
│   ├── d0d5ce3ee8fa6494d61b4f902ee7d8de943e1b36.nq.gz
│   ├── d84880d1956234d57e3af0d1c63c6aa58e89350c.nq.gz
│   ├── e3feda91c12500ccf3a1bbfd1da4819313ff27ac.nq.gz
│   └── fada1ec06a2048ec019cce2275ed6e89be3c76f3.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 06510bdd7d431b13cbd20bcd0d5340d912459672.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 22 files
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

[simonw/llm-plugin](https://github.com/simonw/llm-plugin)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*

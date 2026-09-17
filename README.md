# Repolex Knowledge Graph of peritus/bumpversion

RDF knowledge graph data for [peritus/bumpversion](https://github.com/peritus/bumpversion), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download peritus/bumpversion
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 769b5c56b566d5300deb0ac05fb5564f31df1ee0
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 769b5c56b566d5300deb0ac05fb5564f31df1ee0.nq.gz
│   └── repolex
│       └── 769b5c56b566d5300deb0ac05fb5564f31df1ee0
│           └── chunk-001.nq.gz
├── blob
│   ├── 05c2f3f06c16b04a0073b9ae35f35044f88dc2a4.nq.gz
│   ├── 13248d37003e5318cedd346957000e5382857b71.nq.gz
│   ├── 160fb6e74e259c17264f282ba9ca591685bcd180.nq.gz
│   ├── 29c7ddc0fbc1cecc288dd2156ad7912c5d8d02e9.nq.gz
│   ├── 2c6efd23bb767b455ebd87e4bb9b4a7f41bafafb.nq.gz
│   ├── 3ac9bab51182582c3f64fa3cb59f79df68716df7.nq.gz
│   ├── 673fea8f5a762153ea533cd8fab3215c387187a5.nq.gz
│   ├── 83b94e0618046e845ef3f8bb013c83717e86a4e7.nq.gz
│   ├── 85b1b604a4f7a638be49e60bfaba14e96fe3f4ac.nq.gz
│   ├── 8951ea8e619d97d651aa55e8dee549b29b31a746.nq.gz
│   ├── abcde0af505905a9349f167c4f60bde237d802ac.nq.gz
│   ├── d33900c5e80c3cfec18f94cd7b571ad88702f9c8.nq.gz
│   └── fc4a12bb51fecafdd5bc703b2b01070c1bb7de24.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 769b5c56b566d5300deb0ac05fb5564f31df1ee0.nq.gz
├── filetree
│   └── 769b5c56b566d5300deb0ac05fb5564f31df1ee0.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 23 files
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

## Source repository

[peritus/bumpversion](https://github.com/peritus/bumpversion)

---
*Parsed on 2026-09-17 by [repolex](https://repolex.ai)*

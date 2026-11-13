<div align="center">

# Mikhail / ManSio

**Engineer-practitioner.** Civil-engineering technician (PGS) by education — I build software the way structures are built: with tolerances, inspection records, and a paper trail.

[🇷🇺 Русская версия](README.ru.md) · [Live portfolio](https://mansio.github.io/MSPortfolio/) · [Writing](https://dev.to/mansio) · [LinkedIn](https://www.linkedin.com/in/ManSio)

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white&labelColor=111418)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white&labelColor=111418)
![MCP](https://img.shields.io/badge/MCP-00d9ff?style=flat-square&labelColor=111418)
![SQLite FTS5](https://img.shields.io/badge/SQLite_FTS5-003B57?style=flat-square&logo=sqlite&logoColor=white&labelColor=111418)
![tree-sitter](https://img.shields.io/badge/tree--sitter-2f3b45?style=flat-square&labelColor=111418)
![Cloudflare Workers](https://img.shields.io/badge/Workers-F38020?style=flat-square&logo=cloudflare&logoColor=white&labelColor=111418)

</div>

## What I build

| Project | What it is | State |
|---|---|---|
| [**mscodebase-intelligence**](https://github.com/ManSio/mscodebase-intelligence) | Local-first code intelligence over MCP: BM25/FTS5 + AST graph, impact analysis, project memory, safe writes. Text-first by default, dense optional. Works with OpenCode and Zed. | `v3.5.0` · Python 3.14 · MIT |
| [**MSPortfolio**](https://github.com/ManSio/MSPortfolio) | A portfolio that is also an MCP server and a proof-of-work engine: every claim an agent makes is traceable to a data record, every chat answer shows the tool calls behind it. | live · GitHub Pages + Workers |
| [**gemma_agent**](https://github.com/ManSio/gemma_agent) | Telegram assistant for a small trusted circle — memory, routing, and tools only when needed. | Python |

## Numbers, and their limits

Every number below is published with the command that regenerates it in
[`docs/FACTS.md`](https://github.com/ManSio/mscodebase-intelligence/blob/main/docs/FACTS.md).
Numbers that do not hold up are published too.

| Claim | Value | Limit |
|---|---:|---|
| Search quality, code, `hit@5` | **0.900** | 48-query panel, measured 2026-10-25 — a snapshot, not re-measured per commit |
| Fast mode, `hit@5` | **0.729** | same panel and date |
| Tools registered / visible by default | **69 / 17** | count depends on `MSCODEBASE_MCP_PROFILE` |
| Language grammars | **31** | graph depth varies by grammar |
| Commit localization on external repos | **12/25** and **17/40** | `grep` scored 19/25 and 20/40 on the same corpora — it wins, and that is written down |

No 95% claim, no "beats RAG", no "better than grep": the measured numbers did not support any of them.

## The passport

Those numbers are records, not adjectives. Seven A4 sheets hand the repository
over the way a construction object is handed over: a cover and register, measured
claims with a validity rule, a dated work log, the ADRs that carry the structure,
the conditions of use, a defect registry where red is reserved for what is
actually open, and an acceptance act.

<img src="https://raw.githubusercontent.com/ManSio/MSPortfolio/main/docs/passport/passport-sheet2.en.svg" width="860" alt="Quality passport, sheet 2: test protocols">

<details>
<summary><b>Sheet 6 — defect registry</b> (the only sheet with red)</summary>

<img src="https://raw.githubusercontent.com/ManSio/MSPortfolio/main/docs/passport/passport-sheet6.en.svg" width="860" alt="Quality passport, sheet 6: defect registry">

</details>

[All seven sheets, RU and EN →](https://github.com/ManSio/MSPortfolio/tree/main/docs/passport)

[All four sheets, RU and EN →](https://github.com/ManSio/MSPortfolio/tree/main/docs/passport)

## How I work

- **Negative results are first-class.** Four rerankers (MiniLM, BGE-base, BGE-M3, Qwen3-0.6B) were measured and rejected: BGE-base cut `hit@1` from 0.688 to 0.625 at 3.1 s per query, and Qwen3-0.6B answered in 29–55 s on a 16-query pilot with `hit@1` 0.500. The rejection stays in the log instead of being deleted.
- **A test that cannot fail is not a test.** Before a fix ships, the implementation is broken on purpose to confirm the test goes red.
- **Living documentation.** Code and its docs change in the same commit; a stale number is a bug.
- **"Tumbler" pattern.** Technology does not dictate architecture — the database, the model, and the transport are swappable parts.

## Writing

- [**PageRank vs RAG on a real codebase**](https://dev.to/mansio/i-measured-pagerank-token-savings-on-a-real-codebase-the-result-will-surprise-you-5bnj) — semantic vs structural retrieval, with two rounds of self-correction.
- [**I asked one AI to fact-check another AI**](https://dev.to/mansio/i-asked-one-ai-to-fact-check-another-ais-audit-of-my-own-code-1ac3) — cross-verification against confident hallucinations in security reviews.
- [**The silent vector contamination bug**](https://dev.to/mansio/the-silent-vector-contamination-bug-why-your-concurrent-embeddings-might-be-lying-to-you-5fg7) — thread safety and memory isolation in concurrent embeddings (OpenVINO).

## Talk to the portfolio

The portfolio is an MCP server, so an agent can interview it instead of scraping it:

```sh
claude mcp add --transport http msp-portfolio https://msp-portfolio.mansio-dev.workers.dev/mcp
```

Ask it anything about the projects above — it answers through tools (`get_projects`, `analyze_stack`, `verify_claim`, `get_known_issues`), not vibes.

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=ManSio&show_icons=true&hide_title=true&bg_color=0d1117&title_color=00d9ff&text_color=c9d1d9&icon_color=00d9ff&border_color=30363d" alt="GitHub stats" height="150" />
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ManSio&layout=compact&hide_title=true&bg_color=0d1117&title_color=00d9ff&text_color=c9d1d9&border_color=30363d" alt="Top languages" height="150" />

</div>

# AI Architect Roadmap

Six-month, public, build-in-public roadmap to position myself as an **AI Solutions Architect** with a focus on **regulated and government workloads** (federal contracting, NIST AI RMF, FedRAMP).

- **Start:** 2026-04-27
- **End:** 2026-10-23
- **Cadence:** Mon–Fri, 60–90 min/day. Optional Saturday deep dives.
- **Author:** [Andrés Varela](https://github.com/Andvarjo) — building [OppyHound](https://oppyhound.com) at GovBidAI.

> Each `/week-XX-*/` folder contains the runnable code for that week's theme plus a short README with the deliverable, decisions, and lessons learned.

---

## Why this exists

I already build production LLM systems (hybrid search + reranking, extraction pipelines, billing). What I need next is the architect-level framing: agents at scale, evaluation as a first-class concern, observability, compliance, and reference architectures I can defend in front of a federal customer. This repo is the trail of that work.

---

## Roadmap by week

### Month 1 — Agentic AI Foundations

| # | Dates | Theme | Public deliverable |
|---|---|---|---|
| 01 | Apr 27 – May 01 | LangGraph básico | [`/week-01-langgraph-basics/`](./week-01-langgraph-basics/) — agent w/ tools + branching |
| 02 | May 04 – May 08 | LangGraph en serio | `/week-02-langgraph-advanced/` — persistence + human approval, Mermaid diagram |
| 03 | May 11 – May 15 | MCP — Model Context Protocol | `/week-03-mcp-basics/` — custom MCP server + agent consumer |
| 04 | May 18 – May 22 | MCP aplicado al dominio federal | `/week-04-mcp-federal/` — federal-contracting MCP server |
| 05 | May 25 – May 29 | Evaluation foundations | `/week-05-eval-foundations/` — eval harness in CI |

### Month 2 — Eval avanzado + Production-ready agent

| # | Dates | Theme | Public deliverable |
|---|---|---|---|
| 06 | Jun 01 – Jun 05 | Evals para extracción a fondo | `/week-06-extraction-evals/` — eval suite + dashboard |
| 07 | Jun 08 – Jun 12 | Evals para agentes | `/week-07-agent-evals/` — agent eval suite + known failure modes |
| 08 | Jun 15 – Jun 19 | Agente OppyHound v1 — opportunity research | `/week-08-opportunity-researcher/` — agent v1 + eval + demo |
| 09 | Jun 22 – Jun 26 | Hardening + Blog post #1 | 🎯 **Blog #1**: *Building Agents for Federal Contracting Research* |

### Month 3 — Observability & MLOps for LLMs

| # | Dates | Theme | Public deliverable |
|---|---|---|---|
| 10 | Jun 29 – Jul 03 | Tracing + observability stack | `/week-10-observability/` — full tracing stack |
| 11 | Jul 06 – Jul 10 | Cost, latency, drift | `/week-11-monitoring/` — monitoring + incident runbook |
| 12 | Jul 13 – Jul 17 | Resilience patterns | `/week-12-resilience/` — reusable resilience library |
| 13 | Jul 20 – Jul 24 | Blog post #2 + production checklist | 🎯 **Blog #2**: *Production-Grade Observability for LLM Systems* |

### Month 4 — Cloud cert + Federal compliance

| # | Dates | Theme | Public deliverable |
|---|---|---|---|
| 14 | Jul 27 – Jul 31 | Cert path + NIST AI RMF intro | `/compliance/nist-ai-rmf-notes.md` |
| 15 | Aug 03 – Aug 07 | Cert + FedRAMP | `/compliance/fedramp-notes.md` |
| 16 | Aug 10 – Aug 14 | Cert deep + mapping exercise | `/compliance/oppyhound-mapping-draft.md` |
| 17 | Aug 17 – Aug 21 | Exam + compliance deliverable | 🎯 **Cloud cert passed** + NIST mapping doc |

### Month 5 — Formal architecture

| # | Dates | Theme | Public deliverable |
|---|---|---|---|
| 18 | Aug 24 – Aug 28 | ADRs y decisiones explícitas | [`/adrs/`](./adrs/) — 4–6 documented decisions |
| 19 | Aug 31 – Sep 04 | C4 model + diagramming | `/diagrams/` — C4 diagrams in repo |
| 20 | Sep 07 – Sep 11 | Reference architecture | `/architecture/reference-architecture.md` |
| 21 | Sep 14 – Sep 18 | Lectura de criterio + reflection | `/notes/architecture-readings.md` |

### Month 6 — Visibility & consolidation

| # | Dates | Theme | Public deliverable |
|---|---|---|---|
| 22 | Sep 21 – Sep 25 | LinkedIn + portfolio polish | 🎯 **LinkedIn rebrand** + featured content |
| 23 | Sep 28 – Oct 02 | Blog post #3 + #4 (drafting) | drafts of blogs #3 and #4 |
| 24 | Oct 05 – Oct 09 | Publication + outreach | 🎯 **Blog #3** (RAG + Federal Compliance) + 🎯 **Blog #4** (LLM-as-Judge) |
| 25 | Oct 12 – Oct 16 | Charla + refinement | 🎯 **Public talk delivered** |
| 26 | Oct 19 – Oct 23 | Cierre + planeación próxima fase | 🎯 **5+ applications sent** + final metrics |

---

## Public deliverables (the ones that move positioning)

- [ ] Wk 09 — Blog post #1: *Building Agents for Federal Contracting Research*
- [ ] Wk 13 — Blog post #2: *Production-Grade Observability for LLM Systems*
- [ ] Wk 17 — Cloud certification passed
- [ ] Wk 22 — LinkedIn rebrand complete
- [ ] Wk 24 — Blog post #3: RAG + Federal Compliance
- [ ] Wk 24 — Blog post #4: LLM-as-Judge
- [ ] Wk 25 — Public talk delivered
- [ ] Wk 26 — 5+ applications to target roles

---

## Repo structure

```
.
├── README.md                       # this file
├── log/
│   └── learning-log.md             # daily/weekly learning journal
├── notes/                          # reading notes (papers, blogs, docs)
├── adrs/                           # Architecture Decision Records
├── specs/                          # agent and feature specs
├── runbooks/                       # operational runbooks
├── compliance/                     # NIST / FedRAMP mapping docs
├── diagrams/                       # C4 + system diagrams (added Wk 19)
├── architecture/                   # reference architecture (added Wk 20)
└── week-XX-<theme>/                # one folder per week, with code + README
```

---

## How I'm tracking this

- Daily plan and progress live in the parent Cowork project (private).
- This repo is the public slice: code, ADRs, notes, public deliverables.
- Each weekly folder has its own README with **goal**, **what's in the box**, **decisions**, and **what I'd do differently**.

---

## License

MIT — see [`LICENSE`](./LICENSE) once added.

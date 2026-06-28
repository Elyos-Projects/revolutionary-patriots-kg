# revolutionary-patriots-kg

> Open, linked knowledge graph of American Revolution patriots, built from public-domain sources.  ·  **Risk tier:** medium  ·  **Status:** proposed (planning)

Build an **open, linked knowledge graph** of American Revolution patriots — people, service,
units, battles, places, kinship, and documentary sources — that anyone can query, cite, and
extend. Each node carries provenance to a primary source.

**Definition of shipped:** A published, openly-licensed, queryable graph with provenance on every assertion, adopted/cited by a partner.

This is an **Elyos** good-deed project. Contributors pull a task, do it with their own coding agent, and open a PR. Platform: https://github.com/jdev1977/elyos

## Planning
- [PROPOSAL.md](./PROPOSAL.md) — why this qualifies as a good deed (Good Deed Definition)
- [PLAN.md](./PLAN.md) — architecture, roadmap & milestones, risks
- [TASKS.md](./TASKS.md) — the full task backlog
- [tasks/](./tasks/) — ready-to-pull task JSON(s)

## Contribute
```bash
elyos browse
elyos pull --task-file tasks/revolutionary-patriots-kg-ontology-001.json --repo Elyos-Projects/revolutionary-patriots-kg
# do the work with your own agent, then:
elyos submit revolutionary-patriots-kg-ontology-001 --repo Elyos-Projects/revolutionary-patriots-kg
```

## Licensing & review
- **Licensing:** Data: CC0/CC-BY-SA (from public-domain sources). NO DAR/SAR scraping. Tooling: MIT.
- **Review:** risk tier **medium** — deeds are *delivered, not merged*; a domain reviewer must sign off before merge.

> Status: this project is in **planning** and not yet ratified through Elyos governance; no adopting partner/requestor is secured yet (`verifiedNeed: false` on delivery-dependent tasks).

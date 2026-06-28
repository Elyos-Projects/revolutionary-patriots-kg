# Proposal: revolutionary-patriots-kg (a knowledge graph of American Revolution patriots)

**Proposer:** jdev1977 (drafted by Claude Code)
**Date:** 2026-06-28
**Domain(s):** open-history, public-data, education, genealogy
**Lane:** donated
**Requestor / beneficiary:** genealogists, historians, educators, students, the public  ·  **Verified need:** yes (no open, linked, queryable graph of Revolutionary patriots exists)

## Summary
Build an **open, linked knowledge graph** of American Revolution patriots — people, service,
units, battles, places, kinship, and documentary sources — that anyone can query, cite, and
extend. Each node carries provenance to a primary source.

## ⚠️ Source & license strategy (read first)
A graph **scraped from the DAR Genealogical Research System or the SAR Patriot Research System
would violate their terms of use and the copyright in their compiled databases** — and is therefore
**out of scope** under Elyos's license/privacy guardrail. Instead:

1. **Build from public-domain & openly-licensed primary sources:**
   - U.S. **National Archives (NARA)** Revolutionary War pension & bounty-land warrant application
     files and compiled service records (U.S. government works → public domain).
   - **Founders Online**, **Library of Congress**, state archives (public domain).
   - **Public-domain DAR/SAR lineage books and genealogical volumes** (older published volumes
     whose copyright has expired) — the *published books*, not the live databases.
   - **Wikidata / Wikipedia** (CC0 / CC-BY-SA) for reconciliation and linking.
2. **Pursue an authorized partnership** with DAR and/or SAR for any data they are willing to share
   under an explicit agreement or open release. Treat their cooperation as the ideal path, scraping
   as never-acceptable.
3. **Privacy:** include only long-deceased historical persons (18th-century patriots). **Exclude
   all data about living applicants/members/contributors.**
4. **Provenance per fact:** every assertion links to its public-domain source and records its license.

## Why it qualifies as a good deed
- **Tangible public benefit:** free, linked, citable history for research and education.
- **Freely available:** graph published as open data (e.g., CC-BY-SA / CC0 where derived from PD).
- **Not primarily for-profit:** an open alternative to paywalled genealogy products.
- **No harm/misinformation:** source-linked claims; conflicting records represented, not flattened.
- **Executable by AI sessions:** decomposes per source document / per patriot / per reconciliation.

## Scope / first tasks
- (small) Ontology (Person, Service, MilitaryUnit, Engagement, Place, Document, KinshipRelation) +
  reuse existing vocabularies (schema.org, Wikidata properties) where possible.
- (small) Source allow-list with per-source license/PD status recorded.
- (medium) Extract structured records from one NARA pension-file batch → graph nodes with provenance.
- (small) Wikidata reconciliation + duplicate-merge pass with human review.
- (small) Public query/browse surface (e.g., RDF/JSON-LD export + simple explorer).

## Definition of shipped
A published, openly-licensed, queryable knowledge graph with provenance on every assertion,
seeded from public-domain sources and adopted/cited by an educational or historical partner — with
DAR/SAR engaged for authorized contributions where possible.

## Risks / review needs
**Risk tier: medium.** **License/ToS gate (primary risk):** no scraping of proprietary DAR/SAR
systems; public-domain sources only unless an explicit agreement exists. **Accuracy:** historical
claims need source-citation review; do not invent or "smooth over" gaps. **Privacy:** historical
(deceased) persons only.

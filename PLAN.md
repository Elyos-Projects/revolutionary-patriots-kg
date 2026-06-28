# PLAN — revolutionary-patriots-kg

> Status: Draft · Version: 0.2.0 · Last updated: 2026-06-28 · Owner: TBD (maintainer) · Lane: donated

An open, linked, citable knowledge graph of American Revolution patriots — people, military
service, units, engagements, places, kinship, and the documentary sources that prove each claim —
built **only** from public-domain and openly-licensed primary sources.

## Executive summary

There is no open, linked, queryable knowledge graph of American Revolutionary War patriots. The
richest structured datasets that exist — the **DAR Genealogical Research System (GRS)** and the
**SAR Patriot Research System (PRS)** — are proprietary compiled databases behind terms of use, and
their entries are paywalled or access-controlled. Genealogists, historians, educators, and students
are left to stitch together facts by hand from scattered archives.

This project builds an openly-licensed knowledge graph (RDF / JSON-LD) of 18th-century patriots,
where **every assertion carries provenance** to a specific public-domain source. It reuses
established vocabularies (schema.org, Wikidata) so the graph is interoperable and reconcilable
against the wider linked-data web from day one. A lightweight web explorer and standard data exports
make it usable by non-technical researchers and machine-consumable by other projects.

The single most important constraint is licensing/ToS (see
[Data, licensing & compliance](#data-licensing--compliance)). **Scraping DAR GRS or SAR PRS is out of
scope and never acceptable.** The graph is seeded exclusively from U.S.-government public-domain
records (NARA pension, bounty-land, and compiled service records), Founders Online, the Library of
Congress, state archives, copyright-expired DAR/SAR lineage *books*, and Wikidata/Wikipedia for
reconciliation. In parallel we pursue an **authorized partnership** with DAR and/or SAR as the ideal
path to richer, sanctioned data. Privacy scope is historical deceased persons only; no living
member/applicant/contributor data is collected.

Risk tier: **medium** — driven primarily by license/ToS compliance, with a secondary historical-
accuracy / citation-review requirement.

## Problem & beneficiaries

**The problem.** Revolutionary-era genealogical and military-service facts are real but fragmented.
Authoritative structured collections are proprietary and access-controlled; open sources (NARA,
Founders Online, LoC, state archives, old lineage books) are public domain but unstructured,
un-linked, and hard to query at scale. No free, machine-readable graph connects a patriot to their
unit, their engagements, their pension file, and their documented kin.

**Beneficiaries.**
- **Genealogists** tracing Revolutionary-era ancestry who cannot afford or access paywalled systems.
- **Historians and academic researchers** needing queryable, citable, source-linked data.
- **Educators and students** (K-12 and university) wanting free, trustworthy primary-source history.
- **The public / civic memory** — an open commons of the founding generation's service record.
- **Downstream open projects** (Wikidata, library linked-data, digital-humanities tools) that can
  reconcile against and reuse the graph.

**Verified need.** The *gap* (no open linked graph exists) is real and demonstrable. However, a
**named partner organization or steward who will adopt, host, and cite the output is TO BE
SECURED.** The proposal asserts "verified need: yes," and the gap is genuine, but a committed
last-mile beneficiary (a historical society, library, university department, or DAR/SAR chapter) has
not yet signed on. Per the quality bar ("delivered, not merged"), securing this partner is a
first-class M0/M1 objective and a precondition for declaring the project *shipped*.

**Partner org.** TO BE SECURED. Candidate stewards: a state historical society or archive, an
academic digital-humanities center, a public library's special-collections / linked-data team, or an
authorized DAR/SAR collaboration. DAR/SAR engagement is pursued in parallel as the ideal path.

## Goals and non-goals

**Goals**
- Publish an openly-licensed, queryable knowledge graph of Revolutionary patriots with **provenance
  on every assertion**.
- Define a reusable ontology (Person, Service, MilitaryUnit, Engagement, Place, Document,
  KinshipRelation) layered on schema.org / Wikidata vocabulary.
- Seed the graph from public-domain primary sources, starting with NARA pension/bounty-land/service
  records, and reconcile against Wikidata.
- Represent **conflicting records faithfully** rather than flattening or "smoothing over" gaps.
- Provide RDF/Turtle + JSON-LD exports and a simple public explorer.
- Secure at least one educational/historical partner that adopts and cites the graph.
- Pursue an authorized data-sharing arrangement with DAR and/or SAR.

**Non-goals**
- **Not** a scrape or mirror of DAR GRS, SAR PRS, or any other proprietary genealogy product.
- **Not** a database of living people — no members, applicants, or contributors as data subjects.
- **Not** an authority that adjudicates contested lineage; it records sourced claims with provenance
  and surfaces disagreement.
- **Not** a general-purpose genealogy platform, user-account system, or commercial product.
- **Not** a replacement for DAR/SAR membership verification or for primary-source archives.
- **Not** original historical research that invents facts; it structures what sources attest.

## Success metrics (outcomes)

Outcome-based, beneficiary-centric. Baselines are zero at project start unless noted.

| Metric | Baseline | Target (first 12 months) |
| --- | --- | --- |
| Patriot Person nodes published with ≥1 cited public-domain source | 0 | ≥ 5,000 |
| Share of published assertions carrying a resolvable provenance link | n/a | 100% (hard gate; un-sourced assertions are not published) |
| Distinct public-domain source collections integrated | 0 | ≥ 4 (NARA + Founders Online + LoC + ≥1 state archive / PD lineage book) |
| Person nodes reconciled to a Wikidata QID | 0 | ≥ 40% of published persons |
| Dedup/merge precision (false-merge rate in audit sample) | n/a | **zero confirmed false merges** in the audit sample (coverage without precision corrupts the graph) |
| Conflict-faithful representation (contested facts retaining ≥2 sourced variants) | n/a | 100% — no single-winner assertion ships without a sourced editorial rationale |
| Educational/historical partners adopting or citing the graph | 0 | ≥ 1 committed steward; ≥ 1 citation/use |
| Authorized DAR/SAR engagement | none | ≥ 1 documented contact / MoU discussion (outcome may be "declined," recorded honestly) |
| Data-quality: sampled assertions passing citation review | n/a | ≥ 95% of a **stratified** audit sample verify against the cited source (see sampling frame below) |
| Reuse: external queries / downloads of exports | 0 | tracked from M2; growth trend reported quarterly |

**Citation-audit sampling frame (pins the data-quality metric).** The ≥95% target is meaningless
without a defined sample, so the audit uses: a **minimum sample size** of 200 assertions per release
(or the whole release if smaller); **stratified sampling** across strata defined by *source batch*
and by *extraction method* (human transcription vs. OCR vs. structured import), so no source or
method escapes review; and an **auditor independent of the extractor** of the sampled records (no
self-grading). The dedup-precision audit draws its own stratified sample of proposed/confirmed merges.

We explicitly **do not** treat raw node count, PRs merged, or commits as success. A large graph with
weak provenance is a failure under this plan.

## Scope

**In scope**
- Ontology and source allow-list (with per-source license/PD determination recorded).
- Structured extraction of patriots, service, units, engagements, places, documents, and kinship
  from public-domain sources.
- Wikidata reconciliation, duplicate detection, and human-reviewed merges.
- RDF/Turtle + JSON-LD exports and a simple browse/query explorer.
- Provenance and license metadata on every node and assertion.
- Outreach for an authorized DAR/SAR partnership and for an adopting steward.

**Out of scope (explicit)**
- **Any scraping, bulk download, API harvesting, or re-publication of the DAR Genealogical Research
  System or SAR Patriot Research System, or of any other proprietary/compiled genealogy database.**
  This is a hard refusal under Elyos guardrails, not a deprioritized item.
- Any data about living persons (members, applicants, researchers, contributors as subjects).
- Paid features, accounts, or for-profit packaging of the data.
- Adjudicating or "certifying" lineage; issuing membership-eligibility determinations.
- Importing copyrighted modern lineage books, indexes, or compilations still under copyright.
- AI-generated "fill-in" of unknown facts; gaps stay gaps.

## Solution approach & architecture

A **data/content pipeline** project (with supporting code), not a hosted service.

**Pipeline stages**
1. **Source intake & licensing gate** — each candidate source is logged in a machine-readable
   `sources/allowlist.yml` with: title, custodian, URL, format, license / public-domain
   determination, rights basis, and an explicit `status: approved | rejected | pending`. Nothing is
   processed until `approved`.
2. **Ontology layer** — a documented schema (`ontology/`) defining the seven core classes and their
   properties, mapped to schema.org and Wikidata properties wherever an equivalent exists. Published
   as an OWL/SHACL + human-readable spec.
3. **Extraction** — per-source extractors turn primary documents (e.g., a NARA pension-file batch)
   into typed records. A **per-source extraction-method policy** governs how each source is read:
   **human transcription for handwritten manuscripts** (pension depositions, service abstracts);
   **OCR only for machine-print public-domain books** (copyright-expired lineage volumes). Each
   source's method is recorded in its allow-list entry and carried into provenance. A documented
   **transcription-accuracy baseline** (character/field-level acceptance threshold per method) gates
   a batch before normalization. Where OCR/transcription is involved, the transcription and the
   source image citation are both retained. Extraction is **assistive**; ambiguous fields are
   flagged for human review, never guessed.
4. **Normalization & provenance binding** — records are mapped to ontology entities; **every
   assertion is wrapped with a provenance statement** (source document IRI + license + extraction
   method + confidence) using a reification / named-graph / RDF-star pattern (decision below).
5. **Reconciliation & dedup** — candidate matches against Wikidata (QIDs) and within-graph
   duplicates are proposed automatically and **confirmed by a human reviewer** before merge. Matching
   uses an explicit **blocking-key strategy** (e.g., normalized surname + service state/unit + service
   period) to generate candidate pairs without an all-pairs comparison, with the matcher tuned for
   **precision over recall**. The bar is **zero confirmed false merges** in the audit sample: a wrong
   merge silently corrupts the graph, so missing a merge (recoverable later) is preferred to making a
   bad one. Merges remain reversible and retain both records' provenance.
6. **Validation** — SHACL shape validation + provenance-completeness check (CI gate: no assertion
   without provenance).
7. **Publish** — versioned RDF/Turtle + JSON-LD dumps, a SPARQL-or-static query surface, and a
   simple explorer UI.

**Tech stack**
- Tooling/extractors/validators: **TypeScript, ESM, pnpm** (per Elyos conventions).
- Graph serialization: **RDF (Turtle) + JSON-LD**; identifiers as dereferenceable IRIs.
- Validation: **SHACL** shapes + a custom provenance-completeness linter in CI.
- Reconciliation: **OpenRefine-style** reconciliation against the Wikidata reconciliation API, or a
  scripted matcher; human review via a lightweight worklist.
- Explorer: a static-site explorer over the JSON-LD (and/or an embedded triplestore) — kept simple;
  no accounts, no PII.

**Data model (core classes)**
- **Person** (patriot; deceased historical individual) — subclass/aligned to `schema:Person` /
  Wikidata `Q5`.
- **Service** (an individual's military/​civil service episode: role, rank, dates).
- **MilitaryUnit** (regiment, militia company, Continental line unit).
- **Engagement** (battle, siege, campaign) — aligned to `wd:battle`.
- **Place** (aligned to `schema:Place` / Wikidata; geo where known).
- **Document** (the source record: pension file, service abstract, lineage-book page) — aligned to
  `schema:CreativeWork` / `schema:ArchiveComponent`, carrying its license/PD status.
- **KinshipRelation** (parent/child/spouse/sibling), modeled as qualified relations to support
  source-conflicting kinship claims.

**Key decisions (to ratify in M0)**
- **Provenance mechanism & assertion unit:** RDF-star vs. named graphs vs. PROV-O reification — pick
  one and apply uniformly. (Leaning: named graphs + PROV-O for tool compatibility; RDF-star
  evaluated.) The same decision **defines the countable "assertion"** — the unit the 100%-provenance
  CI gate measures (e.g., one named graph / one reified statement / one RDF-star triple) — so
  "provenance on every assertion" is mechanically checkable rather than aspirational.
- **IRI scheme & persistence:** stable, dereferenceable IRIs under a project namespace. IRI minting
  is **decoupled from the (unsecured) steward**: M0 commits to a **host-independent persistent
  identifier** (w3id.org or a PURL) as the canonical namespace, redirecting to whatever host serves
  the graph. This way identifiers stay stable even if the steward changes or is never secured, and no
  IRI is ever minted under a host we do not control.
- **Conflict representation:** every contested fact retains all sourced variants with provenance;
  no single "winner" is asserted without an editorial, sourced rationale.

## Data, licensing & compliance

**This is the headline gate for the project. Read this section before doing any data work.**

### Hard boundary — proprietary systems are out of scope
A knowledge graph **scraped, harvested, or bulk-copied from the DAR Genealogical Research System
(GRS) or the SAR Patriot Research System (PRS)** would **violate their terms of use and the copyright
in their compiled databases**, and is therefore **OUT OF SCOPE and never acceptable** under Elyos's
license/privacy guardrails. This applies to:
- Automated scraping, crawling, or API harvesting of GRS/PRS or similar paywalled genealogy systems.
- Re-publishing their record entries, indexes, or compiled-database structure.
- Laundering such data through an intermediary export.

A compiled database can carry copyright in its selection/arrangement even where individual
underlying facts are public; ToS can independently bar copying. We assume both protections apply and
**do not touch these systems** absent an explicit written agreement.

**Closing the citation-laundering hole.** A contributor could copy a GRS/PRS entry and back-fill a
plausible-looking public-domain citation. Three controls make that detectable and unacceptable:
- **Page/image-level citations are required** — a citation must point to the specific page or document
  image actually consulted, never to a collection or database as a whole. Collection-level citations
  are rejected at review.
- **Contributor attestation of independent sourcing** — each contributed batch carries a signed
  attestation that the facts were read from the cited public-domain source directly, not transcribed
  or derived from GRS/PRS or any proprietary compilation.
- **Spot-checks for GRS/PRS-distinctive compiled fields** — reviewers sample for tell-tale artifacts
  of the proprietary compilations (their distinctive normalizations, derived/editorial fields, or
  arrangement) that would not appear in the raw underlying record; a hit triggers rejection and a
  flag.

### Approved sources (public domain / openly licensed only)
Every source must be entered in `sources/allowlist.yml` with a recorded license/PD basis and an
`approved` status before use:
- **U.S. National Archives (NARA)** — Revolutionary War **pension & bounty-land warrant application
  files** and **compiled military service records**. U.S. federal government works → **public
  domain** (the records themselves; verify the specific digitization's terms). **Hard M1 entry
  precondition:** the exact NARA access path supplying the M1 batch must be named and shown to deliver
  **PD-clear digitizations** served by NARA itself (e.g., the NARA Catalog) — **not** copies behind
  Fold3/Ancestry terms, whose scans and indexes carry their own restrictions. M1 extraction may not
  begin until this is recorded as cleared in the allow-list.
- **Founders Online** (National Archives / NHPRC) — public domain.
- **Library of Congress** — public-domain manuscript and print collections (verify per item).
- **State archives / state historical societies** — public-domain records (verify per repository).
- **Public-domain (copyright-expired) DAR/SAR lineage books and genealogical volumes** — the
  *published books* whose copyright has lapsed (generally pre-1929 in the U.S.; verify each
  edition). **NOT** the live GRS/PRS databases.
- **Wikidata** (CC0) and **Wikipedia** (CC BY-SA 4.0) — for reconciliation, QIDs, and linking.
  Wikipedia-derived text triggers CC BY-SA share-alike attribution obligations; prefer Wikidata
  (CC0) for imported statements.

**Caveats we will not gloss over:** a public-domain underlying record can be wrapped by a vendor's
copyrighted scan, transcription, or index; "public domain" must be verified for the *specific copy
and edition* used, not assumed from the original's age. Each allow-list entry records this analysis.

### Provenance model
- **Every assertion** links to its source Document IRI at **page/image-level granularity** (not the
  collection) and records that source's license/PD basis, the extraction method (human transcription /
  OCR / structured import), and a confidence value.
- Un-sourced assertions are **never published** — enforced as a CI validation gate over the countable
  assertion unit fixed by the provenance-mechanism decision.
- Conflicting sources are retained side by side with their respective provenance.

### Privacy / PII stance
- **Subjects are long-deceased 18th-century historical persons only.**
- **Exclude all data about living people** — DAR/SAR members, applicants, researchers, contributors,
  or any modern descendant named in a record. Modern application paperwork and member-supplied
  lineage are out of scope.
- No collection of contributor PII beyond standard open-source attribution the contributor chooses
  to provide.

### Attribution & output license
- **Code:** MIT. **Graph/content:** **CC0** where derived purely from public-domain sources;
  **CC BY-SA 4.0** where any CC BY-SA (e.g., Wikipedia-derived) material is incorporated. Mixed
  derivations are labeled at the dataset and, where feasible, the statement level.
- Required attributions (Wikipedia/CC BY-SA, repository acknowledgements) are recorded and surfaced.

### Authorized-partnership path (ideal)
Pursue an explicit agreement with **DAR and/or SAR** for data they are willing to share under an open
release or MoU. Cooperation is the ideal path; scraping is never the fallback. Any partner-supplied
data is governed by the agreement's terms and clearly labeled in provenance.

## Quality, review & risk gates

**Risk tier: medium.** Two review dimensions, both required before a deed is "done":

1. **License/ToS review (primary gate).** Before any source is processed, a reviewer confirms the
   `sources/allowlist.yml` entry: source is public-domain or openly licensed, the *specific copy* is
   cleared, and it is not GRS/PRS-derived. No extraction task may start against a `pending` or
   `rejected` source. Any task that even proposes touching a proprietary system is **refused and
   flagged** per Elyos guardrails.
2. **Historical-accuracy / citation review.** A reviewer with relevant domain skill samples extracted
   assertions against their cited sources; transcription errors, mis-citations, or invented facts
   block sign-off. Conflicting records must be represented, not flattened.

**Definition of Shipped (project level).** A published, openly-licensed, queryable knowledge graph
with: provenance on **100%** of assertions; seeded from ≥4 approved public-domain sources; passing
SHACL + provenance-completeness CI; with at least one educational/historical **partner that has
adopted or cited it**; and DAR/SAR engagement documented (outcome recorded honestly, including
"declined"). Per Elyos, *delivered ≠ merged* — the data must actually be in a beneficiary's hands.

**Per-deed Definition of Done.** Acceptance criteria met + CI green (schema/SHACL/provenance) +
license review passed + accuracy/citation review passed + output published under the declared
license.

## Roadmap & milestones

**M0 — Foundation & licensing spine (cold-start).**
Goal: establish the rails so no data work can bypass the license/provenance gates.
Exit criteria: (a) ontology v0 published covering the 7 classes mapped to schema.org/Wikidata;
(b) `sources/allowlist.yml` schema defined with ≥3 sources analyzed and ≥1 `approved`;
(c) provenance mechanism decision ratified, **including the countable "assertion" unit** the CI gate
measures; (d) CI provenance-completeness + SHACL lint scaffolded; (e) partner/steward outreach started
and DAR/SAR contact attempted (status logged); (f) a **qualified License/ToS reviewer named** (hard
exit; documented fallback if the seat is empty — M0 cannot exit and escalation begins); (g) a
**host-independent persistent identifier (w3id.org/PURL) committed** as the canonical IRI namespace,
decoupled from the unsecured steward.

**M1 — First sourced slice (proof of pipeline).**
Goal: end-to-end one batch from one approved NARA source into the graph with full provenance.
**Hard entry precondition:** the NARA access path for the M1 batch is named and recorded as supplying
PD-clear digitizations (NARA-served, **not** Fold3/Ancestry-terms copies) before extraction starts.
Exit criteria: (a) ≥1 NARA pension/service batch extracted into Person/Service/Unit/Document nodes
(per the per-source extraction-method policy: human transcription for handwritten files);
(b) 100% of new assertions carry provenance and pass CI; (c) **stratified** citation-review audit
(min sample size; by source-batch and extraction method; independent auditor) ≥95% verified;
(d) JSON-LD + Turtle export produced under the persistent-identifier namespace; (e) ≥1 candidate
steward identified and in conversation. Depends on M0.

**M2 — Reconciliation & explorer (usable surface).**
Goal: make the graph discoverable, linked, and browsable.
Exit criteria: (a) Wikidata reconciliation pass with human-reviewed merges; ≥40% of persons carry a
QID; (b) duplicate-merge workflow operational; (c) public explorer + documented exports live;
(d) reuse metrics tracked. Depends on M1.

**M3 — Scale & partner adoption (shipped).**
Goal: broaden sources and lock in real-world use.
Exit criteria: (a) ≥4 source collections integrated and ≥5,000 sourced Person nodes;
(b) ≥1 partner has **adopted or cited** the graph (Definition of Shipped met);
(c) DAR/SAR engagement outcome documented; (d) sustainability/maintenance plan in effect.
Depends on M2.

## Work breakdown

The itemized, schema-mapped backlog lives in [`TASKS.md`](./TASKS.md), organized by the milestones
above (M0–M3) plus a sized backlog. Each task maps to an Elyos Task JSON and carries a type, size,
risk tier, deliverable, dependencies, and reviewer. M0 deliberately front-loads the licensing and
provenance guardrails before any bulk extraction begins.

## Governance, roles & stakeholders

- **Maintainer / Owner:** TBD — accountable for scope, the licensing gate, and releases.
- **License/ToS reviewer:** TBD — must approve every `sources/allowlist.yml` entry; has veto over
  any source. (Mandatory given medium risk tier; primary gate.) **Naming a qualified person to this
  seat is a hard M0 exit criterion** — the licensing gate is the project's headline control and cannot
  rest on an empty seat. **Documented fallback if the seat is empty:** no source advances past
  `pending` and no extraction begins; M0 cannot exit; the maintainer escalates to Elyos
  governance/board to source a qualified reviewer (and may engage qualified pro-bono counsel) before
  any data work proceeds.
- **Domain / accuracy reviewers (rotation):** historians or experienced genealogists who perform
  citation review. TO BE SECURED.
- **Steward (last-mile owner):** the educational/historical partner who adopts, hosts long-term, and
  cites the graph. **TO BE SECURED** — required for "shipped."
- **Partner / requestor:** genealogists, historians, educators, students, the public (diffuse
  beneficiary class); a named representative org is TO BE SECURED.
- **DAR/SAR liaison:** TBD — owns the authorized-partnership outreach.
- **Elyos governance/board:** arbiter for edge cases (e.g., a borderline source) under the published
  conflict-of-interest/veto checklist.

## Dependencies & integrations

- **NARA** digitized pension/bounty-land/service records (intake; verify per-collection terms).
- **Founders Online**, **Library of Congress**, **state archives** (public-domain sources).
- **Wikidata / Wikipedia** (reconciliation; CC0 / CC BY-SA).
- **schema.org / Wikidata property vocabularies** (ontology alignment).
- **SHACL tooling**, an RDF library, and a reconciliation client (TypeScript/ESM ecosystem).
- **Elyos pieces:** Task schema (`packages/schema`), CLI workspace/PR flow (`packages/cli`,
  `packages/core`), governance proposal/registry process. Donated lane — humans run their own agents.
- **DAR / SAR** (optional, ideal) — authorized data under an explicit agreement only.

## Risks & mitigations

| Risk | Likelihood | Impact | Mitigation | Owner |
| --- | --- | --- | --- | --- |
| Contributor scrapes/imports DAR GRS or SAR PRS data (incl. laundered via a fake PD citation) | Medium | Critical (legal/ToS, project-ending) | Hard out-of-scope rule; allow-list gate blocks un-approved sources; license reviewer veto; CI rejects sources not marked `approved`; **anti-laundering controls — page/image-level citations, contributor attestation of independent sourcing, and spot-checks for GRS/PRS-distinctive compiled fields**; refusal + flag per guardrails | License reviewer |
| "Public-domain" source actually wrapped in a copyrighted scan/index | Medium | High | Per-copy/edition rights analysis recorded in allow-list; verify the specific digitization, not just the original's age | License reviewer |
| No steward/partner secured → "delivered ≠ merged" not met | High | High | Treat partner outreach as an M0/M1 deliverable; log status honestly; multiple candidate stewards pursued | Maintainer |
| Inaccurate transcription / mis-citation / invented facts | Medium | High | Mandatory citation-review sampling; provenance-completeness CI gate; assistive (not autonomous) extraction; gaps stay gaps | Domain reviewer |
| Inadvertent inclusion of living-person data | Low | High (privacy guardrail) | Deceased-only scope rule; exclude modern application/member data; review checklist | License/domain reviewers |
| Conflicting historical records flattened into one "truth" | Medium | Medium | Conflict-preserving data model; reviewers reject single-winner assertions lacking sourced rationale; conflict-faithful metric tracked | Domain reviewer |
| Bad/false merges corrupt the graph (precision failure) | Medium | High | Precision-over-recall matcher; explicit blocking-key strategy; human-confirmed, reversible merges; zero-confirmed-false-merge audit target | Domain reviewer |
| Reviewer capacity exhausted / burnout (license + citation review become bottleneck) | Medium | High | Sampling-based review (not 100% manual re-check); reviewer rotation with a response-time SLA; a documented throughput ceiling that throttles intake when review backlog exceeds it | Maintainer |
| Wikipedia (CC BY-SA) text contaminates a CC0 dataset | Medium | Medium | Prefer Wikidata (CC0); label CC BY-SA-derived statements; dataset-level license honesty | Maintainer |
| IRI/host instability breaks dereferenceable links | Medium | Medium | Persistence plan tied to steward; stable namespace + redirect strategy | Maintainer |
| DAR/SAR decline partnership | Medium | Low | Public-domain path is fully self-sufficient; partnership is upside, not a dependency | DAR/SAR liaison |
| Scope creep into general genealogy platform | Medium | Medium | Explicit non-goals; governance review of scope changes | Maintainer |

## Security & privacy

- **Threat surface:** small (data/content project, no accounts, no user PII). Main risks are
  *compliance* (illicit sourcing) and *data integrity* (false/unsourced assertions), addressed by the
  license and accuracy gates above.
- **Secrets handling:** no API keys or tokens are required for public-domain sources; any
  reconciliation credentials stay out of logs, receipts, and commits per Elyos rules. The donated
  lane never runs headless or authenticates an agent.
- **PII:** deceased historical persons only; living-person data is excluded by policy and checked in
  review. Contributor attribution is opt-in and minimal.
- **Abuse/misuse prevention:** the graph is source-linked so claims are auditable; the project
  refuses and flags any attempt to ingest proprietary-system data or to target/deceive living people.
  No surveillance, profiling, or modern-person dossier use is supported.

## Sustainability & maintenance

- **After delivery,** the maintainer plus the secured steward own ongoing curation; the steward
  provides long-term hosting, while the **canonical persistent identifier (w3id.org/PURL) is owned by
  the project, not the host** — so identifiers survive a steward change and the graph is never orphaned
  if the steward seat turns over.
- **Reviewer sustainability:** review runs on **sampling, not exhaustive re-checking**; reviewers work
  a **rotation with a response-time SLA**; and a **documented throughput ceiling** throttles new
  extraction intake when the review backlog exceeds it, so quality gates never silently degrade under
  load.
- **Outcome tracking:** quarterly report on sourced-node growth, provenance completeness (must stay
  100%), reconciliation coverage, citation-audit pass rate, partner adoptions, and reuse/downloads.
- **Contributions** continue via the donated lane with the same license + citation review gates.
- **Versioned releases** of the dataset (with changelogs) keep downstream consumers stable.
- If no steward is secured, the project remains in a maintained-but-not-shipped state and the gap is
  reported honestly rather than declared done.

## Open questions

- Who is the committed steward / adopting partner? (TO BE SECURED — blocks "shipped.")
- Will DAR and/or SAR engage on an authorized data-sharing arrangement, and on what terms?
- Final provenance mechanism: named graphs + PROV-O vs. RDF-star? (The countable assertion unit is
  fixed by whichever is chosen — decided in M0.)
- Dataset license default: CC0-only with CC BY-SA segregated, or CC BY-SA overall?
- Who staffs the domain-reviewer rotation? (Minimum citation-audit sample size is now pinned at ≥200
  with a stratified, independent-auditor frame; rotation staffing remains open.)

*Resolved since v0.1.0:* the IRI namespace is now committed to a host-independent persistent
identifier (w3id.org/PURL) in M0; and the M1 NARA access path / digitization terms are no longer an
open question but a hard M1 entry precondition (must be PD-clear and NARA-served, not Fold3/Ancestry).

## References

- Project proposal: `governance/proposals/revolutionary-patriots-kg.md`
- Elyos work rules: `CLAUDE.md`
- Good Deed Definition & risk tiers: `docs/good-deed-definition.md`
- Task JSON schema: `packages/schema/src/schemas.ts`
- U.S. National Archives — Revolutionary War pension & bounty-land warrant application files; compiled service records
- Founders Online (NARA / NHPRC); Library of Congress digital collections
- Wikidata (CC0) and Wikipedia (CC BY-SA 4.0); schema.org vocabulary
- W3C: RDF, JSON-LD, SHACL, PROV-O, RDF-star

# TASKS — revolutionary-patriots-kg

> Status: Draft · Version: 0.2.0 · Last updated: 2026-06-28 · Owner: TBD (maintainer) · Lane: donated

Itemized backlog for the open knowledge graph of American Revolution patriots. See
[`PLAN.md`](./PLAN.md) for context, the licensing gate, and the roadmap (M0–M3).

## How these tasks map to Elyos

Each task below becomes an Elyos **Task JSON** validated against
`packages/schema/src/schemas.ts`. Field mapping:

- **id** — stable `revolutionary-patriots-kg-<area>-NNN` (the table ID).
- **title** — the table Title.
- **project** — `revolutionary-patriots-kg`.
- **type** — one of `code | research | writing | data | design-spec | maintenance` (table "Type").
- **lane** — `donated` for all tasks here (the proposal's lane). Any future metered run would be
  `funded` and must add `fundedBudgetUsd`.
- **priority** — `high | medium | low`.
- **domain** — e.g. `["open-history","public-data","education","genealogy"]`.
- **riskTier** — `low | medium | high`. License/extraction tasks are **medium** (license/ToS gate);
  scaffolding/docs are **low**.
- **urgent** — boolean (default `false`).
- **deliverable** — `pr | dataset | document | translation` (table "Deliverable").
- **tokenEstimate** — `small | medium | large` (table "Size").
- **status** — `open | in-progress | review | delivered | done` (start `open`).
- **context / objective / acceptanceCriteria[] / resources[] / output** — per task.
- **requestor** — `jdev1977` / beneficiary class until a named partner is secured.
- **verifiedNeed** — **`false`** while no committed partner/steward is secured (honest; the *gap* is
  real but the last-mile beneficiary is TO BE SECURED).
- **outputLicense** — `MIT` (code), `CC0-1.0` (PD-derived data/docs), or `CC-BY-SA-4.0` (where
  CC BY-SA material is incorporated).

> **Standing guardrail on every data/extraction task:** no source may be touched until its
> `sources/allowlist.yml` entry is `approved` by the license reviewer. Any task proposing to scrape,
> harvest, or import DAR GRS / SAR PRS (or any proprietary genealogy database) is **refused and
> flagged** — out of scope, full stop.

---

## Milestone M0 — Foundation & licensing spine

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| revolutionary-patriots-kg-ontology-001 | Define core ontology (7 classes) mapped to schema.org/Wikidata | design-spec | small | low | document | — | Maintainer + domain reviewer |
| revolutionary-patriots-kg-license-001 | Source allow-list schema + licensing-gate policy | design-spec | small | medium | document | — | License reviewer |
| revolutionary-patriots-kg-license-002 | Analyze & record first 3 candidate sources (≥1 approved) | research | medium | medium | document | revolutionary-patriots-kg-license-001 | License reviewer |
| revolutionary-patriots-kg-prov-001 | Ratify provenance mechanism + define countable assertion unit | design-spec | small | low | document | revolutionary-patriots-kg-ontology-001 | Maintainer |
| revolutionary-patriots-kg-iri-001 | Commit host-independent persistent IRI namespace (w3id.org/PURL) | design-spec | small | low | document | revolutionary-patriots-kg-ontology-001 | Maintainer |
| revolutionary-patriots-kg-ci-001 | CI scaffold: SHACL + provenance-completeness linter | code | medium | low | pr | revolutionary-patriots-kg-ontology-001, revolutionary-patriots-kg-prov-001 | Maintainer |
| revolutionary-patriots-kg-partner-001 | Steward outreach + DAR/SAR authorized-partnership contact | research | small | low | document | — | Maintainer |

**Acceptance criteria (key M0 tasks)**

- **revolutionary-patriots-kg-ontology-001**
  - All 7 classes (Person, Service, MilitaryUnit, Engagement, Place, Document, KinshipRelation)
    defined with properties and cardinality.
  - Each class/property maps to a schema.org and/or Wikidata equivalent where one exists; gaps noted.
  - KinshipRelation and conflicting-claim representation explicitly modeled (no single forced "truth").
  - Published as a human-readable spec plus a machine artifact (OWL/SHACL stub).
- **revolutionary-patriots-kg-license-001**
  - `sources/allowlist.yml` schema defines: title, custodian, URL, format, license/PD basis, rights
    analysis, and `status: approved|rejected|pending`.
  - Policy text states GRS/PRS and any proprietary compiled DB are categorically `rejected`.
  - Per-copy/edition rights-verification requirement documented (PD original ≠ PD scan).
- **revolutionary-patriots-kg-license-002**
  - ≥3 sources analyzed with recorded license/PD determination; ≥1 marked `approved`.
  - At least one approved source is a NARA public-domain collection.
  - Any Wikipedia-derived use flagged for CC BY-SA attribution; Wikidata noted as CC0.
- **revolutionary-patriots-kg-prov-001**
  - One provenance mechanism chosen (named-graphs+PROV-O vs RDF-star) and applied uniformly.
  - The countable **"assertion" unit** is defined explicitly (e.g., one named graph / reified
    statement / RDF-star triple) so the 100%-provenance CI gate is mechanically checkable.
- **revolutionary-patriots-kg-iri-001**
  - A host-independent persistent identifier (w3id.org or PURL) is registered/committed as the
    canonical IRI namespace, decoupled from the (unsecured) steward/host.
  - Redirect strategy to the eventual host documented; no IRI minted under a host we do not control.
- **revolutionary-patriots-kg-ci-001**
  - CI fails on any assertion lacking a provenance link.
  - CI runs SHACL validation against the ontology shapes.
  - CI rejects data referencing a source not marked `approved` in the allow-list.

**M0 Definition of Done:** ontology v0 published; allow-list schema + policy merged with ≥3 sources
analyzed and ≥1 approved; provenance mechanism ratified **with the countable assertion unit defined**;
**host-independent persistent IRI namespace committed**; CI provenance + SHACL gates live; partner and
DAR/SAR outreach initiated with status logged; **a qualified License/ToS reviewer named (hard exit; if
the seat is empty M0 cannot exit — escalate per the documented fallback in PLAN.md)**.
`pnpm build && pnpm test && pnpm lint` green.

---

## Milestone M1 — First sourced slice

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| revolutionary-patriots-kg-extract-001 | Build NARA pension/service extractor (assistive, flag-on-doubt) | code | medium | medium | pr | revolutionary-patriots-kg-ci-001, revolutionary-patriots-kg-license-002 | Maintainer |
| revolutionary-patriots-kg-data-001 | Extract one approved NARA batch → graph nodes with provenance | data | large | medium | dataset | revolutionary-patriots-kg-extract-001 | Domain reviewer |
| revolutionary-patriots-kg-qa-001 | Citation-review audit of M1 batch (sample ≥95% verified) | research | small | medium | document | revolutionary-patriots-kg-data-001 | Domain reviewer |
| revolutionary-patriots-kg-export-001 | JSON-LD + Turtle export tooling for the graph | code | medium | low | pr | revolutionary-patriots-kg-data-001 | Maintainer |
| revolutionary-patriots-kg-partner-002 | Identify & engage ≥1 candidate steward for adoption | research | small | low | document | revolutionary-patriots-kg-partner-001 | Maintainer |

**Acceptance criteria (key M1 tasks)**

- **revolutionary-patriots-kg-extract-001**
  - Honors a **per-source extraction-method policy**: human transcription for handwritten manuscripts
    (pension depositions, service abstracts); OCR only for machine-print PD books.
  - A **transcription-accuracy baseline** (per-method acceptance threshold) gates a batch before
    normalization; the method used is recorded into each assertion's provenance.
- **revolutionary-patriots-kg-data-001**
  - Records from one approved NARA batch are mapped to Person/Service/MilitaryUnit/Document nodes.
  - **100%** of new assertions carry a resolvable provenance link (source IRI + license + method).
  - Ambiguous/illegible fields are flagged, not invented; gaps remain gaps.
  - Conflicting source statements are retained with separate provenance.
  - Passes CI (SHACL + provenance + allow-list) before review.
- **revolutionary-patriots-kg-qa-001**
  - A **stratified** sample (min size ≥200 or whole release; strata by source-batch and extraction
    method) is checked against the cited source; ≥95% verify.
  - The **auditor is independent of the extractor** of the sampled records (no self-grading).
  - Citations checked are page/image-level (collection-level citations rejected).
  - Any mis-citations or transcription errors are filed and block sign-off until fixed.
- **revolutionary-patriots-kg-export-001**
  - Produces valid Turtle and JSON-LD with stable IRIs.
  - Export round-trips (re-import validates against SHACL); license metadata included.

**M1 entry precondition (hard gate):** the NARA access path supplying the batch is named and recorded
in the allow-list as a PD-clear, NARA-served digitization (**not** a Fold3/Ancestry-terms copy) before
any extraction begins.

**M1 Definition of Done:** end-to-end pipeline proven on one approved NARA batch; 100% provenance;
stratified citation audit (≥200, independent auditor) ≥95%; exports produced and validated under the
persistent-IRI namespace; ≥1 candidate steward in conversation.

---

## Milestone M2 — Reconciliation & explorer

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| revolutionary-patriots-kg-recon-001 | Wikidata reconciliation pass (propose QID matches) | data | medium | medium | dataset | revolutionary-patriots-kg-data-001 | Domain reviewer |
| revolutionary-patriots-kg-recon-002 | Human-reviewed duplicate-merge workflow | code | medium | medium | pr | revolutionary-patriots-kg-recon-001 | Maintainer + domain reviewer |
| revolutionary-patriots-kg-explorer-001 | Simple public explorer over JSON-LD (no accounts/PII) | code | medium | low | pr | revolutionary-patriots-kg-export-001 | Maintainer |
| revolutionary-patriots-kg-docs-001 | Data dictionary + usage/citation guide for consumers | writing | small | low | document | revolutionary-patriots-kg-explorer-001 | Maintainer |
| revolutionary-patriots-kg-metrics-001 | Reuse-metrics tracking (downloads/queries) | maintenance | small | low | document | revolutionary-patriots-kg-explorer-001 | Maintainer |

**Acceptance criteria (key M2 tasks)**

- **revolutionary-patriots-kg-recon-002**
  - No automatic merge ships without human confirmation.
  - Uses an explicit **blocking-key strategy** (e.g., normalized surname + service state/unit +
    period) to generate candidate pairs; matcher tuned for precision over recall.
  - **Zero confirmed false merges** in the dedup audit sample (precision target).
  - Merges preserve all source provenance from both records; reversible/auditable.
  - ≥40% of published persons carry a Wikidata QID after the pass.
- **revolutionary-patriots-kg-explorer-001**
  - Browse a Person and see service, units, engagements, kin, and **every assertion's source**.
  - Static/no-account; collects no visitor PII; links to raw exports.

**M2 Definition of Done:** reconciliation pass complete with reviewed merges (≥40% QID coverage);
duplicate workflow operational; explorer + documented exports live; reuse metrics tracked.

---

## Milestone M3 — Scale & partner adoption (shipped)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| revolutionary-patriots-kg-data-002 | Integrate ≥3 more approved sources; scale to ≥5,000 persons | data | large | medium | dataset | revolutionary-patriots-kg-recon-002, revolutionary-patriots-kg-license-002 | Domain + license reviewers |
| revolutionary-patriots-kg-partner-003 | Secure steward adoption + ≥1 documented citation/use | research | medium | low | document | revolutionary-patriots-kg-partner-002 | Maintainer |
| revolutionary-patriots-kg-darsar-001 | Conclude & document DAR/SAR engagement outcome | research | small | medium | document | revolutionary-patriots-kg-partner-001 | License reviewer + maintainer |
| revolutionary-patriots-kg-sustain-001 | Sustainability, hosting + reviewer-rotation/throughput plan (IRI namespace committed in M0) | writing | small | low | document | revolutionary-patriots-kg-partner-003 | Maintainer |

**Acceptance criteria (key M3 tasks)**

- **revolutionary-patriots-kg-data-002**
  - ≥4 total source collections integrated; ≥5,000 sourced Person nodes published.
  - Each new source passed the license gate before extraction; 100% provenance maintained.
  - A fresh citation audit sample still ≥95% verified.
- **revolutionary-patriots-kg-partner-003**
  - A named educational/historical steward commits to adopt/host and cite the graph.
  - ≥1 concrete citation or downstream use is documented.

**M3 Definition of Done (project "shipped"):** ≥5,000 sourced persons across ≥4 sources; 100%
provenance; ≥1 partner has adopted/cited the graph; DAR/SAR engagement outcome documented (incl. a
"declined"); persistence/sustainability plan in effect.

---

## Backlog / future (sized, unscheduled)

| ID | Title | Type | Size | Risk | Deliverable | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| revolutionary-patriots-kg-data-003 | Integrate Founders Online correspondence references | data | medium | medium | dataset | PD; links persons↔documents |
| revolutionary-patriots-kg-data-004 | Ingest a copyright-expired DAR/SAR lineage *book* (PD edition) | data | medium | medium | dataset | Verify edition is PD; NOT the live DB |
| revolutionary-patriots-kg-engagement-001 | Engagement/battle gazetteer aligned to Wikidata | data | medium | low | dataset | Place + Engagement enrichment |
| revolutionary-patriots-kg-sparql-001 | Optional hosted SPARQL endpoint | code | large | low | pr | Depends on steward hosting |
| revolutionary-patriots-kg-i18n-001 | Multilingual labels via Wikidata | data | small | low | dataset | CC0 labels |
| revolutionary-patriots-kg-quality-001 | Automated anomaly/outlier flagging for review | code | medium | low | pr | Assistive QA, human-confirmed |

---

## Example task JSON

Schema-valid Task JSON for the first M0 task (`revolutionary-patriots-kg-ontology-001`):

```json
{
  "id": "revolutionary-patriots-kg-ontology-001",
  "title": "Define core ontology (7 classes) mapped to schema.org/Wikidata",
  "project": "revolutionary-patriots-kg",
  "type": "design-spec",
  "lane": "donated",
  "priority": "high",
  "domain": ["open-history", "public-data", "education", "genealogy"],
  "riskTier": "low",
  "urgent": false,
  "deliverable": "document",
  "tokenEstimate": "small",
  "status": "open",
  "context": "An open, linked knowledge graph of American Revolution patriots needs a shared ontology before any data is ingested. Sources are public-domain primary records only (NARA pension/bounty-land/service records, Founders Online, LoC, state archives, copyright-expired lineage books) plus Wikidata/Wikipedia for reconciliation. Scraping DAR GRS or SAR PRS is out of scope. See PLAN.md.",
  "objective": "Define the seven core classes (Person, Service, MilitaryUnit, Engagement, Place, Document, KinshipRelation) and their properties, reusing schema.org and Wikidata vocabulary wherever an equivalent exists, and modeling conflicting/contested claims rather than flattening them.",
  "acceptanceCriteria": [
    "All 7 classes defined with properties, datatypes, and cardinality.",
    "Each class/property mapped to a schema.org and/or Wikidata equivalent where one exists; gaps documented.",
    "KinshipRelation modeled to support source-conflicting kinship claims.",
    "Conflicting-assertion representation specified (no single forced 'truth').",
    "Published as a human-readable spec plus a machine artifact (OWL/SHACL stub).",
    "Every entity reserves a provenance slot (source IRI + license) per the provenance model."
  ],
  "resources": [
    "governance/proposals/revolutionary-patriots-kg.md",
    "planning/projects/revolutionary-patriots-kg/PLAN.md",
    "https://schema.org/",
    "https://www.wikidata.org/"
  ],
  "output": "An ontology specification document (ontology/README.md) plus an OWL/SHACL stub defining the 7 classes and their schema.org/Wikidata mappings, committed via PR.",
  "requestor": "jdev1977",
  "verifiedNeed": false,
  "outputLicense": "CC0-1.0"
}
```

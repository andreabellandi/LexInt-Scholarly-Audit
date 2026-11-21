# LexInt Scholarly Audit

**A human-readable demonstrator and reproducible evaluation of decision-aware scholarly lexicographic publishing.**

[**Explore the demonstrator (English)**](https://andreabellandi.github.io/LexInt-Scholarly-Audit/) · [**Esplora il dimostratore (Italiano)**](https://andreabellandi.github.io/LexInt-Scholarly-Audit/italiano.html)

## What question does this project address?

A scholarly dictionary makes decisions about forms, meanings, and etymologies. Those decisions may later be revised, and some interpretations may remain unresolved. **Can a dictionary show not only what it currently says, but also why it changed, what evidence was considered, and whether the published changes actually match the editorial decisions?**

This repository accompanies the **LexInt scholarly-publication evaluation** discussed in a manuscript for *Digital Scholarship in the Humanities*. It is designed to be approachable by lexicographers, philologists, and digital-humanities scholars, while also offering technical evidence for verification.

## Start with the demonstrator — no technical knowledge needed

Open the [English demonstrator](https://andreabellandi.github.io/LexInt-Scholarly-Audit/) or the [Italian demonstrator](https://andreabellandi.github.io/LexInt-Scholarly-Audit/italiano.html). The pages are static and can also be saved and opened locally.

Follow three scenarios concerning the Italian word *razza*:

1. **A justified editorial revision.** A hypothetical etymological link involving Latin *ratio* is replaced by one involving Old French *haraz*. The system must make precisely the authorized change, preserve earlier versions, and retain the supporting interpretation and decision.
2. **A scholarly question left open.** A contrast between a Fascist text from 1938 and Article 3 of the Italian Constitution (1948) raises a hypothetical question about sense differentiation. The evidence and three candidate statements remain accessible, **but the suspended proposal is not published as an accepted sense**.
3. **What happens when publication goes wrong?** Three controlled mistakes are introduced: the old etymological link wrongly remains, the accepted replacement is missing, or a suspended sense is published. The demonstrator shows why conventional *structural* validation of these records does not establish whether publication followed editorial authorization.

A further section translates **seven SPARQL competency questions** into ordinary scholarly questions with concise answers. No RDF, GraphDB, or programming knowledge is needed to use the website.

> **Interpretive caution:** All editorial decisions in these scenarios are illustrative. The comparison between 1938 and 1948 does not establish distinct lexical senses. The experiment tests the fidelity of publication to decisions, **not the historical truth** of competing interpretations.

## What was evaluated?

The corrected, controlled run of **21 November 2026** (`dsh2027-corrected-20261121-77d2c3e`) recorded:

| Evaluation component | Recorded outcome | What it means |
| --- | --- | --- |
| Publication and audit tests (T1–T12) | **12/12 passed** | Authorization, transaction rollback, version integrity, and audit behavior met the test criteria |
| Scholarly questions (CQ1–CQ7) | **7/7 exact** | Typed, complete result bindings matched pre-established answer keys |
| Deliberate publication errors (CE1–CE3) | **3/3 detected** | All three structurally conformant counterexamples were rejected by the publication-integrity audit |
| Transaction rollback (T09) | **PASS on GraphDB 10.8.14** | A deliberately interrupted transaction left the checked graphs unchanged |

The corrected software revision is [**LexO-server commit `77d2c3e`**](https://github.com/andreabellandi/LexO-server/commit/77d2c3e93b96a4ac0a4f2e6f98f9c40e781079ad). These results describe a *single controlled execution*, not a usability trial or a large-scale performance benchmark.

**Why the comparison matters:** In the three deliberately corrupted cases, the executed structural SHACL baseline reported conformance, while the separate publication-integrity audit reported failure. This demonstrates a need to check *published effects against authorized editorial operations*, not any theoretical impossibility of expressing further checks with more elaborate SHACL/SPARQL rules. An unsupported `sh:xone` reification constraint was checked separately in the experiment.

## For readers who want to inspect the evidence

The corrected evaluation archive contains the RDF versions, fixtures, frozen expectations, test definitions, query results, audit logs, counterexamples, and reproducibility instructions.

- **[Technical replication sources in LexO-server](https://github.com/andreabellandi/LexO-server/tree/77d2c3e93b96a4ac0a4f2e6f98f9c40e781079ad/evaluation/dsh2027)** — fixtures, queries, test cases, and execution scripts. The archived run output includes additional recorded evidence that is not part of the source tree.
- **[Software revision used for the experiment](https://github.com/andreabellandi/LexO-server/commit/77d2c3e93b96a4ac0a4f2e6f98f9c40e781079ad)** — implementation provenance.
- **[Evaluation package and audit results](./evaluation/)** — this directory is reserved for the original, unmodified run archive. The associated file hash should be checked before relying on a downloaded copy.

For technical replication, begin with `evaluation/README.md` and `docs/HANDOFF.md` **inside the corrected evaluation ZIP**, not with the HTML page. The website is an explanatory view over an already recorded run: clicking a scenario **does not execute a test or contact LexO-server**.

## Scope and limitations

This controlled experiment used one GraphDB instance, one coordinated LexO-server writer, RDF 1.1 reification at runtime, and a *declared* test identity. It did not evaluate institutional authentication, multiple concurrent publishers, human usability, or the truth of the historical proposals. The SHACL comparison applies to the specified structural baseline rather than every possible SHACL-based validation policy.

## Project materials

- `index.html` — English, interactive scholarly-audit demonstrator for GitHub Pages.
- `italiano.html` — equivalent Italian-language demonstrator.
- `evaluation/` — downloadable technical evaluation archive.
- `.github/workflows/pages.yml` — static-site deployment configuration.

The pages have no runtime dependency on LexO-server or GraphDB. They can be opened locally, even offline.

## Related software

- [LexInt vocabulary and examples](https://github.com/andreabellandi/LexInt)
- [LexO-server](https://github.com/andreabellandi/LexO-server)

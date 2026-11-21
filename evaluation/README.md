# Technical evaluation package

This directory is the designated location for the **corrected, immutable evaluation archive**:

`dsh2027-lexint-evaluation-dsh2027-corrected-20261121-77d2c3e.zip`

- **Evaluation run:** `dsh2027-corrected-20261121-77d2c3e`
- **Date:** 21 November 2026
- **Software commit:** [LexO-server `77d2c3e`](https://github.com/andreabellandi/LexO-server/commit/77d2c3e93b96a4ac0a4f2e6f98f9c40e781079ad)
- **Original archive size:** 507,734 bytes
- **Contents:** RDF fixtures and snapshots, expected answers (oracle), T01–T12 case definitions and results, CQ01–CQ07 queries and result sets, CE01–CE03 counterexamples, GraphDB rollback traces and audit evidence, checksums, scripts and instructions.

**Current status:** The original binary ZIP must be added to this directory to make the complete recorded run downloadable from this repository. Its SHA-256 checksum is `fc03584abb2086ec7a28943d72b0e44c4b25f26c6fb51f3cd2924a804d166683`.

**Already available for immediate inspection:** the original run's four compact result reports are published in [`results/`](./results/): [`summary.json`](./results/summary.json), [`tests.csv`](./results/tests.csv), [`cq-results.csv`](./results/cq-results.csv), and [`comparison.csv`](./results/comparison.csv). They show the observed test outcomes, but they are not a substitute for the complete archive of traces and snapshots. A source-tree copy is **not** interchangeable with this archive, because the archive also contains the results and traces generated during the experiment.

Until then, the public versioned [LexO-server evaluation source tree](https://github.com/andreabellandi/LexO-server/tree/77d2c3e93b96a4ac0a4f2e6f98f9c40e781079ad/evaluation/dsh2027) provides the experiment's scripts, fixtures, queries, test cases, and oracle definitions.

## How to inspect the complete archive, once uploaded

1. Download the corrected ZIP above without modifying it.
2. Unzip the archive; open `evaluation/README.md` for execution instructions and `docs/HANDOFF.md` for implementation notes.
3. Inspect the `results/<run-id>/` folder: `tests.csv`, `cq-results.csv`, `comparison.csv`, and `summary.json`.
4. Compare the output RDF graphs against the frozen `expected-v1.ttl` and `expected-v2.ttl` fixtures.
5. Use the scripts and isolated test environment if you want to reproduce the run rather than merely inspect the archived observations.

The [scholarly demonstrator](../index.html) is designed for nontechnical readers and does not run tests live. It shows the implications of the same experiment for scholarly interpretation and editorial accountability.

## Uploading the complete evidence archive (repository maintainer)

In the GitHub repository, open the `evaluation/` directory, choose **Add file → Upload files**, and select the unchanged local file `dsh2027-lexint-evaluation-dsh2027-corrected-20261121-77d2c3e.zip`. Commit to `main`. Verify that the SHA-256 of the resulting download matches the checksum above. Do not upload the older, uncorrected run or replace this file with a newly regenerated archive without clearly identifying the new run.

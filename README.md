# XRPL Validator — Daily Engineering Reports

Daily operations and engineering record of [xrpl-validator](https://github.com/ilubxrp589/xrpl-validator): a Rust XRP
Ledger validator and a native Rust transaction engine that is checked byte-for-byte against rippled on live mainnet
traffic.

Each report is compiled automatically just after midnight (US Eastern) for the previous US Eastern calendar day and
covers XRPL work only: the validator's service levels, the native engine's conformance, every receipt with its
disposition, incidents, deployments and merged changes, the independence program, network events, the amendment watch
read from the XRP Ledger, and XRPL research. Tables use UTC. Every report is available as Markdown and PDF.

**Format v3 from 2026-10-20; earlier reports re-issued on 2026-10-21.** Format v3 adds service levels, a receipt
register with dispositions, incidents, a deployment change log, network events and the independence program, and counts
every receipt of the day across all steps and restarts. The format-v2 reports counted only the native-engine shadow's
receipts in the soak running when the report was generated, and listed commits by commit date only. Every earlier
report was re-issued in format v3 on 2026-10-21 from the records that exist for its day; each says which were
available, and the originals are kept in this repository's history.

## How to read these reports

| Term | Meaning |
|---|---|
| Coverage | Validations the validator issued, as a share of the ledgers the network closed in the period. |
| Agreement | Each validation's ledger hash compared with the network's validated hash for that ledger. |
| Reference node | The rippled node the validator compares its own work against. |
| Ledger feed | The validator's stream of newly closed ledgers, which its engine applies. |
| Native engine | The Rust implementation of XRPL transaction application (`crates/xrpl-ledger`). |
| Steps 1–5 | The independence checks: (1) the native engine against libxrpl, rippled's own engine; (2) our transaction records; (3) our transaction order; (4) ledger data and validations from peers; (5) our own ledger hash. |
| Receipt | A recorded difference between the validator's own work and the network's, or trusted validations that reached the validator short of quorum. |
| Receipt register | The day's receipts, each with an ID, time, ledger, step, description and disposition. |
| Disposition | What became of a receipt: fixed (finding, commit, deployment), explained (not a defect, with the reason) or open. |
| Incident | Ledgers the validator left unsigned outside planned maintenance, with impact, cause and action. |
| Deployment / cycle | A build that passed the test suites and mainnet replay windows, deployed, health-checked and soaked. |
| Soak | A 24-hour live run on a fixed build. A clean soak records no engine receipts. |
| Finding (F-number) | A divergence from rippled's behaviour that was diagnosed and fixed; most are pinned as byte-exact regression vectors. |
| Independence program | The goal of 30 consecutive days on which every validation is of a ledger the validator built entirely itself. |
| Campaign | Crafted transactions on testnet or devnet that exercise paths mainnet rarely reaches; their ledger changes become test vectors. |
| Amendment watch | Amendment majorities, activations and voting events, read directly from the XRP Ledger. |

**Coverage.** A report exists for each day with XRPL commits, and for every day from 2026-09-23. Reports dated before
2026-09-23 were compiled retrospectively from the git history and carry no live snapshot. Ledger-derived amendment
data begins on 2026-09-05, the start of the reference node's retained ledger history. Corrections to a published report
appear in the next report's "Corrections to earlier reports" section.

## Reports

| Day | Summary |
|---|---|
| [2026-10-25](reports/2026/2026-10-25.md) · [PDF](reports/2026/2026-10-25.pdf) | Not assessed · 0 engine receipts · 1 deployment |
| [2026-10-24](reports/2026/2026-10-24.md) · [PDF](reports/2026/2026-10-24.pdf) | Normal · coverage 99.658% · 0 engine receipts · 1 deployment |
| [2026-10-23](reports/2026/2026-10-23.md) · [PDF](reports/2026/2026-10-23.pdf) | Normal · coverage 100.000% · 0 engine receipts · 0 deployments |
| [2026-10-22](reports/2026/2026-10-22.md) · [PDF](reports/2026/2026-10-22.pdf) | Normal · coverage 99.663% · 0 engine receipts · 1 deployment |
| [2026-10-21](reports/2026/2026-10-21.md) · [PDF](reports/2026/2026-10-21.pdf) | Degraded · coverage 99.963% · 2 engine receipts · 0 deployments |
| [2026-10-20](reports/2026/2026-10-20.md) · [PDF](reports/2026/2026-10-20.pdf) | Degraded · coverage 99.152% · 2 engine receipts · 3 deployments · 2 findings fixed |
| [2026-10-19](reports/2026/2026-10-19.md) · [PDF](reports/2026/2026-10-19.pdf) | Normal · coverage 99.995% · 0 deployments |
| [2026-10-18](reports/2026/2026-10-18.md) · [PDF](reports/2026/2026-10-18.pdf) | Impaired · coverage 99.915% · 2 deployments |
| [2026-10-17](reports/2026/2026-10-17.md) · [PDF](reports/2026/2026-10-17.pdf) | Impaired · coverage 100.000% · 0 deployments |
| [2026-10-16](reports/2026/2026-10-16.md) · [PDF](reports/2026/2026-10-16.pdf) | Impaired · coverage 99.924% · 2 deployments · 1 finding fixed |
| [2026-10-15](reports/2026/2026-10-15.md) · [PDF](reports/2026/2026-10-15.pdf) | Impaired · coverage 99.874% · 3 deployments |
| [2026-10-14](reports/2026/2026-10-14.md) · [PDF](reports/2026/2026-10-14.pdf) | Impaired · coverage 99.802% · 5 deployments |
| [2026-10-13](reports/2026/2026-10-13.md) · [PDF](reports/2026/2026-10-13.pdf) | Impaired · coverage 99.959% · 1 deployment |
| [2026-10-12](reports/2026/2026-10-12.md) · [PDF](reports/2026/2026-10-12.pdf) | Impaired · coverage 99.960% · 1 deployment |
| [2026-10-11](reports/2026/2026-10-11.md) · [PDF](reports/2026/2026-10-11.pdf) | Normal · coverage 99.960% · 1 deployment · 1 finding fixed |
| [2026-10-10](reports/2026/2026-10-10.md) · [PDF](reports/2026/2026-10-10.pdf) | Normal · coverage 99.951% · 1 deployment · 2 findings fixed |
| [2026-10-09](reports/2026/2026-10-09.md) · [PDF](reports/2026/2026-10-09.pdf) | Normal · coverage 99.960% · 1 deployment · 1 finding fixed |
| [2026-10-08](reports/2026/2026-10-08.md) · [PDF](reports/2026/2026-10-08.pdf) | Degraded · coverage 99.131% · 1 deployment |
| [2026-10-07](reports/2026/2026-10-07.md) · [PDF](reports/2026/2026-10-07.pdf) | Normal · coverage 100.000% · 0 deployments |
| [2026-10-06](reports/2026/2026-10-06.md) · [PDF](reports/2026/2026-10-06.pdf) | Normal · coverage 100.000% · 0 deployments |
| [2026-10-05](reports/2026/2026-10-05.md) · [PDF](reports/2026/2026-10-05.pdf) | Normal · coverage 100.000% · 0 deployments |
| [2026-10-04](reports/2026/2026-10-04.md) · [PDF](reports/2026/2026-10-04.pdf) | Normal (agreement not checked) · coverage 100.000% · 0 deployments |
| [2026-10-03](reports/2026/2026-10-03.md) · [PDF](reports/2026/2026-10-03.pdf) | Normal (agreement not checked) · coverage 99.903% · 2 deployments · 5 findings fixed |
| [2026-10-02](reports/2026/2026-10-02.md) · [PDF](reports/2026/2026-10-02.pdf) | Normal (agreement not checked) · coverage 100.000% · 0 deployments · 1 finding fixed |
| [2026-10-01](reports/2026/2026-10-01.md) · [PDF](reports/2026/2026-10-01.pdf) | Normal (agreement not checked) · coverage 99.960% · 1 deployment |
| [2026-09-30](reports/2026/2026-09-30.md) · [PDF](reports/2026/2026-09-30.pdf) | Normal (agreement not checked) · coverage 99.960% · 1 deployment · 2 findings fixed |
| [2026-09-29](reports/2026/2026-09-29.md) · [PDF](reports/2026/2026-09-29.pdf) | Normal (agreement not checked) · coverage 99.960% · 1 deployment · 2 findings fixed |
| [2026-09-28](reports/2026/2026-09-28.md) · [PDF](reports/2026/2026-09-28.pdf) | Normal (agreement not checked) · coverage 99.919% · 2 deployments · 1 finding fixed |
| [2026-09-27](reports/2026/2026-09-27.md) · [PDF](reports/2026/2026-09-27.pdf) | Normal (agreement not checked) · coverage 99.959% · 1 deployment · 3 findings fixed |
| [2026-09-26](reports/2026/2026-09-26.md) · [PDF](reports/2026/2026-09-26.pdf) | Normal (agreement not checked) · coverage 99.959% · 1 deployment |
| [2026-09-25](reports/2026/2026-09-25.md) · [PDF](reports/2026/2026-09-25.pdf) | Normal (agreement not checked) · coverage 99.892% · 2 deployments · 2 findings fixed |
| [2026-09-24](reports/2026/2026-09-24.md) · [PDF](reports/2026/2026-09-24.pdf) | Normal (agreement not checked) · coverage 99.510% · 1 deployment · 2 findings fixed |
| [2026-09-23](reports/2026/2026-09-23.md) · [PDF](reports/2026/2026-09-23.pdf) | Normal (agreement not checked) · coverage 97.635% · 3 deployments · 40 findings fixed |
| [2026-09-22](reports/2026/2026-09-22.md) · [PDF](reports/2026/2026-09-22.pdf) | Degraded · coverage 98.931% · 2 deployments · 26 findings fixed |
| [2026-09-21](reports/2026/2026-09-21.md) · [PDF](reports/2026/2026-09-21.pdf) | Normal (agreement not checked) · coverage 99.306% · 2 deployments · 1 finding fixed |
| [2026-09-20](reports/2026/2026-09-20.md) · [PDF](reports/2026/2026-09-20.pdf) | Degraded · coverage 99.689% · 1 deployment |
| [2026-09-19](reports/2026/2026-09-19.md) · [PDF](reports/2026/2026-09-19.pdf) | Not assessed · coverage 100.000% · 2 deployments |
| [2026-09-18](reports/2026/2026-09-18.md) · [PDF](reports/2026/2026-09-18.pdf) | Not assessed · 2 deployments |
| [2026-09-17](reports/2026/2026-09-17.md) · [PDF](reports/2026/2026-09-17.pdf) | Not assessed · 6 deployments · 2 findings fixed |
| [2026-09-15](reports/2026/2026-09-15.md) · [PDF](reports/2026/2026-09-15.pdf) | Not assessed · 2 deployments · 1 finding fixed |
| [2026-09-14](reports/2026/2026-09-14.md) · [PDF](reports/2026/2026-09-14.pdf) | Not assessed · 3 deployments · 11 findings fixed |
| [2026-09-13](reports/2026/2026-09-13.md) · [PDF](reports/2026/2026-09-13.pdf) | Not assessed · 3 deployments · 11 findings fixed |
| [2026-09-12](reports/2026/2026-09-12.md) · [PDF](reports/2026/2026-09-12.pdf) | Not assessed · 0 deployments · 1 finding fixed |
| [2026-09-11](reports/2026/2026-09-11.md) · [PDF](reports/2026/2026-09-11.pdf) | Not assessed · 2 deployments · 13 findings fixed |
| [2026-09-10](reports/2026/2026-09-10.md) · [PDF](reports/2026/2026-09-10.pdf) | Not assessed · 0 deployments · 10 findings fixed |
| [2026-09-09](reports/2026/2026-09-09.md) · [PDF](reports/2026/2026-09-09.pdf) | Not assessed · 0 deployments · 14 findings fixed |
| [2026-09-08](reports/2026/2026-09-08.md) · [PDF](reports/2026/2026-09-08.pdf) | Not assessed · 0 deployments · 11 findings fixed |
| [2026-09-07](reports/2026/2026-09-07.md) · [PDF](reports/2026/2026-09-07.pdf) | Not assessed · 0 deployments · 28 findings fixed |
| [2026-09-06](reports/2026/2026-09-06.md) · [PDF](reports/2026/2026-09-06.pdf) | Not assessed · 0 deployments · 12 findings fixed |
| [2026-09-05](reports/2026/2026-09-05.md) · [PDF](reports/2026/2026-09-05.pdf) | Not assessed · 0 deployments · 4 findings fixed |
| [2026-09-04](reports/2026/2026-09-04.md) · [PDF](reports/2026/2026-09-04.pdf) | Not assessed · 0 deployments |
| [2026-09-03](reports/2026/2026-09-03.md) · [PDF](reports/2026/2026-09-03.pdf) | Not assessed · 0 deployments |
| [2026-09-02](reports/2026/2026-09-02.md) · [PDF](reports/2026/2026-09-02.pdf) | Not assessed · 0 deployments |
| [2026-09-01](reports/2026/2026-09-01.md) · [PDF](reports/2026/2026-09-01.pdf) | Not assessed · 0 deployments · 1 finding fixed |
| [2026-08-31](reports/2026/2026-08-31.md) · [PDF](reports/2026/2026-08-31.pdf) | Not assessed · 0 deployments |
| [2026-08-30](reports/2026/2026-08-30.md) · [PDF](reports/2026/2026-08-30.pdf) | Not assessed · 0 deployments |
| [2026-08-29](reports/2026/2026-08-29.md) · [PDF](reports/2026/2026-08-29.pdf) | Not assessed · 0 deployments |
| [2026-08-28](reports/2026/2026-08-28.md) · [PDF](reports/2026/2026-08-28.pdf) | Not assessed · 0 deployments |
| [2026-08-27](reports/2026/2026-08-27.md) · [PDF](reports/2026/2026-08-27.pdf) | Not assessed · 0 deployments |
| [2026-08-26](reports/2026/2026-08-26.md) · [PDF](reports/2026/2026-08-26.pdf) | Not assessed · 0 deployments |
| [2026-08-25](reports/2026/2026-08-25.md) · [PDF](reports/2026/2026-08-25.pdf) | Not assessed · 0 deployments |
| [2026-08-24](reports/2026/2026-08-24.md) · [PDF](reports/2026/2026-08-24.pdf) | Not assessed · 0 deployments |
| [2026-08-23](reports/2026/2026-08-23.md) · [PDF](reports/2026/2026-08-23.pdf) | Not assessed · 0 deployments |
| [2026-08-22](reports/2026/2026-08-22.md) · [PDF](reports/2026/2026-08-22.pdf) | Not assessed · 0 deployments |
| [2026-08-21](reports/2026/2026-08-21.md) · [PDF](reports/2026/2026-08-21.pdf) | Not assessed · 0 deployments |
| [2026-08-20](reports/2026/2026-08-20.md) · [PDF](reports/2026/2026-08-20.pdf) | Not assessed · 0 deployments |
| [2026-08-19](reports/2026/2026-08-19.md) · [PDF](reports/2026/2026-08-19.pdf) | Not assessed · 0 deployments |
| [2026-08-18](reports/2026/2026-08-18.md) · [PDF](reports/2026/2026-08-18.pdf) | Not assessed · 0 deployments |
| [2026-08-17](reports/2026/2026-08-17.md) · [PDF](reports/2026/2026-08-17.pdf) | Not assessed · 0 deployments |
| [2026-08-16](reports/2026/2026-08-16.md) · [PDF](reports/2026/2026-08-16.pdf) | Not assessed · 0 deployments |
| [2026-08-15](reports/2026/2026-08-15.md) · [PDF](reports/2026/2026-08-15.pdf) | Not assessed · 0 deployments |
| [2026-08-14](reports/2026/2026-08-14.md) · [PDF](reports/2026/2026-08-14.pdf) | Not assessed · 0 deployments |
| [2026-08-13](reports/2026/2026-08-13.md) · [PDF](reports/2026/2026-08-13.pdf) | Not assessed · 0 deployments |
| [2026-08-12](reports/2026/2026-08-12.md) · [PDF](reports/2026/2026-08-12.pdf) | Not assessed · 0 deployments |
| [2026-08-11](reports/2026/2026-08-11.md) · [PDF](reports/2026/2026-08-11.pdf) | Not assessed · 0 deployments |
| [2026-08-10](reports/2026/2026-08-10.md) · [PDF](reports/2026/2026-08-10.pdf) | Not assessed · 0 deployments |
| [2026-08-09](reports/2026/2026-08-09.md) · [PDF](reports/2026/2026-08-09.pdf) | Not assessed · 0 deployments |
| [2026-08-08](reports/2026/2026-08-08.md) · [PDF](reports/2026/2026-08-08.pdf) | Not assessed · 0 deployments |
| [2026-08-07](reports/2026/2026-08-07.md) · [PDF](reports/2026/2026-08-07.pdf) | Not assessed · 0 deployments |
| [2026-08-06](reports/2026/2026-08-06.md) · [PDF](reports/2026/2026-08-06.pdf) | Not assessed · 0 deployments |
| [2026-08-05](reports/2026/2026-08-05.md) · [PDF](reports/2026/2026-08-05.pdf) | Not assessed · 0 deployments |
| [2026-08-04](reports/2026/2026-08-04.md) · [PDF](reports/2026/2026-08-04.pdf) | Not assessed · 0 deployments |
| [2026-08-03](reports/2026/2026-08-03.md) · [PDF](reports/2026/2026-08-03.pdf) | Not assessed · 0 deployments |
| [2026-08-02](reports/2026/2026-08-02.md) · [PDF](reports/2026/2026-08-02.pdf) | Not assessed · 0 deployments |
| [2026-08-01](reports/2026/2026-08-01.md) · [PDF](reports/2026/2026-08-01.pdf) | Not assessed · 0 deployments |
| [2026-07-31](reports/2026/2026-07-31.md) · [PDF](reports/2026/2026-07-31.pdf) | Not assessed · 0 deployments |
| [2026-07-30](reports/2026/2026-07-30.md) · [PDF](reports/2026/2026-07-30.pdf) | Not assessed · 0 deployments |
| [2026-07-29](reports/2026/2026-07-29.md) · [PDF](reports/2026/2026-07-29.pdf) | Not assessed · 0 deployments |
| [2026-07-28](reports/2026/2026-07-28.md) · [PDF](reports/2026/2026-07-28.pdf) | Not assessed · 0 deployments |
| [2026-07-27](reports/2026/2026-07-27.md) · [PDF](reports/2026/2026-07-27.pdf) | Not assessed · 0 deployments |
| [2026-07-26](reports/2026/2026-07-26.md) · [PDF](reports/2026/2026-07-26.pdf) | Not assessed · 0 deployments |
| [2026-07-25](reports/2026/2026-07-25.md) · [PDF](reports/2026/2026-07-25.pdf) | Not assessed · 0 deployments |
| [2026-07-24](reports/2026/2026-07-24.md) · [PDF](reports/2026/2026-07-24.pdf) | Not assessed · 0 deployments |
| [2026-07-23](reports/2026/2026-07-23.md) · [PDF](reports/2026/2026-07-23.pdf) | Not assessed · 0 deployments |
| [2026-07-22](reports/2026/2026-07-22.md) · [PDF](reports/2026/2026-07-22.pdf) | Not assessed · 0 deployments |
| [2026-07-21](reports/2026/2026-07-21.md) · [PDF](reports/2026/2026-07-21.pdf) | Not assessed · 0 deployments |
| [2026-07-20](reports/2026/2026-07-20.md) · [PDF](reports/2026/2026-07-20.pdf) | Not assessed · 0 deployments |
| [2026-07-19](reports/2026/2026-07-19.md) · [PDF](reports/2026/2026-07-19.pdf) | Not assessed · 0 deployments |
| [2026-07-18](reports/2026/2026-07-18.md) · [PDF](reports/2026/2026-07-18.pdf) | Not assessed · 0 deployments |
| [2026-07-17](reports/2026/2026-07-17.md) · [PDF](reports/2026/2026-07-17.pdf) | Not assessed · 0 deployments |
| [2026-07-16](reports/2026/2026-07-16.md) · [PDF](reports/2026/2026-07-16.pdf) | Not assessed · 0 deployments |
| [2026-07-15](reports/2026/2026-07-15.md) · [PDF](reports/2026/2026-07-15.pdf) | Not assessed · 0 deployments |
| [2026-07-10](reports/2026/2026-07-10.md) · [PDF](reports/2026/2026-07-10.pdf) | Not assessed · 0 deployments |
| [2026-07-04](reports/2026/2026-07-04.md) · [PDF](reports/2026/2026-07-04.pdf) | Not assessed · 0 deployments |
| [2026-06-30](reports/2026/2026-06-30.md) · [PDF](reports/2026/2026-06-30.pdf) | Not assessed · 0 deployments |
| [2026-06-20](reports/2026/2026-06-20.md) · [PDF](reports/2026/2026-06-20.pdf) | Not assessed · 0 deployments |
| [2026-06-16](reports/2026/2026-06-16.md) · [PDF](reports/2026/2026-06-16.pdf) | Not assessed · 0 deployments |
| [2026-06-15](reports/2026/2026-06-15.md) · [PDF](reports/2026/2026-06-15.pdf) | Not assessed · 0 deployments |
| [2026-06-14](reports/2026/2026-06-14.md) · [PDF](reports/2026/2026-06-14.pdf) | Not assessed · 0 deployments |
| [2026-06-10](reports/2026/2026-06-10.md) · [PDF](reports/2026/2026-06-10.pdf) | Not assessed · 0 deployments |
| [2026-05-31](reports/2026/2026-05-31.md) · [PDF](reports/2026/2026-05-31.pdf) | Not assessed · 0 deployments |
| [2026-05-29](reports/2026/2026-05-29.md) · [PDF](reports/2026/2026-05-29.pdf) | Not assessed · 0 deployments |
| [2026-05-19](reports/2026/2026-05-19.md) · [PDF](reports/2026/2026-05-19.pdf) | Not assessed · 0 deployments |
| [2026-05-17](reports/2026/2026-05-17.md) · [PDF](reports/2026/2026-05-17.pdf) | Not assessed · 0 deployments |
| [2026-05-16](reports/2026/2026-05-16.md) · [PDF](reports/2026/2026-05-16.pdf) | Not assessed · 0 deployments |
| [2026-05-15](reports/2026/2026-05-15.md) · [PDF](reports/2026/2026-05-15.pdf) | Not assessed · 0 deployments |
| [2026-05-05](reports/2026/2026-05-05.md) · [PDF](reports/2026/2026-05-05.pdf) | Not assessed · 0 deployments |
| [2026-05-04](reports/2026/2026-05-04.md) · [PDF](reports/2026/2026-05-04.pdf) | Not assessed · 0 deployments |
| [2026-05-02](reports/2026/2026-05-02.md) · [PDF](reports/2026/2026-05-02.pdf) | Not assessed · 0 deployments |
| [2026-05-01](reports/2026/2026-05-01.md) · [PDF](reports/2026/2026-05-01.pdf) | Not assessed · 0 deployments |
| [2026-04-30](reports/2026/2026-04-30.md) · [PDF](reports/2026/2026-04-30.pdf) | Not assessed · 0 deployments |
| [2026-04-21](reports/2026/2026-04-21.md) · [PDF](reports/2026/2026-04-21.pdf) | Not assessed · 0 deployments |
| [2026-04-19](reports/2026/2026-04-19.md) · [PDF](reports/2026/2026-04-19.pdf) | Not assessed · 0 deployments |
| [2026-04-16](reports/2026/2026-04-16.md) · [PDF](reports/2026/2026-04-16.pdf) | Not assessed · 0 deployments |
| [2026-04-15](reports/2026/2026-04-15.md) · [PDF](reports/2026/2026-04-15.pdf) | Not assessed · 0 deployments |
| [2026-04-13](reports/2026/2026-04-13.md) · [PDF](reports/2026/2026-04-13.pdf) | Not assessed · 0 deployments |
| [2026-04-12](reports/2026/2026-04-12.md) · [PDF](reports/2026/2026-04-12.pdf) | Not assessed · 0 deployments |
| [2026-04-10](reports/2026/2026-04-10.md) · [PDF](reports/2026/2026-04-10.pdf) | Not assessed · 0 deployments |
| [2026-04-07](reports/2026/2026-04-07.md) · [PDF](reports/2026/2026-04-07.pdf) | Not assessed · 0 deployments |
| [2026-04-06](reports/2026/2026-04-06.md) · [PDF](reports/2026/2026-04-06.pdf) | Not assessed · 0 deployments |
| [2026-04-05](reports/2026/2026-04-05.md) · [PDF](reports/2026/2026-04-05.pdf) | Not assessed · 0 deployments |
| [2026-04-04](reports/2026/2026-04-04.md) · [PDF](reports/2026/2026-04-04.pdf) | Not assessed · 0 deployments |
| [2026-04-02](reports/2026/2026-04-02.md) · [PDF](reports/2026/2026-04-02.pdf) | Not assessed · 0 deployments |
| [2026-04-01](reports/2026/2026-04-01.md) · [PDF](reports/2026/2026-04-01.pdf) | Not assessed · 0 deployments |
| [2026-03-31](reports/2026/2026-03-31.md) · [PDF](reports/2026/2026-03-31.pdf) | Not assessed · 0 deployments |
| [2026-03-30](reports/2026/2026-03-30.md) · [PDF](reports/2026/2026-03-30.pdf) | Not assessed · 0 deployments |
| [2026-03-29](reports/2026/2026-03-29.md) · [PDF](reports/2026/2026-03-29.pdf) | Not assessed · 0 deployments |
| [2026-03-25](reports/2026/2026-03-25.md) · [PDF](reports/2026/2026-03-25.pdf) | Not assessed · 0 deployments |
| [2026-03-24](reports/2026/2026-03-24.md) · [PDF](reports/2026/2026-03-24.pdf) | Not assessed · 0 deployments |
| [2026-03-23](reports/2026/2026-03-23.md) · [PDF](reports/2026/2026-03-23.pdf) | Not assessed · 0 deployments |
| [2026-03-22](reports/2026/2026-03-22.md) · [PDF](reports/2026/2026-03-22.pdf) | Not assessed · 0 deployments |
| [2026-03-21](reports/2026/2026-03-21.md) · [PDF](reports/2026/2026-03-21.pdf) | Not assessed · 0 deployments |
| [2026-03-20](reports/2026/2026-03-20.md) · [PDF](reports/2026/2026-03-20.pdf) | Not assessed · 0 deployments |

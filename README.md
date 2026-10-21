# XRPL Validator — Daily Engineering Reports

Daily operations and engineering record of [xrpl-validator](https://github.com/ilubxrp589/xrpl-validator): a Rust XRP
Ledger validator and a native Rust transaction engine that is checked byte-for-byte against rippled on live mainnet
traffic.

Each report is compiled automatically just after midnight (US Eastern) for the previous US Eastern calendar day and
covers XRPL work only: the validator's service levels, the native engine's conformance, every receipt with its
disposition, incidents, deployments and merged changes, the independence program, network events, the amendment watch
read from the XRP Ledger, and XRPL research. Tables use UTC. Every report is available as Markdown and PDF.

**Format v3 from 2026-10-20.** Reports from 2026-10-20 on add service levels, a receipt register with dispositions,
incidents, a deployment change log, network events and the independence program, and count every receipt of the day
across all steps and restarts. Earlier reports (format v2) counted only the native-engine shadow's receipts in the
soak running when the report was generated, and listed commits by commit date only.

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
| [2026-10-20](reports/2026/2026-10-20.md) · [PDF](reports/2026/2026-10-20.pdf) | Degraded · coverage 99.152% · 2 engine receipts · 3 deployments · 2 findings fixed |
| [2026-10-19](reports/2026/2026-10-19.md) · [PDF](reports/2026/2026-10-19.pdf) | 0 commits, 27,640/27,640 ledgers matched |
| [2026-10-18](reports/2026/2026-10-18.md) · [PDF](reports/2026/2026-10-18.pdf) | 2 commits, 5,581/5,581 ledgers matched |
| [2026-10-17](reports/2026/2026-10-17.md) · [PDF](reports/2026/2026-10-17.pdf) | 0 commits, 30,238/30,238 ledgers matched |
| [2026-10-16](reports/2026/2026-10-16.md) · [PDF](reports/2026/2026-10-16.pdf) | 2 commits, 1 finding fixed, 8,019/8,019 ledgers matched |
| [2026-10-15](reports/2026/2026-10-15.md) · [PDF](reports/2026/2026-10-15.pdf) | 12 commits, 10,937/10,937 ledgers matched |
| [2026-10-14](reports/2026/2026-10-14.md) · [PDF](reports/2026/2026-10-14.pdf) | 13 commits, 913/913 ledgers matched |
| [2026-10-13](reports/2026/2026-10-13.md) · [PDF](reports/2026/2026-10-13.pdf) | 4 commits, 20,374/20,374 ledgers matched |
| [2026-10-12](reports/2026/2026-10-12.md) · [PDF](reports/2026/2026-10-12.pdf) | 1 commit, 20,900/20,900 ledgers matched |
| [2026-10-11](reports/2026/2026-10-11.md) · [PDF](reports/2026/2026-10-11.pdf) | 1 commit, 1 finding fixed, 21,474/21,474 ledgers matched |
| [2026-10-10](reports/2026/2026-10-10.md) · [PDF](reports/2026/2026-10-10.pdf) | 4 commits, 2 findings fixed, 21,891/21,893 ledgers matched |
| [2026-10-09](reports/2026/2026-10-09.md) · [PDF](reports/2026/2026-10-09.pdf) | 8 commits, 1 finding fixed, 10,840/10,840 ledgers matched |
| [2026-10-08](reports/2026/2026-10-08.md) · [PDF](reports/2026/2026-10-08.pdf) | 7 commits, 3,759/3,759 ledgers matched |
| [2026-10-07](reports/2026/2026-10-07.md) · [PDF](reports/2026/2026-10-07.pdf) | 2 commits, 98,777/98,777 ledgers matched |
| [2026-10-06](reports/2026/2026-10-06.md) · [PDF](reports/2026/2026-10-06.pdf) | 0 commits, 76,424/76,424 ledgers matched |
| [2026-10-05](reports/2026/2026-10-05.md) · [PDF](reports/2026/2026-10-05.pdf) | 0 commits, 54,097/54,097 ledgers matched |
| [2026-10-04](reports/2026/2026-10-04.md) · [PDF](reports/2026/2026-10-04.pdf) | 0 commits, 31,655/31,655 ledgers matched |
| [2026-10-03](reports/2026/2026-10-03.md) · [PDF](reports/2026/2026-10-03.pdf) | 6 commits, 5 findings fixed, 8,972/8,972 ledgers matched |
| [2026-10-02](reports/2026/2026-10-02.md) · [PDF](reports/2026/2026-10-02.pdf) | 1 commit, 1 finding fixed, 22,815/22,816 ledgers matched |
| [2026-10-01](reports/2026/2026-10-01.md) · [PDF](reports/2026/2026-10-01.pdf) | 1 commit, 524/524 ledgers matched |
| [2026-09-30](reports/2026/2026-09-30.md) · [PDF](reports/2026/2026-09-30.pdf) | 2 commits, 2 findings fixed, 721/721 ledgers matched |
| [2026-09-29](reports/2026/2026-09-29.md) · [PDF](reports/2026/2026-09-29.pdf) | 3 commits, 2 findings fixed, 12,404/12,404 ledgers matched |
| [2026-09-28](reports/2026/2026-09-28.md) · [PDF](reports/2026/2026-09-28.pdf) | 2 commits, 1 finding fixed, 6,333/6,333 ledgers matched |
| [2026-09-27](reports/2026/2026-09-27.md) · [PDF](reports/2026/2026-09-27.pdf) | 3 commits, 3 findings fixed, 15,098/15,099 ledgers matched |
| [2026-09-26](reports/2026/2026-09-26.md) · [PDF](reports/2026/2026-09-26.pdf) | 4 commits, 10,531/10,531 ledgers matched |
| [2026-09-25](reports/2026/2026-09-25.md) · [PDF](reports/2026/2026-09-25.pdf) | 6 commits, 2 findings fixed, 11,965/11,965 ledgers matched |
| [2026-09-24](reports/2026/2026-09-24.md) · [PDF](reports/2026/2026-09-24.pdf) | 11 commits, 2 findings fixed, 4,910/4,910 ledgers matched |
| [2026-09-23](reports/2026/2026-09-23.md) · [PDF](reports/2026/2026-09-23.pdf) | 11 commits, 16 findings fixed, 920/920 ledgers matched |
| [2026-09-22](reports/2026/2026-09-22.md) · [PDF](reports/2026/2026-09-22.pdf) | 13 commits, 26 findings fixed |
| [2026-09-21](reports/2026/2026-09-21.md) · [PDF](reports/2026/2026-09-21.pdf) | 14 commits, 1 finding fixed |
| [2026-09-20](reports/2026/2026-09-20.md) · [PDF](reports/2026/2026-09-20.pdf) | 12 commits |
| [2026-09-19](reports/2026/2026-09-19.md) · [PDF](reports/2026/2026-09-19.pdf) | 16 commits |
| [2026-09-18](reports/2026/2026-09-18.md) · [PDF](reports/2026/2026-09-18.pdf) | 57 commits |
| [2026-09-17](reports/2026/2026-09-17.md) · [PDF](reports/2026/2026-09-17.pdf) | 27 commits, 2 findings fixed |
| [2026-09-15](reports/2026/2026-09-15.md) · [PDF](reports/2026/2026-09-15.pdf) | 7 commits, 1 finding fixed |
| [2026-09-14](reports/2026/2026-09-14.md) · [PDF](reports/2026/2026-09-14.pdf) | 24 commits, 9 findings fixed |
| [2026-09-13](reports/2026/2026-09-13.md) · [PDF](reports/2026/2026-09-13.pdf) | 11 commits, 11 findings fixed |
| [2026-09-12](reports/2026/2026-09-12.md) · [PDF](reports/2026/2026-09-12.pdf) | 2 commits, 1 finding fixed |
| [2026-09-11](reports/2026/2026-09-11.md) · [PDF](reports/2026/2026-09-11.pdf) | 13 commits, 12 findings fixed |
| [2026-09-10](reports/2026/2026-09-10.md) · [PDF](reports/2026/2026-09-10.pdf) | 9 commits, 9 findings fixed |
| [2026-09-09](reports/2026/2026-09-09.md) · [PDF](reports/2026/2026-09-09.pdf) | 5 commits, 5 findings fixed |
| [2026-09-08](reports/2026/2026-09-08.md) · [PDF](reports/2026/2026-09-08.pdf) | 11 commits, 11 findings fixed |
| [2026-09-07](reports/2026/2026-09-07.md) · [PDF](reports/2026/2026-09-07.pdf) | 36 commits, 28 findings fixed |
| [2026-09-06](reports/2026/2026-09-06.md) · [PDF](reports/2026/2026-09-06.pdf) | 12 commits, 12 findings fixed |
| [2026-09-05](reports/2026/2026-09-05.md) · [PDF](reports/2026/2026-09-05.pdf) | 25 commits, 4 findings fixed |
| [2026-09-04](reports/2026/2026-09-04.md) · [PDF](reports/2026/2026-09-04.pdf) | 7 commits |
| [2026-09-03](reports/2026/2026-09-03.md) · [PDF](reports/2026/2026-09-03.pdf) | 39 commits |
| [2026-09-02](reports/2026/2026-09-02.md) · [PDF](reports/2026/2026-09-02.pdf) | 32 commits |
| [2026-09-01](reports/2026/2026-09-01.md) · [PDF](reports/2026/2026-09-01.pdf) | 43 commits, 1 finding fixed |
| [2026-08-31](reports/2026/2026-08-31.md) · [PDF](reports/2026/2026-08-31.pdf) | 21 commits |
| [2026-08-30](reports/2026/2026-08-30.md) · [PDF](reports/2026/2026-08-30.pdf) | 5 commits |
| [2026-08-29](reports/2026/2026-08-29.md) · [PDF](reports/2026/2026-08-29.pdf) | 13 commits |
| [2026-08-28](reports/2026/2026-08-28.md) · [PDF](reports/2026/2026-08-28.pdf) | 6 commits |
| [2026-08-27](reports/2026/2026-08-27.md) · [PDF](reports/2026/2026-08-27.pdf) | 3 commits |
| [2026-08-26](reports/2026/2026-08-26.md) · [PDF](reports/2026/2026-08-26.pdf) | 2 commits |
| [2026-08-25](reports/2026/2026-08-25.md) · [PDF](reports/2026/2026-08-25.pdf) | 2 commits |
| [2026-08-24](reports/2026/2026-08-24.md) · [PDF](reports/2026/2026-08-24.pdf) | 11 commits |
| [2026-08-23](reports/2026/2026-08-23.md) · [PDF](reports/2026/2026-08-23.pdf) | 11 commits |
| [2026-08-22](reports/2026/2026-08-22.md) · [PDF](reports/2026/2026-08-22.pdf) | 8 commits |
| [2026-08-21](reports/2026/2026-08-21.md) · [PDF](reports/2026/2026-08-21.pdf) | 14 commits |
| [2026-08-20](reports/2026/2026-08-20.md) · [PDF](reports/2026/2026-08-20.pdf) | 14 commits |
| [2026-08-19](reports/2026/2026-08-19.md) · [PDF](reports/2026/2026-08-19.pdf) | 18 commits |
| [2026-08-18](reports/2026/2026-08-18.md) · [PDF](reports/2026/2026-08-18.pdf) | 14 commits |
| [2026-08-17](reports/2026/2026-08-17.md) · [PDF](reports/2026/2026-08-17.pdf) | 8 commits |
| [2026-08-16](reports/2026/2026-08-16.md) · [PDF](reports/2026/2026-08-16.pdf) | 4 commits |
| [2026-08-15](reports/2026/2026-08-15.md) · [PDF](reports/2026/2026-08-15.pdf) | 7 commits |
| [2026-08-14](reports/2026/2026-08-14.md) · [PDF](reports/2026/2026-08-14.pdf) | 9 commits |
| [2026-08-13](reports/2026/2026-08-13.md) · [PDF](reports/2026/2026-08-13.pdf) | 4 commits |
| [2026-08-12](reports/2026/2026-08-12.md) · [PDF](reports/2026/2026-08-12.pdf) | 11 commits |
| [2026-08-11](reports/2026/2026-08-11.md) · [PDF](reports/2026/2026-08-11.pdf) | 7 commits |
| [2026-08-10](reports/2026/2026-08-10.md) · [PDF](reports/2026/2026-08-10.pdf) | 6 commits |
| [2026-08-09](reports/2026/2026-08-09.md) · [PDF](reports/2026/2026-08-09.pdf) | 6 commits |
| [2026-08-08](reports/2026/2026-08-08.md) · [PDF](reports/2026/2026-08-08.pdf) | 11 commits |
| [2026-08-07](reports/2026/2026-08-07.md) · [PDF](reports/2026/2026-08-07.pdf) | 8 commits |
| [2026-08-06](reports/2026/2026-08-06.md) · [PDF](reports/2026/2026-08-06.pdf) | 7 commits |
| [2026-08-05](reports/2026/2026-08-05.md) · [PDF](reports/2026/2026-08-05.pdf) | 8 commits |
| [2026-08-04](reports/2026/2026-08-04.md) · [PDF](reports/2026/2026-08-04.pdf) | 5 commits |
| [2026-08-03](reports/2026/2026-08-03.md) · [PDF](reports/2026/2026-08-03.pdf) | 6 commits |
| [2026-08-02](reports/2026/2026-08-02.md) · [PDF](reports/2026/2026-08-02.pdf) | 5 commits |
| [2026-08-01](reports/2026/2026-08-01.md) · [PDF](reports/2026/2026-08-01.pdf) | 6 commits |
| [2026-07-31](reports/2026/2026-07-31.md) · [PDF](reports/2026/2026-07-31.pdf) | 6 commits |
| [2026-07-30](reports/2026/2026-07-30.md) · [PDF](reports/2026/2026-07-30.pdf) | 5 commits |
| [2026-07-29](reports/2026/2026-07-29.md) · [PDF](reports/2026/2026-07-29.pdf) | 1 commit |
| [2026-07-28](reports/2026/2026-07-28.md) · [PDF](reports/2026/2026-07-28.pdf) | 6 commits |
| [2026-07-27](reports/2026/2026-07-27.md) · [PDF](reports/2026/2026-07-27.pdf) | 8 commits |
| [2026-07-26](reports/2026/2026-07-26.md) · [PDF](reports/2026/2026-07-26.pdf) | 3 commits |
| [2026-07-25](reports/2026/2026-07-25.md) · [PDF](reports/2026/2026-07-25.pdf) | 6 commits |
| [2026-07-24](reports/2026/2026-07-24.md) · [PDF](reports/2026/2026-07-24.pdf) | 5 commits |
| [2026-07-23](reports/2026/2026-07-23.md) · [PDF](reports/2026/2026-07-23.pdf) | 14 commits |
| [2026-07-22](reports/2026/2026-07-22.md) · [PDF](reports/2026/2026-07-22.pdf) | 1 commit |
| [2026-07-21](reports/2026/2026-07-21.md) · [PDF](reports/2026/2026-07-21.pdf) | 11 commits |
| [2026-07-20](reports/2026/2026-07-20.md) · [PDF](reports/2026/2026-07-20.pdf) | 6 commits |
| [2026-07-19](reports/2026/2026-07-19.md) · [PDF](reports/2026/2026-07-19.pdf) | 8 commits |
| [2026-07-18](reports/2026/2026-07-18.md) · [PDF](reports/2026/2026-07-18.pdf) | 2 commits |
| [2026-07-17](reports/2026/2026-07-17.md) · [PDF](reports/2026/2026-07-17.pdf) | 14 commits |
| [2026-07-16](reports/2026/2026-07-16.md) · [PDF](reports/2026/2026-07-16.pdf) | 11 commits |
| [2026-07-15](reports/2026/2026-07-15.md) · [PDF](reports/2026/2026-07-15.pdf) | 1 commit |
| [2026-07-10](reports/2026/2026-07-10.md) · [PDF](reports/2026/2026-07-10.pdf) | 1 commit |
| [2026-07-04](reports/2026/2026-07-04.md) · [PDF](reports/2026/2026-07-04.pdf) | 5 commits |
| [2026-06-30](reports/2026/2026-06-30.md) · [PDF](reports/2026/2026-06-30.pdf) | 2 commits |
| [2026-06-20](reports/2026/2026-06-20.md) · [PDF](reports/2026/2026-06-20.pdf) | 2 commits |
| [2026-06-16](reports/2026/2026-06-16.md) · [PDF](reports/2026/2026-06-16.pdf) | 6 commits |
| [2026-06-15](reports/2026/2026-06-15.md) · [PDF](reports/2026/2026-06-15.pdf) | 13 commits |
| [2026-06-14](reports/2026/2026-06-14.md) · [PDF](reports/2026/2026-06-14.pdf) | 7 commits |
| [2026-06-10](reports/2026/2026-06-10.md) · [PDF](reports/2026/2026-06-10.pdf) | 1 commit |
| [2026-05-31](reports/2026/2026-05-31.md) · [PDF](reports/2026/2026-05-31.pdf) | 9 commits |
| [2026-05-29](reports/2026/2026-05-29.md) · [PDF](reports/2026/2026-05-29.pdf) | 1 commit |
| [2026-05-19](reports/2026/2026-05-19.md) · [PDF](reports/2026/2026-05-19.pdf) | 1 commit |
| [2026-05-17](reports/2026/2026-05-17.md) · [PDF](reports/2026/2026-05-17.pdf) | 1 commit |
| [2026-05-16](reports/2026/2026-05-16.md) · [PDF](reports/2026/2026-05-16.pdf) | 1 commit |
| [2026-05-15](reports/2026/2026-05-15.md) · [PDF](reports/2026/2026-05-15.pdf) | 3 commits |
| [2026-05-05](reports/2026/2026-05-05.md) · [PDF](reports/2026/2026-05-05.pdf) | 4 commits |
| [2026-05-04](reports/2026/2026-05-04.md) · [PDF](reports/2026/2026-05-04.pdf) | 2 commits |
| [2026-05-02](reports/2026/2026-05-02.md) · [PDF](reports/2026/2026-05-02.pdf) | 3 commits |
| [2026-05-01](reports/2026/2026-05-01.md) · [PDF](reports/2026/2026-05-01.pdf) | 5 commits |
| [2026-04-30](reports/2026/2026-04-30.md) · [PDF](reports/2026/2026-04-30.pdf) | 1 commit |
| [2026-04-21](reports/2026/2026-04-21.md) · [PDF](reports/2026/2026-04-21.pdf) | 6 commits |
| [2026-04-19](reports/2026/2026-04-19.md) · [PDF](reports/2026/2026-04-19.pdf) | 3 commits |
| [2026-04-16](reports/2026/2026-04-16.md) · [PDF](reports/2026/2026-04-16.pdf) | 7 commits |
| [2026-04-15](reports/2026/2026-04-15.md) · [PDF](reports/2026/2026-04-15.pdf) | 32 commits |
| [2026-04-13](reports/2026/2026-04-13.md) · [PDF](reports/2026/2026-04-13.pdf) | 1 commit |
| [2026-04-12](reports/2026/2026-04-12.md) · [PDF](reports/2026/2026-04-12.pdf) | 2 commits |
| [2026-04-10](reports/2026/2026-04-10.md) · [PDF](reports/2026/2026-04-10.pdf) | 6 commits |
| [2026-04-07](reports/2026/2026-04-07.md) · [PDF](reports/2026/2026-04-07.pdf) | 15 commits |
| [2026-04-06](reports/2026/2026-04-06.md) · [PDF](reports/2026/2026-04-06.pdf) | 13 commits |
| [2026-04-05](reports/2026/2026-04-05.md) · [PDF](reports/2026/2026-04-05.pdf) | 30 commits |
| [2026-04-04](reports/2026/2026-04-04.md) · [PDF](reports/2026/2026-04-04.pdf) | 9 commits |
| [2026-04-02](reports/2026/2026-04-02.md) · [PDF](reports/2026/2026-04-02.pdf) | 11 commits |
| [2026-04-01](reports/2026/2026-04-01.md) · [PDF](reports/2026/2026-04-01.pdf) | 5 commits |
| [2026-03-31](reports/2026/2026-03-31.md) · [PDF](reports/2026/2026-03-31.pdf) | 2 commits |
| [2026-03-30](reports/2026/2026-03-30.md) · [PDF](reports/2026/2026-03-30.pdf) | 1 commit |
| [2026-03-29](reports/2026/2026-03-29.md) · [PDF](reports/2026/2026-03-29.pdf) | 5 commits |
| [2026-03-25](reports/2026/2026-03-25.md) · [PDF](reports/2026/2026-03-25.pdf) | 2 commits |
| [2026-03-24](reports/2026/2026-03-24.md) · [PDF](reports/2026/2026-03-24.pdf) | 13 commits |
| [2026-03-23](reports/2026/2026-03-23.md) · [PDF](reports/2026/2026-03-23.pdf) | 17 commits |
| [2026-03-22](reports/2026/2026-03-22.md) · [PDF](reports/2026/2026-03-22.pdf) | 9 commits |
| [2026-03-21](reports/2026/2026-03-21.md) · [PDF](reports/2026/2026-03-21.pdf) | 36 commits |
| [2026-03-20](reports/2026/2026-03-20.md) · [PDF](reports/2026/2026-03-20.pdf) | 2 commits |

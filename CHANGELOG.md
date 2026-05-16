# Changelog

All notable changes to the `indian-mact-drafting` plugin are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/) and this project adheres to [Semantic Versioning](https://semver.org/).

---

## [0.1.0-alpha] — 2026-05-16 (initial release)

### Added

- **Plugin scaffolding** — `.claude-plugin/plugin.json` manifest · MIT `LICENSE` · `NOTICE.md` provenance and privilege statement · `.gitignore` · this `CHANGELOG.md` · comprehensive `README.md`.
- **Six-agent drafting pipeline** — Reader → Format → Drafter → Verifier → Refiner → Overseer. Each agent is a markdown file under `agents/<name>/<name>.md` with YAML frontmatter declaring `name`, `description`, and `allowed-tools`.
- **Shared infrastructure skills:**
  - `_drafting_common` — anti-pollution rules, encoding standards, language conventions, AI-style-marker blacklist, MACT-specific privacy firewall (acutely sensitive — accident-victim and bereaved-dependant personal data), citation discipline, and statutory currency rules (Motor Vehicles Act 1988 as amended by the Motor Vehicles (Amendment) Act 2019, Central Motor Vehicles Rules 1989, Employees' Compensation Act 1923, Bharatiya Nyaya Sanhita 2023, Bharatiya Nagarik Suraksha Sanhita 2023, Bharatiya Sakshya Adhiniyam 2023, Limitation Act 1963, CPC 1908, applicable State Court-Fees Act, applicable State Stamp Act).
  - `_mact_drafting_base` — universal Indian MACT pleading skeleton (Cause Title with correct forum nomenclature · Parties block · Statutory Opening invoking the operative section · Preamble identifying claimants as legal representatives / injured / property-owner · Tabular Particulars block per the State Motor Vehicles Rules / CMVR Form 54 · Description of the Accident · Negligence Grounds · Quantum Grounds with Sarla Verma + Pranay Sethi multiplier method · Prayer · Verification · Affidavit-in-support · Index · List of Documents · accompanying applications).
- **Ten case-type skill scaffolds:**
  - `mact-petition-section-166-fault-based-draft` — fault-based Claim Petition under Section 166 MV Act 1988 (death / injury / property damage), multiplier method per *Sarla Verma v. DTC* (2009) and *Pranay Sethi* (2017)
  - `mact-petition-section-164-lump-sum-draft` — structured-formula lump-sum Claim Petition under Section 164 MV Act 1988 (post-2019 amendment; supersedes the old Section 163A no-fault scheme)
  - `mact-petition-section-161-solatium-hit-and-run-draft` — Solatium Fund claim under Section 161 MV Act 1988 (hit-and-run cases — unidentified vehicle)
  - `mact-petition-third-party-insurance-section-147-draft` — claim petition with focused pleading of insurer's statutory liability under Section 147 read with Section 149 MV Act 1988
  - `mact-interim-compensation-application-draft` — interim compensation application pending final award (Section 140 MV Act erstwhile no-fault interim relief is now subsumed; the application invokes the Tribunal's procedural power to grant interim compensation)
  - `mact-appeal-section-173-to-high-court-draft` — appeal to the High Court under Section 173 MV Act 1988 (90-day limitation; deposit / pre-deposit requirements where applicable)
  - `mact-claim-execution-application-draft` — execution of MACT award (the award is enforceable as a decree of a civil court under Section 174 MV Act read with the Code of Civil Procedure 1908)
  - `workmen-compensation-claim-draft` — claim before the Commissioner under the Employees' Compensation Act 1923 (formerly the Workmen's Compensation Act); Section 167 MV Act election-clause between EC Act forum and MACT forum
  - `motor-vehicle-criminal-defence-bnss-draft` — defence in rash / negligent-driving prosecutions under BNSS 2023 (the successor provisions to IPC Sections 279, 304A, and the BNS 2023 corresponding sections — Section 281 rash driving, Section 282 endangering life by negligence, Section 283 obstruction of public way, Section 106 causing death by negligence)
  - `compensation-recovery-collector-section-174-draft` — recovery of compensation as arrears of land revenue under Section 174 MV Act 1988 (where the Tribunal's award is unsatisfied and the claimant seeks Collector-route execution)
- **State-config layer (mirroring district-court-drafting's state-config pattern)** — `state-config/state-config-template.md` template + `state-config/exemplars/` containing 8 researched state exemplars (Maharashtra deep · Karnataka · Tamil Nadu · Kerala · Delhi · Uttar Pradesh · West Bengal · Gujarat) and stub-state-exemplar markers for the remaining 20 States / Union Territories (community contribution welcomed). The state-config declares state-specific Motor Vehicles Rules + state-level MACT procedural variations + state-specific schedule of personal-injuries tabular formats per the anomalies log warning that tabular particulars vary significantly by State.
- **Forum-aware design** — the user supplies `case-config.md` declaring the chosen forum (territorial MACT / High Court for Section 173 appeal / Magistrate Court for the rash / negligent-driving criminal trial / Commissioner under the EC Act / Collector under Section 174), accident-trigger date, claimant composition, vehicle particulars, FIR particulars, insurer particulars, multiplier-table inputs (deceased age + monthly income + dependants), and the limitation-clock anchor.

### Notes on this release

This is a **v0.1.0-alpha scaffold release**. The structural skeletons, agent pipeline, base skills, 10 case-type skill frames, and state-config layer (with 1 deep state exemplar + 7 researched-not-validated state exemplars + 20 stub markers) are in place. Deep per-skill encoding (full pleading exemplars for each case type, complete State MV Rules tabular-particulars discipline per the *Magma Nanu Ram* line on consortium, complete *Sarla Verma* / *Pranay Sethi* / *National Insurance v. Birender* / *Jiju Kuruvila* / *Royal Sundaram* / *Magma General* / *Erudhaya Priya* line of Supreme Court precedent encoded in the Verifier, and bench-specific Practice Directions for major MACT districts) will land in v0.1.x and onward.

### Released under

MIT License. Authored by Rushikesh R. Mahajan, Advocate, publishing under the Wolfgang Rush open-source brand for legal-tech infrastructure.

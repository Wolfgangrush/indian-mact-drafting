---
name: _drafting_common
description: Shared reference for all 10 MACT / motor-vehicle-litigation drafting skills. Holds the anti-pollution rules, the MACT-specific privacy firewall protocol (claimant names + deceased / injured names + driver / owner / insurer names + vehicle registration numbers + policy numbers + FIR numbers + hospital names + medical-bill figures + income figures substituted with placeholders before downstream AI processing; real-value re-substitution local-only in the Refiner step), the AI-style-marker blacklist, citation discipline, statutory currency rules (Motor Vehicles Act 1988 as amended 2019 / Central MV Rules 1989 / State MV Rules / Employees' Compensation Act 1923 / BNS / BNSS / BSA 2023 / IPC → BNS section map for rash and negligent driving / CrPC → BNSS / IEA → BSA / old §163A → current §164 / pre-2019 §161 → post-2019 §161 Solatium Fund), the Sarla Verma multiplier table, the Pranay Sethi future-prospects + conventional-heads framework, the Section 168 award-head map, the Section 147 / 149 insurer-liability framework, the Section 167 MV Act election-clause discipline, the limitation framework (Section 166(3) repealed by 1994 Amendment; Section 173 = 90 days; EC Act = 2 years), and the territorial-jurisdiction rule under Section 166(2). NOT invoked directly — referenced from every case-type skill in this plugin.
allowed-tools: Read
---

# `_drafting_common` — shared MACT drafting infrastructure

## Privacy firewall

Motor-accident pleadings contain some of the most sensitive material an advocate handles — deceased identities, post-mortem reports, medico-legal certificates, bereaved-dependant identities, minor children's identities, income-and-tax records, FIR particulars, insurance-policy particulars. The plugin's privacy discipline:

1. **Reader** substitutes every claimant name (legal representative / injured / minor through guardian), every deceased name, every driver name, every owner name, every insurer name, every vehicle registration number, every policy number, every FIR number, every hospital name, every medical-bill figure, and every income figure with structural placeholders before downstream processing.
2. The placeholder → real-value mapping is stored in the header of `case-facts.md` on the user's local machine **only**.
3. **Format / Drafter / Verifier / Overseer** operate **only** on placeholder-substituted content. The underlying AI runtime never holds raw FIR numbers, policy numbers, or victim identities.
4. **Refiner** re-substitutes real values into the final `.docx`, strictly on the user's machine.
5. `.gitignore` excludes `case-facts.md`, `case-config.md`, and `state-config.md` so they cannot be committed accidentally.

## AI-style-marker blacklist

Stripped by the Refiner before output:

- Em-dash (`—`) used as sentence-internal pause (replaced with semicolon or comma-bounded clause)
- Sentence-final *thereby* / *hereby* / *whereby* without an attached verb
- *Moreover*, *furthermore*, *additionally*, *in addition* as sentence-openers — replaced with *"The Claimants submit that"* / *"The Claimants further submit that"*
- *Navigate*, *delve*, *foster*, *robust*, *seamless* (metaphorical uses)
- *It is important to note that*, *it should be noted that*, *worthy of note* — replaced with direct prose
- Bullet-list-style structure in operative paragraphs (operative paragraphs are numbered, not bulleted)

## Citation discipline

The Drafter does **not** generate case names + citations from training memory. Every case citation in any explanatory note or recital must trace to a user-supplied source. Untraceable citations become `[CITATION NEEDED]` placeholders.

Headline cases the Verifier scans for fabrication:

- *Sarla Verma v. Delhi Transport Corporation* (2009) 6 SCC 121 — multiplier table tied to deceased's age band
- *National Insurance Co. Ltd. v. Pranay Sethi* (2017) 16 SCC 680 — constitution-bench reform on future prospects (40% / 25% / 10%) + conventional heads (funeral ₹15,000; loss of estate ₹15,000; loss of consortium ₹40,000) with 10% triennial revision
- *Reshma Kumari v. Madan Mohan* (2013) 9 SCC 65 — reaffirmation of Sarla Verma multiplier framework
- *Magma General Insurance v. Nanu Ram* (2018) 18 SCC 130 — extension of consortium head to filial and parental consortium
- *National Insurance Co. Ltd. v. Birender* (2020) — refinement on quantification of consortium for dependants
- *Royal Sundaram Alliance Insurance Co. Ltd. v. Mandala Yadagari Goud* (2019) 5 SCC 554 — inference of income where direct evidence unavailable
- *Erudhaya Priya v. State Express Transport Corporation* (2020) — quantification for injury claims with permanent disability
- *Jiju Kuruvila v. Kunjujamma Mohan* (2013) 9 SCC 166 — income proof discipline
- *New India Assurance v. Asha Rani* (2003) 2 SCC 223 — gratuitous passenger and goods-carriage liability
- *National Insurance Co. v. Swaran Singh* (2004) 3 SCC 297 — pay-and-recover doctrine; insurer's primary liability to third party with right of recovery against owner on breach
- *Oriental Insurance v. Meena Variyal* (2007) 5 SCC 428 — insurer's liability for owner-self-driving accidents
- *Ningamma v. United India Insurance* (2009) 13 SCC 710 — gratuitous-passenger liability framework
- *Manjuri Bera v. Oriental Insurance* (2007) 10 SCC 643 — heirship and legal-representative entitlement
- *Jai Prakash v. National Insurance Co.* (2010) 2 SCC 607 — Detailed Accident Report (DAR) framework
- *United India Insurance Co. v. Patricia Jean Mahajan* (2002) 6 SCC 281 — international-comparator on compensation methodology

## Statutory currency rules

Every pleading filed today should cite the operative statute. Common substitution checks:

- **IPC Section 279 (rash driving) → BNS 2023 Section 281** in any prosecution arising from a post-BNS-commencement accident.
- **IPC Section 304A (causing death by negligence) → BNS 2023 Section 106** (verify current sub-section in light of post-enactment notifications on the contested hit-and-run sub-clause).
- **IPC Section 336 (endangering safety) → BNS 2023 Section 282**.
- **IPC Section 337 / 338 (causing hurt / grievous hurt by negligence) → BNS 2023 corresponding sections — verify**.
- **CrPC 1973 → BNSS 2023** in any procedural reference (Section 200 → 223; Section 482 → 528; Sections 467 — 473 limitation → BNSS corresponding sections).
- **IEA 1872 → BSA 2023** (Section 65B → 63 for electronic-record admissibility — e.g. dash-cam footage / CCTV; Section 126 → 132 for advocate-client privilege).
- **Old Section 163A MV Act → current Section 164 MV Act** per the Motor Vehicles (Amendment) Act 2019.
- **Pre-2019 Section 161 hit-and-run quantum (₹25,000 death / ₹12,500 grievous hurt) → post-2019 Section 161 Solatium Fund quantum** per current notification (typically ₹2,00,000 / ₹50,000 — verify before drafting).
- **Workmen's Compensation Act 1923 → Employees' Compensation Act 1923** (renamed by the Workmen's Compensation (Amendment) Act 2009).

Dual-citation is acceptable in any transitional pleading.

## Sarla Verma multiplier table (Verifier reference — not for reproduction in pleadings)

The Verifier checks the multiplier applied in the Quantum Grounds against the *Sarla Verma v. DTC* (2009) 6 SCC 121 age-band table (as reaffirmed in *Reshma Kumari* (2013) and *Pranay Sethi* (2017)). The multiplier descends as the deceased's age increases. The Drafter cites *Sarla Verma* as authority, not the table verbatim.

## Pranay Sethi future-prospects framework

Per the constitution-bench in *National Insurance Co. Ltd. v. Pranay Sethi* (2017) 16 SCC 680:

| Age band of deceased | Permanent salaried | Self-employed / fixed wages |
|---|---|---|
| Below 40 | 50% (subsequently moderated to 40% per later High Court line — verify per latest authority) | 40% |
| 40 to below 50 | 30% (or 25% per the moderated line) | 25% |
| 50 to below 60 | 15% (or 10% per the moderated line) | 10% |
| 60 and above | nil | nil |

*Pranay Sethi* itself uses 50/30/15 for permanent salaried. The 40/25/10 figures circulate in subsequent practice in some benches. The Verifier checks the figure against the current authority cited and flags inconsistency.

## Pranay Sethi conventional-heads framework

Per *Pranay Sethi*, the conventional-heads at base values are:

- Funeral expenses — ₹15,000
- Loss of estate — ₹15,000
- Loss of consortium — ₹40,000 (extended to filial / parental consortium per *Magma General v. Nanu Ram*)

These figures stand revised at 10% every three years from the date of the *Pranay Sethi* judgment (31 October 2017). The Verifier checks that the figures applied in the pleading reflect the current triennial revision.

## Section 168 award-head completeness map

For a death claim under Section 166 MV Act, the admissible heads are:

- Loss of dependency (multiplier method)
- Loss of consortium (spousal + filial + parental)
- Loss of estate
- Funeral expenses
- Loss of love and affection (where the High Court recognises it as separate from consortium)
- Medical expenses (with exhibit anchors)
- Transportation expenses

For an injury claim under Section 166 MV Act, the admissible heads are:

- Pain and suffering
- Medical expenses (past and future)
- Attendant charges (where permanent disability)
- Loss of income (past — actual; future — multiplier method on permanent disability)
- Loss of amenities
- Loss of marriage prospects
- Loss of enjoyment of life
- Disfigurement / disability allowance

## Section 147 / 149 insurer-liability framework

Section 147 prescribes the requirements of insurance policies (compulsory third-party cover). Section 149 prescribes the rights of third parties against insurers and the statutory defences available to insurers:

- Section 149(2)(a)(i) — vehicle used in breach of permit / fitness conditions
- Section 149(2)(a)(ii) — driver did not hold an effective driving licence
- Section 149(2)(a)(iii) — vehicle used for a purpose not permitted by the policy
- Section 149(2)(b) — material misrepresentation in the policy

Pay-and-recover doctrine per *National Insurance v. Swaran Singh* (2004) 3 SCC 297 — the insurer remains primarily liable to the third-party claimant even on breach, with a right of recovery against the owner.

## Section 167 MV Act election-clause

Where the workman / employee killed or injured in a motor-accident is entitled to claim either under the EC Act 1923 forum or the MACT forum under the MV Act 1988, the claimant must irrevocably elect ONE forum under Section 167 of the MV Act. The election is irrevocable. The Drafter pleads the election expressly in the opening of the chosen pleading.

## Limitation framework adapted for MACT matters

| Case-type | Limitation rule |
|---|---|
| Section 166 / 164 / 161 / 147 MACT petitions for post-1994 accidents | NO limitation bar — Section 166(3) three-year limitation REPEALED by the Motor Vehicles (Amendment) Act 1994 with effect from 14 November 1994 |
| Section 166 petitions for pre-14-November-1994 accidents | Three-year limitation per the then-operative Section 166(3); condonation of delay application required if outside the three-year window |
| Section 173 HC appeal | 90 days from date of award per Section 173(1) proviso; extendable on sufficient cause shown |
| Section 174 Collector recovery | within the period prescribed in the award + Section 174 statutory window |
| EC Act 1923 claim | within two years of the accident OR within two years of the disease's first manifestation (Section 10 EC Act) |
| BNSS Magistrate prosecution | per the BNSS sections corresponding to CrPC Sections 467 — 473 |

## Territorial-jurisdiction rule under Section 166(2)

The Claim Petition may be filed in the Tribunal having jurisdiction over:

(a) the place where the accident occurred, OR
(b) the place where the claimant resides or carries on business, OR
(c) the place where the defendant resides.

The Drafter pleads the territorial-jurisdiction anchor in the opening paragraphs.

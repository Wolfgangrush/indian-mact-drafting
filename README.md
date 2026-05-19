# indian-mact-drafting

> **Open-source Claude-compatible plugin for drafting Indian motor-accident-claim and motor-vehicle-litigation pleadings.**
>
> Six-agent drafting pipeline · ten case-type skills · case-config-aware · state-config-aware · Motor Vehicles Act 1988 (as amended 2019) + Central Motor Vehicles Rules 1989 + State Motor Vehicles Rules + Employees' Compensation Act 1923 + Bharatiya Nyaya Sanhita 2023 + Bharatiya Nagarik Suraksha Sanhita 2023 + Bharatiya Sakshya Adhiniyam 2023 + Sarla Verma multiplier doctrine + Pranay Sethi constitution-bench future-prospects reform encoded.
>
> Released under MIT. Open infrastructure for the legal community. No commercial engagement offered through this repository — see Disclaimer below.

---

## Table of contents

1. [What this plugin does](#what-this-plugin-does)
2. [Case-type skills (full inventory with statutory authority)](#case-type-skills-full-inventory-with-statutory-authority)
3. [The 6-agent drafting pipeline](#the-6-agent-drafting-pipeline)
4. [Installation](#installation)
5. [Your first pleading — step-by-step walkthrough](#your-first-pleading--step-by-step-walkthrough)
6. [The `case-config.md` file](#the-case-configmd-file)
7. [The `state-config.md` file](#the-state-configmd-file)
8. [Built-in compliance disciplines](#built-in-compliance-disciplines)
9. [Privacy firewall — extra discipline for accident-victim content](#privacy-firewall--extra-discipline-for-accident-victim-content)
10. [Why MIT License](#why-mit-license)
11. [Sibling plugins](#sibling-plugins)
12. [Why this exists](#why-this-exists)
13. [Roadmap](#roadmap)
14. [Contributing](#contributing)
15. [Contact](#contact)
16. [Author and brand](#author-and-brand)
17. [Provenance and privilege statement](#provenance-and-privilege-statement)
18. [Disclaimer and Bar Council of India Rule 36 compliance](#disclaimer-and-bar-council-of-india-rule-36-compliance)
19. [License](#license)

---

## What this plugin does

This plugin lets an Indian advocate, sitting inside the Claude Desktop application, point at a case folder on disk and obtain a complete motor-accident-claim or motor-vehicle-litigation pleading in `.docx` form — Cause Title, Parties, Statutory Opening, Preamble, Tabular Particulars per the State Motor Vehicles Rules / CMVR Form 54, Description of the Accident, Negligence Grounds, Quantum Grounds (with Sarla Verma multiplier and Pranay Sethi future-prospects applied), Prayer, Verification, Affidavit-in-support, Index, List of Documents, and the accompanying applications (interim compensation under the Tribunal's procedural power, ad-interim attachment of the offending vehicle pending insurer's admission of liability, condonation of delay where the Section 166(3) three-year repealed limitation surfaces in a pre-1994 fact-matrix, urgent listing, substituted service on the absconding driver) — formatted in the forum's idiom and the case-type-specific structure, sourced from a `case-config.md` file and a `state-config.md` file the user places in the case folder.

The pipeline is six agents running in sequence:

1. **Reader** — extracts accident-case facts (claimant composition, deceased / injured person particulars, driver and owner particulars, vehicle particulars, FIR particulars, charge-sheet / final report, post-mortem report, medico-legal certificate, hospital records, salary / income particulars, insurance policy particulars, accident-site rough sketch, witness statements) from the case folder with a per-document audit log, and applies the **MACT-specific privacy firewall** (every party name, every vehicle registration number, every policy number, every FIR number, every hospital name, every medical-bill figure, every income figure, every deceased's / injured's / driver's / owner's name substituted with structural placeholders before downstream AI processing; the placeholder → real-value mapping is stored locally on the user's machine only).
2. **Format** — loads the case-type skill template, reads the user's `case-config.md` and `state-config.md`, and pre-substitutes forum name / Member designation / case-number prefix / court-fee / statutory opening / limitation anchor / state-specific tabular-particulars schedule into a `format-shell.md` ready for the Drafter.
3. **Drafter** — writes the actual pleading. Cause Title in the correct MACT / High Court / Magistrate Court / Commissioner / Collector nomenclature, Parties block, Statutory Opening invoking Section 166 / Section 164 / Section 161 / Section 147 / Section 173 / Section 174 / Section 22 EC Act / BNSS sections, Preamble, Tabular Particulars (state-specific schedule), Description of the Accident, Negligence Grounds, Quantum Grounds (Sarla Verma + Pranay Sethi method with stepwise computation), Prayer, Verification, Affidavit-in-support, Index, List of Documents, and accompanying applications.
4. **Verifier** — anti-hallucination firewall **plus** statutory-currency check (IPC 279 / 304A → BNS 2023 corresponding sections; CrPC → BNSS 2023; IEA → BSA 2023; old Section 163A → current Section 164; pre-2019 Section 161 hit-and-run scheme → post-2019 Section 161 Solatium Fund) **plus** Sarla Verma multiplier-table verification **plus** Pranay Sethi future-prospects percentage verification **plus** Section 168 award-head completeness (loss of dependency + loss of consortium + loss of love and affection + loss of estate + funeral expenses + transportation + medical-treatment expenses) **plus** Section 147 / 149 insurer-liability ingredient discipline **plus** limitation computation (the three-year limitation under Section 166(3) was repealed by the Motor Vehicles (Amendment) Act 1994 — the Verifier flags any pleading that wrongly cites the repealed bar) **plus** territorial-jurisdiction check under Section 166(2).
5. **Refiner** — applies Verifier flags, polishes language to formal Indian tribunal / court register, enforces internal numbering and exhibit-cross-reference consistency, strips AI-style markers, and re-substitutes real party names, real vehicle registration numbers, real policy numbers, real FIR numbers, and real medical-bill figures into the final `.docx` (strictly on the user's local machine — the underlying AI never holds real values).
6. **Overseer** — reads the polished draft with an opposing-counsel lens (insurer's counsel for a claimant's petition; claimant's counsel for an insurer's defence; defence counsel for a Bank / owner-side BNSS prosecution; appellant or respondent counsel for a Section 173 appeal). Flags attackable negligence-pleading defects, weak multiplier application, mis-applied Pranay Sethi future-prospects, broken consortium pleading, missing income-evidence anchor, broken limitation pleading on the pre-1994 / post-1994 cusp, missing policy-existence pleading, missing Insurance Act 1938 / IRDAI compliance pleading, missing driver-licence pleading, weak FIR / charge-sheet anchor.

The output is what an advocate would put before the Tribunal or the Court for filing — **not a template. Not a checklist. A pleading** — ready for the advocate's review, professional verification, signature, court fee, and filing.

---

## Case-type skills (full inventory with statutory authority)

The plugin ships with ten case-type skills, each covering a distinct motor-vehicle litigation case-type:

### 1. `mact-petition-section-166-fault-based-draft`

**Statutory authority:** Motor Vehicles Act 1988 — Section 166 (fault-based claim before the Motor Accident Claims Tribunal); Section 165 (constitution of the Tribunal); Section 168 (award structure); Section 169 (procedure and powers); *Sarla Verma v. Delhi Transport Corporation* (2009) 6 SCC 121 (multiplier table); *National Insurance Co. Ltd. v. Pranay Sethi* (2017) 16 SCC 680 (constitution-bench: future-prospects 40% / 25% / 10% based on age + employment status; conventional heads — funeral ₹15,000, loss of estate ₹15,000, loss of consortium ₹40,000, with 10% revision every three years); *Magma General Insurance Co. Ltd. v. Nanu Ram* (2018) 18 SCC 130 (filial consortium for parents and children); *Reshma Kumari v. Madan Mohan* (2013) 9 SCC 65; *Manjuri Bera v. Oriental Insurance* (2007) 10 SCC 643. **Use case:** death / personal injury / property damage caused by use of a motor vehicle, where the claimant pleads negligence on the part of the driver of the offending vehicle. **Output:** complete Section 166 Claim Petition with Cause Title in MACT nomenclature, Section 166 statutory opening, full Preamble, state-specific Tabular Particulars, narrative Description of the Accident anchored to FIR / charge-sheet / post-mortem / medico-legal exhibits, Negligence Grounds, Quantum Grounds with stepwise multiplier computation, Prayer with no-cap compensation + interest + costs.

### 2. `mact-petition-section-164-lump-sum-draft`

**Statutory authority:** Motor Vehicles Act 1988 — Section 164 (post the Motor Vehicles (Amendment) Act 2019 — structured-formula lump-sum scheme replacing the old Section 163A no-fault scheme); the Second Schedule to the Motor Vehicles Act 1988 (operative for the calculation framework — the lump-sum figures notified by the Central Government are read in along with the Schedule); the saving of the claimant's option to elect under Section 165(4) — election between Section 164 (structured lump-sum) and Section 166 (fault-based open-ended). **Use case:** claimant electing structured lump-sum compensation (Section 164: ₹5,00,000 for death / ₹2,50,000 for grievous hurt, per current notification — verify current figure) without proving negligence, against the owner / insurer of the offending vehicle. **Output:** complete Section 164 Claim Petition pleading the structured-formula election expressly, foreclosing the higher Section 166 quantum but securing the no-fault relief.

### 3. `mact-petition-section-161-solatium-hit-and-run-draft`

**Statutory authority:** Motor Vehicles Act 1988 — Section 161 read with the Solatium Scheme notified by the Central Government (post-2019 amendment; the pre-amendment Section 161 hit-and-run quantum was ₹25,000 for death and ₹12,500 for grievous hurt, raised by the 2019 amendment and subsequent notification to ₹2,00,000 for death and ₹50,000 for grievous hurt — verify against latest notification); the Insurance Companies Tariff Advisory Committee Scheme for administration. **Use case:** the offending vehicle is unidentified / untraced / uninsured / driver fled — claim against the Solatium Fund. **Output:** complete Section 161 Claim Petition addressed to the Tribunal with the Solatium-Scheme-designated Claims Enquiry Officer / authority, pleading the hit-and-run particulars + FIR registration + police inquiry result.

### 4. `mact-petition-third-party-insurance-section-147-draft`

**Statutory authority:** Motor Vehicles Act 1988 — Section 146 (compulsory insurance), Section 147 (requirements of policies and limits of liability), Section 149 (rights of third parties against insurers; defences available to insurer); *New India Assurance v. Asha Rani* (2003) 2 SCC 223; *National Insurance Co. v. Swaran Singh* (2004) 3 SCC 297 (insurer cannot escape liability merely on a technical breach; pay-and-recover doctrine); *Oriental Insurance v. Meena Variyal* (2007) 5 SCC 428; *Ningamma v. United India Insurance* (2009) 13 SCC 710 (gratuitous passenger liability). **Use case:** Section 166 claim petition where the third-party-insurance liability of the insurer is the operative head; the petition is structured to defeat the standard Section 149 defences (no policy / lapsed policy / unauthorised use / unlicensed driver / breach of policy condition). **Output:** complete claim petition with focused pleading of the insurer's statutory liability — policy existence + use of vehicle within policy terms + driver-licence compliance + named-driver / paid-driver pleading where applicable.

### 5. `mact-interim-compensation-application-draft`

**Statutory authority:** Motor Vehicles Act 1988 (the erstwhile Section 140 no-fault interim compensation is now subsumed by Section 164 structured lump-sum after the 2019 amendment; the Tribunal's procedural power to grant interim relief pending final award is exercised under the Tribunal's own Procedure Rules); applicable State Motor Vehicles Rules. **Use case:** claimant seeking interim disbursement pending final award (to meet ongoing medical expenses, funeral expenses, immediate dependency). **Output:** complete interim application annexed to or filed alongside the main Section 166 petition, with grounds for urgency, prima-facie liability, and quantum of interim relief sought.

### 6. `mact-appeal-section-173-to-high-court-draft`

**Statutory authority:** Motor Vehicles Act 1988 — Section 173 (appeal to the High Court from any award of the Claims Tribunal); 90-day limitation; Section 173(2) deposit requirement (Rs. 25,000 or 50% of award, whichever is less — verify against current notification) where the appellant is the insurer or the owner. **Use case:** any party aggrieved by an MACT award — claimant seeking enhancement, insurer / owner seeking reduction / reversal, or claimant or driver appealing on contributory-negligence apportionment. **Output:** complete Memorandum of Appeal with Grounds (erroneous appreciation of negligence / misapplication of Sarla Verma multiplier / mis-applied Pranay Sethi future-prospects / wrongful deduction for personal-and-living expenses / wrongful disallowance of consortium / wrongful disallowance of interest / contributory-negligence apportionment / limitation), Prayer, accompanying applications (stay of award / deposit-condition / urgent listing / condonation of delay).

### 7. `mact-claim-execution-application-draft`

**Statutory authority:** Motor Vehicles Act 1988 — the award of the Tribunal is enforceable as a decree of a civil court (Section 174 read with Order 21 of the Code of Civil Procedure 1908); the Insurance Act 1938 and IRDAI regulations operationalise insurer-side payment. **Use case:** claimant seeking execution of an unsatisfied MACT award against the insurer / owner / driver — typically a civil-court route under Order 21 CPC, with reference to the Tribunal's award as the decree. **Output:** complete Execution Application listing the award particulars, the decree-holder and judgment-debtor, the modes of execution sought (attachment of vehicle / attachment of bank account / arrest where applicable).

### 8. `workmen-compensation-claim-draft`

**Statutory authority:** Employees' Compensation Act 1923 (formerly the Workmen's Compensation Act; renamed by the Workmen's Compensation (Amendment) Act 2009); Schedule I (list of compensable injuries); Schedule III (list of occupational diseases); Schedule IV (multiplier-equivalent factors); Section 4 (amount of compensation); Section 22 (procedure before the Commissioner); Section 167 of the Motor Vehicles Act 1988 (election-clause — claimant must choose between EC Act forum and MACT forum; election is irrevocable). **Use case:** workman / employee killed or injured in the course of employment in a motor-vehicle accident; claim before the Commissioner under the EC Act 1923 (typically chosen by the family of a driver / cleaner / loader who was on duty in the offending or victim vehicle). **Output:** complete claim before the Commissioner with the Section 167 MV Act election expressly pleaded and irrevocable.

### 9. `motor-vehicle-criminal-defence-bnss-draft`

**Statutory authority:** Bharatiya Nyaya Sanhita 2023 — Section 281 (rash driving or riding on public way; successor to IPC Section 279), Section 282 (endangering personal safety of others by act or negligence; successor to IPC Section 336), Section 283 (obstruction of public way; successor to IPC Section 283), Section 106 (causing death by negligence; successor to IPC Section 304A; with the contested second sub-section on hit-and-run cases — verify current operative form in light of post-enactment notifications); Bharatiya Nagarik Suraksha Sanhita 2023 (procedural framework — bail, charge-framing, trial); Motor Vehicles Act 1988 — Sections 184 (driving dangerously), 185 (drunken driving), 186 (driving when mentally or physically unfit), 187 (offences relating to accident), 188, 189, 190 (other vehicle-condition offences). **Use case:** defence of an accused driver in a rash / negligent driving prosecution arising from a motor-vehicle accident — typically run alongside a MACT compensation proceeding. **Output:** complete defence pleading — bail application, discharge / quashing application, written statement to charge under BNSS 2023, evidence-led defence, sentence-mitigation submissions.

### 10. `compensation-recovery-collector-section-174-draft`

**Statutory authority:** Motor Vehicles Act 1988 — Section 174 (recovery of money from insurer as arrears of land revenue where the award is not satisfied within the period prescribed). **Use case:** claimant with an unsatisfied MACT award seeking Collector-route recovery as arrears of land revenue (an administrative-recovery channel distinct from civil-court execution under Order 21 CPC). **Output:** complete application before the Collector of the District where the judgment-debtor (typically insurer / owner) resides or carries on business, with the certified copy of the award, proof of non-satisfaction, and the request for issue of a recovery certificate.

### Shared infrastructure skills

- **`_drafting_common`** — anti-pollution rules, MACT-specific privacy firewall (acutely sensitive — accident-victim and bereaved-dependant data), AI-style-marker blacklist, citation discipline, **statutory currency rules** (CrPC → BNSS / IEA → BSA / IPC 279, 304A, 336 → BNS 2023 corresponding sections / old Section 163A → current Section 164 / pre-2019 Section 161 → post-2019 Section 161 Solatium Fund), **Sarla Verma multiplier table reference**, **Pranay Sethi future-prospects table**, **Section 168 award-head map**, **Section 147 / 149 insurer-liability map**, **Limitation Act 1963 Article map adapted for motor-accident matters**, **Section 167 MV Act election-clause (EC Act vs MACT)**.
- **`_mact_drafting_base`** — universal Indian MACT pleading skeleton (Cause Title · Parties block · Statutory Opening · Preamble · Tabular Particulars per state MV Rules / CMVR Form 54 · Description of the Accident · Negligence Grounds · Quantum Grounds with stepwise multiplier method · Prayer · Verification · Affidavit-in-support · Index · List of Documents · accompanying applications).

---

## The 6-agent drafting pipeline

| Agent | What it reads | What it writes | Key MACT-domain specialisation |
|---|---|---|---|
| **`reader`** | Every file in the case folder + the case-type skill's expected exhibits list | `case-facts.md` with per-document audit log + privacy-firewalled placeholder mapping in the header | Privacy firewall — substitutes claimant names + deceased / injured names + driver names + owner names + insurer names + policy numbers + vehicle registration numbers + FIR numbers + hospital names + medical-bill figures + income figures before downstream AI processing; mapping stored locally only |
| **`format`** | `case-facts.md` + `case-config.md` + `state-config.md` + case-type SKILL.md + `_mact_drafting_base` | `format-shell.md` with forum / case-number-prefix / court-fee / statutory-opening / state-specific tabular-particulars schedule pre-substituted | Resolves MACT vs High Court vs Magistrate vs Commissioner vs Collector nomenclature for the Cause Title; pulls state-specific Tabular Particulars schedule from `state-config.md` |
| **`drafter`** | `case-facts.md` + `format-shell.md` + case-type SKILL.md + `_mact_drafting_base` + law PDFs | `draft-v1.md` + `draft-v1.docx` | Writes Cause Title + Parties + Statutory Opening + Preamble + Tabular Particulars + Description of the Accident + Negligence Grounds + Quantum Grounds (Sarla Verma + Pranay Sethi method with stepwise computation) + Prayer + Verification + Affidavit + Index + List of Documents + accompanying applications |
| **`verifier`** | `draft-v1.md` + `case-facts.md` + `case-config.md` + `state-config.md` + law PDFs | `verification-report.md` | Anti-hallucination + statutory-currency (IPC 279, 304A → BNS 2023 / CrPC → BNSS / IEA → BSA / old §163A → §164 / pre-2019 §161 → post-2019 §161) + Sarla Verma multiplier-table verification + Pranay Sethi future-prospects percentage verification + Section 168 award-head completeness + Section 147 / 149 insurer-liability ingredient check + limitation computation (Section 166(3) repealed by 1994 Amendment) + territorial-jurisdiction check |
| **`refiner`** | `draft-v1.md` + `verification-report.md` + `case-config.md` + `case-facts.md` | `draft-v2.md` + `draft-v2.docx` | Polish to Indian tribunal / court formal register + internal numbering / cross-reference / exhibit-marker consistency + privacy-firewall reversal (real values re-substituted from local mapping into final `.docx`) |
| **`overseer`** | `draft-v2.docx` + `case-facts.md` + `case-config.md` | `opposing-notes.md` + `final-draft.docx` | Opposing-counsel critique — negligence-pleading defects, multiplier-application defects, Pranay Sethi mis-application, consortium-pleading defects, income-evidence gaps, limitation pleading on the pre-1994 / post-1994 cusp, policy-existence pleading gaps, driver-licence pleading gaps, FIR / charge-sheet anchor gaps, Section 149 statutory-defence preview |

---

## Installation

This is a Claude-compatible plugin in the Anthropic plugin format, designed to run inside the **Claude Desktop application** (available at <https://claude.ai/download>). The plugin folder location depends on your OS:

| OS | Plugin folder path |
|---|---|
| **macOS** | `~/Library/Application Support/Claude/plugins/` |
| **Windows** | `%APPDATA%\Claude\plugins\` |
| **Linux** | `~/.config/Claude/plugins/` |

Clone the plugin into that folder:

```bash
# macOS / Linux
mkdir -p ~/Library/Application\ Support/Claude/plugins
cd ~/Library/Application\ Support/Claude/plugins
git clone https://github.com/Wolfgangrush/indian-mact-drafting.git indian-mact-drafting

# Windows (PowerShell)
mkdir -Force $env:APPDATA\Claude\plugins
cd $env:APPDATA\Claude\plugins
git clone https://github.com/Wolfgangrush/indian-mact-drafting.git indian-mact-drafting
```

Restart the Claude Desktop application. The plugin is auto-discovered on the next session start.

### Verifying the install

In a Claude session, type:

- *"draft MACT 166 petition"* — triggers `mact-petition-section-166-fault-based-draft`
- *"draft MACT 164 lump sum petition"* — triggers `mact-petition-section-164-lump-sum-draft`
- *"draft hit-and-run solatium claim"* — triggers `mact-petition-section-161-solatium-hit-and-run-draft`
- *"draft third-party insurance MACT petition"* — triggers `mact-petition-third-party-insurance-section-147-draft`
- *"draft interim compensation application"* — triggers `mact-interim-compensation-application-draft`
- *"draft Section 173 MV Act appeal"* — triggers `mact-appeal-section-173-to-high-court-draft`
- *"draft MACT execution application"* — triggers `mact-claim-execution-application-draft`
- *"draft EC Act workmen compensation claim"* — triggers `workmen-compensation-claim-draft`
- *"draft BNSS rash driving defence"* — triggers `motor-vehicle-criminal-defence-bnss-draft`
- *"draft Section 174 Collector recovery"* — triggers `compensation-recovery-collector-section-174-draft`

---

## Your first pleading — step-by-step walkthrough

Suppose you wish to draft a **Section 166 Claim Petition** before the MACT at the territorial district where the accident occurred, for the legal representatives of a deceased aged 35 earning a monthly income of ₹40,000, leaving behind a spouse and two minor children.

### Step 1 — create a case folder

```
~/Desktop/cases/
└── mact-166-2026-RTA-MATTER/
    ├── case-config.md
    ├── state-config.md
    ├── inputs/
    │   ├── fir-copy.pdf
    │   ├── final-report-charge-sheet.pdf
    │   ├── post-mortem-report.pdf
    │   ├── medico-legal-certificate.pdf
    │   ├── salary-certificate.pdf
    │   ├── income-tax-return.pdf
    │   ├── driving-licence-deceased.pdf
    │   ├── death-certificate.pdf
    │   ├── relationship-certificate.pdf
    │   ├── insurance-policy-offending-vehicle.pdf
    │   ├── registration-certificate-offending-vehicle.pdf
    │   ├── rough-sketch-accident-site.pdf
    │   └── witness-statements.pdf
    └── laws/
        ├── motor-vehicles-act-1988.pdf
        ├── central-motor-vehicles-rules-1989.pdf
        ├── state-motor-vehicles-rules.pdf
        ├── employees-compensation-act-1923.pdf
        ├── sarla-verma-2009.pdf
        ├── pranay-sethi-2017.pdf
        └── magma-nanu-ram-2018.pdf
```

### Step 2 — write `case-config.md`

```yaml
forum: "Motor Accident Claims Tribunal, [District]"
case_type: "mact-petition-section-166-fault-based"
case_number_year: 2026
date_of_accident: "[Date-of-Accident-Placeholder]"
place_of_accident: "[Place-of-Accident-Placeholder]"
fir_number: "[FIR-No.-Placeholder]"
fir_police_station: "[Police-Station-Placeholder]"
deceased_or_injured: "deceased"
deceased_age_at_death: 35
deceased_monthly_income_rupees: 40000
deceased_employment_status: "salaried_permanent"
number_of_dependants: 3
deceased_marital_status: "married"
applicable_state_court_fees_act: "Bombay Court-Fees Act 1959"
limitation_note: "Section 166(3) three-year limitation REPEALED by Motor Vehicles (Amendment) Act 1994 — no limitation bar"
claimants:
  - role: "Claimant No. 1 (Widow)"
    party_type: "Legal representative — spouse of deceased"
    party_name: "[Claimant-1-Placeholder]"
  - role: "Claimant No. 2 (Minor child through natural guardian)"
    party_type: "Legal representative — child of deceased"
    party_name: "[Claimant-2-Placeholder]"
  - role: "Claimant No. 3 (Minor child through natural guardian)"
    party_type: "Legal representative — child of deceased"
    party_name: "[Claimant-3-Placeholder]"
respondents:
  - role: "Respondent No. 1 (Driver of offending vehicle)"
    party_name: "[Driver-Placeholder]"
  - role: "Respondent No. 2 (Owner of offending vehicle)"
    party_name: "[Owner-Placeholder]"
  - role: "Respondent No. 3 (Insurer of offending vehicle)"
    party_name: "[Insurer-Placeholder]"
offending_vehicle_registration: "[Vehicle-Reg-Placeholder]"
offending_vehicle_policy_number: "[Policy-No.-Placeholder]"
offending_vehicle_policy_period: "[Policy-Period-Placeholder]"
```

### Step 3 — write `state-config.md`

Copy from `state-config/exemplars/maharashtra.md` (or your State exemplar) into your case folder, then customise.

### Step 4 — invoke the plugin

> *draft MACT 166 petition*

The pipeline runs: Reader → Format → Drafter → Verifier → Refiner → Overseer.

The advocate now reviews `final-draft.docx` against `opposing-notes.md`, makes professional adjustments, applies court fee, signs the verification, swears the affidavit, and files.

---

## The `case-config.md` file

This file declares all forum-level / case-type-level / matter-level constants that the plugin substitutes into the format shell. Keep it on the user's local machine — `.gitignore` excludes it from any git repo.

Minimum fields:

- `forum` — exact name of the Tribunal / Court (e.g. *"Motor Accident Claims Tribunal, Nagpur"* / *"High Court of Judicature at Bombay, Nagpur Bench"* / *"Court of the Judicial Magistrate First Class, Nagpur"* / *"Commissioner under the Employees' Compensation Act 1923, Nagpur"* / *"Collector of the District, Nagpur"*)
- `case_type` — one of the ten supported case types
- `case_number_year` — current year for case-number placeholder
- `date_of_accident` / `place_of_accident` / `fir_number` / `fir_police_station`
- `deceased_or_injured` / `deceased_age_at_death` / `deceased_monthly_income_rupees` / `deceased_employment_status` / `number_of_dependants` / `deceased_marital_status`
- `claimants` / `respondents` — list of party-role + party-type + party-name-placeholder
- `offending_vehicle_registration` / `offending_vehicle_policy_number` / `offending_vehicle_policy_period`

Case-type-specific fields (for the relevant skill) layer on top of the minimum schema — see each case-type SKILL.md.

---

## The `state-config.md` file

Tabular Particulars in MACT pleadings vary significantly by State — each State's Motor Vehicles Rules carry their own schedule for the particulars to be filed with a Section 166 / Section 164 / Section 161 petition. The plugin's `state-config` layer addresses this: the user copies the right State exemplar from `state-config/exemplars/` into the case folder as `state-config.md`, and the Format agent reads the State's tabular-particulars schedule + State Court-Fees Act + State Stamp Act + State-specific MACT Procedure Rules from that file.

State exemplars in the plugin (v0.1.0-alpha):

- **Deep · battle-tested:** `maharashtra.md` (Bombay HC Nagpur Bench is the author's practice)
- **Researched · not validated:** `karnataka.md`, `tamil-nadu.md`, `kerala.md`, `delhi.md`, `uttar-pradesh.md`, `west-bengal.md`, `gujarat.md`
- **Stub markers — community contribution welcomed:** the remaining 20 States and Union Territories. Open a GitHub Issue with your bench's tabular-particulars schedule + state-specific MV Rules variations, and the exemplar will be added.

---

## Built-in compliance disciplines

The Verifier enforces several disciplines mandatory in Indian motor-accident practice — see `skills/_drafting_common/SKILL.md` for the full discipline framework. Headline disciplines:

- **Sarla Verma multiplier discipline** — the multiplier is mapped to the deceased's age at the time of death per the table in *Sarla Verma v. DTC* (2009) 6 SCC 121 (reaffirmed in *Reshma Kumari* (2013) and *Pranay Sethi* (2017))
- **Pranay Sethi future-prospects discipline** — 40% for permanent salaried below 40, 25% from 40 to 50, 10% from 50 to 60; for self-employed below 40 — 40%, from 40 to 50 — 25%, from 50 to 60 — 10%
- **Pranay Sethi conventional-heads discipline** — funeral expenses ₹15,000, loss of estate ₹15,000, loss of consortium ₹40,000 — to be revised at 10% every three years; the Verifier flags any pleading that under-claims these heads
- **Section 168 award-head completeness** — every claim petition must plead all admissible heads to claim them; the Verifier flags missing heads
- **Section 147 / 149 insurer-liability discipline** — policy existence + period of validity + use of vehicle within policy terms + driver-licence compliance + named-driver pleading where applicable
- **Limitation discipline** — Section 166(3) three-year limitation was **repealed by the Motor Vehicles (Amendment) Act 1994** for cases arising post-1994 — the Verifier flags any pleading that cites the repealed bar; for Section 173 appeals, the 90-day limitation under Section 173(1) proviso applies
- **Section 167 MV Act election-clause** — claimant electing the EC Act forum must expressly plead the irrevocable election; the Verifier flags any pleading that fails to declare the election
- **Statutory-currency discipline** — IPC Section 279 (rash driving) → BNS 2023 Section 281; IPC Section 304A (causing death by negligence) → BNS 2023 Section 106; IPC Section 336 (endangering safety) → BNS 2023 Section 282; CrPC → BNSS 2023; IEA → BSA 2023; old Section 163A → current Section 164; pre-2019 Section 161 quantum → post-2019 Section 161 Solatium Fund

---

## Privacy firewall — extra discipline for accident-victim content

Motor-accident pleadings contain some of the most sensitive material an advocate handles — deceased identities, post-mortem reports, medico-legal certificates, bereaved-dependant identities, minor children's identities, injury photographs, income-and-tax records, family-relationship certificates, FIR particulars, insurance-policy particulars. The plugin's privacy discipline is calibrated for this acute sensitivity:

1. **Reader** substitutes every claimant name (legal representative / injured / minor through guardian), every deceased name, every driver name, every owner name, every insurer name, every vehicle registration number, every policy number, every FIR number, every hospital name, every medical-bill figure, and every income figure with structural placeholders before downstream processing.
2. The placeholder → real-value mapping is stored in the header of `case-facts.md` on the user's local machine **only**.
3. **Format / Drafter / Verifier / Overseer** operate **only** on placeholder-substituted content. The underlying AI runtime never holds raw FIR numbers, policy numbers, or victim identities.
4. **Refiner** re-substitutes real values into the final `.docx`, strictly on the user's machine.
5. `.gitignore` excludes `case-facts.md`, `case-config.md`, and `state-config.md` so they cannot be committed accidentally.

The user can verify the firewall by inspecting `case-facts.md` after the Reader runs — every claimant name appears as `[Claimant-1]` / `[Claimant-2]`, every deceased's name as `[Deceased]`, every FIR number as `[FIR-No.-Placeholder]`. The mapping is in the header of the same file.

---

## Why MIT License

The MIT licence is the most permissive widely-recognised open-source licence. Anyone may use, modify, distribute, sublicense, or sell the plugin or any derivative. The licence is short, well-understood, and compatible with every other open-source licence the legal community is likely to encounter. No proprietary gating, no field-of-use restriction, no contributor licence agreement (CLA) gymnastics. The accompanying `NOTICE.md` does not modify the licence — it documents the provenance and the privilege position so that any future audit can verify the plugin's clean origin.

---

## Sibling plugins

This plugin is one in the **Wolfgang Rush** family of Indian legal-drafting plugins. All thirteen siblings ship under the same six-agent pipeline (Reader → Format → Drafter → Verifier → Refiner → Overseer) and the family-of-plugins doctrine — each plugin narrowly scoped to one practice area / forum:

| Plugin | GitHub repo | Scope |
|---|---|---|
| `supreme-court-drafting` | [supreme-court-drafting-litigation](https://github.com/Wolfgangrush/supreme-court-drafting-litigation) | SLPs · Writ Art 32 · Transfer · Review · Curative — Supreme Court of India |
| `indian-hc-drafting` | [indian-hc-drafting-litigation](https://github.com/Wolfgangrush/indian-hc-drafting-litigation) | Pleadings across all 25 Indian High Courts (bench-config-aware) |
| `district-court-drafting` | [district-court-drafting-litigation](https://github.com/Wolfgangrush/district-court-drafting-litigation) | Plaints · WS · CPC applications · BNSS complaints across 25+ States (state-config) |
| `indian-family-drafting` | [indian-family-drafting-litigation](https://github.com/Wolfgangrush/indian-family-drafting-litigation) | HMA · SMA · IDA · matrimonial · custody · DV Act · maintenance · adoption |
| `indian-contracts-drafting` | [indian-contracts-drafting-litigation](https://github.com/Wolfgangrush/indian-contracts-drafting-litigation) | MSA · NDA · employment · lease · sale · GPA · SHA · will · loan · arbitration |
| `indian-banking-drafting` | [indian-banking-drafting-litigation](https://github.com/Wolfgangrush/indian-banking-drafting-litigation) | DRT · SARFAESI · NI Act 138 · IBC §7 / §95 · DRAT |
| `indian-labour-drafting` | [indian-labour-drafting-litigation](https://github.com/Wolfgangrush/indian-labour-drafting-litigation) | ID Act · POSH · PG · EPF · ESI · MW · IESO + State exemplars |
| `indian-property-drafting` | [indian-property-drafting-litigation](https://github.com/Wolfgangrush/indian-property-drafting-litigation) | Gift · Exchange · Release · Trust · Wakf · Easement · Partition · Settlement · Mortgage · TIR |
| `indian-company-drafting` | [indian-company-drafting](https://github.com/Wolfgangrush/indian-company-drafting) | NCLT (241/242 · 245 · 230-232 · 66 · 252 · 213) · NCLAT (421 + 61) · IBC §9 / §10 |
| `indian-tax-drafting` | [indian-tax-drafting](https://github.com/Wolfgangrush/indian-tax-drafting) | Form 35 CIT(A) · Form 36 ITAT · Form 10A · Sec 148A · 263/264 · 271/270A · 144C · 201 · 260A |
| `indian-consumer-drafting` | [indian-consumer-drafting](https://github.com/Wolfgangrush/indian-consumer-drafting) | District / State / NCDRC + medical-negligence + product liability |
| `indian-mact-drafting` (this) | [indian-mact-drafting](https://github.com/Wolfgangrush/indian-mact-drafting) | MV Act 1988 (2019 amended) · Sarla Verma + Pranay Sethi · state-config |
| `indian-ip-drafting` | [indian-ip-drafting](https://github.com/Wolfgangrush/indian-ip-drafting) | Copyright · Trade Marks · Patents · Designs + HC IP Divisions (post-IPAB-abolition) + Anton Piller / John Doe |

Each plugin can be installed independently, each plugin's Rule 36 firewall is narrow and reviewable, each plugin's bench / forum discipline is depth-validated within its scope, and the user installs only what they need.

---

## Why this exists

Indian motor-accident practice has no open-source pleading-drafting infrastructure. Practising advocates piece together pleadings from their own past drafts, from senior advocates' templates, from such precedent collections as the publishers issue from time to time, and from the various Civil-Manual and Criminal-Manual annexures. The result is uneven quality, uneven compliance with the latest statutory-currency rules (BNS / BNSS / BSA 2023; the 2019 amendment to the Motor Vehicles Act 1988 that repositioned the no-fault scheme from old Section 163A to current Section 164 and revised the hit-and-run Solatium Fund quantum under Section 161), uneven discipline on the Sarla Verma multiplier application, mis-applied Pranay Sethi future-prospects, broken Section 168 award-head completeness, broken Section 147 / 149 insurer-liability pleading, and routine omissions that opposing counsel exploit.

A plugin that codifies the procedural skeletons + the statutory-currency rules + the multiplier discipline + the Verifier-side discipline + the privacy firewall is the first piece of infrastructure that the Indian motor-accident practice has had — the second piece is community contribution from advocates who file regularly in specific MACT districts and who deepen the state-specific tabular-particulars discipline.

Foreign legal-AI tools cannot fill this gap. The procedural conventions are jurisdiction-specific; the statutory framework is Motor Vehicles Act 1988 + State MV Rules + BNS / BNSS / BSA 2023 + EC Act 1923 which no foreign training data has indexed at depth; the formatting requirements at the Registry counter of an MACT are matters of bench practice that no foreign tool has encountered.

This plugin opens that door. It is most-deeply-validated for the practice idiom of the author at the Bombay High Court Nagpur Bench, and shall be deepened with respect to other benches as community contributors raise GitHub issues and Pull Requests with their bench's specific Practice Directions and State MV Rules variations.

---

## Roadmap

- [x] **v0.1.0-alpha (current)** — universal MACT pleading skeleton + 10 case-type skills + 6-agent pipeline + privacy firewall + Verifier disciplines + state-config layer with 1 deep + 7 researched-not-validated state exemplars
- [ ] **v0.1.x** — deep validation of the 7 researched-not-validated state exemplars (Karnataka · Tamil Nadu · Kerala · Delhi · UP · West Bengal · Gujarat) through community contribution; bug fixes; quality-gate iteration; language-register polish
- [ ] **v0.x onward** — bench-specific Practice Direction calibration deepening per MACT district; additional case-type skills (Section 140 erstwhile no-fault scheme for pre-2019 pending matters; Section 163A erstwhile structured-formula scheme for pre-2019 pending matters; Section 175 bar of jurisdiction of civil courts pleadings; Lok Adalat compromise pleadings under Section 19 Legal Services Authorities Act 1987); periodic updates as Solatium Scheme notifications and Pranay Sethi conventional-head revisions arrive
- [ ] **v1.0.0** — stable release after community-validated formatting and field-testing

Per-state deep validation will arrive in the order advocates contribute. The plugin's state-config architecture means any advocate filing regularly before a given MACT can deepen the calibration for that State by opening an issue or pull request with their State's MV Rules + tabular-particulars schedule — no central roadmap is needed to enable that. The roadmap above is therefore intentionally open-ended.

---

## Contributing

Advocates with regular motor-accident / motor-vehicle-litigation practice are invited to contribute state-config calibration for the specific State / MACT district they practise before. Open a GitHub issue with:

- Your practice State / MACT district (e.g., *"MACT Bengaluru Urban"* / *"MACT Chennai"* / *"MACT Lucknow"*)
- Your State Motor Vehicles Rules tabular-particulars schedule (for Section 166 / Section 164 / Section 161 petitions)
- Your State Court-Fees Act + State Stamp Act references
- Your bench's Cause Title format
- Your bench's case-number convention
- Your bench's filing-counter conventions (annexure markers / index format / verification format)
- Recent Practice Directions issued by the bench affecting pleading format

Pull requests are welcome with a one-paragraph explanation of the change and a reference to the State rule or Practice Direction that justifies it.

This plugin is open source under MIT.

---

## Contact

Author and maintainer: **Rushikesh R. Mahajan**, Advocate, enrolled with the Bar Council of Maharashtra and Goa.

GitHub: <https://github.com/Wolfgangrush>

Issues raised with reproducible context are handled on a best-effort basis; this is an open-source contribution maintained outside the author's professional engagements and does not constitute a vehicle for legal services.

---

## Author and brand

The author is **Rushikesh R. Mahajan**, Advocate, practising before the Bombay High Court, Nagpur Bench. The plugin is published under the open-source brand **Wolfgang Rush**, which is the author's publishing handle for legal-technology infrastructure. Personal accountability under the Advocates Act 1961 attaches to the author regardless of the use of a publishing handle.

---

## Provenance and privilege statement

See `NOTICE.md` for the full provenance + privilege + privacy + Rule 36 compliance statement. The short version:

- The plugin contains only universal procedural skeletons, formatting conventions, statutory references, and generic placeholders
- The plugin contains no specific client matter, no client communications, no client documents, no personal data of any data principal, and no tracking / telemetry / analytics
- The plugin is, in legal character, identical to a published motor-accident-law textbook — procedural knowledge in machine-readable form
- The author retains full enrolment, full responsibility, and full liability under the Advocates Act 1961 and the Bar Council of India Rules

---

## Compliance posture — Supreme Court e-Committee AI framework

This plugin is **assistive drafting infrastructure**, not autonomous decision-making software. Its operational posture is aligned with the Supreme Court of India e-Committee's stated position on AI in legal work.

> *"AI and digital tools must be used as supportive instruments and should not be allowed to override judicial reasoning."*
>
> — **Justice Rajesh Bindal**, Judge, Supreme Court of India
> [*Judicial Process Re-engineering and Digital Transformation*](https://www.sci.gov.in/press-release-dated-april-12-2026/) conference, 11–12 April 2026
> Organised by the Supreme Court e-Committee in collaboration with the Department of Justice, Government of India.
> ([Coverage — Law Trend](https://lawtrend.in/ai-must-not-replace-judicial-reasoning-warns-supreme-court-justice-rajesh-bindal/))

The same posture underpins the Supreme Court's own AI infrastructure for the judiciary:

- **[SUPACE](https://www.drishtiias.com/daily-news-analysis/ai-portal-supace)** — *Supreme Court Portal for Assistance in Court Efficiency.* AI-enabled assistive tool launched on 6 April 2021 by then-CJI S.A. Bobde. Provides legal research, fact extraction, document review, and drafting assistance to judges and legal researchers. **By design, SUPACE is not a decision-making system** — it processes facts and surfaces them to the human user. The Supreme Court has recommended adoption across all Indian High Courts.

- **[SUVAS](https://www.drishtijudiciary.com/current-affairs/supreme-court-vidhik-anuvaad-software-suvas)** — *Supreme Court Vidhik Anuvaad Software.* AI-powered translation tool launched in November 2019 by then-CJI S.A. Bobde. Translates judicial documents, orders, and judgments between English and ten Indian regional languages.

### What this plugin does — and does not — do under that framework

**Does:**

- Generate structural skeletons of pleadings, drawing on public statutes, schedule forms, and court rules.
- Run a six-agent assistive pipeline (Reader → Formatter → Drafter → Verifier → Refiner → Overseer) over the user's case facts.
- Surface citations, procedural anchors, and bench-specific conventions for advocate review.

**Does NOT:**

- Generate final filings autonomously.
- Substitute for advocate professional judgment.
- Replace human verification.
- Operate without an enrolled advocate retaining full professional responsibility.

**Every draft produced through this plugin must be advocate-owned and human-verified before filing.** The enrolled advocate using this plugin retains full professional responsibility under the Advocates Act 1961 and the Bar Council of India Rules, including verification of facts, accuracy of citations, correctness of legal grounds, propriety of the prayer, and signature on every pleading filed.

This is the same standard the Supreme Court itself applies to its own AI infrastructure (SUPACE / SUVAS): **AI as supportive instrument, never as decision-maker.**

---

## Disclaimer and Bar Council of India Rule 36 compliance

This repository is published as a personal open-source contribution to the legal-technology ecosystem. It is **not** an advertisement of professional services, **not** a solicitation of work, **not** an undertaking to act as counsel in any matter, and **not** a vehicle through which the author accepts professional engagement.

Bar Council of India Rule 36 of the Standards of Professional Conduct and Etiquette prohibits an advocate from soliciting work or advertising professional services through any medium. This repository complies with Rule 36 in both letter and spirit:

- No commercial offering is made through this repository
- No representation of professional results is made
- No invitation to engage the author professionally is made
- The README contains no contact details inviting professional retainer

The plugin is published in the same legal character as any practitioner's open-source library, public continuing-legal-education contribution, or published textbook chapter — the medium is software, the content is procedural knowledge, the practitioner retains full Bar discipline and accountability.

---

## License

MIT — see `LICENSE`.

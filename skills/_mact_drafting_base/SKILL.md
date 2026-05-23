---
name: _mact_drafting_base
description: Universal Indian MACT pleading skeleton. Shared base for all 10 case-type drafting skills in the indian-mact-drafting plugin. Holds the standard structure (Cause Title -> Parties block -> Statutory Opening -> Preamble -> Tabular Particulars per State MV Rules / Form 54 CMVR 1989 -> Description of the Accident -> Negligence Grounds -> Quantum Grounds with stepwise Sarla Verma + Pranay Sethi computation -> Prayer -> Verification -> Affidavit-in-support -> Index -> List of Documents -> accompanying applications). Extends `_drafting_common` with MV-Act-specific multiplier doctrine + State MV Rules variation envelope. NOT invoked directly — extended by every case-type skill in this plugin.
allowed-tools: Read
---

# `_mact_drafting_base` — universal Indian MACT pleading skeleton

This base skill defines the **structural shape** of any motor-accident-claim or motor-vehicle-litigation pleading drafted by the plugin. Case-type skills extend this base with case-type-specific statutory openings, tabular-particulars line-items, negligence grounds, quantum-grounds framework, prayer clauses, and accompanying applications. Extends `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`.

## Universal skeleton

```
1. CAUSE TITLE
   {{forum.name}} {{forum.bench}}
   {{case_type.case_number_prefix}} No. ____ of {{year}}

   {{party_block_template}}
   {{claimant_block}} ... {{claimant_role}}
                                  Versus
   {{respondent_block}} ... {{respondent_role}}

2. STATUTORY OPENING
   {{case_type.statutory_opening}}

3. PREAMBLE
   (Short paragraph identifying the Claimants as legal representatives
   of the deceased / as the injured-self / as the property-owner, with
   relationship to the deceased and the basis of their claim.)

4. TABULAR PARTICULARS (state-specific schedule)
   {{state_config.tabular_particulars_schedule}}
   (Typical items per Form 54 CMVR 1989 and State MV Rules schedules:
    1.  Name of claimant(s) with age, occupation, relationship to deceased
    2.  Name, age, occupation of deceased / injured
    3.  Date, time, and place of accident
    4.  Brief description of the accident
    5.  Name and address of driver of offending vehicle
    6.  Name and address of owner of offending vehicle
    7.  Registration number and type of offending vehicle
    8.  Make, model, year of offending vehicle
    9.  Insurer's name and address
   10.  Policy number and period of validity
   11.  FIR number and police station
   12.  Charge-sheet / final report status
   13.  Nature and extent of injury
   14.  Period of hospitalisation
   15.  Treatment particulars
   16.  Permanent disability percentage (where applicable)
   17.  Monthly income of deceased / injured (pre-accident)
   18.  Documentary basis for income (salary certificate / ITR / etc.)
   19.  Compensation claimed — head-wise break-up
   20.  Total compensation claimed
   21.  Interest claimed (% per annum from date of)
   22.  Court fee paid
   23.  Application for condonation of delay (legacy item — Section 166(3) repealed 1994)
   24.  Any other particular required by the State MV Rules)

5. DESCRIPTION OF THE ACCIDENT (numbered narrative paragraphs)
   5.1 Date, time, and place of accident (refer Exhibit / Annexure A
       — FIR copy).
   5.2 Manner of the accident — speed, direction, lane, signal, weather,
       visibility, road condition (refer Exhibit / Annexure B — rough
       sketch of accident site).
   5.3 Identification of offending vehicle (refer Exhibit / Annexure C
       — registration certificate; Exhibit / Annexure D — insurance
       policy).
   5.4 FIR registration and police investigation (refer Exhibit /
       Annexure A — FIR copy; Exhibit / Annexure E — charge-sheet /
       final report).
   5.5 Post-mortem report / medico-legal certificate (refer Exhibit /
       Annexure F — post-mortem report; Exhibit / Annexure G — medico-
       legal certificate).
   5.6 Hospitalisation and treatment particulars (refer Exhibit /
       Annexure H — hospital records; Exhibit / Annexure I — discharge
       summary).
   5.7 Death certificate / permanent-disability certificate
       (refer Exhibit / Annexure J).
   5.8 Income particulars of the deceased / injured (refer Exhibit /
       Annexure K — salary certificate; Exhibit / Annexure L — income-
       tax return).
   5.9 Family composition and dependency (refer Exhibit / Annexure M
       — relationship certificate; legal-heir certificate).
   5.10 Cause of action for the present pleading.
   5.11 Limitation note — for post-1994 accidents, no limitation bar
        under Section 166(3) (repealed by the Motor Vehicles
        (Amendment) Act 1994 with effect from 14 November 1994).
   5.12 Territorial jurisdiction under Section 166(2) MV Act — the
        Tribunal has jurisdiction as (a) the accident occurred within
        the local limits / (b) the Claimants reside within the local
        limits / (c) the Respondents reside within the local limits.

6. NEGLIGENCE GROUNDS (numbered)
   6.1 {{case_type.negligence_ground_1}}
   6.2 {{case_type.negligence_ground_2}}
   ...
   (For Section 166 fault-based: rash and negligent driving + breach of
    duty of care + composite / contributory negligence considerations +
    res ipsa loquitur where applicable.
    For Section 164 lump-sum: no-fault election expressly pleaded;
    foreclosure of higher Section 166 quantum acknowledged.
    For Section 161 hit-and-run: unidentified-vehicle pleaded with FIR
    + police-investigation report.)

7. QUANTUM GROUNDS (with stepwise Sarla Verma + Pranay Sethi
   computation; for Section 166 / 173 cases)
   7.1 Established monthly income of deceased: ₹___
   7.2 Future-prospects addition per Pranay Sethi: ___%
   7.3 Adjusted monthly income: ₹___
   7.4 Personal-and-living deduction per Sarla Verma: 1/4 / 1/3 / 1/2
   7.5 Monthly contribution to dependants: ₹___
   7.6 Annual contribution: ₹___ × 12 = ₹___
   7.7 Multiplier per Sarla Verma age table: ___
   7.8 Loss of dependency: 7.6 × 7.7 = ₹___
   7.9 Conventional heads per Pranay Sethi (with current triennial
       revision applied):
        - Funeral expenses: ₹___
        - Loss of estate: ₹___
        - Loss of consortium (spousal + filial + parental per Magma
          General v. Nanu Ram): ₹___
   7.10 Loss of love and affection (where the bench recognises as
        separate head): ₹___
   7.11 Special damages — medical expenses, transportation, attendant
        charges: ₹___ (with exhibit anchors)
   7.12 Total compensation claimed: ₹___
   7.13 Interest claimed: ___% per annum from date of accident / claim
        petition till realisation

8. PRAYER
   {{case_type.prayer_clauses}}

   And for such further and other reliefs as this Hon'ble Tribunal /
   Court may deem fit and proper.

9. VERIFICATION
   I, [Name of Lead Claimant / Natural Guardian], being the [role] of
   the deceased / injured, do hereby verify that the contents of
   paragraphs ___ to ___ of the {{case_type.pleading_type}} are true
   to my personal knowledge and the contents of paragraphs ___ to ___
   are true on the basis of information received from the [FIR /
   charge-sheet / hospital records / police records] and believed to
   be true. No part of this verification is false and nothing material
   has been concealed therefrom.

   Verified at [Place] on this __ day of [Month, Year].

                                       [Lead Claimant]

10. AFFIDAVIT-IN-SUPPORT
    I, [Name of Lead Claimant / Natural Guardian], aged ___ years,
    occupation [Occupation], residing at [Address], do hereby solemnly
    affirm on oath and state as under:
    1. That I am the [legal representative / natural guardian of minor
       Claimants / injured-self] of the deceased / injured herein, and
       am acquainted with the facts and circumstances of the case from
       the records available with me and from my own knowledge of the
       events.
    2. That I have read and understood the contents of the
       {{case_type.pleading_type}} comprising paragraphs 1 to ___ and
       the same are true and correct.
    3. That the documents annexed are true copies / certified true
       copies of the originals available with me / the records.

    Affirmed at [Place] on this __ day of [Month, Year].

                                       [Lead Claimant]

    Solemnly affirmed before me on solemn affirmation under the
    Bharatiya Sakshya Adhiniyam 2023.

                                       [Notary Public / Oath
                                        Commissioner / Tribunal
                                        Officer]

11. INDEX
    (Running paragraph-anchored index — paragraph numbers, content
    summary, exhibit references.)

12. LIST OF DOCUMENTS / EXHIBITS / ANNEXURES
    Exhibit / Annexure A — FIR copy dated ____
    Exhibit / Annexure B — Rough sketch of accident site
    Exhibit / Annexure C — Registration certificate of offending
                          vehicle
    Exhibit / Annexure D — Insurance policy of offending vehicle
    Exhibit / Annexure E — Charge-sheet / final report dated ____
    Exhibit / Annexure F — Post-mortem report dated ____
    Exhibit / Annexure G — Medico-legal certificate dated ____
    Exhibit / Annexure H — Hospital records (admission to discharge)
    Exhibit / Annexure I — Discharge summary dated ____
    Exhibit / Annexure J — Death certificate / Permanent-disability
                          certificate dated ____
    Exhibit / Annexure K — Salary certificate / income proof of
                          deceased / injured
    Exhibit / Annexure L — Income-tax return for assessment year ____
    Exhibit / Annexure M — Relationship / legal-heir certificate
    Exhibit / Annexure N — Driving licence of offending driver (where
                          available)
    Exhibit / Annexure O — Vehicle inspection report
    Exhibit / Annexure P — Photographs of accident
    Exhibit / Annexure Q — Witness statements
    ... (further case-type-specific exhibits)

13. ACCOMPANYING APPLICATIONS
    {{case_type.accompanying_applications}}
    (Common examples: interim compensation application / ad-interim
    attachment of the offending vehicle pending insurer's admission of
    liability / urgent listing / substituted service on the absconding
    driver / appointment of natural guardian of minor claimants /
    condonation of delay (only where a pre-1994 accident engages the
    repealed Section 166(3) bar).)
```

## Statute references the plugin handles

- Motor Vehicles Act 1988 (as amended by the Motor Vehicles (Amendment) Act 2019)
- Central Motor Vehicles Rules 1989 (including Form 54 — accident-information form)
- State Motor Vehicles Rules (per State; see `state-config/exemplars/`)
- Employees' Compensation Act 1923 (formerly the Workmen's Compensation Act; renamed 2009)
- Bharatiya Nyaya Sanhita 2023 (Section 281 rash driving; Section 282 endangering safety; Section 283 obstructing public way; Section 106 causing death by negligence)
- Bharatiya Nagarik Suraksha Sanhita 2023 (procedural framework)
- Bharatiya Sakshya Adhiniyam 2023 (Section 63 electronic-records admissibility — for dash-cam / CCTV evidence; Section 132 advocate-client privilege)
- Insurance Act 1938 (insurer-operations framework)
- IRDAI Regulations on motor third-party insurance
- Code of Civil Procedure 1908 (Order 21 for MACT award execution under Section 174 read with CPC)
- Limitation Act 1963
- Fatal Accidents Act 1855 (residual relevance for non-MV accidents; rarely engaged for motor-vehicle accidents post-MV Act 1988)
- Indian Stamp Act 1899 + applicable State Stamp Acts (for affidavit + vakalatnama stamp)
- Applicable State Court-Fees Acts (Bombay Court-Fees Act 1959; Karnataka Court-Fees and Suits Valuation Act 1958; Tamil Nadu Court-Fees and Suits Valuation Act 1955; Kerala Court-Fees and Suits Valuation Act 1959; Court-Fees Act 1870 with State amendments; etc.)

## Sarla Verma + Pranay Sethi quantum doctrine — operative summary

Base authority: *Sarla Verma v. DTC* (2009) 6 SCC 121 (multiplier table); *National Insurance v. Pranay Sethi* (2017) 16 SCC 680 (constitution-bench; future prospects + conventional heads); *Magma General v. Nanu Ram* (2018) 18 SCC 130 (filial / parental consortium extension); subsequent affirmations.

The Drafter applies the framework in stepwise computation; the Verifier checks each step against the operative authority; the Refiner ensures arithmetic consistency end-to-end.

## State-config integration

The `state-config.md` file in the case folder (copied from `state-config/exemplars/<state>.md`) supplies:

- State name + local language of pleadings
- State Motor Vehicles Rules reference
- State-specific Tabular Particulars schedule (the 22-to-24-item table varies by State — pull the State's schedule verbatim into the format-shell)
- State Court-Fees Act + Stamp Act
- State-specific MACT Procedure Rules
- Bench-specific filing-counter conventions (annexure markers / index format / verification format)

The Format agent pulls the State-specific schedule into `format-shell.md` so the Drafter's Tabular Particulars block matches the bench's expectation at the filing counter.


---

## v0.2.1 RENDER DISCIPLINE (load-bearing — Drafter must follow)

**Pandoc + reference.docx + post-pandoc fix script.** The Drafter writes Markdown using the heading discipline below. Pandoc converts the Markdown to `.docx` using the SHIPPED reference.docx at `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/reference.docx` — pre-customised with locked Word styles matching the filing-grade Bombay HC Nagpur convention (extracted from an actual filed Second Appeal pleading):

- **Body (Normal)** — TNR 14pt, 1.5 line spacing, justified, 0.5cm first-line indent
- **Heading 1** — TNR 14pt **bold + centered** (NOT underlined) — for the Court / Forum / Tribunal header line and the case-number line
- **Heading 2** — TNR 14pt **bold + UNDERLINED + centered + letter-spacing** — for spaced section headers (`F A C T S`, `G R O U N D S`, `P R A Y E R`, `I N D E X`, `S Y N O P S I S`, `L I S T   O F   A N N E X U R E S`, `V E R I F I C A T I O N`)
- **Heading 3** — TNR 14pt **bold + UNDERLINED + centered** — for unspaced section headers (`SUBSTANTIAL QUESTIONS OF LAW`, `ACTS & RULES`, `CITATIONS`) and statutory opening (`WRIT PETITION UNDER ARTICLE 226 …`)
- **Heading 4** — TNR 14pt **bold + UNDERLINED + left-aligned** — for left-anchored bold-underlined headings (`MOST RESPECTFULLY SHEWETH:`)
- **Tables** — `tblLayout = fixed`; first row bold centered; cell margins locked

### Markdown heading mapping

| Markdown | Rendered as | Used for |
|---|---|---|
| `# Heading 1` | Bold centered (no underline) | Court header line; case-number line; cover-page anchors |
| `## Heading 2` | Bold centered UNDERLINED with letter-spacing | Spaced section headers (`## F A C T S`, `## G R O U N D S`, `## P R A Y E R`, `## I N D E X`, `## S Y N O P S I S`, `## L I S T   O F   A N N E X U R E S`, `## V E R I F I C A T I O N`) |
| `### Heading 3` | Bold centered UNDERLINED | Unspaced section headers + statutory opening |
| `#### Heading 4` | Bold left UNDERLINED | `#### MOST RESPECTFULLY SHEWETH:` |
| Body paragraph | TNR 14pt justified 1.5 spacing 0.5cm first-line indent | Everything else |
| `**Bold inline**` | Bold | Property descriptors / annexure markers / key terms inline within Facts narrative |

### Bold-number paragraph convention

Facts and Grounds paragraphs use **BOLD NUMBERS**: `**1.**`, `**2.**`, `**3.**` followed by a tab + body. Renders as the gold-standard pleading layout.

### Two-step pandoc command (Step 2 is NON-NEGOTIABLE)

```bash
# Step 1 — pandoc → .docx with locked Word styles
pandoc draft-v1.md -o draft-v1.docx \
  --reference-doc="${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/reference.docx" \
  --from=markdown+pipe_tables+raw_tex

# Step 2 — force table column widths
python3 "${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/fix_docx_tables.py" draft-v1.docx
```

Step 2 forces column widths on every table — 5-col (Sr.No / Annx / Particulars / Date / Pgs) = 8/8/60/14/10; 4-col = 10/10/65/15; 3-col = 10/75/15; 2-col Dates–Events = 18/82. Locks first-row bold + centered + vertically-centered cells. **Skipping the fix script reproduces the v0.2.0 Index-table defect (Sr.No / Annx columns stacking vertically).**

Do NOT auto-generate a fresh reference.docx in the case folder. Use the shipped one or a `<case-folder>/reference.docx` override.

### Cover-page discipline

INDEX, SYNOPSIS, LIST OF ANNEXURES each begin on a new page (`\newpage` in Markdown) and carry ONLY: forum header (`#`) + case-number line (`#`) + short cause-title (Petitioner short name `///VERSUS///` Respondent short name) + section header (`##`) + table + Counsel block. DO NOT repeat the full party address block on cover pages.

### Pipeline-optionality (advocate-cost discipline)

The full 6-agent pipeline (Reader → Format → Drafter → Verifier → Refiner → Overseer) is **NOT** mandatory. Only the first three stages are required to produce a filing-grade draft. Stages 4–6 are OPTIONAL QC layers the advocate explicitly invokes. Default exit point is here, after Drafter (~280K tokens). Full pipeline ~600K tokens — disproportionate for routine pleadings.

When `draft-v1.docx` is written, the Drafter's job is complete. The advocate decides whether to invoke the QC stages.

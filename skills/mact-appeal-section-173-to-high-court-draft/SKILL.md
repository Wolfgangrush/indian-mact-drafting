---
name: mact-appeal-section-173-to-high-court-draft
description: Draft an appeal to the High Court under Section 173 of the Motor Vehicles Act 1988 against an award of the Motor Accident Claims Tribunal. Encodes the 90-day limitation under Section 173(1) proviso, the Section 173(2) deposit requirement (₹25,000 or 50% of award, whichever is less, where the appellant is the insurer or the owner — verify current notification), the grounds framework (erroneous appreciation of negligence, mis-applied Sarla Verma multiplier, mis-applied Pranay Sethi future-prospects, wrongful deduction, contributory-negligence apportionment, limitation, jurisdiction), and the stay-of-award framework. Auto-fires on "draft Section 173 MV Act appeal", "draft MACT High Court appeal", "draft motor accident first appeal", "draft MV Act first appeal".
allowed-tools: Read, Write, Edit, Bash, Glob
---

# MACT Section 173 High Court Appeal Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: FIRST APPEAL UNDER SECTION 173 OF THE MOTOR VEHICLES ACT 1988 AGAINST THE AWARD OF THE MOTOR ACCIDENT CLAIMS TRIBUNAL
case_short_code: MACT_173
case_number_prefix: First Appeal   # State-specific — "First Appeal" / "F.A." / "F.A.O." (First Appeal from Order) per High Court Registry convention
pleading_type: Memorandum of First Appeal
typical_forum: High Court of [State] — territorial bench corresponding to the MACT whose award is appealed (e.g. Bombay HC Nagpur Bench for an MACT Nagpur / Wardha / Bhandara / Gondia award)
typical_parties: Appellant (claimant seeking enhancement OR insurer / owner seeking reduction / reversal) + Respondent(s) (the original opposite parties before the MACT)
statutory_opening: "This First Appeal is filed under Section 173 of the Motor Vehicles Act 1988 against the Award dated [Award-Date-Placeholder] passed by the [Motor Accident Claims Tribunal] in M.A.C.P. No. [MACT-Case-No.-Placeholder] of [Year-Placeholder], whereby the Tribunal has [granted compensation of ₹___ to the Claimants / dismissed the petition / apportioned contributory negligence at ___% against the deceased / injured]."
negligence_grounds:
  - "Erroneous appreciation of negligence — the Tribunal has [over-emphasised / under-emphasised] the contributory negligence of the deceased / injured contrary to the weight of the FIR + charge-sheet + post-mortem evidence; composite-negligence framing was wrongly displaced by contributory-negligence framing."
  - "Mis-applied Sarla Verma multiplier — the Tribunal has applied a multiplier of ___ corresponding to age band ___, whereas the correct multiplier per Sarla Verma v. DTC (2009) is ___ for age band ___."
  - "Mis-applied Pranay Sethi future-prospects — the Tribunal has applied future-prospects of ___% for [age band] [employment status], whereas the correct figure per Pranay Sethi (2017) constitution-bench is ___%."
  - "Wrongful deduction for personal-and-living expenses — the Tribunal has deducted 1/2 / 1/3 / 1/4 contrary to the Sarla Verma framework for the family-composition before it."
  - "Wrongful disallowance / under-grant of conventional heads — funeral / loss of estate / loss of consortium — without applying the Pranay Sethi triennial revision."
  - "Wrongful disallowance of loss of love and affection / filial / parental consortium per Magma General v. Nanu Ram (2018)."
  - "Wrongful disallowance / under-grant of interest — interest must run from the date of claim petition at a fair rate (typically 7.5% to 9% per annum)."
  - "Contributory-negligence apportionment — the Tribunal has wrongly apportioned ___% contributory negligence against the deceased / injured without evidentiary basis."
  - "Limitation challenge — the Tribunal has wrongly applied / wrongly disregarded the limitation framework."
  - "Jurisdictional challenge — the Tribunal has exercised territorial jurisdiction beyond its authority under Section 166(2)."
prayer_clauses:
  - "(a) Set aside / modify the Award dated ___ of the Motor Accident Claims Tribunal in M.A.C.P. No. ___ of ___;"
  - "(b) Enhance / reduce the compensation to ₹___ (Rupees ___ only);"
  - "(c) Direct that interest at ___% per annum run from the date of claim petition till realisation;"
  - "(d) Stay the operation of the impugned Award pending disposal of this Appeal;"
  - "(e) Award costs of the appeal;"
mandatory_exhibits:
  - certified_copy_of_impugned_mact_award
  - copy_of_main_claim_petition_before_mact
  - copies_of_oral_evidence_recorded_before_mact
  - copies_of_documentary_evidence_filed_before_mact
  - proof_of_section_173_2_deposit_where_appellant_is_insurer_or_owner
accompanying_applications:
  - "I.A. for stay of operation of the impugned Award pending disposal of appeal"
  - "I.A. for condonation of delay (where the appeal is beyond the 90-day limitation; sufficient cause to be pleaded)"
  - "I.A. for waiver / reduction of the Section 173(2) deposit (where the appellant is the insurer or the owner and seeks reduction; verify current notification on whether reduction is available)"
  - "I.A. for urgent listing"
court_fee: "Appeal court fee per the State Court-Fees Act applicable to High Court appeals. The Drafter computes and reflects."
limitation_note: "90 days from the date of the impugned Award per Section 173(1) proviso. Extendable on sufficient cause shown (Section 5 of the Limitation Act 1963 applied to MV Act appeals via the saving clause)."
```

## Section 173(2) deposit discipline

For an appeal by the insurer or by the owner, Section 173(2) requires deposit of ₹25,000 or 50% of the amount awarded, whichever is less. The deposit is a condition precedent. The Drafter computes the deposit from the impugned award amount, reflects deposit-particulars in the appeal memo (deposit-challan / receipt / proof), or files a separate application for reduction / waiver where the Insurer / Owner challenges the deposit as excessive in the facts.

## Cross-references

- *Sarla Verma v. DTC* (2009) 6 SCC 121 — for any multiplier-mis-application ground
- *Pranay Sethi* (2017) 16 SCC 680 — for any future-prospects-mis-application ground; for conventional-heads triennial revision
- *Magma General v. Nanu Ram* (2018) 18 SCC 130 — for filial / parental consortium grounds
- *Royal Sundaram v. Mandala Yadagari Goud* (2019) 5 SCC 554 — for income-inference grounds
- *Erudhaya Priya* (2020) — for injury-claim quantification with permanent disability

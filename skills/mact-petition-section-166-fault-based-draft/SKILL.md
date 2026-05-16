---
name: mact-petition-section-166-fault-based-draft
description: Draft a fault-based Claim Petition before the Motor Accident Claims Tribunal under Section 166 of the Motor Vehicles Act 1988 (as amended 2019), claiming just and adequate compensation for death / personal injury / property damage caused by the rash and negligent use of a motor vehicle. Encodes the Section 165 Tribunal constitution, the Section 168 award structure, the Section 169 procedure, the Sarla Verma multiplier table (Sarla Verma v. DTC (2009) 6 SCC 121), the Pranay Sethi future-prospects + conventional-heads framework (National Insurance v. Pranay Sethi (2017) 16 SCC 680, constitution bench), the Magma General v. Nanu Ram (2018) 18 SCC 130 filial-consortium extension, the territorial-jurisdiction rule under Section 166(2), and the note that the Section 166(3) three-year limitation was repealed by the Motor Vehicles (Amendment) Act 1994 with effect from 14 November 1994. Auto-fires on "draft MACT 166 petition", "draft Section 166 MV Act claim", "draft fault-based motor accident claim", and similar trigger phrases.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# MACT Section 166 Fault-Based Claim Petition Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: CLAIM PETITION UNDER SECTION 166 OF THE MOTOR VEHICLES ACT 1988
case_short_code: MACT_166
case_number_prefix: M.A.C.P.   # State-specific prefix — pull from state-config.md (M.A.C.P. in Maharashtra; M.V.C. in Karnataka; M.C.O.P. / O.P. (M.V.) in TN; M.A.C. in Kerala; MAC App. in Delhi; etc.)
pleading_type: Claim Petition
typical_forum: Motor Accident Claims Tribunal of the District constituted under Section 165 of the Motor Vehicles Act 1988, having territorial jurisdiction per Section 166(2) — (a) place of accident OR (b) Claimants' residence OR (c) Respondents' residence
typical_parties: Claimants (legal representatives of deceased / injured-self / property-owner) + Respondent No. 1 (driver of offending vehicle) + Respondent No. 2 (owner of offending vehicle) + Respondent No. 3 (insurer of offending vehicle) + additional respondents for composite-negligence (driver / owner / insurer of second vehicle) where applicable
statutory_opening: "This Claim Petition is filed under Section 166 of the Motor Vehicles Act 1988 (as amended) read with Section 168 of the said Act, claiming just and adequate compensation for the death / personal injury / property damage caused by the rash and negligent driving of the offending vehicle bearing Registration No. [Vehicle-Reg-Placeholder] on [Date-of-Accident-Placeholder] at [Place-of-Accident-Placeholder]."
negligence_grounds:
  - "Rash and negligent driving — the offending vehicle was driven at excessive speed / on the wrong side / in violation of the lane discipline / in violation of the signal at the relevant time, in breach of the duty of care owed to other road users."
  - "Composite negligence (where multiple vehicles involved) — the Respondents are jointly and severally liable to the Claimants per the composite-negligence framework; the Claimants are not concerned with inter-se apportionment."
  - "Res ipsa loquitur (where applicable) — the manner and circumstances of the accident raise a presumption of negligence on the part of the driver of the offending vehicle (e.g. vehicle mounting footpath / vehicle in stationary position struck from behind / pedestrian on zebra crossing struck)."
  - "Negligence corroborated by FIR + charge-sheet / final report (Exhibit ___) + rough sketch of accident site (Exhibit ___) + post-mortem report / medico-legal certificate (Exhibit ___) + witness statements (Exhibit ___)."
  - "Statutory presumptions — the Respondents have failed to discharge the burden of rebutting the statutory presumptions arising under Sections 184 / 187 of the Motor Vehicles Act 1988 / under Section 106 of the Bharatiya Nyaya Sanhita 2023 in the cognate criminal proceeding."
quantum_grounds_framework: "stepwise — established monthly income → Pranay Sethi future-prospects addition → adjusted monthly income → Sarla Verma personal-and-living deduction → monthly contribution → annual contribution → Sarla Verma multiplier per age band → loss of dependency + Pranay Sethi conventional heads (funeral + estate + consortium per Magma General) + loss of love and affection (where the bench recognises) + special damages + interest"
prayer_clauses:
  - "(a) Award just and adequate compensation of ₹___ (Rupees ___ only) to the Claimants jointly and severally with interest at ___% per annum from the date of filing of the Claim Petition till realisation;"
  - "(b) Direct that the said award shall be a joint and several liability of the Respondents and that the Insurer (Respondent No. ___) shall satisfy the award in the first instance, with right of recovery against the owner / driver where the policy contains a recovery clause;"
  - "(c) Award costs of the proceedings to the Claimants;"
mandatory_exhibits:
  - fir_copy
  - charge_sheet_or_final_report
  - post_mortem_report_or_medico_legal_certificate
  - hospital_records_and_discharge_summary
  - death_certificate_or_permanent_disability_certificate
  - salary_certificate_or_income_proof
  - income_tax_return_for_relevant_assessment_year
  - relationship_or_legal_heir_certificate
  - registration_certificate_of_offending_vehicle
  - insurance_policy_of_offending_vehicle
  - rough_sketch_of_accident_site
  - photographs_of_accident
  - witness_statements
  - permanent_disability_certificate_where_applicable
accompanying_applications:
  - "I.A. for interim compensation pending final award (where the Tribunal's procedural power supports interim disbursement)"
  - "I.A. for ad-interim attachment of the offending vehicle pending the Insurer's admission of liability"
  - "I.A. for urgent listing (where the Claimants are in immediate financial distress)"
  - "I.A. for substituted service on the absconding driver (where the driver has fled the jurisdiction)"
  - "I.A. for appointment of natural guardian of minor Claimants"
court_fee: "Per the State Court-Fees Act — pull the applicable Article from state-config.md. Many States grant total exemption or a nominal slab for MACT petitions. The Drafter computes the fee from `case-config.md` and reflects it in the petition memo."
limitation_note: "Section 166(3) three-year limitation REPEALED by the Motor Vehicles (Amendment) Act 1994 with effect from 14 November 1994 — NO limitation bar for post-1994 accidents. For pre-1994 accidents, the repealed three-year bar applied and a condonation-of-delay application may be required."
```

## Section 166(2) territorial-jurisdiction note

The Claim Petition may be filed in the Tribunal having jurisdiction over (a) the place where the accident occurred, OR (b) the place where the claimant resides or carries on business, OR (c) the place where the defendant resides. The Drafter pleads the chosen anchor expressly in the opening paragraphs.

## Section 168 award-structure note

The Tribunal's award under Section 168 must contain (a) the amount of compensation, (b) the person or persons to whom it is payable, (c) the amount payable by the insurer / owner / driver, and (d) the period within which it is to be paid. The Tribunal's interest order forms part of the award. The Drafter's prayer mirrors this structure for ease of award-drafting by the Tribunal.

## Cross-references to Section 167 election-clause

If the deceased / injured was a workman in the course of employment in a motor accident, the Claimants must irrevocably elect between the MACT forum (Section 166) and the EC Act forum. The Drafter records the election expressly in the opening of the petition.

## Cross-reference to the Section 164 lump-sum alternative

The Claimants electing the higher Section 166 fault-based claim foreclose the structured Section 164 lump-sum. The Drafter records the election expressly to pre-empt any insurer-side argument of election-by-omission.

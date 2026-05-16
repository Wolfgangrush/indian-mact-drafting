---
name: workmen-compensation-claim-draft
description: Draft a claim under the Employees' Compensation Act 1923 (formerly the Workmen's Compensation Act 1923, renamed by the Workmen's Compensation (Amendment) Act 2009) before the Commissioner under the said Act, for a workman / employee killed or injured in the course of employment in a motor-vehicle accident. Encodes the Section 4 (amount of compensation) framework, Schedule I (list of compensable injuries), Schedule III (occupational diseases), Schedule IV (multiplier-equivalent factors), Section 22 (procedure before the Commissioner), and the irrevocable election under Section 167 of the Motor Vehicles Act 1988 between the EC Act forum and the MACT forum. Auto-fires on "draft EC Act workmen compensation claim", "draft Employees' Compensation Act claim", "draft workman compensation MV accident", "draft Section 22 EC Act claim".
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Employees' Compensation Act 1923 Claim Draft Skill (motor-vehicle context)

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPLICATION UNDER SECTION 22 READ WITH SECTION 4 OF THE EMPLOYEES' COMPENSATION ACT 1923
case_short_code: EC_ACT
case_number_prefix: EC Case   # "EC Case" / "WC Case" (legacy) / "ECA No." per State Commissioner's nomenclature
pleading_type: Application before the Commissioner
typical_forum: Commissioner under the Employees' Compensation Act 1923 of the area where (a) the accident occurred OR (b) the workman / employee ordinarily resides OR (c) the employer has its principal place of business — per the EC Act Rules of the State
typical_parties: Applicant (workman / employee — for injury claims; legal representatives of deceased workman — for death claims) + Opposite Party (employer of the workman) + Insurer of the employer's liability under the EC Act / motor-vehicle policy with EC Act endorsement
statutory_opening: "This Application is filed under Section 22 read with Section 4 of the Employees' Compensation Act 1923, with the irrevocable election under Section 167 of the Motor Vehicles Act 1988 of the Employees' Compensation Act forum over the Motor Accident Claims Tribunal forum, for compensation for the death / injury caused to the workman [Workman-Name-Placeholder] in the course of and arising out of his / her employment, in the motor-vehicle accident dated [Date-of-Accident-Placeholder] at [Place-of-Accident-Placeholder]."
negligence_grounds:
  - "Employment relationship — the deceased / injured workman was at the relevant time an employee of the Opposite Party as [driver / cleaner / loader / conductor / helper / supervisor], on monthly wages of ₹___, in continuous employment from ___."
  - "In the course of and arising out of employment — the accident occurred while the workman was performing the duties of his / her employment (driving the employer's vehicle on an authorised trip / loading / unloading / accompanying the consignment / returning to the employer's premises after the day's work)."
  - "Personal injury caused by accident — the workman sustained [death / permanent total disablement / permanent partial disablement / temporary disablement / Schedule I injury] in the said accident as established by the post-mortem report / medico-legal certificate / hospital records (Exhibit ___)."
  - "Election under Section 167 MV Act — the Applicants irrevocably elect the EC Act forum over the MACT forum; the election precludes any subsequent MACT petition for the same accident."
  - "Insurer's liability — the employer's motor-vehicle policy (Exhibit ___) contains a workmen-compensation / EC Act endorsement that covers the employer's liability under the EC Act; the Insurer is liable in the first instance."
quantum_grounds_framework: "Section 4 of the EC Act 1923 formula — for death: 50% of monthly wages × relevant factor under Schedule IV (mapped to age); for permanent total disablement: 60% of monthly wages × relevant factor; for permanent partial disablement: percentage of (60% × monthly wages × relevant factor) per Schedule I; for temporary disablement: 25% of monthly wages payable as a half-monthly periodical payment; minimum compensation as notified by the Central Government from time to time; funeral expenses of ₹5,000 (Section 4(4) — verify current notification)"
prayer_clauses:
  - "(a) Award compensation of ₹___ (Rupees ___ only) to the Applicants under Section 4 of the EC Act 1923;"
  - "(b) Award interest at 12% per annum from one month after the accident (Section 4A(3) EC Act);"
  - "(c) Award penalty at 50% on the principal compensation where the employer has not deposited the compensation within one month (Section 4A(3)(b) EC Act);"
  - "(d) Direct the Insurer to satisfy the award;"
  - "(e) Award costs of the proceedings;"
mandatory_exhibits:
  - employment_proof_appointment_letter_or_employer_certificate_or_wage_register
  - wage_certificate_for_three_months_preceding_accident
  - fir_copy_of_motor_vehicle_accident
  - post_mortem_report_or_medico_legal_certificate
  - hospital_records_and_discharge_summary
  - death_certificate_or_permanent_disability_certificate
  - relationship_or_legal_heir_certificate
  - employer_s_motor_vehicle_policy_with_ec_act_endorsement
  - section_167_mv_act_election_declaration
accompanying_applications:
  - "Application for interim disbursement under EC Act Rules"
court_fee: "Per the EC Act Rules of the State; pull from state-config.md."
limitation_note: "Two years from the date of the accident OR two years from the date of the disease's first manifestation (Section 10 EC Act 1923). Condonation of delay possible on sufficient cause."
```

## Section 167 MV Act election-clause discipline

Section 167 MV Act prescribes that where a workman is entitled to claim under both the EC Act 1923 forum and the MACT forum (under the MV Act 1988), the claimant must irrevocably elect ONE forum. The election is irrevocable. The Drafter records the election expressly at the opening of the EC Act application AND files a separate election-declaration affidavit. Filing under the EC Act forum forecloses any subsequent MACT petition.

## Statutory-currency check (Verifier surface)

- References to *"Workmen's Compensation Act 1923"* → flag; correct name post-2009 is *"Employees' Compensation Act 1923"*
- References to the pre-2009 quantum framework → verify against current Section 4 + notification
- References to *"Commissioner for Workmen's Compensation"* → correct name is *"Commissioner under the Employees' Compensation Act 1923"*

## Election strategy note

The EC Act forum typically yields LOWER compensation than the MACT forum (no Sarla Verma multiplier, no Pranay Sethi future-prospects, no Magma General consortium). However, the EC Act forum is FASTER, has fixed-formula certainty, and applies even on no-fault basis (the workman need not prove negligence of the employer or any other party). The Drafter notes the strategic election in the case-config rationale; the choice rests with the Claimants and their counsel.

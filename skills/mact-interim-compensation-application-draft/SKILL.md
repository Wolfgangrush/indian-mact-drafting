---
name: mact-interim-compensation-application-draft
description: Draft an interim compensation application before the Motor Accident Claims Tribunal pending final award in a Section 166 / 164 / 161 / 147 claim petition. The erstwhile Section 140 no-fault interim compensation has been subsumed under the post-2019 Section 164 structured-formula scheme; this application invokes the Tribunal's procedural power under Section 169 MV Act and the Tribunal's own Procedure Rules to grant interim relief pending final award (for ongoing medical expenses, funeral expenses, immediate dependency). Encodes the urgency-grounds + prima-facie-liability + quantum-of-interim framework. Auto-fires on "draft interim compensation application", "draft interim relief MACT", "draft MACT interim disbursement".
allowed-tools: Read, Write, Edit, Bash, Glob
---

# MACT Interim Compensation Application Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPLICATION FOR INTERIM COMPENSATION PENDING FINAL AWARD UNDER THE MOTOR VEHICLES ACT 1988
case_short_code: MACT_INTERIM
case_number_prefix: I.A. (Interlocutory Application within the main Claim Petition)
pleading_type: Interlocutory Application
typical_forum: same MACT seised of the main Claim Petition
typical_parties: same as the main petition
statutory_opening: "This Application is filed under Section 169 of the Motor Vehicles Act 1988 read with the Tribunal's Procedure Rules and the Tribunal's inherent power to do justice between the parties, for interim disbursement of compensation pending final award in M.A.C.P. No. ___ of ___, in view of the immediate financial distress of the Claimants and the prima-facie liability of the Respondents."
negligence_grounds:
  - "Urgency — the Claimants are in immediate financial distress on account of (a) ongoing medical expenses of the injured Claimant / (b) funeral and post-death expenses / (c) immediate dependency loss of the deceased's family / (d) loss of livelihood pending final award."
  - "Prima-facie liability — the FIR (Exhibit ___) + charge-sheet (Exhibit ___) + post-mortem report (Exhibit ___) establish a prima-facie case of rash and negligent driving against the offending vehicle; the insurance policy (Exhibit ___) establishes prima-facie insurer liability."
  - "Tribunal's procedural power — Section 169 MV Act read with the Tribunal's Procedure Rules empowers the Tribunal to regulate its own procedure for doing complete justice between the parties; interim disbursement is a recognised exercise of that power."
  - "Quantum of interim relief — the Claimants seek interim disbursement of ₹___ for (a) medical expenses ₹___ / (b) funeral expenses ₹___ / (c) immediate dependency ₹___, against the eventual final award."
prayer_clauses:
  - "(a) Direct interim disbursement of ₹___ (Rupees ___ only) to the Claimants by the Insurer (Respondent No. ___) pending final award;"
  - "(b) Direct that the interim disbursement shall stand adjusted against the final award;"
  - "(c) Award costs of the Application;"
mandatory_exhibits:
  - copy_of_main_claim_petition
  - fir_copy
  - charge_sheet_or_status_of_police_investigation
  - hospital_records_showing_ongoing_treatment_or_funeral_bills
  - insurance_policy_of_offending_vehicle
  - statement_of_financial_distress_with_supporting_documents
accompanying_applications:
  - "I.A. for urgent listing (where the medical situation is critical or the funeral is pending)"
court_fee: "Nominal application fee per State Court-Fees Act; pull from state-config.md."
limitation_note: "No independent limitation — moves within the limitation framework of the main petition."
```

## Section 140 → Section 164 transition note

The erstwhile Section 140 MV Act (no-fault interim compensation of a fixed amount) has been OMITTED by the Motor Vehicles (Amendment) Act 2019, with the no-fault scheme consolidated under the structured Section 164 lump-sum. The interim compensation application now rests on the Tribunal's procedural power under Section 169 MV Act and its own Procedure Rules — not on the repealed Section 140.

## Statute-currency check (Verifier surface)

- Section 140 MV Act reference for the interim application → flag as obsolete (repealed by 2019 Amendment)
- The application invokes Section 169 + Tribunal's procedure power, NOT Section 140

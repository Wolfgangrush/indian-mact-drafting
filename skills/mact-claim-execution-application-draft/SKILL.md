---
name: mact-claim-execution-application-draft
description: Draft an execution application for an unsatisfied MACT award. The award of the Motor Accident Claims Tribunal is enforceable as a decree of a civil court under Section 174 of the Motor Vehicles Act 1988 read with Order 21 of the Code of Civil Procedure 1908. Encodes the modes of execution (attachment of vehicle, attachment of bank account, attachment of immovable property, arrest where applicable), the insurer-side payment route under IRDAI regulations, and the cross-reference to Section 174 Collector recovery as an alternative. Auto-fires on "draft MACT execution application", "draft execution of motor accident award", "draft MACT award enforcement", "draft Order 21 CPC MACT".
allowed-tools: Read, Write, Edit, Bash, Glob
---

# MACT Award Execution Application Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: EXECUTION APPLICATION UNDER ORDER 21 CPC READ WITH SECTION 174 OF THE MOTOR VEHICLES ACT 1988
case_short_code: MACT_EXEC
case_number_prefix: Execution Application   # "E.A." / "Execution Application" / "Darkhast" per State Civil Manual
pleading_type: Execution Application
typical_forum: Civil Court of competent jurisdiction (typically the District Court / Civil Judge Senior Division of the District where the judgment-debtor resides or holds attachable assets); the MACT itself does not execute its award — the award is treated as a decree of the civil court per Section 174 MV Act
typical_parties: Decree-Holder (the original Claimant / claimants) + Judgment-Debtor(s) (the original Respondents — driver / owner / insurer who failed to satisfy the award within the period prescribed)
statutory_opening: "This Execution Application is filed under Order 21 of the Code of Civil Procedure 1908 read with Section 174 of the Motor Vehicles Act 1988, for execution of the Award dated [Award-Date-Placeholder] passed by the Motor Accident Claims Tribunal in M.A.C.P. No. [MACT-Case-No.-Placeholder] of [Year-Placeholder], whereby the Tribunal awarded compensation of ₹[Award-Amount-Placeholder] to the Decree-Holder against the Judgment-Debtor(s), which Award has not been satisfied within the period prescribed."
grounds:
  - "Award unsatisfied — the Tribunal's Award dated ___ directed payment of ₹___ within ___ days; the said period has expired and the Judgment-Debtor has not paid the full / any amount."
  - "Award enforceable as a decree — Section 174 of the MV Act 1988 declares that any amount due under an Award may be recovered in the same manner as an arrear of land revenue OR enforced as a decree of a civil court; the Decree-Holder elects the civil-court route under Order 21 CPC."
  - "Modes of execution sought — (a) attachment of the offending vehicle; (b) attachment of bank account of the Judgment-Debtor; (c) attachment of immovable property; (d) arrest of the Judgment-Debtor where applicable (Section 51 + Section 55 + Order 21 Rule 37 CPC)."
prayer_clauses:
  - "(a) Direct execution of the Tribunal's Award dated ___ by attachment and sale of the offending vehicle bearing Registration No. ___;"
  - "(b) Direct attachment of the bank accounts of the Judgment-Debtor maintained at [Bank-Name-Placeholder];"
  - "(c) Direct attachment and sale of the immovable property of the Judgment-Debtor situated at [Property-Particulars-Placeholder];"
  - "(d) Issue warrant of arrest against the Judgment-Debtor under Order 21 Rule 37 CPC where applicable;"
  - "(e) Award costs of the execution proceedings;"
mandatory_exhibits:
  - certified_copy_of_mact_award
  - copy_of_proof_of_service_of_award_on_judgment_debtor
  - statement_of_unsatisfied_balance
  - particulars_of_attachable_assets_of_judgment_debtor
  - insurance_policy_of_offending_vehicle_for_insurer_side_recovery
accompanying_applications:
  - "Application for issue of attachment warrant"
  - "Application for issue of warrant of arrest under Order 21 Rule 37 CPC (where the Judgment-Debtor is the owner or driver and is wilfully avoiding satisfaction)"
court_fee: "Per the State Court-Fees Act for execution applications; pull from state-config.md."
limitation_note: "12 years from the date of the decree (Article 136 of the Schedule to the Limitation Act 1963) for execution of a money decree. The Tribunal's Award is treated as a decree for this purpose."
```

## Insurer-side payment route

For insurer-side awards, the Insurance Regulatory and Development Authority of India (IRDAI) regulations operationalise the insurer's payment to the Claimant. Where the Insurer accepts the award, payment is typically by way of demand draft / bank transfer through the Tribunal. Where the Insurer disputes the award, the Insurer files Section 173 appeal and (where ordered) deposits the Section 173(2) amount; the un-deposited / un-disputed balance is recoverable in execution.

## Cross-reference to Section 174 Collector recovery

Section 174 MV Act provides TWO modes for recovery of an unsatisfied award:

(a) recovery as arrears of land revenue (via the Collector — see the `compensation-recovery-collector-section-174-draft` skill), AND
(b) execution as a decree of a civil court (this skill, Order 21 CPC).

The Decree-Holder may elect either route. The Drafter notes the election in the execution application.

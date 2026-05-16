---
name: compensation-recovery-collector-section-174-draft
description: Draft an application before the Collector of the District for recovery of an unsatisfied MACT award as arrears of land revenue, under Section 174 of the Motor Vehicles Act 1988. Section 174 provides TWO modes for recovery of an unsatisfied award — (a) recovery as arrears of land revenue (Collector route, this skill), AND (b) execution as a decree of a civil court (Order 21 CPC route, see mact-claim-execution-application-draft). The Collector route is an administrative-recovery channel distinct from civil-court execution and is typically faster for cases where the judgment-debtor's assets are immovable or easily attachable through the revenue machinery. Auto-fires on "draft Section 174 Collector recovery", "draft MACT recovery as arrears land revenue", "draft Collector route motor accident award recovery".
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Section 174 Collector-Route Recovery Application Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: APPLICATION UNDER SECTION 174 OF THE MOTOR VEHICLES ACT 1988 FOR RECOVERY OF UNSATISFIED MACT AWARD AS ARREARS OF LAND REVENUE
case_short_code: MACT_174_COLLECTOR
case_number_prefix: Recovery Application   # State-specific revenue-Department prefix
pleading_type: Application before the Collector
typical_forum: Collector of the District where the Judgment-Debtor (typically the insurer / owner) resides or carries on business
typical_parties: Applicant (the original Claimant who holds the unsatisfied MACT award — the Decree-Holder) + Opposite Party (the Judgment-Debtor — insurer / owner / driver who has failed to satisfy the award)
statutory_opening: "This Application is filed under Section 174 of the Motor Vehicles Act 1988, requesting the Collector of the District to recover the unsatisfied compensation awarded by the Motor Accident Claims Tribunal in M.A.C.P. No. [MACT-Case-No.-Placeholder] of [Year-Placeholder] dated [Award-Date-Placeholder], as arrears of land revenue from the Opposite Party (Judgment-Debtor) whose name and address are stated below."
grounds:
  - "Award passed and unsatisfied — the Motor Accident Claims Tribunal awarded ₹___ to the Applicant by Award dated ___ in M.A.C.P. No. ___; the period prescribed for payment has expired and the Judgment-Debtor has not paid the full / any amount of the award."
  - "Statutory authority for Collector-route recovery — Section 174 of the MV Act 1988 provides that any amount due under an Award may, on a certificate issued by the Tribunal, be recovered by the Collector as if it were arrears of land revenue."
  - "Election of recovery route — the Applicant elects the Collector-route recovery under Section 174 in preference to civil-court execution under Order 21 CPC; the election does not preclude subsequent civil-court execution if the Collector-route recovery proves inadequate."
  - "Particulars of the Judgment-Debtor — the Judgment-Debtor resides / carries on business within the territorial jurisdiction of the Collector of [District-Placeholder]; the attachable assets include [bank-deposits / immovable-property / vehicle / business-receivables — particulars Exhibit ___]."
  - "Certificate of the Tribunal — the Tribunal has issued the certificate under Section 174 read with the State Revenue Recovery Rules (Exhibit ___); the certificate is the operative instrument for Collector-route recovery."
prayer_clauses:
  - "(a) Recover the sum of ₹___ (Rupees ___ only) from the Judgment-Debtor as arrears of land revenue under Section 174 of the Motor Vehicles Act 1988 read with the [State] Revenue Recovery Act / Land Revenue Code;"
  - "(b) Issue notices of demand / attachment / sale to the Judgment-Debtor in accordance with the prescribed procedure;"
  - "(c) Disburse the recovered amount to the Applicant after deduction of the prescribed administrative charges;"
  - "(d) Pass such further and consequential orders as may be necessary for due recovery;"
mandatory_exhibits:
  - certified_copy_of_mact_award
  - tribunal_s_section_174_certificate_for_revenue_recovery
  - statement_of_unsatisfied_balance
  - particulars_of_attachable_assets_of_judgment_debtor
  - proof_of_service_of_award_on_judgment_debtor
accompanying_applications:
  - "Application for early issue of demand notice"
  - "Application for attachment of bank accounts / immovable property pending recovery"
court_fee: "Per State Revenue Recovery Rules / nominal application fee; pull from state-config.md."
limitation_note: "The Section 174 certificate must be acted upon within the period prescribed under the State Revenue Recovery Act / Land Revenue Code; for the underlying decree, the 12-year limitation under Article 136 of the Schedule to the Limitation Act 1963 continues to apply for any residual civil-court execution route."
```

## Choice-of-route note

The Decree-Holder may elect EITHER the Collector route (this skill) OR the civil-court execution route (the `mact-claim-execution-application-draft` skill). The Collector route is typically faster where the Judgment-Debtor's assets are immovable or where revenue-Department machinery has better reach than the civil court bailiff system; the civil-court route is preferred where the assets are movable (vehicle / bank accounts) and arrest of the Judgment-Debtor is sought under Order 21 Rule 37 CPC.

The election under Section 174 is NOT irrevocable in the same sense as Section 167 — the Decree-Holder may shift between the two routes if one proves inadequate, subject to the limitation framework.

## State Revenue Recovery integration

Each State has its own Revenue Recovery Act / Land Revenue Code that operationalises the Collector's recovery machinery (e.g. Maharashtra Land Revenue Code 1966; Karnataka Land Revenue Act 1964; Tamil Nadu Revenue Recovery Act 1864; Uttar Pradesh Zamindari Abolition and Land Reforms Act 1950 + State Revenue Recovery framework). The Drafter pulls the applicable State Revenue Recovery reference from `state-config.md` and cites it in the application's procedural anchor.

---
name: mact-petition-section-164-lump-sum-draft
description: Draft a structured-formula lump-sum Claim Petition before the Motor Accident Claims Tribunal under Section 164 of the Motor Vehicles Act 1988 (as inserted by the Motor Vehicles (Amendment) Act 2019, with effect from 1 April 2022). Section 164 replaces the old Section 163A no-fault scheme — the post-2019 framework provides a fixed lump-sum (currently ₹5,00,000 for death and ₹2,50,000 for grievous hurt — verify against current notification) without proof of negligence. Encodes the structured-formula election, the Section 165(4) election between Section 164 (lump-sum) and Section 166 (fault-based open-ended), and the foreclosure consequence. Auto-fires on "draft MACT 164 lump sum petition", "draft Section 164 MV Act claim", "draft no-fault motor accident claim", "draft structured lump-sum motor claim".
allowed-tools: Read, Write, Edit, Bash, Glob
---

# MACT Section 164 Lump-Sum Claim Petition Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: CLAIM PETITION UNDER SECTION 164 OF THE MOTOR VEHICLES ACT 1988
case_short_code: MACT_164
case_number_prefix: M.A.C.P.   # Per state-config — same prefix as Section 166 petitions in most States
pleading_type: Claim Petition (structured lump-sum)
typical_forum: Motor Accident Claims Tribunal of the District constituted under Section 165 MV Act, having jurisdiction per Section 166(2)
typical_parties: Claimants (legal representatives of deceased / injured-self) + Owner + Insurer of the offending vehicle (driver may be impleaded for completeness; for Section 164 the focus is owner / insurer)
statutory_opening: "This Claim Petition is filed under Section 164 of the Motor Vehicles Act 1988 (as inserted by the Motor Vehicles (Amendment) Act 2019, with effect from 1 April 2022), invoking the structured-formula lump-sum compensation scheme of ₹5,00,000 for death / ₹2,50,000 for grievous hurt (verify current notification) against the Owner and Insurer of the offending vehicle bearing Registration No. [Vehicle-Reg-Placeholder] for the accident dated [Date-of-Accident-Placeholder] at [Place-of-Accident-Placeholder]. The Claimants expressly elect under Section 165(4) of the said Act for the structured Section 164 scheme in lieu of the open-ended fault-based scheme under Section 166, and acknowledge that the present election forecloses the higher Section 166 quantum."
negligence_grounds:
  - "No-fault scheme — the Claimants invoke the structured-formula lump-sum under Section 164 without proof of negligence on the part of the driver of the offending vehicle; the use of a motor vehicle for the accident is the sole jurisdictional fact, in accordance with Section 164."
  - "Use of motor vehicle established — the accident arose out of the use of the offending vehicle bearing Registration No. ___, as evidenced by the FIR (Exhibit ___) and the registration certificate (Exhibit ___)."
  - "Insurer's statutory liability — the Insurer is liable under Section 147 of the Motor Vehicles Act 1988 read with the policy (Exhibit ___) for the Section 164 lump-sum compensation."
quantum_grounds_framework: "fixed lump-sum — ₹5,00,000 for death / ₹2,50,000 for grievous hurt per the Section 164 framework and current notification under the said section. No multiplier method. No future-prospects. No conventional-heads computation. The Drafter pleads the fixed quantum directly and notes that the election forecloses Section 166 quantum."
prayer_clauses:
  - "(a) Award the structured-formula lump-sum compensation of ₹5,00,000 (Rupees Five Lakhs only) / ₹2,50,000 (Rupees Two Lakhs and Fifty Thousand only) (verify current notification) to the Claimants under Section 164 of the Motor Vehicles Act 1988;"
  - "(b) Direct the Insurer (Respondent No. ___) to satisfy the said lump-sum within the period prescribed in the award;"
  - "(c) Award interest at ___% per annum from the date of filing till realisation;"
  - "(d) Award costs of the proceedings;"
mandatory_exhibits:
  - fir_copy
  - death_certificate_or_permanent_disability_certificate
  - registration_certificate_of_offending_vehicle
  - insurance_policy_of_offending_vehicle
  - relationship_or_legal_heir_certificate
  - medico_legal_certificate_for_grievous_hurt
accompanying_applications:
  - "I.A. for interim compensation pending final award"
  - "I.A. for urgent listing where the Claimants are in immediate financial distress"
court_fee: "Per the State Court-Fees Act for Section 164 lump-sum petitions — typically the same nominal slab as Section 166 petitions; pull from state-config.md."
limitation_note: "Section 166(3) three-year limitation was repealed by the Motor Vehicles (Amendment) Act 1994 — no limitation bar for the Section 164 lump-sum claim arising from a post-1994 accident. The Section 164 lump-sum scheme is a post-2019 insertion; cases pre-1 April 2022 fall under the erstwhile Section 163A no-fault scheme (now repealed) and require pleading under the saved provisions per the General Clauses Act 1897."
```

## Election-foreclosure note

The election under Section 164 forecloses the open-ended fault-based quantum under Section 166. The Drafter pleads the election expressly and records that the Claimants understand the foreclosure. This pre-empts any insurer-side argument that the Claimants attempted to keep both options open.

## Section 163A → Section 164 transition note

The old Section 163A (structured-formula no-fault scheme, with the Second Schedule operating directly) was OMITTED by the Motor Vehicles (Amendment) Act 2019, replaced by the simpler Section 164 fixed-lump-sum framework. The Verifier flags any pleading that wrongly cites Section 163A for a post-2019 accident.

## Statute-currency check (Verifier surface)

- Section 163A reference → flag as obsolete for post-2019 accidents
- Pre-2019 hit-and-run quantum reference (₹25,000 / ₹12,500) → flag as obsolete; current Section 161 Solatium Fund quantum is higher (verify notification)
- Old Workmen's Compensation Act reference → flag as obsolete; correct name is Employees' Compensation Act 1923

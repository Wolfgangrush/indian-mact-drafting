---
name: mact-petition-third-party-insurance-section-147-draft
description: Draft a Section 166 Claim Petition before the MACT with focused pleading of the insurer's statutory third-party-insurance liability under Section 147 of the Motor Vehicles Act 1988 (compulsory cover) read with Section 149 (rights of third parties + statutory defences available to insurer). Pre-empts the standard Section 149 defences — no policy / lapsed policy / unauthorised use / unlicensed driver / breach of policy condition / gratuitous passenger — and invokes the pay-and-recover doctrine per National Insurance v. Swaran Singh (2004) 3 SCC 297. Encodes the named-driver / paid-driver / hire-or-reward considerations and the pleading discipline for goods-carriage and passenger-vehicle policies. Auto-fires on "draft third-party insurance MACT petition", "draft Section 147 MV Act petition", "draft insurer-liability MACT claim".
allowed-tools: Read, Write, Edit, Bash, Glob
---

# MACT Third-Party Insurance / Section 147 Claim Petition Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: CLAIM PETITION UNDER SECTION 166 READ WITH SECTIONS 147 AND 149 OF THE MOTOR VEHICLES ACT 1988 (THIRD-PARTY INSURANCE LIABILITY FOCUS)
case_short_code: MACT_147
case_number_prefix: M.A.C.P.   # Per state-config — same prefix as Section 166
pleading_type: Claim Petition (insurer-liability focused)
typical_forum: MACT of the District per Section 166(2)
typical_parties: Claimants + Driver + Owner + Insurer of the offending vehicle (Insurer is the central respondent in this case-type framing)
statutory_opening: "This Claim Petition is filed under Section 166 of the Motor Vehicles Act 1988 read with Sections 147 and 149 of the said Act, seeking compensation for the death / injury caused by the rash and negligent driving of the offending vehicle bearing Registration No. [Vehicle-Reg-Placeholder] on [Date-of-Accident-Placeholder], and invoking the statutory third-party-insurance liability of the Insurer (Respondent No. ___) under the policy bearing No. [Policy-No.-Placeholder] valid from [Policy-Start-Placeholder] to [Policy-End-Placeholder]."
negligence_grounds:
  - "Rash and negligent driving — as established in the FIR + charge-sheet + post-mortem report + medico-legal certificate + witness statements."
  - "Insurance policy in force on date of accident — policy bearing No. ___ issued by the Insurer was valid on the date of the accident and covers the offending vehicle for third-party risks under Section 147 MV Act."
  - "Use of vehicle within policy terms — the offending vehicle was used on date of accident for the purpose permitted by the policy (private use / commercial use / hire-or-reward / goods-carriage / passenger-vehicle / agricultural-tractor — as the case may be)."
  - "Driver-licence compliance — the driver of the offending vehicle held a valid and effective driving licence as on date of accident, authorising the driver to operate the class of vehicle involved; the licence (Exhibit ___) was issued by [Issuing-Authority] and was valid from ___ to ___; the Section 149(2)(a)(ii) statutory defence is pre-empted."
  - "Permit / fitness compliance (for commercial vehicles) — the offending vehicle had a valid permit (Exhibit ___) and a valid fitness certificate (Exhibit ___) as on date of accident; the Section 149(2)(a)(i) statutory defence is pre-empted."
  - "Pay-and-recover doctrine — even if any minor breach of policy condition were to be established, the Insurer remains primarily liable to the Claimants as third-party beneficiaries under Section 149 MV Act read with National Insurance v. Swaran Singh (2004) 3 SCC 297; the Insurer's remedy lies in recovery from the Owner, not in denial to the Claimants."
quantum_grounds_framework: "stepwise Sarla Verma + Pranay Sethi — same framework as Section 166 fault-based; the insurer-liability focus is on the GROUNDS framework, not the QUANTUM framework"
prayer_clauses:
  - "(a) Award just and adequate compensation of ₹___ to the Claimants jointly with interest at ___% per annum from the date of filing till realisation;"
  - "(b) Direct the Insurer (Respondent No. ___) to satisfy the said award in the first instance, with right of recovery against the Owner / Driver only where the policy expressly authorises recovery and the conditions of recovery are made out at the Tribunal's satisfaction;"
  - "(c) Award costs of the proceedings;"
mandatory_exhibits:
  - fir_copy
  - charge_sheet_or_final_report
  - post_mortem_report_or_medico_legal_certificate
  - hospital_records_and_discharge_summary
  - death_certificate_or_permanent_disability_certificate
  - salary_certificate_or_income_proof
  - registration_certificate_of_offending_vehicle
  - insurance_policy_of_offending_vehicle_with_schedule_of_coverage
  - driver_licence_of_offending_driver
  - permit_and_fitness_certificate_for_commercial_vehicle
  - relationship_or_legal_heir_certificate
accompanying_applications:
  - "I.A. for production of insurance policy by the Insurer (where the Claimants do not have a copy)"
  - "I.A. for interim compensation pending final award"
court_fee: "Per the State Court-Fees Act — same as Section 166 petition; pull from state-config.md."
limitation_note: "No limitation bar (Section 166(3) repealed for post-1994 accidents)."
```

## Section 149 defences anticipated

The Drafter pre-empts the Section 149(2) defences:

- **Section 149(2)(a)(i)** — vehicle used in breach of permit / fitness conditions. Pre-empted by pleading valid permit + fitness as on date of accident.
- **Section 149(2)(a)(ii)** — driver did not hold an effective driving licence. Pre-empted by pleading valid licence as on date of accident.
- **Section 149(2)(a)(iii)** — vehicle used for a purpose not permitted by the policy. Pre-empted by pleading use within policy terms.
- **Section 149(2)(b)** — material misrepresentation in the policy. Pre-empted by pleading good-faith policy procurement.

## Gratuitous passenger / goods-carriage considerations

- For **goods-carriage** vehicles, a gratuitous passenger (a person riding in the goods carriage who is not the owner of the goods being carried) is not covered under the standard third-party policy — see *New India Assurance v. Asha Rani* (2003) 2 SCC 223. The Drafter must plead the status of the deceased / injured (owner of goods / paid driver / authorised cleaner / loader / gratuitous passenger) and the consequence for insurer-liability.
- For **passenger** vehicles (taxi / auto-rickshaw / bus), the passenger is covered under the standard third-party policy.
- For **private cars** used for hire, the breach of the "private-use only" policy condition surfaces a Section 149(2)(a)(iii) defence — to be pre-empted by pleading no hire-or-reward as on date of accident.

## Pay-and-recover doctrine

Per *National Insurance Co. v. Swaran Singh* (2004) 3 SCC 297 (three-judge bench), even where the Insurer establishes a breach of policy condition (no licence / no permit / wrong use), the Insurer remains primarily liable to the third-party claimant. The Insurer's remedy is recovery from the Owner under the recovery clause of the policy or under Section 149(4) MV Act. The Drafter incorporates this doctrine in the GROUNDS framework.

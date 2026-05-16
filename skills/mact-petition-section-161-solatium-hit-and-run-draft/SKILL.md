---
name: mact-petition-section-161-solatium-hit-and-run-draft
description: Draft a Claim Petition under Section 161 of the Motor Vehicles Act 1988 (read with the Solatium Scheme notified by the Central Government, as amended post-2019) for compensation from the Solatium Fund for a hit-and-run accident — accident caused by an unidentified / untraced / unidentifiable motor vehicle. Encodes the Solatium Fund administration framework, the post-2019 quantum revision (verify current notification — typically ₹2,00,000 for death and ₹50,000 for grievous hurt), the FIR + police-investigation registration requirement, and the role of the Claims Enquiry Officer / authority designated under the Solatium Scheme. Auto-fires on "draft hit-and-run solatium claim", "draft Section 161 MV Act claim", "draft solatium fund claim", "draft hit and run motor accident".
allowed-tools: Read, Write, Edit, Bash, Glob
---

# MACT Section 161 Solatium Fund / Hit-and-Run Claim Petition Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: CLAIM PETITION UNDER SECTION 161 OF THE MOTOR VEHICLES ACT 1988 (SOLATIUM FUND — HIT-AND-RUN)
case_short_code: MACT_161
case_number_prefix: M.A.C.P.   # Same prefix as Section 166 in most States; pull from state-config.md
pleading_type: Claim Petition (Solatium Fund)
typical_forum: Motor Accident Claims Tribunal of the District (or the Claims Enquiry Officer designated under the Solatium Scheme — verify per State's current notification); the petition is filed in the Tribunal having territorial jurisdiction over the place of accident or the Claimants' residence per Section 166(2)
typical_parties: Claimants (legal representatives of deceased / injured-self) + General Insurance Council / designated administering authority of the Solatium Fund (typically the General Insurance Corporation of India or its nominee per the Solatium Scheme) + State Transport Authority of the State where the accident occurred (where the Scheme so requires)
statutory_opening: "This Claim Petition is filed under Section 161 of the Motor Vehicles Act 1988 read with the Solatium Scheme notified by the Central Government under the said section (as amended post-2019), claiming compensation from the Solatium Fund for the hit-and-run accident dated [Date-of-Accident-Placeholder] at [Place-of-Accident-Placeholder], caused by an unidentified motor vehicle whose driver fled the scene of the accident without being identified, as recorded in FIR No. [FIR-No.-Placeholder] dated [FIR-Date-Placeholder] registered at [Police-Station-Placeholder]."
negligence_grounds:
  - "Hit-and-run accident — the offending vehicle was unidentified / untraced / unidentifiable; the driver fled the scene without being identified; the FIR (Exhibit ___) records the hit-and-run particulars."
  - "Police investigation conclusion — the final report of the police investigation (Exhibit ___) records that the offending vehicle could not be traced despite due investigation; in the alternative, the investigation is closed as undetected (Form A)."
  - "Use of motor vehicle established — the accident occurred by the use of a motor vehicle (as defined under Section 2(28) of the MV Act 1988), as evidenced by the injury-pattern in the post-mortem report / medico-legal certificate (Exhibit ___) and the on-scene observations recorded in the FIR (Exhibit ___) and the rough sketch (Exhibit ___)."
  - "Conditions for Solatium Fund relief satisfied — the accident occurred on a public road / a place to which the public has access; the death / grievous hurt arose out of the accident; the offending vehicle remains unidentified despite police investigation; the Claimants have not received compensation from any other source for this accident."
quantum_grounds_framework: "fixed lump-sum per the current Solatium Scheme notification — typically ₹2,00,000 for death and ₹50,000 for grievous hurt (verify against latest notification before drafting; the pre-2019 quantum was ₹25,000 / ₹12,500 and has been revised post-amendment). No multiplier method. No Pranay Sethi conventional heads. The Drafter pleads the fixed quantum directly."
prayer_clauses:
  - "(a) Award the Solatium Fund compensation of ₹___ (Rupees ___ only) to the Claimants under Section 161 of the Motor Vehicles Act 1988 read with the Solatium Scheme;"
  - "(b) Direct the General Insurance Council / the designated administering authority of the Solatium Fund to satisfy the said compensation within the period prescribed in the Scheme;"
  - "(c) Award interest at ___% per annum from the date of filing till realisation, in accordance with the Solatium Scheme;"
  - "(d) Award costs of the proceedings;"
mandatory_exhibits:
  - fir_copy_recording_hit_and_run
  - final_report_or_undetected_closure_of_police_investigation
  - post_mortem_report_or_medico_legal_certificate
  - hospital_records_and_discharge_summary
  - death_certificate_or_grievous_hurt_certificate
  - relationship_or_legal_heir_certificate
  - rough_sketch_of_accident_site
  - statement_of_non_receipt_of_compensation_from_other_source
accompanying_applications:
  - "I.A. for urgent listing where the Claimants are in immediate financial distress"
  - "I.A. for issue of notice to the General Insurance Council / designated administering authority"
court_fee: "Per the State Court-Fees Act — typically the same nominal slab as a Section 166 petition; pull from state-config.md."
limitation_note: "No limitation bar (Section 166(3) repealed). The Solatium Scheme may prescribe its own time-window for application before the designated authority — verify against the current Scheme notification."
```

## Solatium Scheme administration note

The Solatium Fund is administered by the General Insurance Council under the Solatium Scheme notified by the Central Government under Section 161 MV Act. The scheme prescribes the application form, the verification by the Claims Enquiry Officer, and the disbursement mechanism. The post-2019 amendment to Section 161 has increased the quantum substantially over the pre-2019 figures; the Drafter pulls the current notification figure from `laws/solatium-scheme-notification.pdf` (user-supplied) and applies it. Verify before filing — Solatium Scheme notifications are revised from time to time.

## Statute-currency check (Verifier surface)

- Pre-2019 quantum reference (₹25,000 death / ₹12,500 grievous hurt) → flag as obsolete; pull current quantum from user-supplied Solatium Scheme notification
- Old "Section 161 and Section 163" framework reference (pre-amendment hit-and-run was administered partly under Section 161 + erstwhile provisions) → flag as obsolete; consolidated post-2019 under revised Section 161

## Cross-references

- Where the offending vehicle is identified during pendency of the Section 161 petition, the petition may be amended to a Section 166 / Section 164 petition; the Solatium Fund award (if already received) is set off against the eventual Section 166 / 164 award.

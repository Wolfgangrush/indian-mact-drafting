---
name: motor-vehicle-criminal-defence-bnss-draft
description: Draft defence pleadings in a rash / negligent-driving prosecution arising from a motor-vehicle accident, under the Bharatiya Nyaya Sanhita 2023 (Section 281 rash driving — successor to IPC 279; Section 282 endangering personal safety by negligence — successor to IPC 336; Section 283 obstructing public way — successor to IPC 283; Section 106 causing death by negligence — successor to IPC 304A) and the Bharatiya Nagarik Suraksha Sanhita 2023 (procedural framework — bail / charge / trial / sentence). Also engages the cognate MV Act offences (Sections 184 driving dangerously, 185 drunken driving, 186 unfit driving, 187 offences relating to accidents, 188 — 190 vehicle-condition offences). Encodes bail application, discharge / quashing application, written statement to charge, trial defence strategy, and sentence-mitigation submissions. Auto-fires on "draft BNSS rash driving defence", "draft Section 281 BNS defence", "draft Section 106 BNS defence", "draft motor accident criminal defence".
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Motor-Vehicle Criminal Defence (BNSS 2023) Draft Skill

Extends: `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
Common rules: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`

## Case-type metadata

```yaml
case_type_line: DEFENCE IN PROSECUTION UNDER SECTIONS 281 / 282 / 283 / 106 OF THE BHARATIYA NYAYA SANHITA 2023 READ WITH SECTIONS 184 / 185 / 187 OF THE MOTOR VEHICLES ACT 1988
case_short_code: MV_CRIM_DEFENCE
case_number_prefix: R.C.C.   # "R.C.C." / "C.C." / "S.T." per State Magistrate / Sessions Court convention; varies per offence-seriousness
pleading_type: Defence (multi-stage — bail / discharge / WS to charge / trial defence / sentence-mitigation)
typical_forum: Court of the Judicial Magistrate First Class (where the offence is triable by Magistrate) OR Court of Sessions (for the contested second sub-section of BNS Section 106 where it has been notified and engaged); for offences against the State per the BNSS schedule of triability
typical_parties: State / Complainant + Accused (driver of the offending vehicle); the Owner is typically not made an accused in driver-rash-driving cases unless owner's vicarious-criminal-liability is specifically engaged
statutory_opening: "The Accused is charged under Section 281 / Section 282 / Section 283 / Section 106 of the Bharatiya Nyaya Sanhita 2023 read with Section 184 / Section 185 / Section 187 of the Motor Vehicles Act 1988, in connection with the alleged motor-vehicle accident dated [Date-of-Accident-Placeholder] at [Place-of-Accident-Placeholder] (FIR No. [FIR-No.-Placeholder] of Police Station [Police-Station-Placeholder])."
defence_grounds:
  - "FIR registration delay — the FIR was registered ___ hours / days after the alleged accident, casting doubt on the prosecution's narrative of identification of the offending vehicle / driver."
  - "Eye-witness contradiction with rough-sketch and post-mortem — the witness statements contradict the rough-sketch of the accident site and the injury-pattern in the post-mortem / medico-legal certificate; the prosecution's narrative is inconsistent with the physical evidence."
  - "Mechanical-inspection report inconsistent with alleged manner of accident — the mechanical inspection (Exhibit ___) shows the brakes / tyres / steering of the offending vehicle to have been in working condition / shows damage-pattern inconsistent with the alleged speed and direction."
  - "Driver's licence + permit + fitness in order — the Accused held a valid and effective driving licence; the offending vehicle had valid permit and fitness; this defeats any per-se-negligence inference under MV Act Sections 184 / 187."
  - "Alternative cause established — the post-mortem / medico-legal report is consistent with an alternative cause (sudden medical event of the deceased / pre-existing condition / contributory negligence of the deceased / third-party interference); the chain of causation is broken."
  - "Charge-framing defects — the charge mis-describes the section / mis-describes the accused / mis-describes the date / mis-describes the place; the Accused is entitled to discharge under the BNSS provision corresponding to CrPC Section 227 / 239."
  - "No prima-facie case — on the materials placed before the Court at the stage of charge, no prima-facie case under the cited sections is made out; the Accused is entitled to discharge."
prayer_clauses:
  - "Bail Application stage — (a) Grant regular bail to the Accused on such terms and conditions as this Court may deem fit; (b) Direct release on bail forthwith;"
  - "Discharge stage — (a) Discharge the Accused on the ground that no offence under BNS Sections 281 / 282 / 283 / 106 is made out on the materials before this Court; (b) Drop further proceedings;"
  - "Trial stage — (a) Acquit the Accused after full trial on the ground that the prosecution has failed to prove the offence beyond reasonable doubt; (b) Award costs against the prosecution where the charge is found to be vexatious;"
  - "Sentence-mitigation stage — (a) Impose minimum sentence having regard to the Accused's clean antecedents, family responsibilities, advanced age, lack of motive; (b) Grant probation under the Probation of Offenders Act 1958 / suspend sentence under BNSS provision corresponding to CrPC Section 360;"
mandatory_exhibits:
  - fir_copy
  - charge_sheet_or_final_report
  - rough_sketch_of_accident_site
  - mechanical_inspection_report_of_offending_vehicle
  - driving_licence_of_accused_driver
  - registration_certificate_permit_fitness_of_offending_vehicle
  - post_mortem_report_or_medico_legal_certificate
  - eye_witness_statements_recorded_under_section_corresponding_to_crpc_161
  - any_alternative_cause_evidence
accompanying_applications:
  - "Bail Application (regular / anticipatory per stage)"
  - "Application for discharge under BNSS section corresponding to CrPC 227 / 239"
  - "Application for return of seized vehicle on supratnama / bond"
  - "Application for quashing of FIR / charge-sheet under BNSS section corresponding to CrPC 482 (= BNSS 528) before the High Court — separate pleading"
court_fee: "Nominal process / vakalat fee per local Magistrate court schedule."
limitation_note: "BNSS prescribes limitation per the sections corresponding to CrPC 467 — 473 (verify current BNSS numbering). For offences punishable with imprisonment not exceeding 3 years, limitation is typically 3 years; for offences punishable with imprisonment exceeding 3 years, no limitation."
```

## Statutory-currency check (critical for this skill)

The Verifier flags the IPC → BNS transition rigorously:

| IPC 1860 reference | BNS 2023 corresponding section |
|---|---|
| Section 279 (rash driving on public way) | Section 281 |
| Section 304A (causing death by negligence) | Section 106 |
| Section 336 (endangering personal safety by negligence) | Section 282 |
| Section 337 (causing hurt by negligence) | verify current BNS numbering |
| Section 338 (causing grievous hurt by negligence) | verify current BNS numbering |
| Section 283 (obstructing public way) | Section 283 (numbering retained) |

Note on Section 106 BNS: the contested sub-section relating to hit-and-run liability of the driver who fails to report the accident has been the subject of post-enactment notifications and operational deferral. The Drafter / Verifier should verify the current operative form before pleading or before raising a defence on its applicability.

## Procedural-currency check

- CrPC 1973 references → BNSS 2023 corresponding sections (verify section-by-section: 227 / 239 discharge, 360 probation, 482 inherent power → 528, 161 statements → corresponding BNSS section, 200 complaint → 223, 313 examination → corresponding section)
- IEA 1872 references → BSA 2023 corresponding sections (Section 65B → 63 for electronic-record / dash-cam / CCTV admissibility)

## Cognate MV Act offences

For motor-accident prosecutions, the cognate MV Act offences often run alongside the BNS charges:

- **Section 184** — driving dangerously (max 6 months / ₹1,000)
- **Section 185** — driving under influence of drink / drugs (max 6 months / ₹2,000; enhanced for repeat)
- **Section 186** — driving when mentally or physically unfit (max ₹200)
- **Section 187** — offences relating to accidents (failure to report accident / failure to stop) (max 3 months / ₹500)
- **Section 188** — abetment of certain offences
- **Section 189** — racing and trials of speed
- **Section 190** — using vehicle in unsafe condition / emitting smoke / excessive noise / etc.

The Drafter pleads the defence to each cognate MV Act offence separately where engaged.

## Cross-reference to MACT compensation proceeding

The criminal trial and the MACT compensation proceeding are independent. An acquittal in the criminal trial does NOT bar a successful MACT compensation claim (the MACT applies a balance-of-probabilities standard whereas the criminal trial applies beyond-reasonable-doubt). The Drafter notes this distinction in the trial strategy.

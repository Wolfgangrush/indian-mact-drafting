# state-config — Maharashtra (indian-mact-drafting)

**Validation depth:** Researched · awaiting Registry-acceptance validation.

```yaml
state: "Maharashtra"
local_language_of_pleadings: "English (Marathi permitted in select MACTs per Section 137 CPC State amendment and Maharashtra Civil Manual practice)"
bar_council: "Bar Council of Maharashtra and Goa"

mact_case_number_prefix: "M.A.C.P."           # Standard across Maharashtra MACTs (Mumbai · Pune · Nagpur · Aurangabad · Nashik · Kolhapur · Wardha · Bhandara · etc.)
mact_appeal_prefix_high_court: "First Appeal"  # Section 173 appeals are filed as "First Appeal" before the Bombay HC and its Benches (Nagpur · Aurangabad · Goa)

state_court_fees_act: |
  Bombay Court-Fees Act 1959 (as amended) — Maharashtra MACT petitions are subject to a nominal slab; verify against the latest notification under the Act
mact_court_fee_special_provision: |
  Under the Bombay Court-Fees Act and Maharashtra Government notifications, MACT petitions attract a nominal slab fee; in some categories (claimants below poverty line; widows; minor claimants) full exemption may be claimed on application

state_motor_vehicles_rules: "Maharashtra Motor Vehicles Rules 1989"
state_mv_rules_tabular_particulars_schedule_reference: "Schedule per the Maharashtra MV Rules — 22-item table aligned to Form 54 CMVR 1989 with State extensions (RTO-jurisdiction of registration · Maharashtra State Road Transport Corporation status where applicable · permit-area particulars)"

state_stamp_act: "Maharashtra Stamp Act 1958"

state_revenue_recovery_act: "Maharashtra Land Revenue Code 1966"

tabular_particulars_schedule: |
  Standard Maharashtra MACT Tabular Particulars block (22 items):

  1.  Name and address of claimant(s) with relationship to deceased / injured
  2.  Age of claimant(s)
  3.  Occupation of claimant(s)
  4.  Name, age, occupation, and monthly income of deceased / injured
  5.  Date, time, and place of accident
  6.  Name and address of driver of offending vehicle
  7.  Name and address of owner of offending vehicle
  8.  Registration number, make, model, year of offending vehicle
  9.  Insurer's name and address; policy number; period of validity
  10. RTO of registration; permit-area (for commercial vehicles)
  11. FIR number, date, and Police Station
  12. Charge-sheet / final report status
  13. Brief description of the accident
  14. Nature and extent of injury / death particulars
  15. Period of hospitalisation; treating hospital(s)
  16. Permanent disability percentage (where applicable)
  17. Documentary basis for income (salary certificate / ITR / business proof)
  18. Number of dependants and their relationship
  19. Compensation claimed — head-wise break-up (loss of dependency / consortium / conventional heads / special damages)
  20. Total compensation claimed
  21. Interest claimed (% per annum from date of)
  22. Court fee paid + any application for exemption

vakalatnama_format: |
  Bar Council of Maharashtra and Goa standard vakalatnama; ₹5 advocate-attached stamp; client signature + advocate signature

exhibit_prefix: "EXHIBIT-"
exhibit_prefix_alternative: "ANNEXURE-"        # Both accepted in different MACTs

paper_size: A4
font_family: "Times New Roman"
font_size_body: 14
line_spacing: 1.5

notes: |
  Maharashtra Civil Manual permits English-language pleadings as the default at MACT level. Marathi pleadings accepted under Section 137 CPC State amendment in MACTs where Marathi is the principal language of business (typically interior districts — Wardha, Yavatmal, Chandrapur, Gadchiroli). Mumbai MACT and Pune MACT typically operate in English only.

  Bombay HC Nagpur Bench Section 173 First Appeals: filed in the High Court Registry at Nagpur; appeal court fee per Bombay Court-Fees Act Schedule I; Section 173(2) deposit by insurer / owner = ₹25,000 or 50% of award, whichever is less; deposit-challan annexed to appeal memo.

  Pre-litigation Lok Adalat conciliation under MV Act and Legal Services Authorities Act 1987 is increasingly used by Maharashtra insurers (national and state PSU insurers) for fast-track settlement; the advocate may consider conciliation pre-MACT-filing for liquidated and uncontested cases.
```

# state-config-template.md (indian-mact-drafting)

This is a **template**. Copy this file into your case folder, rename to `state-config.md`, and fill in the values for your specific State / Union Territory. The plugin's Format and Drafter agents read this file at run-time alongside the case-type SKILL templates to render motor-accident-claim pleadings in your State's idiom.

**Do not edit this template in the plugin folder.** Always work on a copy inside your case folder. Validated State exemplars are in `state-config/exemplars/` — copy the right one for your State, then customise per your specific MACT district (Nagpur MACT vs Mumbai MACT vs Pune MACT, etc.).

The State configuration matters acutely for MACT pleadings because:

- The Tabular Particulars block in a Section 166 / 164 / 161 petition varies significantly by State — each State's Motor Vehicles Rules carry their own schedule (the Form 54 Central MV Rules 1989 is the common base, with State extensions adding 4 — 6 items)
- The case-number prefix varies (M.A.C.P. in Maharashtra; M.V.C. in Karnataka; M.C.O.P. / O.P. (M.V.) in Tamil Nadu; M.A.C. in Kerala; MAC App. in Delhi; etc.)
- The Court-Fees Act varies (Bombay 1959; Karnataka 1958; Tamil Nadu 1955; Kerala 1959; AP 1956; Punjab 1932; Court-Fees Act 1870 with State amendments; etc.)
- The State MV Rules carry State-specific procedural variations (filing-counter conventions; annexure prefixes; index format; verification format)

---

## Section 1 — State / UT identification

```yaml
state: "Maharashtra"                          # Your practice State / UT
local_language_of_pleadings: "English"        # Most MACTs: English. Some accept regional language per State practice
bar_council: "Bar Council of Maharashtra and Goa"
```

## Section 2 — MACT case-numbering convention

```yaml
mact_case_number_prefix: "M.A.C.P."           # Per State convention — varies as listed below
mact_case_number_prefix_alternatives:
  - "M.V.C."                                   # Karnataka
  - "M.C.O.P."                                 # Tamil Nadu
  - "O.P. (M.V.)"                              # Tamil Nadu alternative
  - "M.A.C."                                   # Kerala
  - "MAC App."                                 # Delhi
  - "M.A.C.T. No."                             # Pan-India generic
```

## Section 3 — Court-Fees Act

```yaml
state_court_fees_act: |
  Bombay Court-Fees Act, 1959                  # Maharashtra; also Gujarat
                                               # Karnataka Court-Fees and Suits Valuation Act 1958
                                               # Tamil Nadu Court-Fees and Suits Valuation Act 1955
                                               # Kerala Court-Fees and Suits Valuation Act 1959
                                               # AP Court-Fees and Suits Valuation Act 1956 (AP/TG)
                                               # West Bengal Court-Fees Act 1971
                                               # Court-Fees Act 1870 (Central — Delhi/UP/MP/Bihar/some others with State amendments)
                                               # Rajasthan Court-Fees and Suits Valuation Act 1961
mact_court_fee_special_provision: |
  Some States provide total exemption from court fee for MACT petitions; some provide a nominal slab. Verify against the State's current notification under the State Court-Fees Act.
```

## Section 4 — State Motor Vehicles Rules

```yaml
state_motor_vehicles_rules: "Maharashtra Motor Vehicles Rules 1989 (as amended)"
state_mv_rules_tabular_particulars_schedule_reference: "Schedule / Form per the State MV Rules — to be pulled verbatim into the format-shell"
```

## Section 5 — State Stamp Act

```yaml
state_stamp_act: "Maharashtra Stamp Act 1958"  # Or "Indian Stamp Act 1899 as amended by [State]"
```

## Section 6 — State Revenue Recovery framework (for Section 174 Collector route)

```yaml
state_revenue_recovery_act: "Maharashtra Land Revenue Code 1966"
                                               # Karnataka Land Revenue Act 1964
                                               # Tamil Nadu Revenue Recovery Act 1864
                                               # AP Revenue Recovery Act 1864 (AP/TG)
                                               # Kerala Revenue Recovery Act 1968
                                               # West Bengal Revenue Recovery Act per State practice
                                               # UP Zamindari Abolition + Revenue Recovery framework
                                               # Each State has its own framework
```

## Section 7 — Tabular Particulars schedule (the critical State-variable for MACT)

```yaml
tabular_particulars_schedule: |
  The 22-to-24-item Tabular Particulars block per the State MV Rules / Form 54 CMVR 1989, to be pulled VERBATIM into the format-shell. Items vary significantly by State — see anomalies log on Phase 03 work. The advocate must verify the current State schedule before filing.

  (Pull from State MV Rules; common base aligned to Form 54 CMVR 1989 + 4 — 6 State-specific items.)
```

## Section 8 — Vakalatnama

```yaml
vakalatnama_format: |
  Standard advocate vakalatnama per State Bar Council; signed by claimant + advocate; stamped per State Stamp Schedule.
state_specific_vakalatnama_notes: |
  Maharashtra: Bar Council of Maharashtra and Goa standard vakalatnama with ₹5 advocate-attached stamp
  Tamil Nadu: Bar Council of Tamil Nadu and Puducherry standard
  Karnataka: Bar Council of Karnataka standard
  Each State Bar Council publishes its own vakalatnama template
```

## Section 9 — Exhibit / Annexure marker convention

```yaml
exhibit_prefix: "EXHIBIT-"                    # Common pan-India default
exhibit_prefix_alternatives:
  - "ANNEXURE-A"                              # Some State practices use ANNEXURE prefix
  - "Doc. No. 1"                              # Some State Civil Manuals prefer Doc. No.
```

## Section 10 — Language and paper

```yaml
paper_size: A4
font_family: "Times New Roman"
font_size_body: 14                            # Or 12 per some State Civil Manuals
line_spacing: 1.5
```

## Section 11 — State-specific procedural quirks

```yaml
notes: |
  (List any State-specific quirks that affect MACT drafting — e.g., Maharashtra Marathi-language permission in some MACTs; UP Hindi requirement in some MACTs; Tamil Nadu Tamil-language acceptance under Section 137 CPC State amendment; some States have a specialised Lok Adalat for MACT pre-litigation conciliation; etc.)
```

---

## How to use this file

1. Pick the right State exemplar from `state-config/exemplars/` (8 major State exemplars provided; 20 stubs await community contribution).
2. Copy to your case folder: `cp state-config/exemplars/<your-state>.md <case-folder>/state-config.md`
3. Customise the values per your specific MACT (Nagpur vs Mumbai vs Pune vs other district MACTs).
4. The plugin's Format and Drafter agents read this file alongside the case-type SKILL to render in your State's idiom.

## Contributing state-config exemplars

Advocates practising in States not yet exemplified are invited to submit filled exemplars via GitHub Issue. Each State exemplar that lands in the public folder benefits every advocate in that State. Particularly valuable: the verbatim Tabular Particulars schedule from the State MV Rules.

Do NOT include any case-specific information — only the State's standard procedural conventions.

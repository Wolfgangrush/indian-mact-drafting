---
name: format
description: Second agent in the Indian MACT drafting pipeline. Loads the case-type-specific skill template (RSH / the user names the case type — the agent does NOT classify). Reads the user's case-config.md and state-config.md and pre-substitutes forum name, Member designation, registry filing requirements, court-fee article, claim head, state-specific tabular-particulars schedule, and limitation-clock anchor into a format-shell ready for the Drafter. Outputs format-shell.md.
allowed-tools: Read, Write, Edit, Bash, Glob
---

# Format Agent (MACT pipeline)

Second in the 6-agent Indian MACT drafting pipeline. References: `${CLAUDE_PLUGIN_ROOT}/skills/_drafting_common/SKILL.md`, `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`, the named case-type skill at `${CLAUDE_PLUGIN_ROOT}/skills/<case-type>-draft/SKILL.md`, and the State exemplar in `${CLAUDE_PLUGIN_ROOT}/state-config/exemplars/<state>.md`.

## Job

Take the universal MACT-pleading skeleton + the case-type-specific extensions + the user's `case-config.md` + `state-config.md`, produce a `format-shell.md` that already has all forum / court-fee / state-specific tabular-particulars / limitation values pre-substituted. The Drafter then writes the actual content; it never has to look up forum-level or state-level data.

## Inputs

- `<case-folder>/case-facts.md` (from Reader)
- `<case-folder>/case-config.md`
- `<case-folder>/state-config.md`
- `${CLAUDE_PLUGIN_ROOT}/skills/_mact_drafting_base/SKILL.md`
- `${CLAUDE_PLUGIN_ROOT}/skills/<case-type>-draft/SKILL.md`

## Outputs

Single file: `<case-folder>/format-shell.md`

## Behaviour

1. **Resolve forum** — pull Tribunal / Court / Authority name verbatim from `case-config.md`. Use the correct nomenclature:
   - MACT (Section 166 / 164 / 161 / 147 / interim) — *"BEFORE THE MOTOR ACCIDENT CLAIMS TRIBUNAL, [District]"* (e.g. *"MOTOR ACCIDENT CLAIMS TRIBUNAL, NAGPUR"*)
   - High Court (Section 173 appeal) — *"IN THE HIGH COURT OF JUDICATURE AT [Seat], [Bench]"* (e.g. *"HIGH COURT OF JUDICATURE AT BOMBAY, NAGPUR BENCH"*)
   - Magistrate (BNSS criminal defence — rash / negligent driving) — *"BEFORE THE COURT OF THE [Judicial Magistrate First Class / Chief Judicial Magistrate / Sessions Judge], [Place]"*
   - Commissioner (EC Act 1923) — *"BEFORE THE COMMISSIONER UNDER THE EMPLOYEES' COMPENSATION ACT 1923, [Place]"*
   - Collector (Section 174) — *"BEFORE THE COLLECTOR OF THE DISTRICT, [District]"*
   - Execution Court (MACT award execution under Order 21 CPC) — *"IN THE COURT OF THE [Designation], [Place] — execution of MACT award dated ___"*
2. **Resolve case-numbering convention** — use the bench's case-number prefix (e.g. *"M.A.C.P. No. ____ of 2026"* for Maharashtra MACT; *"M.V.C. No. ____ of 2026"* for Karnataka; *"M.A.C.T. No. ____ of 2026"* / *"O.P. (M.V.) No. ____ of 2026"* per State; *"First Appeal No. ____ of 2026"* for Section 173 HC appeal; *"R.C.C. No. ____ of 2026"* for BNSS Magistrate case; *"EC Case No. ____ of 2026"* for EC Act).
3. **Resolve court-fee** — apply the correct fee schedule:
   - MACT — court fee per the State Court-Fees Act (typically a nominal slab tied to compensation claimed; some States grant total exemption for MACT petitions — see state-config)
   - HC Section 173 appeal — appeal court fee per the State Court-Fees Act
   - BNSS Magistrate — process fee per local Magistrate court schedule
   - EC Act — fee per the EC Act Rules
   - Collector recovery — nominal application fee per State revenue rules
4. **Resolve statutory opening** — load the case-type's statutory opening text from the case-type skill.
5. **Resolve State-specific Tabular Particulars schedule** — pull the State's tabular-particulars schedule from `state-config.md` (the format of the 24-item particulars table varies significantly by State — see the anomalies log; for Maharashtra and several other States, the table is built on the lines of Form 54 of the Central Motor Vehicles Rules 1989; for some States, the State MV Rules carry their own schedule).
6. **Resolve limitation anchor** — write the limitation paragraph:
   - For Section 166 / 164 / 161 / 147 petitions — note that Section 166(3) three-year limitation was repealed by the Motor Vehicles (Amendment) Act 1994; no limitation bar for post-1994 accidents
   - For Section 173 HC appeal — 90 days from the date of award (Section 173(1) proviso — extendable on sufficient cause)
   - For Section 174 Collector recovery — within the period prescribed in the award + Section 174 statutory window
   - For EC Act 1923 claim — within two years of the accident or two years of the disease's first manifestation (Section 10 EC Act)
   - For BNSS Magistrate prosecution — limitation per BNSS Section corresponding to CrPC Sections 467 — 473 (verify current BNSS numbering)
7. **Resolve verification + affidavit nomenclature** — *"Solemnly affirmed on oath"* + BSA 2023 reference for perjury.
8. **Pre-substitute placeholders** into the format-shell from `case-config.md` (forum name, Member designation, claim head, multiplier-table inputs — age at death, monthly income, dependants).
9. **Hand off to Drafter** — `format-shell.md` is now ready; the Drafter writes the actual content into it.

## Anti-classification rule

The Format agent does NOT classify the case. The user / the orchestrator names the case-type via the trigger phrase (e.g. *"draft MACT 166 petition"* / *"draft hit-and-run solatium claim"* / *"draft Section 173 MV Act appeal"*). Misclassification by the user produces a wrong-shape draft — that is acceptable; classification is the user's professional call, not the plugin's.

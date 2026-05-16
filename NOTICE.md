# NOTICE — Provenance and Privilege Statement

This document is part of the public release of the `indian-mact-drafting` plugin (v0.1.0-alpha and onwards). It declares the provenance of the plugin's content, in order to address any question about advocate-client privilege, client confidentiality, professional ethics, personal-data protection, victim-and-survivor sensitivity, and commercial confidentiality that may be raised by any reader, complainant, regulator, or Bar Council disciplinary authority.

The plugin is **case-config-aware and state-config-aware**: the universal structural skeleton of any Indian motor-accident-claim or motor-vehicle-litigation pleading is uniform, and the parties' chosen forum (Motor Accident Claims Tribunal of the territorial district, High Court for Section 173 appeal, Magistrate Court for the rash / negligent-driving criminal trial under BNSS 2023, Collector of the District for Section 174 recovery), accident-trigger date, claimant composition (deceased's legal representatives / injured claimant / property-damage claimant), vehicle particulars, FIR particulars, insurer particulars, multiplier-table inputs (deceased age + monthly income + dependants), and State Motor Vehicles Rules variations are supplied by the user via `case-config.md` and `state-config.md` files in the case folder.

This NOTICE is published in plain language so that any reader — practising advocate, judge, Bar Council officer, regulator, member of the public, fellow developer — can understand the position without ambiguity.

---

## 1. What this plugin contains

This plugin contains the following categories of content, and **only** the following categories of content:

(a) **Universal MACT-pleading skeleton** — the structural shape of any Indian motor-accident-claim or motor-vehicle-litigation pleading (Cause Title with correct forum nomenclature, Parties block, Statutory Opening invoking the operative section of the Motor Vehicles Act 1988 as amended 2019, Tabular Particulars block per the State Motor Vehicles Rules / Form 54 of the Central Motor Vehicles Rules 1989, Description of the Accident, Grounds, Prayer, Verification, Affidavit-in-support, Index, List of Documents, accompanying applications).

(b) **Formatting conventions** — text-formatting conventions for pleadings before the Motor Accident Claims Tribunals (constituted under Section 165 of the Motor Vehicles Act 1988), the High Courts exercising Section 173 appellate jurisdiction, Magistrate Courts exercising criminal jurisdiction under BNSS 2023 over rash / negligent driving offences, the Commissioner under the Employees' Compensation Act 1923, and the Collector under Section 174 of the Motor Vehicles Act 1988.

(c) **Statutory references** — citations to public statutes (Motor Vehicles Act 1988 as amended by the Motor Vehicles (Amendment) Act 2019, Central Motor Vehicles Rules 1989, State Motor Vehicles Rules, Employees' Compensation Act 1923, Bharatiya Nyaya Sanhita 2023, Bharatiya Nagarik Suraksha Sanhita 2023, Bharatiya Sakshya Adhiniyam 2023, Insurance Act 1938, Code of Civil Procedure 1908, Limitation Act 1963, Fatal Accidents Act 1855, applicable State Court-Fees Acts, applicable State Stamp Acts).

(d) **Procedural rule references** — citations to public rules (Central Motor Vehicles Rules 1989, State Motor Vehicles Rules, applicable Motor Accident Claims Tribunal Rules per State, IRDAI regulations on motor third-party insurance, Solatium Scheme notifications issued under Section 161 of the Motor Vehicles Act 1988, the Detailed Accident Report (DAR) framework introduced by the Supreme Court in *Jai Prakash v. National Insurance Co. Ltd.* (2010) 2 SCC 607 and refined in subsequent practice directions).

(e) **Generic placeholders** — every variable in every template is a placeholder (`[Claimant-1]`, `[Claimant-2]`, `[Deceased]`, `[Injured-Claimant]`, `[Driver]`, `[Owner]`, `[Insurer]`, `[Vehicle-Registration-No.]`, `[Policy-No.]`, `[FIR-No.]`, `[Date-of-Accident]`, `[Place-of-Accident]`, `[Hospital]`, `[Medical-Bill-Total]`, `[Monthly-Income]`, `[Age-at-Death]`, `[Number-of-Dependants]`). No placeholder is filled with any specific claimant, deceased, driver, owner, insurer, vehicle, policy, FIR number, hospital, medical figure, or any other identifying information.

(f) **Anti-hallucination and privacy-firewall workflow** — six agents (Reader, Format, Drafter, Verifier, Refiner, Overseer) that operate on a case folder supplied by the user. The plugin itself contains no case folder. The Reader substitutes every party name, every vehicle registration number, every policy number, every FIR number, every hospital name, every medical-bill figure, and every authorised-signatory name with structural placeholders before downstream AI processing.

---

## 2. What this plugin does NOT contain

This plugin does **not** contain any of the following, and has never contained any of the following at any point in any committed version:

(a) **No specific client matter or motor-accident case.** No client of the author, and no specific motor-vehicle accident, claim, defence, or appeal handled by the author or any client, appears in the plugin — by name, by FIR number, by vehicle registration, by policy number, by injury description, by deceased's identity, by claimant identity, by hospital name, by award amount, or by any other identifying signature.

(b) **No client communications.** No oral or written communication made to the author by or on behalf of any client (whether a claimant, an injured person, a deceased's legal representative, a driver, an owner, an insurer, or any other party) appears in the plugin in any form.

(c) **No client documents.** No document or instrument with which the author has become acquainted in the course of professional employment as an advocate appears in the plugin, in original, in redacted, in summary, in extract, or in pattern. This includes — but is not limited to — FIRs, charge-sheets, post-mortem reports, medico-legal certificates, hospital records, discharge summaries, salary certificates, income-tax returns, driving licences, vehicle registration certificates, fitness certificates, permits, insurance policies, cover notes, claim petitions, written statements, depositions, awards, or appeal memoranda of any specific accident.

(d) **No personal data of any data principal.** The plugin processes no personal data, collects no personal data, stores no personal data. The personal data of accident victims, deceased persons, injured claimants, and bereaved dependants is **acutely sensitive** and the plugin's privacy firewall is calibrated for that sensitivity.

(e) **No specific medico-legal certificate, no specific post-mortem report, no specific salary certificate, no specific insurance policy** of any specific accident handled by the author or any other advocate.

(f) **No client list, no panel-counsel list of any insurance company, no chamber list, no associate list, no opposing-counsel list, no Member-specific intelligence of any Motor Accident Claims Tribunal.**

(g) **No tracking, no telemetry, no analytics, no opt-in error reporting, no login, no account, no cloud sync.** The plugin runs entirely on the user's machine. The author receives no information about who installs the plugin, who uses it, on what cases, with what consideration, with what outcomes.

---

## 3. The legal distinction

Indian law has long recognised a clear distinction between two categories:

(i) **Specific client communications and documents** — protected under Section 132 of the Bharatiya Sakshya Adhiniyam 2023 (formerly Section 126 of the Indian Evidence Act 1872) and under Rule 17 of the Bar Council of India Standards of Professional Conduct and Etiquette. This category is privileged and confidential.

(ii) **General professional knowledge of motor-vehicle accident law, MACT procedure, multiplier doctrine, third-party-insurance liability, and pleading craft** — an advocate's accumulated knowledge of how a Section 166 Claim Petition is structured, how the Sarla Verma multiplier table is applied (*Sarla Verma v. Delhi Transport Corporation* (2009) 6 SCC 121), how the *National Insurance Co. Ltd. v. Pranay Sethi* (2017) 16 SCC 680 constitution-bench reform on future prospects operates, what Section 147 of the Motor Vehicles Act 1988 prescribes for compulsory third-party insurance, what the Section 168 award structure must contain, how the post-2019 Section 164 lump-sum scheme operates in place of the old Section 163A, how the Section 161 Solatium Scheme operates for hit-and-run cases, how a Section 173 appeal to the High Court is structured. This category is the advocate's own professional knowledge. It is not the property of any specific client. It is not privileged.

This plugin operates **entirely within category (ii)**.

Every Indian advocate practising in motor-accident litigation accumulates this knowledge through years of practice, through study of the standard commentaries (Justice S.K. Sarvaria, Kishan Vij, Bhandari, R.K. Bangia on Law of Torts as applied to motor-accident liability), the IRDAI regulations on motor third-party insurance, the steady jurisprudence of the Supreme Court and the High Courts on contributory negligence, composite negligence, no-fault liability, the Sarla Verma multiplier, the Pranay Sethi future-prospects reform, the deductions for personal and living expenses, the conventional heads (loss of consortium, loss of estate, loss of love and affection, funeral expenses, transportation), and the *Magma General Insurance v. Nanu Ram* (2018) line on filial consortium. The plugin codifies that accumulated procedural knowledge into machine-readable form. It does not codify any client's confidential information.

The plugin is, in this respect, identical in legal character to a published motor-accident-law textbook, a continuing legal education handout, or a senior advocate's drafting-style lecture. The medium is software. The content is procedural knowledge.

---

## 4. The author's professional position

The author is **Rushikesh R. Mahajan**, Advocate, enrolled with the Bar Council of Maharashtra and Goa, practising before the Bombay High Court, Nagpur Bench. The plugin is published under the open-source brand **Wolfgang Rush**, which is the author's publishing handle for legal-technology infrastructure; the real-identity accountability declared in this section attaches to the author personally and is not displaced by the use of a publishing handle.

The author retains full enrolment, full responsibility, and full liability under the Advocates Act 1961, the Bar Council of India Rules, and the Standards of Professional Conduct and Etiquette.

The plugin is published as a personal contribution to the open-source legal-technology ecosystem. It is published without any commercial channel, without any solicitation of professional work, without any advertisement of professional services, and without any acceptance of work through this repository.

This NOTICE is filed of record in this open-source repository so that any person who reads, reviews, audits, or assesses this plugin has full transparency about its provenance and its scope from the moment of release.

---

## 5. Verification of clean provenance

The repository owner shall maintain, on a private offline record, a build log demonstrating that every line of every file in the plugin was either:

(a) authored from scratch as procedural skeleton, OR
(b) derived from public statute, public rule, public judgment, or public motor-accident-law textbook, OR
(c) derived from the author's own original procedural knowledge as a practitioner.

No line of any file was, at any stage, copied from, paraphrased from, summarised from, or pattern-matched against any specific client matter, motor-accident case, client communication, or client document.

This NOTICE is the author's signed declaration of that position.

---

## 6. Reporting concerns

If any reader, regulator, fellow advocate, or member of the public believes any specific content in this plugin is derived from a specific client matter or specific confidential communication, the reader is requested to:

(a) identify the file and line at issue in the plugin,
(b) identify the specific client matter or communication believed to be the source,
(c) explain the basis of the belief,

and raise the concern via a GitHub Issue on this repository.

Concerns raised with these particulars will be investigated and the file or line will be removed or rewritten if the concern is well-founded. Concerns raised without these particulars cannot be acted upon.

---

## 7. Standing instruction to forks and derivatives

Any fork, derivative, downstream redistribution, or commercial integration of this plugin or its content shall preserve this NOTICE in unmodified form, and shall extend the same provenance discipline to any content added in the fork or derivative.

This NOTICE travels with the code under the same MIT licence that governs the source.

---

*Signed and dated by way of public commit history on the repository. The author stands by every line of this notice.*

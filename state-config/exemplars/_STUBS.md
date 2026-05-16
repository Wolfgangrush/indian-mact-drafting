# Stub State / UT exemplars — community contribution welcomed

The 8 exemplars in this folder (Maharashtra · Karnataka · Tamil Nadu · Kerala · Delhi · Uttar Pradesh · West Bengal · Gujarat) provide a starting point for the major MACT-volume jurisdictions. Of these, only **Maharashtra is deep-validated by the author's direct practice**; the other 7 are researched-not-validated and await community confirmation.

The following States and Union Territories are **stub-states** for v0.1.0-alpha — no exemplar file is shipped, and community contribution is invited via GitHub Issue / Pull Request. To contribute a State exemplar, copy `state-config/state-config-template.md`, fill in the values for the State, and submit a PR (or open an Issue with the filled YAML for the maintainer to commit).

## Stub States / UTs (v0.1.0-alpha)

1. Andhra Pradesh
2. Telangana
3. Bihar
4. Jharkhand
5. Madhya Pradesh
6. Chhattisgarh
7. Rajasthan
8. Odisha
9. Punjab
10. Haryana
11. Himachal Pradesh
12. Uttarakhand
13. Goa
14. Assam
15. Meghalaya
16. Manipur
17. Mizoram
18. Nagaland
19. Tripura
20. Arunachal Pradesh
21. Sikkim
22. Jammu and Kashmir (UT)
23. Ladakh (UT)
24. Chandigarh (UT)
25. Puducherry (UT)
26. Andaman and Nicobar Islands (UT)
27. Lakshadweep (UT)
28. Dadra and Nagar Haveli and Daman and Diu (UT)

(28 stubs — totalling 36 State / UT exemplars when complete; the 8 shipped + 28 stub = full coverage of the Indian Union)

## What a stub means in practice

If your State is in the stub list, **the plugin still works** — you can use the `state-config/state-config-template.md` directly, copy it to your case folder as `state-config.md`, and fill in the State-specific values yourself. The Format and Drafter agents will pull from your custom values. The plugin's procedural skeletons are State-agnostic; only the State-specific extensions (case-number prefix, Court-Fees Act, MV Rules schedule, Stamp Act, Revenue Recovery Act, Tabular Particulars items, vakalatnama format, language) require State data.

The stub-marker is the maintainer's signal that the State has not been researched at exemplar depth — not that the State is unsupported.

## Why the anomalies-log warning matters here

Per the Phase 03 anomalies log on the India-Legal Corpus pipeline: *"Motor Vehicle Claims: Tabular particulars for Personal Injuries vary significantly by state-specific Motor Vehicle Rules."*

This is why the state-config layer exists. The 22-to-24-item Tabular Particulars block in a Section 166 / 164 / 161 petition is the most State-variable part of the entire MACT pleading. Without a State exemplar, the user must verify the State's MV Rules schedule against the State's own MV Rules text and against bench practice at the local MACT — typically a 30-minute exercise the first time.

## Contributing

To contribute a State exemplar, open a GitHub Issue with the title "State exemplar: [State Name]" and the filled YAML body. Particularly valuable: the verbatim Tabular Particulars schedule from the State's MV Rules + any State-specific procedural quirks at the MACT filing counter + the case-number prefix convention used in the State.

Do NOT include any case-specific information — only the State's standard procedural conventions.

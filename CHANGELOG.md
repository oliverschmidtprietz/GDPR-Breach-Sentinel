# Changelog — breach-sentinel

All notable changes to this skill are documented here.

Format: `## [vX.Y] — YYYY-MM-DD`

---

## [v3.2] — 2026-07-21

Digital Omnibus instrument-citation correction. Legal-accuracy patch; no change to breach method, thresholds or templates.

- **`references/strategic-advisory.md` — wrong instrument corrected.** The Digital Omnibus proposal was cited as *COM(2025) 833 final*. The Digital Omnibus package of 19 November 2025 is **COM(2025) 836** (Digital Omnibus on AI, 2025/0359(COD)), **COM(2025) 837** (Digital Omnibus Regulation — data, privacy and cybersecurity, 2025/0360(COD), carrying the GDPR amendments in **Article 3**) and **COM(2025) 838** (European Business Wallets). **No Commission proposal bears the number COM(2025) 833** — EUR-Lex has no `52025PC0833`. The regulatory-horizon note now cites COM(2025) 837 final, procedure 2025/0360(COD), with the GDPR amendments pinpointed to Article 3, plus an instrument note recording the correction and the primary-source URL.
- **Substance unaffected.** The proposed 72h → 96h Art. 33(1) window and the "high risk" reporting threshold were described correctly; only the document identifier was wrong.
- Verified 2026-07-21 against EUR-Lex (CELEX 52025PC0837) and the European Parliament Legislative Train entry for the digital package; corroborated by `data-subject-rights/sources/verification-log.md` §4.1.

**Status:** reviewed (carried from v3.1).

---

## [v3.1] — 2026-07-07

AI Act Art. 73 date re-sync (Omnibus) + canonical name normalization.

- `SKILL.md` Art. 73 check (step 4) and `parallel-regimes.md`: Annex I product-embedded high-risk date corrected to **2 Aug 2028** (was pre-Omnibus 2 Aug 2027); Annex III postponement to **2 Dec 2027** now stated; both now cite the EU-AI-Act-Suite canonical timeline file as the date source.
- Frontmatter `name:` normalized to **breach-sentinel** (was the lawve.ai slug `gdpr-breach-sentinel-oliver-schmidt-prietz` — the slug is applied at lawve package time, per the pattern used by all sibling skills); `evals/evals.json` skill_name aligned. Sibling cross-references (e.g. privacy-notice-eu) already used `breach-sentinel`.

---

## [v3.0] — 2026-06-11

EDPB-template-aligned evidence file + AI Act correction + legal-threshold hardening. Triggered by the EDPB's adoption of the *Template [2026] for personal data breach notification* (v1.0, plenary 10 June 2026, public consultation until 5 August 2026) and an external legal review of v2.3.

**Legal corrections (publication blockers fixed):**

- **AI Act Art. 62 → Art. 73.** All serious-incident references corrected from the 2021 proposal numbering to the final Regulation (EU) 2024/1689: reporting by providers of high-risk AI systems to the market surveillance authority of the Member State where the incident occurred; deadlines ≤15 days (≤2 days widespread/critical-infrastructure, ≤10 days death); incomplete-then-complete reports allowed; full Art. 3(49) serious-incident definition; applicability from 2 Aug 2026 (Annex I product-embedded: 2 Aug 2027) now stated. Fixed across SKILL.md, README.md, web-research.md, evals, and the product page.
- **ENISA score reframed as decision support.** Score→notification tables renamed to "Presumptive action (subject to Art. 33/34 legal test)"; new mandatory **Legal Bridge** block (score → facts → safeguards → likely impact → Art. 33(1)/34(1) conclusions) in every assessment, with a worked example (`enisa-methodology.md` §4a) and bridge sub-blocks in the Internal Compliance Log and Non-Notification Justification templates.
- **Processor track corrected.** Removed the erroneous "statutory 72h from T0" instruction for processors. Track B now: notify controller **without undue delay** (Art. 33(2)); DPA windows are contractual on top; no direct SA notification; controller deemed aware **when the processor informs it** (Guidelines 9/2022); controller 72h shown as downstream duty only. Track B output spec, hybrid dashboard, and processor notice template aligned; new Processor → Controller Handoff Package.

**New modules:**

- **EDPB Breach Evidence File** (`references/edpb-template-evidence-file.md`): full field map of the Template [2026] (all 7 sections, 126 fields incl. incident taxonomy, conditional logic, attachments inventory), assessment→field mapping table, fill rules (`[UNKNOWN — investigate]` / `[N/A]`), draft-status banner. Verified against the published DOCX.
- **Breach Qualification Gate**: incident-vs-personal-data-breach triage (Art. 4(12)) before intake, with four verdicts; emergency intake gains the triage question as Q0.
- **Art. 34 Decision Module** (`references/art34-communication.md`): high-risk test, all three Art. 34(3) exceptions — (b) subsequent measures and (c) disproportionate effort → public communication were previously uncovered — content requirements, communication strategy, SA backstop (Art. 34(4)), decision memo.
- **Sectoral Parallel-Regime Screen** (`references/parallel-regimes.md`): AI Act Art. 73 in depth + NIS2 (cross-link to `nis2-navigator`), DORA, eIDAS, ePrivacy, criminal, insurance, contractual, works council. Identify-only by default.
- **Confidentiality & Input Hygiene guardrail** at session start; **Evidence Posture block** (facts / assumptions / unknowns / confidence / impact) in every assessment.

**Hardening:**

- Cross-border: one-stop-shop requires genuine cross-border processing (Art. 4(23)) and EU main establishment; non-EU controllers notify every concerned SA (Guidelines 9/2022 v2.0 para 73); no inference from multi-state subject residence alone.
- Web research: source-discipline rules (official sources first, no SEO basis for legal conclusions, access dates, never invent portal links); Germany SA routing moved here.
- EDPB cases: analogy warning (illustrative, not binding; misdirected email only analogised to postal cases — differences must be stated).
- Templates: 8 new (follow-up, withdrawal, late-notification explanation, processor handoff package, Art. 34 decision memo, attachment inventory, country-by-country table, other-authority log) → 17 total.
- Evals: 8 → 13 cases, 73 → 132 assertions (new: Art. 73 death-case deadlines; processor 72h trap; evidence-file completeness; Art. 34(3)(b)/(c); triage gate). Spot-checked, no full benchmark.
- Structure: decision trees and borderline table moved into `enisa-methodology.md`; SKILL.md restructured (~570 lines).

**Status:** reviewed (carried from v2.3; spot-check verification this release).

---

## [v2.3] — 2026-05-31

Regulatory-horizon watch-note (no change to operative guidance).

- **Digital Omnibus (PROPOSED).** `references/strategic-advisory.md` gains a clearly-fenced "Regulatory horizon" section flagging the Commission's Digital Omnibus (COM(2025) 833 final, 19 Nov 2025) breach-notification proposals: Art. 33(1) deadline 72h → 96h, SA-notification threshold raised to "high risk", and a single ENISA-maintained EU reporting entry point. EDPB/EDPS support the change (Joint Opinion 2/2026, 11 Feb 2026). Flagged not-in-force — the 72-hour clock and current thresholds remain operative.

**Status:** reviewed (carried from v2.2).

---

## [v2.2] — 2026-03-12

- Structural refactor: SKILL.md trimmed 670 -> 493 lines by extracting strategic advisory, mitigation playbook, post-notification tracking, and web research to reference files
- Eval infrastructure added: 8 test cases, 73 assertions
- Eval grading tightened: numeric ENISA values, labeled flags, arithmetic consistency checks, 72h clock calculations

## [v2.1] — 2026-02-09

- DPC score capping (bounds enforcement)
- Fast Path expanded to 11 data points
- Emergency Mode DPA deadline question
- Multi-select breach types
- UK GDPR nuances
- "Under Investigation" pathway
- Sub-processor chain guidance
- Two-stage T0 analysis
- Docx skill fallback
- Quick decision tree
- Improved web research queries

## [v2.0] — 2026-02-07

- Fast Path intake
- Strategic Advisory
- Flexible mitigation playbooks
- Dynamic web research
- SA contact lookup
- AI Act integration
- DPA deadline tracking
- .docx generation
- Post-notification tracking
- Borderline score analysis

## [v1.0] — 2026-01-01

- Initial release: ENISA severity assessment, EDPB case matching, document templates

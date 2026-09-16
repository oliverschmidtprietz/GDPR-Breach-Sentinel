# Changelog — breach-sentinel

All notable changes to this skill are documented here.

Format: `## [vX.Y] — YYYY-MM-DD`

---

## [v3.5] — 2026-09-15

Two fixes from external review (2026-09-08) and portfolio-wide intake alignment, both confirmed/ruled by the author 2026-09-15.

- **Finding 8 — UK territorial scope corrected.** The routing table's `🇬🇧 UK SUBJECTS` row treated "UK residents affected" as sufficient to trigger a separate ICO notification. It is not: UK GDPR Art. 3 applies where the controller/processor is established in the UK (Art. 3(1)), or offers goods/services to people in the UK, or monitors their behaviour in the UK (Art. 3(2)) — not on the mere residence or nationality of an affected individual (a UK resident buying from a Germany-only shop is outside scope; a UK-based visitor being monitored there can be inside it). Renamed the flag to `🇬🇧 UK GDPR APPLICABILITY`, rewrote its trigger to the Art. 3 test, and added a **UK Territorial-Scope Check** (three yes/no questions on establishment, goods/services offered in the UK, and behaviour monitored in the UK) that runs before any ICO-notification conclusion. All three "No" → no ICO duty even with UK residents affected, and that reasoning must be recorded, not silently dropped. A UK-established controller notifies both its EU lead/competent SA and the ICO — the UK sits outside the one-stop-shop. Updated the UK GDPR Note and Critical Reminder #11 to match. No UK/ICO-specific eval existed to correct.
- **Portfolio-wide intake addition — free-text/special-category screen.** Added a 12th intake data point (Guided Mode question 12; Fast Path now extracts 12 data points, up from 11) asking what free-text/unstructured inputs the affected system held, whether any control (not merely a policy) actually caught special-category content in them, and whether such content has been observed. New rule: if such channels accepted subject/staff input and no control caught sensitive content, treat the compromised free text as potentially containing special-category data for the Art. 33/34 risk assessment (feeds the DPC score as if Art. 9 data were present) and note observed frequency. Updated `evals/evals.json` eval 4's assertion, which hard-coded "all 11 data points" — its fast-path prompt enumerates only structured CRM fields, so the corrected assertion now expects 11 of 12 to be extracted directly and the 12th (Free-Text/Special-Category Screen) to be asked for.

**Status:** unreviewed. Drift check run: `grep -rn '3\.4' skills/breach-sentinel/ | grep -v CHANGELOG.md` and `grep -rn 'v3\.4\|UK residents' docs/portfolio/generate.py docs/portfolio/skill_pages/breach-sentinel.py` — no stragglers found (see handoff note).

---

## [v3.4] — 2026-08-21

Corrects a stale "ongoing public consultation" framing for the EDPB *Template [2026]* found in the portfolio audit (`AUDIT-2026-08-19.md`, CF-10, CF-11) — the consultation window closed 5 August 2026, and the skill was still asserting it as a present-tense ongoing status in multiple places with no caveat attached at the point of the claim.

- **CF-10:** Reworded every occurrence of the "DRAFT — public consultation until 5 Aug 2026" framing (SKILL.md Critical Reminders, the Version & Regulatory Basis table, the Document Generation section, README.md's feature bullet, feature table, and Regulatory Basis table, and both flagged spots in `references/edpb-template-evidence-file.md`, including the generated-document provenance stamp text) to state plainly: the public consultation window closed 5 August 2026, final adoption status has not yet been re-verified, check the EDPB site before relying on the template, and national SA portals remain authoritative. The caveat is now attached locally at each occurrence, not only in one table.
- **CF-11:** Applied the same wording correction to `docs/portfolio/skill_pages/breach-sentinel.py`'s Regulatory Basis entry for the EDPB Template [2026], which previously carried the stale claim with no refresh instruction at all. The generated `index.html` itself is regenerated from this source in a later step, not hand-patched here.

**Status:** documentation/wording correction only — no change to the qualification gate, ENISA scoring, Art. 33/34 bridge, deadlines, or document generation logic.

---

## [v3.3] — 2026-07-25

Routes Article 32 security-of-processing work to the `toms-art32` skill. Part of the coordinated **sibling-routing pass** (`ropa` v2.15, `dpia-sentinel` v1.11, `dpa-art28` v1.2, `breach-sentinel` v3.3, `tia` v1.3) that closes the toms-art32 portfolio-integration gate recorded as Finding 1 in `docs/projects/gdpr-skills-marathon/ROADMAP-2026-07-25.md`. Routing pointers only — no Article 32 methodology is duplicated into any sibling.

- **New "Article 32 handoff" subsection** under the Mitigation Playbook. Containment and the Art. 33(3)(d) / Art. 34(3)(b) description of measures taken or proposed stay here; the standing security posture — whether the pre-incident measures were appropriate, which controls change permanently, who owns them, what evidence and retest they need, how the TOM annex to controllers/customers is updated — goes to `toms-art32` (post-incident mode).
- **Two handover rules.** (1) Never conclude the pre-incident measures were inadequate merely because the breach occurred — Art. 32 requires measures appropriate to the risk, not measures that guarantee no incident; that reassessment is made on the measures' own merits by `toms-art32`. (2) Hand over only what the Evidence Posture marks as established fact; assumptions and unknowns travel labelled as such.

**Status:** reviewed (carried from v3.2) — routing/documentation only; no change to the qualification gate, ENISA scoring, Art. 33/34 bridge, deadlines or document generation.

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

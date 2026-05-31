# Changelog — breach-sentinel

All notable changes to this skill are documented here.

Format: `## [vX.Y] — YYYY-MM-DD`

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

# Dynamic Web Research Module

After completing the ENISA calculation and EDPB case matching, **automatically** perform targeted web research to enrich the assessment. Use web_search to find:

## Research Queries (run these in sequence, using specific case details)

Construct targeted queries using the specific details of the breach. Generic queries yield generic results — specificity is key.

1. **Recent enforcement:** Search for `"[specific SA name]" breach fine [specific data category] [year]` — e.g., `"BayLDA" breach fine health data 2025` rather than just `GDPR breach notification fine`. If the sector is known, include it: `"CNIL" fine [sector] data breach [year]`.
2. **SA-specific guidance:** Search for `"[specific SA name]" breach notification guidance requirements [year]` — e.g., `"LfDI Baden-Württemberg" breach notification requirements 2025`. Include the SA's local language name if relevant.
3. **Sector-specific precedent:** Search for `GDPR [specific sector] [specific data type] breach enforcement [year]` — e.g., `GDPR healthcare patient records breach enforcement 2025` rather than just `GDPR healthcare data breach enforcement`.
4. **EDPB updates:** Search for `EDPB guidelines data breach notification [year]` to check for any updates to guidance since the skill's reference documents were created.
5. **AI Act incidents** (if AI flag set): Search for `EU AI Act serious incident reporting Article 62 [year]` for latest implementation guidance.
6. **Damages precedent** (if subject notification likely): Search for `GDPR data breach damages claim [specific data type] [jurisdiction] [year]` — e.g., `GDPR health data breach damages claim Germany 2025` to inform the Strategic Advisory on litigation risk.

## How to Use Research Results

- **Enforcement precedents**: Reference relevant SA decisions to contextualize the risk level. Example: "The Spanish AEPD fined [Company] €X for a similar [breach type] in [year], highlighting that [specific factor] was considered an aggravating circumstance."
- **Updated guidance**: If EDPB has issued new guidelines or opinions since the reference documents, note them and explain how they might affect the assessment.
- **Sector trends**: Flag if the user's sector has been subject to heightened SA scrutiny recently.
- **Caveat all research**: Clearly label web-sourced information as supplementary context, not as the basis for the formal ENISA/EDPB assessment.

## Output Section
Add a "Regulatory Intelligence" section to the Assessment Dashboard summarizing key findings.

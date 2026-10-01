---
name: satno-tender-radar
description: Develop and operate SATNO Tender Radar workflows for Iranian tenders and inquiries. Use for WordPress plugin work, source normalization, tender scoring, deadline extraction, de-duplication, report generation, Bale delivery, and CRM queue integration.
---

# SATNO Tender Radar

## Primary objective
Identify actionable tender and inquiry opportunities relevant to SATNO and convert them into structured, readable, de-duplicated opportunities.

## Source priority
Treat the Iranian government's electronic procurement system as a primary source when applicable. Other aggregators may be added as supplemental sources but must not be assumed authoritative without verification.

## Geographic priority
1. Khuzestan
2. Chaharmahal and Bakhtiari
3. Ilam
4. Lorestan
5. Important nationwide opportunities

## Required opportunity fields
Where available extract and normalize:
- title
- organization
- province
- publication date
- deadline
- Need No / call number / tender identifier
- source URL
- category/topic
- importance score
- urgency
- deduplication key

## Scoring
Use transparent A/B/C classification based on subject relevance, geography, importance, and deadline urgency. Explain the factors rather than assigning unexplained labels.

## Output quality
- Normalize Persian/Gregorian dates consistently for the target report.
- Prefer structured table/card/PDF/Word output over dense plain text when practical.
- Keep the existing production sender intact until the replacement is installed, activated, and verified.
- Do not silently disable legacy production behavior.

## Integration
Prepare A/B opportunities for CRM intake with stable identifiers and enough metadata for follow-up.

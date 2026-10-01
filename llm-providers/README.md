# SATNO LLM Provider Bank

This directory tracks LLM API providers and discovery sources relevant to SATNO projects.

## Discovery source

### awesome-free-llm-apis
- Repository: `mnfst/awesome-free-llm-apis`
- License: CC0-1.0
- Purpose: discovery of providers with permanent free tiers
- Status: external reference, not trusted as authoritative for production terms
- Rule: always verify provider terms, quotas, privacy, and regional availability directly before production use

## Current SATNO shortlist

| Provider | Best use | Privacy note | SATNO fit |
|---|---|---|---|
| Groq | fast extraction/classification | verify current terms | Bale Market / Tender Radar |
| OpenRouter | model routing/fallback | provider/model terms vary | shared fallback layer |
| NVIDIA NIM | heavier reasoning / many models | verify model/provider terms | analysis / experiments |
| Cloudflare Workers AI | edge inference | account/project policy required | lightweight services |
| Mistral AI | text/code | free mode data terms must be reviewed | code/text experiments |
| Gemini | multimodal / large context | free-tier privacy and region rules matter | multimodal/public data |
| OVHcloud AI Endpoints | anonymous EU-hosted testing | low free rate | experiments only |
| Ollama Cloud / local Ollama | private/local-friendly architecture | local preferred for sensitive data | CRM/private workflows |

## Important
Free does not mean suitable for confidential data. Provider terms can change without notice.

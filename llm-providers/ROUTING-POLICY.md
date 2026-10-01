# SATNO LLM Routing Policy

## Default decision order

1. Determine privacy class: P0 / P1 / P2.
2. Determine task type.
3. Exclude providers that do not meet privacy requirements.
4. Filter by modality and context length.
5. Rank remaining providers by latency, reliability, cost, and quality.
6. Select primary and explicit fallback.
7. Record routing decision in observability metadata.

## Baseline routes

### Bale Market
- Extraction/classification: Groq
- Fallback: OpenRouter
- Heavy reasoning: NVIDIA NIM

### Tender Radar
- Extraction: Groq
- Scoring/explanation: OpenRouter or NVIDIA NIM
- Public data only unless explicitly reclassified

### SATNO CRM
- Customer, finance, staff, authentication data: P2
- Default: local Ollama or approved private/paid provider
- Free APIs: only for non-sensitive tooling/test/public-data tasks

### Voice Agent
- Keep STT, LLM, and TTS independently swappable
- Prefer low-latency provider
- Never lower privacy class during fallback

## Never
- log API keys
- log raw sensitive prompts by default
- send P2 data to free endpoints without explicit review
- assume a provider's free-tier terms are permanent

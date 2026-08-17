# ADR 0005 — Isolamento de PII

- Status: proposto; retenção bloqueia produção
- Decisão: minimizar e separar PII reversível, usar hashes normalizados para analytics e fornecer apenas agregados a externos.
- Consequência: queries operacionais autorizadas são separadas das analíticas; prazos dependem do DPO/jurídico.


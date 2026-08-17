# ADR 0004 — Conectores e jobs

- Status: proposto
- Decisão: portas/adaptadores, fila com entrega ao menos uma vez, consumidores idempotentes, cursor transacional, retry com jitter e DLQ.
- Consequência: mocks e produção compartilham contratos; efeitos duplicados devem ser impedidos também por constraints.


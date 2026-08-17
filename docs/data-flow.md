# Fluxo de dados

```mermaid
flowchart LR
  A[Scheduler/backfill] --> B[Fila]
  B --> C[Worker]
  C --> D[Resolver referência no cofre]
  C --> E[Buscar página incremental]
  E --> F[Validar schema e minimizar PII]
  F --> G[Normalizar]
  G --> H[Upsert transacional idempotente]
  H --> I[Atualizar cursor após commit]
  H --> J[Agregações e qualidade]
  J --> K[API com escopo + RLS]
  K --> L[Dashboards/exports]
  C --> M[sync_runs / sync_errors]
  F --> N[Rejeitados / DLQ]
```

## Garantias

- Entrega ao menos uma vez; efeitos exatamente uma vez são aproximados por constraints, chave de idempotência e transação.
- Cursores só avançam depois do commit dos dados correspondentes.
- Um lock lógico impede a mesma integração e janela de executar concorrentemente.
- Payload inválido não contamina tabelas normalizadas.
- Contagens de recebidos, processados, ignorados e rejeitados são persistidas.
- Backfills não substituem silenciosamente históricos e são auditados.

## Reconciliação

Valores de cada fonte são preservados. A fonte oficial do KPI é escolhida no dicionário; diferenças geram `data_quality_issues` e nunca são ajustadas automaticamente para coincidir.

